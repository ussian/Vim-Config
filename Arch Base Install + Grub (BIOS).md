###Pre reading notes

Notes completed xx-xx-xxxx
Last update xx-xx-xxxx

To print this file in a descent format, click the "Raw" button in the top right corner of this box.
Disclaimer: Im no way a Linux or Arch Linux pro user, ive just written down what i did to make it work for me.


A good place to read up on most if not all of this stuff is the [Arch wiki](https://wiki.archlinux.org/).
Else a quick google search can get you a long way

###Create bootable media

Make a bootable device(USB, CD/DVD etc.) with archlinux iso ([link](https://www.archlinux.org/download/)). <BR>
You can do this with Rufus on windows (its free), or if using Ubuntu follow these instructions (https://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu).
Else you run the following command or something similar (Maybe even google it?).

replace then anglebrackets <something> with the appropiate path.
sudo dd bs=4M if=<path to iso file> of=<path to device> && sync

Then boot into your install media (USB, CD/DVD etc.) by rebooting and at the begging of the startup process hit F9 (or whatever F# button that opens the bootmenu).
If its booted correctly into the bootmedia, it should greet you with Arch Linux menu and the following options
    "Boot Arch Linux (x86_64)" (Choose this if you want a 64 bit Arch installation). 
           #(|__if this option is not avaible you properly not able to install 64 bit on your machine)
    "Boot Arch Linux (i686)" (Choose this if you want a 32 bit Arch installation).
    "Boot existing OS"
    "Run Memtest86+ (Ram test)"
    "Hardware Information"
    "Reboot"
    "Power Off"

You can navigate the menu with the arrow keys and click enter to choose the option
For these notes i will be installing x86_64 Arch
After choosing 64 or 32 bit arch will do its thing for a while and when its ready it will greet you with the following:
    "Arch Linux "(version number)""
     "archiso login: root (automatic login)"
    "root@archiso ~ #"

This means you have a root prompt ready for use. Be warned you can potentionaly destroy all data on your disks which i will do during the partioning. You can also follow my partioning with ubuntu installed there i will keep my ubuntu data for dual boot.
