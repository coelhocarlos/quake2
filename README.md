# quake2


Quake 2
Introduction
Quake 2 is a first-person-shooter from idSoftware. It was removed from the repositories in Ubuntu 9.04 (Jaunty Jackalope). Instructions to install Quake 2 and popular Quake 2 mods.

Installation (CD-ROM)
Data Files

mkdir /home/zombie/Server/Games/quake2
mount /cdrom
cp -r /cdrom/Install/Data/baseq2 /<path to install>/quake2
Binaries

cd /home/zombie/Server/Games/quake2
wget https://ftp.gwdg.de/pub/misc/ftp.idsoftware.com/idstuff/quake2/unix/quake2-3.20-i386-unknown-linux2.0.tar.gz

tar -xvzf quake2-3.20-glibc-i386-unknown-linux2.0.tar.gz
Launcher

echo \#\!/bin/sh > quake2_
echo cd \"/home/zombie/Server/Games/quake2\" >> quake2_
echo exec ./quake2 \"\$\@\" >> quake2_
md5sum

f77d245ef7f011617625ad8ee0d0588e  baseq2/gamei386.so
1ec55a724dc3109fd50dde71ab581d70  baseq2/pak0.pak
c8217cc5557b672a87fc210c2347d98d  baseq2/pak2.pak
Troubleshooting
Rendering

sudo echo /home/zombie/Server/Games/quake2 > etc/quake2.conf
ln -s /usr/lib32/libGL.so.1 libGL.so
ln -s libGL.so opengl32
Sound
If you have no sound with the following error message in console

/dev/dsp: Input/output error
Could not mmap /dev/dsp
you can try the following fix

sudo vi /etc/init.d/bootmisc.sh
add "echo 'quake2 0 0 direct' > /proc/asound/card0/pcm0p/oss" above : exit 0
Playing
GL Renderer

./quake2 +set vid_ref glx
Software Renderer

./quake2 +set vid_ref softx


// ********************** START OF INSECURE SHELLSCRIPT TO START THE SERVER **********************
// FILENAME : /home/quake2/start-airrocket-insecure-testq2-server.sh

#!/bin/sh
ip="CHANGEME"
port="27911"
name="q2insecure"
q2dir="/home/zombie/Server/Games/quake2/"

echo WARNING: running insecure q2 server $name on $ip : $port

cd $q2dir
screen -A -m -d -S $name ./quake2 +set dedicated 1 +set ip $ip +set port $port +exec q2srv.cfg +set deathmatch 1 +map q2dm1 &


// ********************** END OF INSECURE SHELLSCRIPT TO START THE SERVER **********************


Here's the final script we'll use that launches the r1q2 server:

// ********************** START OF SHELLSCRIPT TO START THE R1Q2 SERVER **********************
// FILENAME : /home/quake2/start-airrocket-r1q2-server.sh

#!/bin/sh
ip="CHANGEME"
port="27910"
name="r1q2"
q2dir="/home/zombie/Server/Games/quake2/"

echo running server $name on $ip : $port

cd $q2dir
screen -A -m -d -S $name ./r1q2ded-old +set dedicated 1 +set ip $ip +set port $port +exec q2srv.cfg +exec r1q2srv.cfg +map q2dm1 &



// ********************** END OF SHELLSCRIPT TO START THE R1Q2 SERVER **********************
