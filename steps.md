# Disable Journalling on ext4
# When creating ext4 partition disable journalling
mkfs.ext4 -O ^has_journal /dev/sda10
mke2fs -t ext4 -O ^has_journal /dev/sda10
#tune2fs -o journal_data_writeback /dev/sda10

tune2fs -O ^has_journal /dev/sda10
e2fsck -f /dev/sda10
dumpe2fs /dev/sda10 |more

# Making & Configure tmpfs

tmpfs	/home/user/.cache/chromium	tmpfs	noatime,nodiratime,nodev,nosuid,uid=1000,gid=1000,mode=0700,size=2000M	0	0
tmpfs	/home/user/.config/chromium	tmpfs	noatime,nodiratime,nodev,nosuid,uid=1000,gid=1000,mode=0700,size=2000M	0	0

# Browsers cache on tmpfs

chromium --incognito --disk-cache-dir=/home/user/.chrome/ramdisk

#For more performance add fstab opions: data=writeback,noatime,nodiratime
/dev/sda10 /opt ext4 defaults,data=writeback,noatime,nodiratime 0 0

# Add contrib and non-free repositories

# deb cdrom:[Debian GNU/Linux stretch-DI-alpha5 _Stretch_ - Official Snapshot amd64 NETINST Binary-1 20160108-10:53]/ stretch main

#deb cdrom:[Debian GNU/Linux stretch-DI-alpha5 _Stretch_ - Official Snapshot amd64 NETINST Binary-1 20160108-10:53]/ stretch main

deb http://ftp.de.debian.org/debian/ stretch main contrib non-free
deb-src http://ftp.de.debian.org/debian/ stretch main contrib non-free

deb http://security.debian.org/debian-security stretch/updates main contrib non-free
deb-src http://security.debian.org/debian-security stretch/updates main contrib non-free

# Non-free firmware
sudo apt-get install firmware-linux firmware-linux-free firmware-linux-nonfree

# UI & UX apps
sudo apt-get install i3 xdotool feh light-locker

# Command Line Useful tools
sudo apt-get install vim-nox ranger cmus trash-cli htop

# PDF & DJVU readers
sudo apt-get install zathura zathura-djvu zathura-pdf-poppler mupdf

# Archive
sudo apt-get install p7zip-full p7zip-rar rar unrar zip unzip

# Fonts
sudo apt-get install ttf-mscorefonts-installer ttf-xfree86-nonfree ttf-dejavu

# Multimedia
sudo apt-get install youtube-dl

# Install chromium and pepperflashplugin-nonfree
sudo apt-get install chromium pepperflashplugin-nonfree

# Development
sudo apt-get install git

# vi-like behaviour (Do Not install)
NetHack
vifm
calcurse
mutt
apvlv
vimperator/vimprobable
dwm
dwb
uzbl
lynx
vimb

# Remove apps from xfce4 default package
sudo apt-get autoremove --purge exfalso gimp gimp-data quodlibet xsane xsane-common
xfce4-clipman xfce4-clipman-plugin xfce4-cpufreq-plugin xfce4-cpugraph-plugin xfce4-dict xfce4-mailwatch-plugin xfce4-netload-plugin xfce4-notes xfce4-notes-plugin  xfce4-sensors-plugin xfce4-smartbookmark-plugin xfce4-systemload-plugin xfce4-taskmanager xfce4-timer-plugin xfce4-verve-plugin xfce4-wavelan-plugin xfce4-weather-plugin

# Warning: Do Not Remove this packages:
xfce4-appfinder
