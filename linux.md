Linux commands
==============

Bash relatives
--------------

### Delete last word from command line
`CTRL + w`

### Delate current line from command line
`CTRL + u`

### Logout current terminal
`CTRL + d`

### Recursive search
`CTRL + r`
and
`CTRL + p`

### Clear screen
`CTRL + l`

### Begin of line
`CTRL + a`

### End of line
`CTRL + e`

### Paste
`CTRL + y`

### Edit command in VIM (you should have set EDITOR variable)
`CTRL + x` + `CTRL + e`

### Call back last command 
`!!`

### Call back last VIM command 
`!vim`


find relatives
--------------

### find string in file
`find . -name MY_FILE_PATTERN | xargs grep 'MY_STRING'`  

### delete files recursively
`find . -name .DS_Store -delete`

sed relatives
--------------

### search and replace in files
`sed -i 's/SEARCH/REPLACE/g' **/*.txt`

file relatives
--------------

### less on a source file with syntax highlighting
`highlight -l -A SOURCE_FILE  | less -R`  

media relatives
---------------

### erase a CDRW
`sudo cdrecord blank=all -immed dev=/dev/cdrw`  

### mount an Iso file
`mount -o loop -t iso9660 file.iso /media/iso`  

### extract audio from a video (without reencoding it)
`ffmpeg -i mandelbrot.flv -vn -acodec copy mandelbrot.mp3`  

### do a screenshot later
`gnome-panel-screenshot --delay 5`


MySQL
-------------
### Default path to MySQL databases
`/var/lib/mysql`

Sharing tips
------------

### Share a file via HTTP
`nc -v -l 8080 < file_to_share`

### Share current folder by HTTP
`python -m SimpleHTTPServer`

### Serve current dir files by a simple web server
python -m SimpleHTTPServer

System relatives
-----------------

### List installed packages
dpkg --get-selections

### List package files
dpkg -L package-name

### Hash a password from command line
`echo "password_to_hash\cD" | sha1sum`

### Display a desktop notification
`notify-send "Title" "This is a message"`  

### When the system's freezed :
`Keep Left Alt & Print Screen pressed, then R, S, E, I, U, B (Raising a Skinny Elephant Is Utterly Boring)`  

### Find broken symlinks in a specified directory
`for i in ``find MY_DIRECTORY -type l``; do [ -e $i ] || echo $i is broken; done`  

### Get BIOS version
`sudo dmidecode -s bios-version`  

### kill a process by its window
`xkill #And squeeze the trigger`
