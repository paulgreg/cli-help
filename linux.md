Linux commands
==============

zsh
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

### Move word by word
`ALT + SHIFT + f`

### Move word by word backward
`ALT + SHIFT + b`

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

### Fetch the x to y arguments from last commands
`ls file1 file2 file3; cat !!:1-2`

### Search in a dictionnary
`dict someName`


Find
--------------

### find string in file
`find . -name MY_FILE_PATTERN | xargs grep 'MY_STRING'`

### delete files recursively (Warning : use with caution and make a backup first !)
`find . -name .DS_Store -delete`

### find files and copy them
`find . -iname "*foobar*" -exec cp "{}" ~/tmp \;`

### find images more than 100 Kb
`find . -type f -size +100k -name '*.jpg'`

### find what directory uses the most inodes
`find / -xdev -printf '%h\n' | sort | uniq -c | sort -k 1 -n`

### to recursively give directories read & execute privileges
`find /path/to/base/dir -type d -exec chmod 755 {} +`

### to recursively give files read privileges
`find /path/to/base/dir -type f -exec chmod 644 {} +`


Sed
--------------

### search and replace in files
`sed -i 's/SEARCH/REPLACE/g' **/*.txt`


Awk
--------------

### Compute average on a list of numbers
` awk '{ total += $1; count++ } END { print total/count }' data.txt`


File
--------------

### List directories size (with sort)
`du -skh * | sort -n`

### Calculate the size of all png files
`find . -iname "*.png" -print0 | xargs -0 du -ch | tail -1`

### less on a source file with syntax highlighting
`highlight -l -A SOURCE_FILE  | less -R`

### Move file to trash
`gvfs-trash filename`

### dd with progress indicator
`sudo dd if=./ubuntu-20.04.2.0-desktop-amd64.iso of=/dev/sdb bs=4M status=progress && sync`


File renaming tips
------------

### Rename all photo using date
`for i in *jpg; do jhead -n%Y-%m-%d-%f $i; done`

### Rename extension for multiple files
`for file in *.html; do mv "$file" "$(basename "$file" .html).txt"; done`


Archive
--------------

### List files in a tar.gz
`tar ztvf file.tar.gz`

### Extract archive to a chosen directory
`tar xvzf file.tar.gz -C directory`

### Create a tar.gz archive
`tar czvf archive.tar.gz path/`

### Extract xz archive while keeping compressed file
`xz --decompress --keep 2024-11-19-raspios-bookworm-armhf.img.xz`


Media
---------------

### resize images (by maximal width or height) using convert from imagemagick package
`for i in $( ls *.jpg); do convert -resize 2048x2048\> $i re_$i; done`
or
`find /path/to/your/image -type f -iname "*.jpg" -exec convert -resize 2048x2048\> {} {} \;`

### rename image with date / time
`exiftool -ext jpg '-FileName<CreateDate' -d %Y_%m_%d__%H_%M_%S%%-c.%%e .`

### erase a CDRW
`sudo cdrecord blank=all -immed dev=/dev/cdrw`

### convert wav to mp3
`ffmpeg -i input.wav -vn -ar 44100 -ac 2 -b:a 192k output.mp3`

### mount an Iso file
`mount -o loop -t iso9660 file.iso /media/iso`

### extract audio from a video (without reencoding it)
`ffmpeg -i video.flv -vn -acodec copy audio.mp3`

### extract audio from a video
`ffmpeg -i video.mp4 -q:a 0 -map a audio.mp3`

### do a screenshot later
`gnome-panel-screenshot --delay 5`

### Merge 2 video files
`mencoder -ovc copy -oac copy video1.avi video2.avi -o completevideos.avi`

### extract qr code
`zbarimg img.png`

### Set album in mp3 tags
`id3tool -a AlbumName *.mp3`


PDF
-----

### Agregate PDFs
`pdftk pdf_file_1 pdf_file_2 cat output final_pdf_file`


Web
--------------

### Check status of all link from a web page or rss feed
`wget -O - http://blog.valtech.fr/podcasts/podcasts.xml | grep -o -E 'http://([^"#<]+)' | cut -d'"' -f2 | sort | uniq | parallel "curl -o /dev/null --silent --head --write-out '%{http_code} %{url_effective}\n' {1}"`

### Show HTTP headers
`curl -v -A "user agent string" -sI "http://www.google.com"`

### Send an HTTP POST
`curl https://api.faker.com/v1/customers -i -XPOST -H 'Content-Type: application/json' -d '{"firstName":"Justin", "lastName":"Bieber"}'`

### Using jq to filter JSON (http://stedolan.github.com/jq/)
`curl 'http://search.twitter.com/search.json?q=bieber&rpp=5&include_entities=true' | jq '.results[0] | {from_user, text}'`

### Using curl to bypass Varnish
`curl --verbose --header 'Host: www.example.com' 'http://10.1.1.36:8000/path'`


Security
---------------

### Encrypt via gpg
`gpg --encrypt -r "identity" file.txt`

### decrypt via gpg
`gpg --decrypt file.txt.gpg > file.txt`

### List personals keys
`gpg --list-secret-keys --keyid-format LONG`

