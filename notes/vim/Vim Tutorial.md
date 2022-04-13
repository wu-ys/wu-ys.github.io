## Vim Tutorial

[TOC]

------

*This part is concluded from [(MIT)The missing semeter/editor](https://missing.csail.mit.edu/2020/editors/)*.

### Modes

Normal: Press `Esc` to escape from other modes
Insert `i`, enter-and-insert `o`
Replace `R`
Visual `v`, visual line `V`, visual block `Ctrl+V`
Command line `:`

### Commands

`:q`: quit (close current window)	`:qa`: quit all windows
`:w`: write(save)
`:qw`: quit-and-save
`:q!`: quit-without-save
`:e <file-name>`: open file for editing
`:help <key>`: ask for help for some key
`:sp`: separate current tab
`:tabnew`: create new window in the current tab

### Movement Shortcuts

`hjkl`: Movements left/down/up/right
`w`,`b`: Move forward/backward for one word
`e`: Move to end of the word
`0`,`$`: Move to beginning/end of a line
`^`: Move to non-empty beginning of a line
`Ctrl+U`,`Ctrl+d`: Scroll up/down
`G`,`gg`: Move to end/beginning of the buffer
`H`,`M`,`L`: Move to Top/Middle/Bottom of screen
`f+{char}`,`F+{char}`: Move to the next/last char in this line
`t+{char}`,`T+{char}`: 

`Ctrl+W+j`,`Ctrl+W+k`: moving to the above/below window
`Ctrl+h`

### Editing Shortcuts

`d+{movement}`: delete the contents along the movement. Example:
`dw`: delete the word
`de`: delete end of the word
`dl`: delete one char
`dj`: delete one line
`dd`: delete the current line

`c+{movement}`: exactly same function with the `d` command, and turns into insert mode
`cc`: change the current whole line

`u`: undo
`Ctrl+R`: redo

`x`: delete one char
`r+{char}`: replace one char

`y+{movement}`: copying the movement area
`p`: pasting

### Counts

Enter a number s.t. to execute the following command for many times

`4j` = `jjjj`

### Modifiers

In `c` and `d` command, we can select movement in a range bracketed by something.
`ci[`: change contents **inside** the bracket []
`da[`: delete contents around the bracket [] (included)

`%`: Jump to the matching bracket
`/something`: search for something
`.`: repeat the same editing command as previous

### Subtitution

`:s` substitute command (one-line)
`:%s`: substitute command (all lines)

Examples:

- `:s/foo/bar/g`: Find each occurrence of 'foo' (in the current line only), and replace it with 'bar'.

- `:%s/foo/bar/g`: Find each occurrence of 'foo' (in all lines), and replace it with 'bar'.

- `:%s/foo/bar/gc`: Change each 'foo' to 'bar', but ask for confirmation first.

- `:%s/\<foo\>/bar/g`: Change only **whole words** exactly matching 'foo' to 'bar'.

- `:5,12s/foo/bar/g`: Change each 'foo' to 'bar' for all lines from line 5 to line 12 (inclusive) 

- `:.,$s/foo/bar/g`: Change each 'foo' to 'bar' for all lines from the current line (.) to the last line ($) inclusive. 
- `:.,+2s/foo/bar/g`: Change each 'foo' to 'bar' for the current line (.) and the two next lines (+2).