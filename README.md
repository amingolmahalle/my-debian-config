# my-Debian-config
How to Install **Debian**:

First, install **Debian** without choosing a desktop environment. (**unselect** Gnome, KDE, Xfce and etc. **just select** utilities)

After finishing the installation, first, log in to the system.

Wow. already we can work just the command line.

Good. everything will be ok.

Run the below commands with the root user to check update packages:
> su

> apt update

> apt upgrade -y

 Then install **sudo** command:
 
> apt install sudo

After installation, we should add our user to the sudo group:

> su -l

> adduser myuser sudo

**Optional**:

You can change the password to an easy password.

> su

> passwd myuser 111

> passwd root 111

OK...!!!

Now we are installing **some practical applications** on the system:

>sudo apt update
 
> sudo apt install -y wget curl htop vim kate tmux feh mirage okular bc zip unzip rar unrar cowsay cmatrix libreoffice

Now we should install **i3** with the below command:

(**i3** a best of Windows manager that I know)

Help link: [windows manager list](https://wiki.debian.org/DesktopEnvironment)

> sudo apt install i3

After installation, we should reboot the system

To customize **i3** copy and paste the config file in the below link to **~/.config/i3**.

[customize i3 config](https://github.com/amingolmahalle/my-debian-config/blob/196ea4c4c9ed47c0d5657961033c5aaa232c23c7/.config/i3/config)

Then we should install **lightdm**.

(lightdm is a cross-desktop display manager.)

> sudo apt install lightdm

After installation, reboot the system again

I hope everything is ok and we don’t have any errors.

Now we need a **file manager** to see files, folders etc, run the below command for installation:

> sudo apt install nautilus

To change the **nautilus** theme from **light mode** to **dark mode**:

> sudo apt-get install libgtk-3-dev

To customize **gtk3.0** run the below code step by step:

> cd ~/.config/

> mkdir gtk-3.0

> cd gtk-3.0/

 copy [settings.ini](https://github.com/amingolmahalle/my-debian-config/blob/97b474e71b49a95311a75ced973978e27631327f/.config/gtk-3.0/settings.ini) file and paste here.

Now, I suggest installing **Terminator** as a default terminal system.

Because of writing with Python, this is the best, fastest, and most beautiful I know. easy to work.

> sudo apt install terminator

To customize **Terminator** copy the file in the below link and paste **~/.config/terminator**.

[custom terminator config](https://github.com/amingolmahalle/my-debian-config/blob/196ea4c4c9ed47c0d5657961033c5aaa232c23c7/.config/terminator/config)

To add another keyboard language:

(**e.g.** add the **Persian** language)

> sudo dpkg-reconfigure keyboard-configuration

To install **Wireless Driver** and connect to that do the below commands step by step:

> sudo -i

> apt install net-tools (for use the ifconfig command)

> ifconfig -a

This command shows all network cards that exist in this system.

check the network card should be **IP address**. if any network card here we should install that.

> lspci

(**e.g.** for me: Network controller: Broadcom Inc. and subsidiaries BCM43142 802.11b/g/n)

Supported Broadcom wireless network cards: 

BCM4311-, BCM4312-, BCM4313-, BCM4321-, BCM4322-, BCM43142-, BCM43224-, BCM43225-, BCM43227-, BCM43228-, BCM4331-, BCM4360-, and BCM4352

> vim /etc/apt/sources.list

Add **contrib non-free** at the end of every line after of **main** word and save the changes.

(**e.g.** deb http://deb.debian.org/debian/ bullseye main contrib non-free)

> apt install firmware-brcm80211

> apt install broadcom-sta-dkms

After installation reboot the system.

Run again

> sudo -i

> ifconfig -a

Now you see an added new network card to the system.

Then copy the below file in **/usr/local/bin**:

[connect to wifi script](https://github.com/amingolmahalle/my-debian-config/blob/97b474e71b49a95311a75ced973978e27631327f/wifi/connect_wifi)

Copy the new network card name and replace every line that uses the network card name with the new network card name.

(**e.g.** replace wlo1 with wlp4s0)

Then access execution to that:

> sudo chmod +x connect_wifi

> complete -W “connect_wifi” connect_wifi

How to control **Audio**:

> sudo apt-get install alsa-utils

> sudo alsamixer

To increase or decrease the **mic** volume:

> amixer set Capture 5%+

> amixer set Capture 5%-

Set Up a **Firewall**:
> sudo apt install ufw

> sudo ufw enable

> sudo ufw status verbose

Now **ufw** is active in your system

Extend the **battery life** of laptops:
> sudo apt install tlp -y

> sudo reboot

> sudo systemctl status tlp

Now **tlp** is active in your system
(This tool provides automatic power settings that reduce energy usage)

Install gparted: A graphical tool for managing disks and partitions.
> sudo apt update

> sudo apt install gparted -y

I hope you enjoy **Debian**.