### Export public key
`gpg --armor --export YOUR_KEY_ID > public-key.asc`

### Show certificate informations
`openssl x509 -in ca.pem -inform pem -noout -text`

### Extract the public key from a private key
`openssl rsa -in privkey.pem -pubout > key.pub`

### Check certificate expiration
`echo | openssl s_client -connect fr.mappy.com:443 2>/dev/null | openssl x509 -noout -enddate`

### Inspect a certicate (pem)
`openssl x509 -in GandiStandardSSLCA2.pem -inform pem -noout -text`

### Check OSCP stapling
`echo QUIT | openssl s_client -connect www.google.com:443 -status 2> /dev/null | grep -A 17 'OCSP response:' | grep -B 17 'Next Update'`


dmcrypt
-----------------

### Format a drive
`sudo cryptsetup -y -v luksFormat /dev/sdX1`

### Open/unlock a drive
`sudo cryptsetup luksOpen /dev/sdX1 mappingName`

`mount /dev/mapper/mappingName /media/mountName`

### Format a fresh created drive
`sudo mkfs.ext4 /dev/mapper/mappingName`

### Close/lock a drive
`umount /media/mountName`

`sudo cryptsetup luksClose mappingName`

### Add key to a drive
`sudo cryptsetup luksAddKey /dev/sdX1`

### Check keyslots
`sudo cryptsetup luksDump /dev/sdX1`

### Remove key to a drive
`sudo cryptsetup luksRemoveKey /dev/sdX1`

### Check drive info
`sudo cryptsetup -v status mappingName`


Network
---------------

### SSH tunneling (distant port 6081 to local port 80)
`ssh -L80:localhost:6081 user@server`

### Capture web traffic
` ngrep -d eth0 -q -W byline port 80`
or
`sudo httpry -i eth0`

### Throttle a program
`trickle -d 10 -u 10 google-chrome`

### Show current connections opened
`lsof -i`

### Show which PID is using socket 9876
`lsof -i TCP:9876`

### Show current connections opened in real time
`iftop`

### Info about opened socket
`ss -s`

### Port scanning using netcat
`nc -z -v -n 127.0.0.1 21-25`

### Reverse DNS query using dig
`dig +noall +answer -x 10.0.1.167`

### Capture traffic with tcpdump to import in Wireshark
`tcpdump -i eth0 -s 65535 -w tcpdump.dump`

### Know who are blocking thoses ports
`netstat -tulpn`

### Discover hosts on local network
`nmap -sP 192.168.0.0/24`


Nginx
-------------

### order 404
`zgrep ' 404 ' /var/log/nginx/access.log.*gz | awk '{print $7}' | sort | uniq -c | sort -nr | less`


MySQL
-------------
### Default path to MySQL databases
`/var/lib/mysql`

### Change root password
`mysqladmin -u root -p'oldpassword' password 'newpassword'`


Sharing tips
------------

### Share a file via HTTP
`nc -v -l 8080 < file_to_share`

### Share current folder by HTTP
`npx http-server -a localhost .`

or

`python3 -m http.server --bind 127.0.0.1`

or

`python -m SimpleHTTPServer`



System
-----------------

### Fetch missing APT keys
`sudo apt-key adv --keyserver keyserver.ubuntu.com --recv- keys MISSING_KEY_ID`

### What is currently running
`pstree -a`

### Make computer sleep (RAM)
`sudo pm-suspend`

### Make computer hibernate (hdd)
`sudo pm-hibernate`

### List installed packages
`dpkg -l`

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

### List devices
`lspci` or `sudo dmidecode`

### Mount LVM partition
`sudo apt-get install lvm2 && sudo modprobe dm-mod`
`sudo vgchange -a y`

## clean old journalctl files
`journalctl --vacuum-time=10d`

## Look and set default apps

    gio mime inode/directory # to inspect
    gio mime inode/directory org.gnome.Nautilus.desktop # to set



Disk
-----------------

## Smart tests
`sudo smartctl -t {short/long/conveyance} /dev/sdX`

## Smart status check
`sudo smartctl -a /dev/sdX`

### Badblocks (read only)
`sudo badblocks -sv -b 4096 /dev/sdX`

### Badblocks (write/read - non desctructive)
`sudo badblocks -nsv -b 4096 /dev/sdX`

### Badblocks (desctructive !)
`sudo badblocks -wsv -b 4096 /dev/sdX`

### Check alignment
`parted /dev/sdX align-check optimal 1`

### Realign (it’s destructive !)

    sudo parted /dev/sdX
    mklabel gpt # recreate gpt partition table
    mkpart primary 1MiB 100%
    align-check optimal 1



software RAID
-----------------

### Create a new RAID array
`mdadm --create --verbose /dev/md0 --level=5 /dev/sdX1 /dev/sdY1 /dev/sdZ1`

### Remove a disk from an array
`mdadm /dev/md0 --fail /dev/sdX1 --remove /dev/sdX1`

### Add a disk to an array
`mdadm --add /dev/md0 /dev/sdX1`

### Check RAID status
`cat /proc/mdstat`
and
`mdadm --detail /dev/md0`
