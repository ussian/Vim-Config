####Table of contents
 * [Pre reading notes](Arch-Base-Install-+-Grub-(BIOS).md#pre-reading-notes)
 * [Create bootable media](Arch-Base-Install-+-Grub-(BIOS).md#create-bootable-media)
 * [Arch Linux iso image Boot Menu](Arch-Base-Install-+-Grub-(BIOS).md#arch-linux-iso-image-boot-menu)
 * [First things first](Arch-Base-Install-+-Grub-(BIOS).md#first-things-first)
 * [](Arch-Base-Install-+-Grub-(BIOS).md#)
 * [](Arch-Base-Install-+-Grub-(BIOS).md#)

###Pre reading notes

 Notes completed xx-xx-xxxx
 Last update xx-xx-xxxx

To print this file in a descent format, click the "Raw" button in the top right corner of this box.
Disclaimer: Im no way a Linux or Arch Linux pro user, ive just written down what i did to make it work for me.


A good place to read up on most if not all of this stuff is the [Arch wiki](https://wiki.archlinux.org/).
Else a quick google search can get you a long way

###Create bootable media

Make a bootable device(USB, CD/DVD etc.) with archlinux iso ([Download site](https://www.archlinux.org/download/)). <BR>
You can do this with [Rufus](https://rufus.akeo.ie/) on windows (its free), or if using Ubuntu follow these [instructions] (https://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu).
Else you run the following command or something similar.

replace the `/home/ussian/Downloads/ArchVersion.iso` and `/dev/sdb1` with the appropiate path.<BR>
`sudo dd bs=4M if=/home/ussian/Downloads/ArchVersion.iso of=/dev/sdb1 && sync`<BR>
###Arch Linux iso image Boot Menu<BR>
Boot the Arch install media (USB, CD/DVD etc.)<BR>
You do this by rebooting and at the beginning of the startup process (ie. BIOS startup) and hiting F9 (or whatever F# button that opens the bootmenu) and then choosing your install media. <BR>
If it´s booted correctly into the bootmedia, it should greet you with an Arch Linux menu and the following options <BR><BR>
    `Boot Arch Linux (x86_64)` (x86_64 means 64 bit) <BR>
    `Boot Arch Linux (i686)` (i686 means 32 bit) <BR>
    `Boot existing OS` <BR>
    `Run Memtest86+ (Ram test)` <BR>
    `Hardware Information` <BR>
    `Reboot` <BR>
    `Power Off` <BR><BR>
    
You can navigate the menu with the arrow keys and click enter to choose the highlighted option. <BR>
The option `Boot Arch Linux (x86_64)` wont be availble if your machine can´t run 64 bit OS <BR><BR>

For these notes i will be installing x86_64 Arch <BR>
After choosing 64 or 32 bit arch will do its thing for a while and when its ready it will greet you with the following:<BR>
    `Arch Linux "(version number)"` <BR>
    `archiso login: root (automatic login)`<BR>
    `root@archiso ~ #`<BR>

This means you have a root prompt ready for use. **Be warned** you can potentionaly destroy all data on your disks in this terminal. its most likely to happen during the partioning and formatting.<BR>

###First things first

First thing to is remove the anoying beeb sound when ever you tab-complete or try to tab-complete a command. (or doing something the terminal doesnt like in general)<BR>
```setterm -blength 0```
**-------------------------------> Is setterm permantly or temporary <-------------------------------**


Second thing to do is load the correct keymap (The standard is US)

replace DK with yours country´s letter (eg. dk for denmark, uk for united kingdom, us for united states, es for spain)<BR>
`loadkeys dk`<BR>
This command is only temporary, that means after restart it will be back at US

To list all avaible keymaps do the following 
find /usr/share/kbd/keymaps | less

Or to find only those with your country letters. (this finds all files in keymaps that contains <your country letters>)
find /usr/share/kbd/keymaps | grep -i <country letters go here>
You will propally see something like this
    /usr/share/kbd/keymaps/i386/qwerty/dk-latin1.map.gz
    /usr/share/kbd/keymaps/i386/qwerty/dk.map.gz
    /usr/share/kbd/keymaps/i386/qwerty/mac-dk-latin1.map.gz
    
For more information on "nodeadkeys" look here (http://askubuntu.com/questions/56560/what-exactly-is-meant-by-eliminate-dead-keys)
I dont know the difference between "dk-latin1" and "dk", so just try one or other and test the layout byt typing speciel characters. if the wrong character comes try another keymap.

To set current keymap, and to make it permantly do the following:
localectl set-keymap --no-convert <insert keymap file>


Next up is to check your internet connection (I recommend that you use a Ethernet connection ie. a cable connection)
ping google.dk
You can allways swap out google with a site you know that you can reach. the site have to be on the World Wide Web (ie, www)
If you get "Name or service not know" you either typed the site wrong or you got no connection


To check the time of the system type:
timedatectl
This should show you a date and a clock, plus some more stuff
to make sure the clock is accurate do this:
timedatectl set-ntp true
