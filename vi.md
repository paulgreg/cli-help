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
`CTRL+ws` : Split windows

`CTRL+ww` : switch between windows

`CTRL+wq` : Quit a window

`CTRL+wv` : Split windows vertically

### Search
`*` : Search current word accross file (then n/b to go forward/backward)

### Edition inside tags
vat,dat,yat,cat : (visualise,delete,yank,change) a tag
vit,dit,yit,cit : will empty a tag pair 
va',da',ya',ca' : (visualise,delete,yank,change) text inside quote

### Go to last/next change
`CTRL+i`
`CTRL+o`

### Vim Diff
`do` : Get changes from other window into the current window.
`dp` : Put the changes from current window into the other window.
`]c` : Jump to the next change.
`[c` : Jump to the previous change.
`Ctrl W + Ctrl W` : Switch to the other split window.
