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

### Previous search
`CTRL + p`

### Last argument
`alt .`

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

### Use tr to display your $PATH
`echo $PATH | tr ":" "\n" | sort`


find relatives
--------------

### find string in file
`find . -name MY_FILE_PATTERN | xargs grep 'MY_STRING'`  

### delete files recursively (Warning : use with caution and make a backup first !)
`find . -name .DS_Store -delete`

### find files and copy them 
`find . -iname "*foobar*" -exec cp "{}" ~/tmp \;`


sed relatives
--------------

### search and replace in files
`sed -i 's/SEARCH/REPLACE/g' **/*.txt`


file relatives
--------------

### less on a source file with syntax highlighting
`highlight -l -A SOURCE_FILE  | less -R`

### Works on a bunch of file, like translate mp4s to mp3s
``for i in *.mp4; do ffmpeg -i "$i" "`basename $i .mp4`.mp3"; done``

### Calculate the size of all png files
`find . -iname "*.png" -print0 | xargs -0 du -ch | tail -1`


Web relatives
--------------

### Check status of all link from a web page or rss feed
`wget -O - http://blog.valtech.fr/podcasts/podcasts.xml | grep -o -E 'http://([^"#<]+)' | cut -d'"' -f2 | sort | uniq | parallel "curl -o /dev/null --silent --head --write-out '%{http_code} %{url_effective}\n' {1}"`

### Show HTTP headers
`curl -v -A "user agent string" -sI "http://www.google.com"`

### Send an HTTP POST
`curl https://api.faker.com/v1/customers -i -XPOST -H 'Content-Type: application/json' -d '{"firstName":"Justin", "lastName":"Bieber"}'`

### Using jq to filter JSON (http://stedolan.github.com/jq/)
`curl 'http://search.twitter.com/search.json?q=bieber&rpp=5&include_entities=true' | jq '.results[0] | {from_user, text}'`


Network relatives
---------------

### SSH tunneling (distant port 6081 to local port 80)
`ssh -L80:localhost:6081 user@server`

### Using ngrep to capture web traffic
` ngrep -d en1 -q -W byline "^(GET|POST) .*"`

### Throttle a program
`trickle -d 10 -u 10 google-chrome`


media relatives
---------------

### resize images using convert from imagemagick package
`for i in $( ls *.jpg); do convert -resize 50% $i re_$i; done` 

### erase a CDRW
`sudo cdrecord blank=all -immed dev=/dev/cdrw`  

### mount an Iso file
`mount -o loop -t iso9660 file.iso /media/iso`  

### extract audio from a video (without reencoding it)
`ffmpeg -i mandelbrot.flv -vn -acodec copy mandelbrot.mp3`  

### do a screenshot later
`gnome-panel-screenshot --delay 5`

### Merge 2 video files
`mencoder -ovc copy -oac copy video1.avi video2.avi -o completevideos.avi`


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


File renaming tips
------------

### Rename all photo using date
`for i in *jpg; do jhead -n%Y-%m-%d-%f $i; done`


System relatives
-----------------

### Make computer sleep (RAM)
`sudo pm-suspend`

### Make computer hibernate (hdd)
`sudo pm-hibernate`

### List installed packages
`dpkg --get-selections`

### List package files
`dpkg -L package-name`

### Hash a password from command line
`echo "password_to_hash\cD" | sha1sum`

### Display a desktop notification
`notify-send "Title" "This is a message"`  

### When the system's freezed :
`Keep Left Alt & Print Screen pressed, then R, S, E, I, U, B (Raising a Skinny Elephant Is Utterly Boring)`  

### Find broken symlinks in a specified directory
``for i in `find MY_DIRECTORY -type l`; do [ -e $i ] || echo $i is broken; done``

### Get BIOS version
`sudo dmidecode -s bios-version`  

### kill a process by its window
`xkill #And squeeze the trigger`

### Cleanup /boot on Ubuntu
`dpkg --get-selections|grep 'linux-image*'|awk '{print $1}'|egrep -v "linux-image-$(uname -r)|linux-image-generic" |while read n;do apt-get -y remove $n;done`
