# Notes realesed xx-xx-xxxx
# Last update xx-xx-xxxx

# To print this file in a descent format, click the "Raw" button in the top right corner of this box.
# Disclaimer: Im no way a Linux or Arch Linux pro user, ive just written down what i did to make it work for me.


# A good place to read up on most if not all of this stuff is the Arch wiki (https://wiki.archlinux.org/).
# Else a quick google search can get you a long way


# Make a bootable device(USB, CD/DVD etc.) with archlinux iso (https://www.archlinux.org/download/).
# You can do that with Rufus on windows (its free), or if using Ubuntu follow these instructions (https://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu).
# Else you run the following command or something similar (Maybe even google it?).

# replace then anglebrackets <something> with the appropiate path.
sudo dd bs=4M if=<path to iso file> of=<path to device> && sync

# Then boot into your install media (USB, CD/DVD etc.) by rebooting and at the begging of the startup process hit F9 (or whatever F# button that opens the bootmenu).
# If its booted correctly into the bootmedia, it should greet you with Arch Linux menu and the following options
    # "Boot Arch Linux (x86_64)" (Choose this if you want a 64 bit Arch installation). 
           #(|__if this option is not avaible you properly not able to install 64 bit on your machine)
    # "Boot Arch Linux (i686)" (Choose this if you want a 32 bit Arch installation).
    # "Boot existing OS"
    # "Run Memtest86+ (Ram test)"
    # "Hardware Information"
    # "Reboot"
    # "Power Off"

# You can navigate the menu with the arrow keys and click enter to choose the option
# For these notes i will be installing x86_64 Arch
# After choosing 64 or 32 bit arch will do its thing for a while and when its ready it will greet you with the following:
    # "Arch Linux "(version number)"
    # "archiso login: root (automatic login)
    # "root@archiso ~ #"

# This means you have a root prompt ready for use. Be warned you can potentionaly destroy all data on your disks which i will do during the partioning. You can also follow my partioning with ubuntu installed there i will keep my ubuntu data for dual boot.


# First thing to is remove the anoying beeb sound when ever you tab-complete or try to tab-complete a command. (or doing something the terminal doesnt like in general)
setterm -blength 0
-------------------------------> Is setterm permantly or temporary <-------------------------------


# Second thing to do is load the correct keymap (The standard is US)

# replace DK with yours country's letter (eg. dk for denmark, uk for united kingdom, us for united states, es for spain)
loadkeys <country letters goes here>
# This command is only temporary, that means after restart it will be back at US

# To list all avaible keymaps do the following 
find /usr/share/kbd/keymaps | less

# Or to find only those with your country letters. (this finds all files in keymaps that contains <your country letters>)
find /usr/share/kbd/keymaps | grep -i <country letters go here>
# You will propally see something like this
    # "/usr/share/kbd/keymaps/i386/qwerty/dk-latin1.map.gz
    # "/usr/share/kbd/keymaps/i386/qwerty/dk.map.gz
    # "/usr/share/kbd/keymaps/i386/qwerty/mac-dk-latin1.map.gz
    
# For more information on "nodeadkeys" look here (http://askubuntu.com/questions/56560/what-exactly-is-meant-by-eliminate-dead-keys)
# I dont know the difference between "dk-latin1" and "dk", so just try one or other and test the layout byt typing speciel characters. if the wrong character comes try another keymap.

# To set current keymap, and to make it permantly do the following:
localectl set-keymap --no-convert <insert keymap file>


# Next up is to check your internet connection (I recommend that you use a Ethernet connection ie. a cable connection)
ping google.dk
# You can allways swap out google with a site you know that you can reach. the site have to be on the World Wide Web (ie, www)
# If you get "Name or service not know" you either typed the site wrong or you got no connection


# To check the time of the system type:
timedatectl
# This should show you a date and a clock, plus some more stuff
# to make sure the clock is accurate do this:
timedatectl set-ntp true


# Now is the time for disk Format and pationing
# There is a handfull of tools and commands avaiable ill only be using some of them. You check the list here (https://wiki.archlinux.org/index.php/Partitioning#Partitioning_tools)
# To list file systems and disks:
lsblk -f -p
# This should show something like this:
    # "NAME         FSTYPE      LABEL       UUID
    # "/dev/sdb                                                                                                 "
    # "└─/dev/sdb1  vfat        ARCH_201701 1702-0227                               /run/archiso/bootmnt        "
    # "/dev/sr0                                                                                                 "
    # "/dev/loop0   squashfs                                                        /run/archiso/sfs/airootfs   "
    # "/dev/sda                                                                                                 "
    # "└─/dev/sda1  ext4                    f2b67d75-090a-4d96-8dfb-e814dd07fd13                                "

