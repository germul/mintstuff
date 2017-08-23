# mintstuff
# settings for personal use by myself
# feel free to use if they can be of some use to you!

################
## MINT SETUP ##
################

################

Default Apps:

sudo apt-get install clementine smplayer shutter handbrake dvdbackup x264 qbittorrent dvdauthor flac gnome-mahjongg

###############
WOEID Dublin

560743

##############


SSD Tweaks:

sudo nano /etc/fstab

add noatime to ssd mount points

for ntfs change umask to 

uid=ger,gid=users 0    0

###############

Change grub boot delay

sudo nano /etc/default/grub

change default wait and then do

sudo update-grub


set trim job ~~hold off pending test - 01-12-2016~~

sudo mv -v /etc/cron.weekly/fstrim /etc/cron.daily

to revert:

sudo mv -v /etc/cron.daily/fstrim /etc/cron.weekly

#############

swappiness

sudo nano /etc/sysctl.conf

# Sharply reduce the inclination to swap
vm.swappiness=1

#################

disable hibernate

sudo mv -v /etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla /


#######################

disable suspend

sudo nano /etc/polkit-1/localauthority/90-mandatory.d/disable-suspend.pkla

insert following text and save:

[Disable suspend (upower)]
Identity=unix-user:*
Action=org.freedesktop.upower.suspend
ResultActive=no
ResultInactive=no
ResultAny=no

[Disable suspend (logind)]
Identity=unix-user:*
Action=org.freedesktop.login1.suspend
ResultActive=no

[Disable suspend for all sessions (logind)]
Identity=unix-user:*
Action=org.freedesktop.login1.suspend-multiple-sessions
ResultActive=no

###########################

nvidia-settings --assign CurrentMetaMode="nvidia-auto-select +0+0 { ForceFullCompositionPipeline = On }"

then add { ForceFullCompositionPipeline = On } as required

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "Stereo" "0"
    Option "metamodes" "nvidia-auto-select +0+0 { ForceFullCompositionPipeline = On }"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

###########################

SMPlayer

To install SMPlayer from this PPA, run these commands on a terminal:

sudo add-apt-repository ppa:rvm/smplayer
sudo apt-get update && sudo apt-get install smplayer smtube smplayer-themes smplayer-skins

####

Handbrake PPA

sudo add-apt-repository ppa:stebbins/handbrake-releases
sudo apt-get update

####

GPU drivers PPA

sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt-get update

###########################

REFERENCE:
https://sites.google.com/site/easylinuxtipsproject/ssd

###########################
