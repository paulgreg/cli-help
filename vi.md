VIM commands
==============

### By default, VI is installed on most linux system, install vim to have syntax coloration on many files (it's a MUST) !
`sudo apt-get install vim`  

### General commands
`~` Toggle case

### Browse for a file
`CTRL+e`

### Auto complete 
`CTRL+p` and `CTRL+n`

### Global replace
`:%s/old/new/g`

### To open a file from vim
`:open filename`

### To enable syntax
`:syntax on`

### List buffers
`:ls`

### Next buffer
`:bn`

### Previous buffer
`:bp`

### Go to buffer by number
`:bX`

### Go to buffer by name
`:b yourFileName`

### Cycle between last and current buffer
`:b#`

### Visual commands
`>` Shift right

`<` Shift left

`=` Auto indent

### Numbers
`CTRL+a` : increment

`CTRL+x` : decrement

### Split windows
`CTRL+w s` : Split windows horizontaly

`CTRL+w v` : Split windows vertically

`CTRL+w w` : switch between windows

`CTRL+w l` : go to splits at right

`CTRL+w h` : go to splits at left

`CTRL+w k` : go to splits at top

`CTRL+w j` : go to splits at bottom

`CTRL+wq` : Quit a window

### Search
`*` : Search current word accross file (then n/b to go forward/backward)

### Edition inside tags
vat,dat,yat,cat : (visualise,delete,yank,change) a tag
vit,dit,yit,cit : will empty a tag pair 
va',da',ya',ca' : (visualise,delete,yank,change) text inside quote

### Go to last/next location

`CTRL+i` Go to next location

`CTRL+o` go to last location

### Vim Diff
`do` : Get changes from other window into the current window.
`dp` : Put the changes from current window into the other window.
`]c` : Jump to the next change.
`[c` : Jump to the previous change.
`Ctrl W + Ctrl W` : Switch to the other split window.