# The "/dev/sdb" is my pc disk with my previous Arch Linux installation while the "/dev/sda" is my bootable usb-disk, where the Arch is image is placed.
# Disk name in linux are named after the alfabet, so sd*(where * is the next letter in the alfabet). (eg. sda for the first disk, sdb for the secound disk, sdc for the third disk etc.)
# The secound line "└─/dev/sdb1" is a partion of disk "sdb" so partions are named after number (eg. sdb1, sdb2, sdb3)
# You should just ignore "/dev/sr0", "/dev/loop0" and your bootmedia (in my case /dev/sda). All of these are used by the bootmedia.

# There is alot of different ways to partion your disks so for more info check out the formating and partioning methods folder (or look it up on google)
# For these notes i will make just 1 partion (a root partion) for everything.
# The command for that is the following:
cfdisk /dev/sda

# Replace "sda" with the disk you want to install Arch Linux on
# That command will bring up a "Pseudo-graphics" interface. You use the arrow keys to navigate.

# If you by mistake deletes a partion you didn´t want to delete, just click enter when you are hovering over "[   Quit    ]"

# I only have 1 partion so i will be deleting just that by hovering over "/dev/sda1" with the up and down arrow keys and choose "[ Delete ]" by moving the hover bar with left and right arrow keys.
# When you are hovering over the partion and "[ Delete ]" hit enter to delete it

# There should now be a new device called "Free space" which obviously isn´t a device but is just unallocated space
# If you have multiple partions that you delete those will add up into the free space.

# To make a new partion hover over the "Free space" and "[   New   ]" then hit enter.
# It will by default suggest the maximum size of the partion which should amount to the same amount of free space
# And this is, as i said earlier, where there are multiple choicses on what to do and for those go look at the "partioning and formatting folder"

# Well i´ll be making just one root partion. To do this, you just choose the default size (eg. all of the free space)
# After choosing the size it will ask if should be a "[ primary ]" or "[extended]" you should choose "[ primary ]" if you are gonna have  four partions or less (more info in the "partioning and formatting folder").
# When you have choosen the partion type you should be back at the same screen as when you ran the "cfdisk" command only difference would be the partions.

# I will be marking my single partion as "bootable" by hovering over the partion and the option "[bootable]" then hitting enter
# More information on which partion should be bootable in the "partioning and formatting folder"

# To confirm the partion changes you will need to hover over the "[  Write  ]" option and hit enter
# You will then be asked if you are sure that you want to make these changes. type "yes" or "no" depending if you are done. Be warned you type "yes" you wont be able to get the data back.
# Afterwards you just the hoverbar to the "[  Quit  ]" and hit enter to exit.

# Now when we are done with partioning we need to format (And again more details in "partioning and formatting folder")
# We will just format our single root partion to the filsystem "ext4". To do this run this command:
mkfs.ext4 /dev/sda1
# Remember that we format partions and NOT disk so put that number at the end even if you only have one partion.
# If the partion contains a filesystem (even if you did delete you partion) it will ask if you want to proceed anyway here you should answer "y".
# if any errors occur, try googling it :)


# Now we are done with partioning and formatting and we now need to mount our newly made ROOT partion filesystem, you do that like so:
mount /dev/sda1 /mnt
# "/dev/sda1" is you partion and "/mnt" is where you mount the partion to.
# you´ll also need to mount your other partions if you have any other partions. I wont be doing this i´ll only show how to do it. So i wont be doing anything inside that box.
┌───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────┐
│# create a folder for your partion on you mounted root partion for this example ill be doing it for the "boot" partion │
│mkdir /mnt/boot                                                                                                        │
│# That will create the boot folder on your root partion                                                                │
│# Now you need to mount the boot partion to your boot folder:                                                          │
│mount /dev/sda2 /mnt/boot                                                                                              │
│# /dev/sda2 should be changed into the coresponding partion (ie. if you boot partion is "/dev/sdb3")                   │
└───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────┘








ASCII signs [ └ ┐ ─ ┌ ┘ │ ]
