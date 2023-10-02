# fedora-guide

Hello reader, this is a guide for installing Fedora Linux. I will try my best to update this for the latest Fedora version. Right now that is Fedora 38. Please open an issue if it is out of date.

I made this guide because I find it appalling that this information is so hard to find for new Fedora users. I realize it will be harder to find for new users, but I hope it still helps those who do.

My current laptop is an [Asus TUF Dash F15 (2022)](https://www.asus.com/laptops/for-gaming/tuf-gaming/asus-tuf-dash-f15-2022/). Because this is an ASUS laptop, I will be installing some extra software. If you have an ASUS device as well, it would behoove you to check out [asus-linux.org](https://asus-linux.org/).

The guide is pretty long-winded because I explain things in detail. You may skip to relevant parts if you are familiar with the topic being discussed.

# Pre-install

## Which Fedora fits your head?

There are many different ways to install Fedora. This guide will cover the traditional Fedora versions. Immutable Fedora versions like Silverblue, Kinoite, or Sericea require specialized instructions for how to set them up.

The easiest way to get Fedora is to use Fedora Media Writer to download the disk image you want to use. You can obtain that [here](https://www.fedoraproject.org/en/workstation/download/)

### Fedora GNOME

You will need a CD or a USB device formatted with a Fedora Disk Image. The main Fedora image uses the GNOME desktop environment. This can be acquired [here](https://www.fedoraproject.org/workstation/).

### Fedora with other desktops

Fedora's **best-kept secret** is that you do not need to install Fedora with the GNOME desktop! You actually have a lot of options here. **Fedora Spins** are a collection of disk images that allow you to install Fedora with your choice of desktop environment. You can download these [here](https://www.fedoraproject.org/spins/).

### Fedora for newer machines

If you have **newer hardware**, you might experience issues with your Fedora installation. This might be because your disk image itself was built on release day with the software versions they had at the time. This can be problematic if, say, a new kernel version was released since then that includes support for your processor or graphics card, and your disk image does not have it. Fortunately, there is a Fedora Special Interests Group (SIG) that provides disk images built with the **latest** Fedora software available. Their page can be found [here](https://fedoraproject.org/wiki/Respins-SIG), and their images can be found [here](https://dl.fedoraproject.org/pub/alt/live-respins/).

### Fedora for the indecisive

So you don't know what desktop environment you want to install. You might want to install Fedora multiple times, with diifferent desktop environments, or you might not want to deploy Fedora on a system that does not need an entire desktop environment. You may not have the most experience with each desktop, you might have a smaller install medium, or you might want to tailor the operating system to your needs.

**Fedora Everything** is a disk image that has **all** the software for all the Fedora Spins available at install time for you to choose from. It is available [here](https://fedoraproject.org/everything/download/), and is a great deal smaller than the other disk images. You could even burn it on a CD! This is because it is a "Net Install", meaning that it downloads the latest version of packages from the Fedora Repositories before installing. This can be a great time saver!

### Bleeding-edge Fedora Rawhide

A Linux "Rolling-release" distribution is a Linux distro that does not have specific release dates, and allows you to install the latest versions of packages directly from the distribution's package manager. "Fedora Rawhide" is a special version of Fedora that ships the latest packages, for dev testing purposes. To install Fedora Rawhide **directly**, you can use disk images obtained [here](https://openqa.fedoraproject.org/nightlies.html). For beta versions of the next Fedora release, you can use [Beta](https://openqa.fedoraproject.org/nightlies.html) disk images. Personally, I have had issues installing ffmpeg for video codecs because the openH264 repository was not configured properly, but they may have fixed that since then. Only one way to find out!

## Burning the disk image

So you have your install medium (The USB flash drive, CD, or DVD you are going to use) ready. You removed the files on the storage medium and put them onto your machine. Now that you have the **.iso** file for the version of Fedora you have chosen, you must "burn" it.

If you have Fedora Media Writer, you can use that to flash whichever Fedora version you choose onto your disk.

If you are using a DVD or a CD for whatever reason, you can burn the ISO image using Brasero on Linux, or Windows Explorer on Windows. If you are using a USB Flash drive, you can use **Balena Etcher** to "burn" the ISO file onto your drive in a way that makes it bootable. This software is available [here](https://etcher.balena.io/).

New Linux users, "distrohoppers", or advanced users may want to have multiple disk images on a single flash drive. For that, **Ventoy** is a powerful solution. Personally I have had issues getting Fedora ISOs to boot from these, but your mileage may vary. You can download Ventoy [here](https://www.ventoy.net/en/index.html).

Even if you intend to dual-boot (using two operating systems on your computer), you must still make a backup of your entire system on a separate drive, just to be on the safe side. If your machine has any drivers you cannot find online, make sure to back these up too. My ASUS laptop has a "esupport" folder at _C:\esupport_ that I cannot redownload online. It is always best to do your research before you get a nasty surprise!

# Installation

## First steps

So you have your Fedora installation medium ready. You have all your files backed up on a separate drive. To install Linux, you will have to disable **Secure Boot**. Secure boot is a security standard to make sure that your device only boots with trusted software. Your computer's "UEFI" (Unified Extensible Firmware Interface) uses complex cryptography to make sure that you are only running what you want to run. This helps prevent against "rootkit" attacks, where malware may execute during your machine's "kernel startup" phase. Personally, I keep it disabled because enabling Secure Boot on an Nvidia system adds complexity, and I do not play Valorant.

Reboot your computer. When your computer logo shows up, repeatedly mash a function key. Depending on your motherboard manufacturer, the specific function key you will have to mash can differ. Once you enter the UEFI, you must look for the option to disable secure boot. It may be under "advanced settings -> boot" for example. Once you have disabled secure boot, save your settings and exit. Once your computer reboots from this, repeatedly mash your function key and try to enter the boot selection screen, if you have one. Select your USB drive or your disc drive and you are good to go!

## Installing Fedora

Once you boot from the Fedora medium, you will see a screen like this:

![Install Fedora 38, Test + install](screenshots/installer-grub.webp)

It is best to test before installing, if you recently "burned" this disk image. This will help you avoid problems with your install.

### Anaconda

The Fedora installer, Anaconda, is split into different categories. To change settings, you click on a category, edit it, and then click "back". I am using the Everything installer with i3 window manager for this guide, so it may look a little different depending on which installer you use.

![Screenshot of Anaconda](screenshots/anaconda.webp)

### WIFI

Once you have chosen your language, it is time to configure your internet. This is not required on installations from a Fedora Spin, but it is necessary on Fedora Everything installations. If you are using a home connection with just a password, you might choose WPA-number Personal. If you are using institutional WIFI with a username and a password, select Enterprise or PEAP, and enter your username and password. For non-standard WIFI setups, some exploring may be required.

Depending on your selected spin or install medium, you may see an error next to "Installation Source" on the main page. Click it, and immediately click "Back". Give it some time to refresh, and if it still shows an error, you may have issues with your internet.

### Disk partitioning

**This is the most critical part to get right.** BTRFS (B-TRee File System) is a file system that includes advanced features that make life much easier.

-   **CoW** (Copy-on-Write) will save you lots of disk space because of data deduplication
-   Filesystem **Snapshots** will allow you to "go back in time" if you install a bad update or file
-   Data **compression** allows you to fit more stuff on your drive

Fedora's BTRFS partitioning scheme is non-standard and does not allow the use of snapshots. To specify your own scheme, click **Advanced Custom** on the "Installation Destination" screen. You will have to click "Done" to enter "Blivet", the disk partitioner for the Fedora installer.

![Disks page](screenshots/disks.webp)

Because you are using a custom disk layout, you must specify where the operating system stores the files necessary for you to boot your computer. Choose the "**EFI system partition**" option, mounted at _/boot/efi_. You can choose its size depending on how many Linux kernel versions you want to keep. I usually give it 512 MiB of space. Since I am using a virtual machine, it uses a legacy "BIOS", so I do not have this.

![EFI partition](screenshots/efi.webp)

For your main BTRFS partition, select the "BTRFS Volume" option under "Device Type". Name it something special, and **do not select a mountpoint**. We will configure that later

![BTRFS partition](screenshots/btrfs.webp)

The snapshot program "Timeshift" is a user-friendly program that allows you to create and restore snapshots, and it requires you to name your partitions a certain way. For each partition listed here, click the **+** button, and set the names and mountpoints accordingly, without the quotation marks:

-   name: "@", mountpoint: "/"
-   name: "@home", mountpoint: "/home"
-   name: "@log", mountpoint: "/var/log"
-   name: "@cache", mountpoint: "/var/cache"
-   name: "@tmp", mountpoint: "/tmp"

![disk layout](screenshots/subvolumes.webp)

Timeshift only backs up the BTRFS subvolume named "@". Excluding these /var directories saves disk space, while excluding the /home directory will allow you to keep any work or important documents you have if you need to restore your system.

### User accounts

In a UNIX-ish operating system like Linux, it is critical to use a separate user account for your day-to-day computing. Fedora disables the root account by default for security reasons, because this is a very common target for brute-force attacks. I enable the root account, because if my user account was to break, say, by a program adding the bash keyword "exit" to my shell configuration, I want to be able to fix my account, or even switch to using a new one. It is important to have a strong and secure password for your root account if you add it.

![my root account settings](screenshots/root.webp)

The Fedora installer only lets you add a single user account by default, but you are definitely allowed to add more in the future! For my use case (programming, gaming, etc.), you might want to add your user account to "groups", which are groups of user accounts that are given permissions. For example, the "wheel" group has permission to use the "sudo" command, the "input" group has permission to, among other things, use udev rules, and the "docker" group allows users to create docker containers without having to use sudo. All of this is under the "Advanced settings" button.

![my user settings](screenshots/user.webp)

Once you have everything ready, you can click "Begin installation". Good luck!

# Important Software

## Finding the terminal

After installing Fedora, you will need to do several other important configuration steps. Some of these will require you to use the terminal, so find the terminal for your desktop in the menus.

If you are using the i3 or Sway spin, press "Enter" to generate your configuration, and select "Win" (Super) as your modkey. Press Super + Enter to open a terminal, press Super + D to open dmenu (a minimal program launcher), press Super + (arrow key) to switch which window you have focused, and press Super + (number) to switch your focused workspace.

## Repositories

Once you open the terminal, run the command `sudo dnf upgrade --refresh`. This will tell Fedora's package manager, **dnf**, to upgrade your system packages, and refresh the "repository metadata", the system's list of available and installed packages. For those coming from other distributions, this is like running `sudo apt update && sudo apt upgrade`, or `pacman -Syu`.

Once you refresh your system packages, you will be adding some repositories, or places that you can download software from. Run the command `sudo dnf install "https://mirrors.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm" "https://mirrors.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm"`. Depending on your country's copyright law, you may also be able to install the `rpmfusion-free-release-tainted` and the `rpmfusion-nonfree-release-tainted` repositories. Please make sure that you read the [RPMfusion FAQ](https://rpmfusion.org/FAQ#Free_Tainted) first. By enabling these repositories, you may make yourself liable to legal reprocussions. I do not condone breaking the law, and I am not liable for their usage.

After this, run the following commands. The lines starting with "#" are comments and should be skipped.

```sh
sudo dnf update
sudo dnf install gstreamer1-plugins-{good-\*,base} gstreamer1-plugin-openh264 gstreamer1-libav --exclude=gstreamer1-plugins-bad-free-devel -y
sudo dnf install ffmpeg ffmpeg-devel --allowerasing

# WARNING: Illegal in certain European countries. Only available if you have the tainted repositories enabled
sudo dnf install libdvdcss

# VA-API (Hardware-accelerated media playback) for intel GPUs and laptops (so you can watch youtube videos without draining your battery with your dedicated GPU or CPU encoding)
sudo dnf install intel-media-driver

# Nvidia NVENC VA-API driver for Nvidia Desktops
sudo dnf install nvidia-vaapi-driver
```

## Nvidia/Hardware support

If you have a somewhat more recent nvidia graphics card, you will need to install the proprietary nvidia drivers. If you are unsure of which drivers you need, read [this](https://rpmfusion.org/Howto/NVIDIA). I have an Nvidia RTX 3060 TI laptop GPU, so I will run the following commands:

```sh
sudo dnf install kernel-devel
sudo dnf install akmod-nvidia xorg-x11-drv-nvidia-cuda xorg-x11-drv-nvidia-power
# wait for your kernel modules to build
sudo systemctl enable nvidia-hibernate.service nvidia-suspend.service nvidia-resume.service nvidia-powerd.service
```

Depending on your hardware, you might have to enable certain "copr" repositories. COPR is a build system that allows you to download software that is not in the regular DNF repos. Since I have an ASUS laptop, I will install certain software that is necessary for me to have more control over my device.

```sh
sudo dnf copr enable lukenukem/asus-linux
# kernel repository only required for newer laptops
sudo dnf copr enable lukenukem/asus-kernel

sudo dnf update --refresh -y

sudo dnf install power-profiles-daemon switcheroo-control
sudo dnf install asusctl supergfxctl asusctl-rog-gui power-profiles-daemon
sudo systemctl enable supergfxd.service
```

## GRUB

After installing nvidia drivers, you will likely have to go in and tweak your grub bootloader config. run `sudoedit /etc/default/grub` and remove any duplicate entries related to nvidia. While you're in there, it is also a good time to lower your **GRUB_TIMEOUT** if you want your computer to boot faster. If you want to see a list of all your system services as your computer boots, remove the keys `rhgb quiet`.

My GRUB config looks like this:

```
GRUB_TIMEOUT=1
GRUB_DISTRIBUTOR="$(sed 's, release .*$,,g' /etc/system-release)"
GRUB_DEFAULT=saved
GRUB_DISABLE_SUBMENU=true
GRUB_TERMINAL_OUTPUT="console"
GRUB_CMDLINE_LINUX="rd.driver.blacklist=nouveau modprobe.blacklist=nouveau nvidia-drm.modeset=1"
GRUB_DISABLE_RECOVERY="true"
GRUB_ENABLE_BLSCFG=true
```

## Polkit

If you are using a desktop like sway or i3, you will not have a policykit daemon installed. These will allow GUI apps to run commands as root without asking you directly for your sudo password. You must have one installed for timeshift to work properly. Personally, I use xfce-polkit. Install it with `sudo dnf install xfce-polkit` and set it to autostart on login in your config file _~/.config/i3_ or _~/.config/sway_ with the following line: `exec --no-startup-id /usr/libexec/xfce-polkit`.

## reboot

After doing all of this, reboot your system!

## Timeshift

Now you should set up your filesystem snapshots. Run the command `sudo dnf install timeshift`. It is relatively straightforward to set up. Select `btrfs` snapshots, select the frequency and amount you will need, and you should be good to go!

## Flatpak

Unfortunately, Fedora does not ship with Flathub out of the box. On Fedora Workstation, you can enable it, but on spins, you must enable it yourself.

```sh
sudo dnf install flatpak
flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo

# Remove Fedora's flathub selection, as it is redundant
flatpak remotes
flatpak remote-delete fedora

# Install flatseal to manage flatpak permissions
flatpak install com.github.tchx84.Flatseal

# I like using browsers inside of flatpak for added security
flatpak install com.brave.Browser org.mozilla.firefox

# Packages that are better to have as flatpaks than distro packages
flatpak install org.audacityteam.Audacity com.discordapp.Discord com.obsproject.Studio

# Prismlauncher, a Minecraft launcher that is MUCH better than the vanilla launcher
flatpak install org.prismlauncher.PrismLauncher

# Steam compatibility
sudo dnf install steam-devices vulkan-tools mangohud gamemode gamescope vkBasalt
flatpak install com.valvesoftware.Steam com.github.Matoking.protontricks org.freedesktop.Platform.VulkanLayer.MangoHud org.freedesktop.Platform.VulkanLayer.vkBasalt net.davidotek.pupgui2 org.freedesktop.Platform.VulkanLayer.gamescope

# Desktop theme customization
# I use `gradience` to customize my desktop theme. This has support for all modern GTK versions.
sudo dnf install adw-gtk3-theme
flatpak install com.github.GradienceTeam.Gradience
# just install all versions of adw-gtk3 there are
flatpak install org.gtk.Gtk3theme.adw-gtk3-dark org.gtk.Gtk3theme.adw-gtk3

# Then open flatseal and give all apps access to "xdg-config/GTK-3.0" and "xdg-config/GTK-4.0"
```
