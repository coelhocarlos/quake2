# Quake II

[![N|Solid](https://images.launchbox-app.com/4895c11d-4620-4a7c-9268-529701afad41.jpg)](https://nodesource.com/products/nsolid)

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
### Mods 
  Install any mods you want in the /<path to isntall>/ directory you just created (not into /<path to isntall>/baseq2/) (optional).
 
> quake2@myserver> $ mv some_mod_linux.zip ~/quake2/
>  quake2@myserver> $ cd ~/quake2/
> quake2@myserver> $ unzip some_mod_linux.zip
 
 ### Config Script 
 Create the server config and maprotation file
 A very basic server.cfg comes with Quake II, it should look similar to this one (note that I renamed it to q2srv.cfg here):
  ********************** START OF Q2 SERVER FILE **********************
// FILENAME : /home/quake2/quake2/baseq2/q2srv.cfg
```sh
>set hostname "CHANGEME"
set ServerAdmin "CHANGEME"
set email "CHANGEME"
set webpage "http://CHANGEME"
set deathmatch "1"
set rcon_password "CHANGEME"
set timelimit "30"
set fraglimit "100"
set maxclients "16"
set allow_download "1"
set allow_download_players "0"
set allow_download_models "1"
set allow_download_sounds "1"
set allow_download_maps "1"
set public "1"
set setmaster "q2master.planetquake.com master0.gamespy.com satan.idsoftware.com"
set mapqueue "maps.lst"
map q2dm1
```
// ********************** END OF Q2 SERVER FILE **********************

You'll also need a more advanced r1q2 config file.
Use the r1q2 config generator to generate one, it should look similar to this one (WARNING: adapt the passwords if you copy the example file given here!) :
>

// ********************** START OF R1Q2 SERVER FILE **********************
// FILENAME : /home/quake2/quake2/baseq2/r1q2srv.cfg
```sh
>set sv_restartmap "q2dm1"
set sv_filter_userinfo "1"
set sv_filter_stringcmds "1"
set sv_blackholes "1"
set sv_allownodelta "1"
set sv_iplimit "3"
set sv_connectmessage "Welcome to the CHANGEME Quake II server"
set sv_nc_visibilitycheck "0"
set sv_max_download_size "9000000"
set sv_downloadserver "http://CHANGEME/quake2/files/"
set sv_download_drop_file ""
set sv_download_drop_message "Sorry, you don't have a required file. See http://CHANGEME for more info."
set sv_mapdownload_ok_message "A map file you don't have is automatically downloaded atm..."
set sv_mapdownload_denied_message "Sorry, download of a map you need to connect failed.\n See http://CHANGEME for more info."
set sv_max_netdrop "20"
set sv_hidestatus "0"
set sv_hideplayers "0"
set sv_fpsflood "250"
set sv_randomframe "0"
set sv_uptime "0"
set sv_gamedebug "0"
set sv_strafejump_hack "1"
set sv_reserved_slots "2"
set sv_reserved_password "CHANGEME"
set sv_allow_map "0"
set sv_allow_unconnected_cmds "0"
set sv_strict_userinfo_check "0"
set sv_calcpings_method "1"
set sv_no_game_serverinfo "0"
set sv_ratelimit_status "10"
set sv_new_entflags "0"
set sv_validate_playerskins "1"
set sv_idlekick "600"
set sv_packetentities_hack "0"
set sv_entity_inuse_hack "0"
set sv_force_reconnect ""
set sv_enforcetime "1"
set sv_download_refuselimit "0"
set sv_blackhole_mask "32"
set sv_badcvarcheck "1"
set sv_rcon_showoutput "1"
set sv_show_name_changes "1"
set sv_enhanced_setplayer "1"
set sv_predict_on_lag "0"
set sv_format_string_hack "0"
set sv_lag_stats "0"
set sv_max_packetdup "0"
set sv_func_entities_hack "0"
set net_maxmsglen "1390"
set net_ignoreicmp "0"
set sv_anticheat_required "0"
set sv_anticheat_error_action "0"
set sv_anticheat_message "You need the r1q2 anticheat module to connect."
set sv_anticheat_badfile_action "2"
set sv_anticheat_badfile_message "Anticheat module detected bad file at your host. All other players were notified of this."
set sv_anticheat_badfile_max "0"
set sv_anticheat_nag_time "0"
set sv_anticheat_nag_message ""
set sv_anticheat_nag_defer "0"
set sv_anticheat_show_violation_reason "1"
set sv_anticheat_client_disconnect_action "0"
set sv_anticheat_disable_play "0"
map q2dm1
```
// ********************** END OF R1Q2 SERVER FILE **********************
 
 ### Create a shellscript to start the server
 
. We'll use the unix program 'screen' in this script, so again make sure you have installed it.
. An example startup script is given below. Don't forget to adapt your servers IP, port and any name you want to identify the server.
. Some notes on adapting the script to your needs:

* choose a port > 1024. Port 27910 is recommended because it's the standard q2 port.
* you can easily start multiple q2a servers if you set a different port for each of the servers.

### Here's an insecure startscript (for testing / debugging purposes if problems occur only!) that launches a normal (non-r1q2) q2 server:

// ********************** START OF INSECURE SHELLSCRIPT TO START THE SERVER **********************
// FILENAME : /home/quake2/start-airrocket-insecure-testq2-server.sh
```sh
>#!/bin/sh
ip="CHANGEME"
port="27911"
name="q2insecure"
q2dir="/home/quake2/quake2/"
echo WARNING: running insecure q2 server $name on $ip : $port
cd $q2dir
>screen -A -m -d -S $name ./quake2 +set dedicated 1 +set ip $ip +set port $port +exec q2srv.cfg +set deathmatch 1 +map q2dm1 &
```
// ********************** END OF INSECURE SHELLSCRIPT TO START THE SERVER **********************
 Here's the final script we'll use that launches the r1q2 server:
// ********************** START OF SHELLSCRIPT TO START THE R1Q2 SERVER **********************
// FILENAME : /home/quake2/start-airrocket-r1q2-server.sh
```sh
>#!/bin/sh
ip="CHANGEME"
port="27910"
name="r1q2"
q2dir="/home/quake2/quake2/"
echo running server $name on $ip : $port
cd $q2dir
screen -A -m -d -S $name ./r1q2ded-old +set dedicated 1 +set ip $ip +set port $port +exec q2srv.cfg +exec r1q2srv.cfg +map q2dm1 &
```
// ********************** END OF SHELLSCRIPT TO START THE R1Q2 SERVER **********************
 
### GOOD GAME 
