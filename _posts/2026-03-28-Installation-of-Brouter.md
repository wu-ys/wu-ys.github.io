---
layout: article
tag: tutorial
title: "Installation of BRouter on Linux"
mathjax: false
excerpt_type: html
---

## 1 BRouter是什么？

[BRouter](https://brouter.de/brouter/index.html) is a routing software, meaning it can calculate a route on a map and generate navigation instructions. It can run on a smartphone or on a personal computer or a server. <!--more-->

简单说，BRouter是一个依托开源地图OpenStreetMap进行自定义导航（更准确地说，是寻路）的软件，可以在 [brouter-web](https://brouter.de/brouter-web/) 在线使用。

与一般导航软件不同的是，它可以对OSM中任意类型的路径进行寻路，如公路、自行车道、人行道、水路、**铁路**等等；同时，它赋予了我们很高的寻路自由度——我们可以为各种类型的路径、节点设定不同的权重，以实现定制化需求的寻路。

本篇将讲述如何在linux端部署本地的BRouter应用，并下载相应的地图数据；这将使得我们可以离线使用BRouter应用，同时也能完成在线应用中不能实现的一些更为定制化的需求（如区分某些在在线应用中没有区分的OSM标签）

参考文献：

- [1] https://blog.devops.uber.space/2024/202405.html#build.rd5
- [2] https://blog.devops.uber.space/2024/202407.html
- [3] https://github.com/abrensch/brouter/blob/master/docs/developers/build_segments.md
- [4] https://phyks.me/2018/11/build-your-own-brouter-segments-files.html

## 2 安装BRouter前后端应用

### 2.1 Requirements

Ubuntu Linux系统（或wsl），主要依赖项为 java runtime environment（jre）：

```bash
# First, update the index of your package manager 
sudo apt update
# unzip
sudo apt install unzip
# Java
sudo apt install default-jre
# Python3, for running http.server
sudo apt install python3

# Not really necessary
# wget 
sudo apt install wget
# gedit, if a graphical text editor is preferred
sudo apt install gedit
# screen, for running programs in the background
sudo apt install screen
```

### 2.2 下载BRouter前后端程序

最简易的方法是下载官方release：[BRouter web releases page](https://github.com/nrenner/brouter-web/releases).

```bash
# create new directory called brouter-web
mkdir brouter-web
# change to new directory
cd brouter-web
# change url to the version you want to download
wget https://github.com/nrenner/brouter-web/releases/download/0.18.1/brouter-web-standalone.0.18.1.zip 
# unzip Brouter
unzip brouter-web-standalone.*.zip
# copy configuration
cp brouter-web/config.template.js brouter-web/config.js
```

### 2.3 编辑配置文件

如果使用自己的PC作为后端（使用本地主机localhost）的话，不需要修改这里的配置

如果想部署到网站上，则需要对`brouter-web/config.js`进行编辑，将localhost换为自己的域名（例如example.com）：

- 将 `BR.conf.host = 'http://localhost:17777';` 替换为 `BR.conf.host = 'http://example.com:17777';`
- 将 `BR.conf.profilesUrl = 'http://localhost:8000/profiles2/';` 替换为 `BR.conf.profilesUrl = 'http://example.com:8000/profiles2/';` 或 `BR.conf.profilesUrl = '../profiles2/';`

### 2.4 启动后端寻路引擎

`./standalone/server.sh &`

注意：这类方法下前后端的通信是不安全的，仅仅建议在localhost使用

### 2.5 启动前端网页

#### Unsecure web server

同样注意，前后端的通信是不安全的

利用python运行：``python3 -m http.server 7878`

#### Other webserver

You can also use a big web server like Apache or Nginx and let them restart if the server reboots, etc.

#### 在浏览器中查看

在浏览器打开`localhost:7878`，或利用命令打开：`firefox-esr http://example.com:7878/brouter-web`

### 2.6 一键管理前后端

按照上述方法启动前后端，需要使用`ps -u`寻找对应的进程号后手动终止进程，比较麻烦。可以使用`screen`一键管理：

```bash
#!/bin/bash

BACKEND_NAME="backend"
FRONTEND_NAME="frontend"

start() {
    echo "Starting services with screen..."

    # backend
    if screen -list | grep -q "$BACKEND_NAME"; then
        echo "Backend already running"
    else
        screen -dmS $BACKEND_NAME bash -c "bash ./standalone/server.sh"
        echo "Backend started"
    fi

    # frontend
    if screen -list | grep -q "$FRONTEND_NAME"; then
        echo "Frontend already running"
    else
        screen -dmS $FRONTEND_NAME bash -c "python -m http.server 7878"
        echo "Frontend started"
    fi
}

stop() {
    echo "Stopping services..."

    screen -S $BACKEND_NAME -X quit 2>/dev/null && echo "Backend stopped"
    screen -S $FRONTEND_NAME -X quit 2>/dev/null && echo "Frontend stopped"
}

status() {
    echo "Current screen sessions:"
    screen -ls
}

attach_backend() {
    screen -r $BACKEND_NAME
}

attach_frontend() {
    screen -r $FRONTEND_NAME
}

case "$1" in
    start) start ;;
    stop) stop ;;
    restart) stop; sleep 1; start ;;
    status) status ;;
    backend) attach_backend ;;
    frontend) attach_frontend ;;
    *)
        echo "Usage: $0 {start|stop|restart|status|backend|frontend}"
        ;;
esac
```

将这个文件命名为`service.sh`，之后只需要`bash service.sh start` `bash service.sh stop` 即可便捷启动/终止前后端服务。

当然到目前为止，在网页中尝试寻路时后端服务器将不会有响应，这是因为后端还没有加载地图数据——

## 3 下载地图数据，生成RD5文件

BRouter为了达成快速寻路的目标，会将osm地图数据进行一次预处理，以每个（经度5°×纬度5°）的地图方块为单位生成`.rd5`文件。所有在线应用使用的rd5文件都可以在这里找到：https://brouter.de/brouter/segments4/

- 例如，E120_N30.rd5就包含了东经120-125度，北纬30-35度范围内所有预处理后的数据

如果你的目标仅仅是在本地部署一个一样的BRouter应用，那么直接下载现成的rd5文件（只需要下载你感兴趣的区域内），将rd5文件存放至`brouter-web/segments4`目录下即可。

但如果你想要利用在线应用中不支持的osm标签作为寻路权重的依据的话，那么你就需要参考下面的教程，自己手动生成rd5文件了。

### 3.1 下载Brouter源代码

注意，这里应该使用与上面的前后端不同的目录，后者下载的是已经打包好的`brouter.jar`执行文件。

```bash
# assume current directory is ${PWD}
PWD=$(pwd)
mkdir brouter
cd brouter
git clone https://github.com/abrensch/brouter.git
cd brouter
```

检查java版本并编译；如果wsl系统中未安装java则需要安装。

```bash
java -version

# install java development kit if not existing, as we need to compile java
sudo apt install -y openjdk-17-jdk

# build may fail without '-x test'
# just ignore these tests
./gradlew clean build fatJar -x test
```

### 3.2 下载地图数据

打开[Geofabrik](https://download.geofabrik.de)，选择下载你所需要的地区的osm数据并移动到`misc/scripts/mapcreation`，或者使用命令下载。例如中国大陆：

```bash
cd misc/scripts/mapcreation/
wget --continue https://download.geofabrik.de/asia/china-latest.osm.pbf
```

根据[1]的方法，需要将下载的`.osm.pbf`文件更名为`planet-latest.osm.pbf`

```bash
mv *.osm.pbf planet-latest.osm.pbf
```

如果你下载了多个区域的`.osm.pbf`文件，则你需要将他们合并为一个文件；

```bash
sudo apt install osmium-tool
osmium merge *.pbf -o planet-latest.pbf
```

### 3.3 下载高程数据

* 这是选做步骤，如果你只想进行平面寻路而不关心高度变化，也能接受BRouter生成的gpx文件不带高程数据的话，完全可以跳过这一步

Brouter-web使用的高程数据来自于[CIGAR-SCI](https://csidotinfo.wordpress.com/data/srtm-90m-digital-elevation-database-v4-1/)，但是这个网站上的下载链接因为不明原因损坏了，只能使用 https://srtm.csi.cgiar.org/srtmdata/ 下载每5°×5°区域内的高程数据。

将下载的所有数据（.zip文件即可，不用解压缩）存放至`misc/srtm`文件夹中，之后执行（仍然在`misc/scripts/mapcreation/`目录下）：

```bash
mkdir ../../srtm_bef
java -Xmx2600m -Xms2600m -Xmn32m -cp ../../../brouter-server/build/libs/brouter-*-all.jar -Ddeletetmpfiles=false -DuseDenseMaps=true  btools.mapcreator.ElevationRasterTileConverter all ../../srtm/ ../../srtm_bef
```

将zip文件转换为bef文件，存放在`misc/srtm_bef`文件夹中。

### 3.4 生成RD5文件

我使用了[1]中提供的以下脚本，并进行了少量修改使其更为简洁：

```bash
#!/bin/bash
set -e
cd "$(dirname "$0")"

# set file current time as last changed field for the file lastmaprun.date
touch lastmaprun.date

## set variables
JAVA='java -Xmx2600m -Xms2600m -Xmn32m'
BROUTER_PROFILES=$(realpath "../../profiles2")
BROUTER_JAR=$(realpath $(ls ../../../brouter-server/build/libs/brouter-*-all.jar))
PLANET_FILE=${PLANET_FILE:-$(realpath "./planet-latest.osm.pbf")} # or change filename to your .osm.pbf file
SRTM_PATH="../../../srtm_bef" # directory of converted .bef files

## Start map computation
rm -rf tmp
mkdir tmp
cd tmp
mkdir nodetiles #create directory nodetiles
${JAVA} -cp ${BROUTER_JAR} -DavoidMapPolling=true btools.mapcreator.OsmCutter \
    ${BROUTER_PROFILES}/lookups.dat \
    nodetiles ways.dat relations.dat restrictions.dat \
    ${BROUTER_PROFILES}/all.brf ${PLANET_FILE}

echo
echo "nodetiles"
#ftiles creation expects .tls file extension
for file in nodetiles/*.ntl; do
    cp "$file" "${file%.ntl}.tls"
done

mkdir ftiles
${JAVA} -cp ${BROUTER_JAR} -Ddeletetmpfiles=false -DuseDenseMaps=true btools.mapcreator.NodeFilter \
    nodetiles ways.dat ftiles

${JAVA} -cp ${BROUTER_JAR} -Ddeletetmpfiles=false -DuseDenseMaps=true btools.mapcreator.RelationMerger \
    ways.dat ways2.dat relations.dat \
    ${BROUTER_PROFILES}/lookups.dat \
    ${BROUTER_PROFILES}/trekking.brf \
    ${BROUTER_PROFILES}/softaccess.brf

echo
echo "waytiles"
for file in ftiles/*.tls; do
    cp "$file" "${file%.tls}.tlf"
done
mkdir waytiles #create a directory named waytiles
${JAVA} -cp ${BROUTER_JAR} -Ddeletetmpfiles=false -DuseDenseMaps=true btools.mapcreator.WayCutter \
    ftiles ways2.dat waytiles

echo
echo "waytiles55"
#waytiles55 creation expects .ntl file extension
for file in ftiles/*.tls; do
    cp "$file" "${file%.tls}.ntl"
done
mkdir waytiles55
${JAVA} -cp ${BROUTER_JAR} -Ddeletetmpfiles=false -DuseDenseMaps=true btools.mapcreator.WayCutter5 \
    ftiles waytiles waytiles55 bordernids.dat

echo
echo "nodes55"
mkdir nodes55
${JAVA} -cp ${BROUTER_JAR} -Ddeletetmpfiles=false -DuseDenseMaps=true btools.mapcreator.NodeCutter \
    ftiles nodes55

echo
echo "unodes55"
mkdir unodes55
${JAVA} -cp ${BROUTER_JAR} -Ddeletetmpfiles=false -DuseDenseMaps=true btools.mapcreator.PosUnifier \
    nodes55 unodes55 bordernids.dat bordernodes.dat ${SRTM_PATH}

echo
echo "segments"
mkdir segments
${JAVA} -cp ${BROUTER_JAR} -DuseDenseMaps=true btools.mapcreator.WayLinker \
    unodes55 waytiles55 bordernodes.dat restrictions.dat \
    ${BROUTER_PROFILES}/lookups.dat ${BROUTER_PROFILES}/all.brf \
    segments rd5
ls segments #list all files in the segments directory

# Copy files to the server directory
# cp ./segments/*.rd5 ../../../../../brouter-web/segments4/ #copy all files in segments that end with .rd5 to the directory where the standalone BRouter web server runs
```

将以上脚本保存到`misc/scripts/mapcreation`中，注意将第9-15行的环境变量修改为正确的路径，之后在bash中执行即可。

代码中自带的`process_pbf_planet.sh`我没有尝试，不确定是否可以使用。

生成后的rd5文件位于`misc.scripts/mapcreation/tmp/segments4/`中，用类似上面脚本最后一行的指令将其复制到`brouter-web/segments4/`中，然后启动前后端服务就可以开始使用啦！

## 下期预告

- 一些BRouter的使用方式介绍
- 如何使用`.prf`文件实现定制化寻路
- 想使用更为复杂的标签？`lookups.dat`的语法和作用
