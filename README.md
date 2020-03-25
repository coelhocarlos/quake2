# Quake II

[![N|Solid](https://images.launchbox-app.com/4895c11d-4620-4a7c-9268-529701afad41.jpg)](https://nodesource.com/products/nsolid)

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)

# Introduction
Quake 2 is a first-person-shooter from idSoftware. It was removed from the repositories in Ubuntu 9.04 (Jaunty Jackalope). Instructions to install Quake 2 and popular Quake 2 mods.

  - Installation (CD-ROM)
  - Data Files
  
# Installation (CD-ROM)
```sh
  $ mkdir /<path to install>/quake2
  $ mount /cdrom
  $ cp -r /cdrom/Install/Data/baseq2 /<path to install>/quake2
```

### Binaries:
```sh
  $ cd /<path to install>/quake2
  $ wget https://ftp.gwdg.de/pub/misc/ftp.idsoftware.com/idstuff/quake2/unix/quake2-3.20-glibc-i386-unknown-linux2.0.tar.gz
  $ tar -xvzf quake2-3.20-glibc-i386-unknown-linux2.0.tar.gz
```

### Launcher:
```sh
$ echo \#\!/bin/sh > quake2_
$ echo cd \"/<path to install>/quake2\" >> quake2_
$ echo exec ./quake2 \"\$\@\" >> quake2_
```
### md5sum:

>f77d245ef7f011617625ad8ee0d0588e  baseq2/gamei386.so
>1ec55a724dc3109fd50dde71ab581d70  baseq2/pak0.pak
>c8217cc5557b672a87fc210c2347d98d  baseq2/pak2.pak

This text you see here is *actually* written in Markdown! To get a feel for Markdown's syntax, type some text into the left window and watch the results in the right.

### Troubleshooting
Rendering
* sudo echo /<path to isntall>/quake2 > etc/quake2.conf
* ln -s /usr/lib32/libGL.so.1 libGL.so
* ln -s libGL.so opengl32

### Sound
```sh
$ /dev/dsp: Input/output error
$ Could not mmap /dev/dsp
```
### you can try the following fix
```sh
$ sudo vi /etc/init.d/bootmisc.sh
$ add "echo 'quake2 0 0 direct' > /proc/asound/card0/pcm0p/oss" above : exit 0
```


Install the dependencies and devDependencies and start the server.

```sh
$ cd dillinger
$ npm install -d
$ node app
```

For production environments...

```sh
$ npm install --production
$ NODE_ENV=production node app
```
