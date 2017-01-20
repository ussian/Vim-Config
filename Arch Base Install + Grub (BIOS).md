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

replace then anglebrackets <something> with the appropiate path.
```bash
sudo dd bs=4M if=/home/ussian/Downloads/ArchVersion.iso of=/dev/sdb1 && sync
```
### Boot the Arch install media (USB, CD/DVD etc.) <BR>
You do this by rebooting and at the beginning of the startup process (ie. BIOS startup) and hiting F9 (or whatever F# button that opens the bootmenu). <BR>
If it´s booted correctly into the bootmedia, it should greet you with an Arch Linux menu and the following options <BR><BR>
    `Boot Arch Linux (x86_64)` (x86_64 means 64 bit) <BR>
    `Boot Arch Linux (i686)` (i686 means 32 bit) <BR>
    `Boot existing OS` <BR>
    `Run Memtest86+ (Ram test)` <BR>
    `Hardware Information` <BR>
    `Reboot` <BR>
    `Power Off` <BR><BR>
    
You can navigate the menu with the arrow keys and click enter to choose the highlighted option. <BR>
The option `Boot Arch Linux (x86_64)` wont be availble if your machine cant run 64 bit OS <BR><BR>
For these notes i will be installing x86_64 Arch
After choosing 64 or 32 bit arch will do its thing for a while and when its ready it will greet you with the following:
    `Arch Linux "(version number)"` <BR>
    `archiso login: root (automatic login)`<BR>
    `root@archiso ~ #`<BR>

This means you have a root prompt ready for use. Be warned you can potentionaly destroy all data on your disks which i will do during the partioning. You can also follow my partioning with ubuntu installed there i will keep my ubuntu data for dual boot.
