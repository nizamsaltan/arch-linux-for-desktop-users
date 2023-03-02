
# 0. Foreword
Welcome to the online book for learning Arch Linux for Desktop Users! Whether you are trying to learn Arch Linux for academic purposes, to pursue a career or simply looking for a hobby, this book will teach you the basics and the intermediate knowledge. The aim of Arch Linux for Desktop Users is to show how to turn base linux operating system into fully functional desktop in an easy-to-understand fashion.

### What you will learn?
Using base an advanced linux distro can be difficult escpecialy for beginners. This book will aim to teach all the details and background proccess of daily linux computer. We will go from installing Arch Linux to our system, learning window managers, audio servers, file managers etc. If you have interset about learning or custumizing your computer to spciflcy to you then this book is for you!

> Quick Note: This book still in progress and there is have some wrong writing fails or unfinished parts. However, the accuracy of the information taught will be checked from several different sources and the sources will be given with links.


# 1. Basic Command Line Knowledge

### TODO: Make something more understandable

./_file_name_ -> file in current directory
_folder_name_/_another_folder_ -> _folder_ under current directory
/_folder_name_/_another_folder_ -> folder under root directory 

ls -> list files in current directory
-> `ls -a` show hidden files 
-> `ls /usr/share` list inside /usr/share folder

cd -> change directy
-> `cd share/bin` change diretory to share/bin under current directory
-> `cd /usr/share/bin` change diretory to /usr/share/bin under root directory

cat -> print file 
`cat picom.conf` print picom.conf file under current directory

tar -> .tar based archive manager
`tar -xf _file_name.tar.xz_` extract _file_name.tar.xz_
`tar -cf _name_of_archive.tar.xz_ /path/to/folder` create archive named _name_of_archive.tar.xz_ that contains /path/to/folder

mkdir -> make directory
`mkdir /usr/share/folder_name` make folder named folder_name under /usr/share directory

rmdir -> remove empity directory
`rmdir empty_folder` remove empty_folder under current directory

rm -> remove file or folder
`rm -rf /usr/share/unececary_folder` force to remove unececary_folder (can be file too)


# 2. Installing Arch Linux  
So many people would disagree with me about recommending Arch Linux for beginners. But learning the basics of Linux and with a proper guide, it’s relatively simple to use. Everyone’s reason for using Arch Linux is different, just like having various reasons for using Linux. I am using Arch Linux because I want to get as much freedom from Linux, and it also has a great package manager called ‘Pacman’.  
  
## Pre Instalation  
You can download the .iso file from *[https://archlinux.org/download/*](https://archlinux.org/download/*) and then flash the file to a USB drive using a flasher tool like _balena etcher._ I recommend first installing it into a virtual machine to understand and prevent any failures in the primary system. In this guide, I will use Virtual Box. But this book does not cover using virtual machines or flashing USBs. If you don’t know how to do them check the websites below.  
  
- [https://www.virtualbox.org/manual/ch01.html](https://www.virtualbox.org/manual/ch01.html)  
- [https://www.balena.io/etcher](https://www.balena.io/etcher)  
  
## First Boot  
You can check offical guide via this link: *[https://wiki.archlinux.org/title/Installation_guide*](https://wiki.archlinux.org/title/Installation_guide*)  
  
After we first boot into Arch Linux, there is have some ugly terminal to help us install AL to our system. We have to option to install Arch Linux to our system. First is going to be manual if you want extreme configuration over your installation. Second is using an built in script to automate this process (of course it configurable because of it's arch).

## Using archinstall script 
To run built in instalation script type 

    archinstall
    
to terminal. After this you will see a window like this.
![archinstall script](https://raw.githubusercontent.com/nizamsaltan/arch-linux-for-desktop-users/main/images/archinstall/archinstall_menu.png)
Let's go over each of them.

### Archinstall language
This option is language set for archinstall script. Not system language!

### Keyboard layout
Pick your keyboard layout 
> hint: you can use '/' key to search

### Locale language
This option is language set for your system.

### Locale encoding
Options for encoding texts. Keep it as UTF-8

### Drive(s)
Choose wich drive to install linux in your system.

### Disk layout
Partitioning your disk layout. If you installing Linux along side with other OSs than you would choose 'Select what to do with each individual drive' option to enter partitioning. 
If you want an clean install choose 'Wipe all selected drives and use a best-effort default partition layout' option. This option asks you to should create seprate partition for home folder. Let's discuss what is /home parition?

#### /home Parition
'/home' is mount point of partition. Which means every files inside your home folder will be stored in diffrent disk parition. Some kinda backup parition. Because when we decided to change our distro or computer, we don't need to copy and save whoole data. because most of our important files is already inside '/home' partition.

### Encription password
This option gives us opurtunity to encript our disk. This is not password of your system! Instead password of your disk. Meaning, password to read data from your disk. This option is useful if you want to encript your disk sepratly from your system. I personaly dont like to use seprate encription for my disk but if you keep important files in your system than this option is highly recommended among community.

### Bootloader
In order to boot our Linux system, a Linux-capable boot loader must be set up. The boot loader is responsible for loading the kernel and initial ramdisk before initiating the boot process. Archinstall script gives us a default option depending on our system. Best to keep it as default in most of the time. Further read: https://wiki.archlinux.org/title/Arch_boot_process

### Swap
Swap space can be used for two purposes, to extend the virtual memory beyond the installed physical memory (RAM), and also for suspend-to-disk support. Highly recommended if you low on RAM resources.

### Hostname
A hostname is a unique name created to identify a machine on a network. You can give whatever you want if you using your home network.

### Root password
Password of root. Keep it something that you can remember. 

### User account
Add users to your system.
> Tip: It's recommended to add your main account to sudoers group.
![Adding user account](https://raw.githubusercontent.com/nizamsaltan/arch-linux-for-desktop-users/main/images/archinstall/adding_user.png)

### Profile
You can choose the profile of your instalation (ie. Desktop env. or Window Manager etc.). But since will will going to install our Window Manager by ourself, you can choose `xorg` option with your desired graphics card drivers.

### Audio
In Linux systems, we have 2 option for audio server. These are [PipeWire](https://pipewire.org/) and [PulseAudio](https://en.wikipedia.org/wiki/PulseAudio).  

Audio servers in it self is huge topic, and [Tony Tascioglu](https://www.youtube.com/@TonyTascioglu) has a greate video about this. You can check his video from [here](https://www.youtube.com/watch?v=HxEXMHcwtlI). But overall my personal preference is using PipeWire. 

### Kernels
// TODO:

### Additional packages
In this part, we can install some packages to use in our system. If you already choose a Window Manager or a Desktop Enviroment without an terminal emulator or web browser, it's recommended to do it in here. For example we can install Firefox and Xfce4 Terminal Emulator by typing

    firefox xfce4-terminal

### Network configuration
Configuration of your network. You have muliple options in hier. Because of we are going to use xorg profile, choose 'manual configuration' option. In hier choose 'Add interface' after this you are going to see available network interfaces. Choose wich interface you want to configure. Then you need to choose mode for your network interface. Best to keep it as 'DHCP' (auto detect) if you don't know your ip address.

### Timezone
Choose your time zone
> hint: you can use '/' key to search

### Automatic time sync
It's personal preference. But true option would be best for most of us.

### Optional repositories
Arch Linux official repositories contain essential and popular software, readily accessible via pacman. They are maintained by package maintainers. 
Packages in the official repositories are constantly upgraded: when a package is upgraded, its old version is removed from the repository. There are no major Arch releases: each package is upgraded as new versions become available from upstream sources. Each repository is always coherent, i.e. the packages that it hosts always have reciprocally compatible versions. 
Further read: https://wiki.archlinux.org/title/Official_repositories
My personal preferance: enable multilib

##

After all finaly click install to install Arch Linux in your system. After this you are going to see option for 'Enter chroot' click yes to enter because we need to install some packages.


# 3. Understaning Window Systems in Unix like Systems
After installing base linux system, we need some base packages to use our computer traditionaly. For example we need web browser to surf on the web or an app launcher to launch apps in our system, like web browser. There is have so much to talk about but to understand how computers interact with hardware, let's take a look at  **Xorg**

## Xorg
The X.Org project provides an open source implementation of the X Window System. The development work is being done in conjunction with the [freedesktop.org](http://freedesktop.org) community. The [X.Org Foundation](https://x.org/wiki/XorgFoundation/) is the educational non-profit corporation whose [Board](https://x.org/wiki/BoardOfDirectors/) serves this effort, and whose [Members](https://x.org/wiki/Membership/) lead this work.

But what is X Window System? you might ask. Here is answer.

The **X Window System** (**X11**, or simply **X**) is a [windowing system](https://en.wikipedia.org/wiki/Windowing_system "Windowing system") for [bitmap](https://en.wikipedia.org/wiki/Bitmap "Bitmap") displays, common on [Unix-like](https://en.wikipedia.org/wiki/Unix-like "Unix-like") operating systems.

X provides the basic framework for a GUI environment: drawing and moving windows on the display device and interacting with a mouse and keyboard. X does not mandate the user interface – this is handled by individual programs. As such, the visual styling of X-based environments varies greatly; different programs may present radically different interfaces.

In basic terms, X Window System is gets input from hardware, gives information to current running apps and then draws output on the screen. We need to run X before running our GUI apps. 

There is also another option for X11 called Wayland. Wayland is a replacement for the X11 window system protocol and architecture with the aim to be easier to develop, extend, and maintain. But beacuse of newness of Wayland, we don't use it in this guide, rather than more mature X11.

We can start X by simply typing `startx` command followed by path to the window manager. For example `startx /usr/bin/i3`. So without making things more complicated for X, let's look at **Window Managers**

## Window Managers
In ist core, window managers handle the placement and appereance of windows on the screen. It can be part of a Desktop Environments or be used as standalone. There is have 3 diffrent types of window managers;

-   [Stacking/Floating](https://wiki.archlinux.org/title/Window_manager#Stacking_window_managers) window managers is the traditional WMs used in commercial operating systems like Windows and macOS. In these WMs windows can be stacked on top of each other. KWin, Sawfish or Openbox is popular options for stacking WMs. 
-   [Tiling](https://wiki.archlinux.org/title/Window_manager#Tiling_window_managers) window managers "tile" the windows so that none are overlapping. They usually make very extensive use of key-bindings and have less (or no) reliance on the mouse. Tiling window managers may be manual, offer predefined layouts, or both. i3, Qtile or Xmonad is popular options for tiling WMs. 
-   [Dynamic](https://wiki.archlinux.org/title/Window_manager#Dynamic_window_managers) window managers can switch between floating and tiling window layout.


# 4. Base System Requirements
In order to interact with our computer, we need some basic tools. These are include *Window Manager*, *App launcher* etc. But in this section, don't install tools, this is just introduction to them. You can select them in next part.

> Here is litte cheatsheet for *Base System Requirements*.
> - Window manager
> - Terminal emulator
> - App launcher
> - Web browser
> - File viewer
> - Command line text editor

Yes you can live without them but I call them *Base System Requirements* because these tool going to make everyones life easier. So let's start by installing window manager.

## Window Manager
This is realy depens on personal preferences. In previus chapter, we discussed diffrent types of window managers and some examples for them.

## i3 Gaps 
To make clear, the most (or only) diffrence between *i3* and *i3 gaps* is as it named i3 gaps have gap/space betwen windows. This help *[r/unixporn](reddit.com/r/unixporn/)* comunity to rice better and for us better visual.
> i3 is a [tiling window manager](https://en.wikipedia.org/wiki/Tiling_window_manager), completely written from scratch. The target platforms are GNU/Linux and BSD operating systems, our code is Free and Open Source Software (FOSS) under the BSD license. i3 is primarily targeted at advanced users and developers.

but before running X to runing *gui apps* let's install some more tools.

## Terminal Emulators
 First, we need an terminal emulator to run run command in gui. We have so many options for chosing terminal emulator. [Here](https://en.wikipedia.org/wiki/List_of_terminal_emulators) is list of all terminal emulators if you are nerd, if not here is some examples and screenshots of them. 
 
### Konsole
 Konsole is KDE's offical terminal emulator. Features 
 * Multiple tabs support
* Multiple profiles support
* Silence and Activity monitoring
* Bookmark support
* Searching
* Saving output
* Multiple splits in any tab

 [https://konsole.kde.org/](https://konsole.kde.org/)
 ![Screenshot of Konsole in KDE Plasma ](https://upload.wikimedia.org/wikipedia/commons/3/38/Konsole_21.12.0_screenshot.png)

### Alacritty
Alacritty is a modern terminal emulator that comes with sensible defaults, but allows for extensive configuration. By integrating with other applications, rather than reimplementing their functionality, it manages to provide a flexible set of features with high performance. The supported platforms currently consist of BSD, Linux, macOS and Windows.

[https://alacritty.org/](https://alacritty.org/)![Alacritty](https://upload.wikimedia.org/wikipedia/commons/thumb/9/9c/Alacritty-screenshot-with-vim.png/1280px-Alacritty-screenshot-with-vim.png)

### Gnome Terminal
**GNOME Terminal** is a terminal emulator for the GNOME written by [Havoc Pennington](https://en.wikipedia.org/wiki/Havoc_Pennington "Havoc Pennington") and others. Terminal emulators allow users to access a UNIX shell while remaining on their graphical desktop.

[https://wiki.gnome.org/Apps/Terminal](https://wiki.gnome.org/Apps/Terminal)
![GNOME Terminal 3.43 with the theme set to Adwaita-dark](https://upload.wikimedia.org/wikipedia/commons/thumb/1/15/GNOME_Terminal_3.43_Adwaita-dark.png/1280px-GNOME_Terminal_3.43_Adwaita-dark.png)

###  Xfce4 Terminal
Xfce Terminal is a lightweight and easy to use terminal emulator application with many advanced features including drop down, tabs, unlimited scrolling, full colors, fonts, transparent backgrounds, and more.

[https://docs.xfce.org/apps/terminal/start](https://docs.xfce.org/apps/terminal/start)
![enter image description here](https://camo.githubusercontent.com/48f61a4be8fa223bbf6689cd82bce693a2a4bfbc/68747470733a2f2f7261772e6769746875622e636f6d2f696c6c6172696f6e4b2f6261736531362d78666365342d7465726d696e616c2f6d61737465722f6261736531362d78666365342d7465726d696e616c2e706e67)

## Application Launcher
Most popular application launchers are *[DMenu](https://tools.suckless.org/dmenu/)* and *[Rofi](https://github.com/davatorium/rofi)*. dmenu is a dynamic menu for X, originally designed for [dwm](https://dwm.suckless.org/). It manages large numbers of user-defined menu items efficiently. On the other hand Rofi, like dmenu, will provide the user with a textual list of options where one or more can be selected. This can either be running an application, selecting a window, or options provided by an external script.

## File manager functionality
From wiki.archlinux.org

>**Note:** When installed, the software packages listed below will automatically be sourced by all installed - and capable - file managers, and within all desktop environments and/or window managers.

A file manager alone will not provide the features and functionality that users of full desktop environments such as [Xfce](https://wiki.archlinux.org/title/Xfce "Xfce") or [KDE](https://wiki.archlinux.org/title/KDE "KDE") will be accustomed to. This is because additional software packages will be required to enable a given file manager to:

-   Display and access other partitions
-   Display, mount, and access removable media (e.g. USB sticks, optical discs, and digital cameras)
-   Enable networking / shared networks with other installed operating systems
-   Enable thumbnailing
-   Archive and extract compressed files
-   Automatically mount removable media

When a file manager has been installed as part of a full desktop environment, most of these packages will usually have been installed automatically. Consequently, where a file manager has been installed for a standalone window manager then - as is the case with the window manager itself - only a basic foundation will be provided. The user must then determine the nature and extent of the features and functionality to be added.

## File Viewer
After adding file manager functionality, we can chose right tool to view it. File viewer can be both command line based or gui based, so it will be advantage to have both of them. Some of the options for command line file viewers are [**lf**](https://github.com/gokcehan/lf) or [**ranger**](https://ranger.github.io/). For gui, we have much of options. Examples can be [**dolphin**](https://en.wikipedia.org/wiki/Dolphin_%28file_manager%29) for kde, [**natuilus**](https://en.wikipedia.org/wiki/GNOME_Files) (or gnome files) for gnome and [**thunar**](https://en.wikipedia.org/wiki/Thunar) for xfce.

## Command Line Text Editors
 In some distro's there is have more than one command line text editor. And most popular one can be *vim* and *nano* Nano is relativly more beginner freindly because of listing some of the important shortcuts at bottom. On the other hand vim targets more advanced users. We can have multiple text editors in our system. Later of this book, we will configure these editors to get better experience. For example syntax highligting, line numbers etc.

## Downloading Base System Requiments
Finaly we understand big part of how DE works and we can start installing packages now!

### Choosing Window Manager
My pick for Window Manager will be i3-gaps because of easy configuration, custumization and also being lightweight.
Download i3-gaps by typing:
	
	$ pacman -S i3-gaps

### Choosing Terminal Emulator
I love xfce's terminal emulator because it's simple yet super custuziable. Download xfce4-terminal by
	
	$ pacman -S xfce4-terminal

### Downloading Web Browser
After downloading terminal emulator, we can start installing a web browser. Some popular options would be chrome but because of open source and already including in arch's package manager I will use firefox for this. Download Firefox by typing;

    $ pacman -S firefox
 
### Downloading Application Launcher
We need an application launcher to launch apps. Rofi is popular because of being super configurable and can be use in other panels to *(we will talk about them later on)* Download rofi by typing

    $ pacman -S rofi

### Downloading Command Line Text Editors
We can download nano and vim by typing;

    $ pacman -S nano vim

### Downloading File Viewer
My pick for file manager is again will be xfce's file manager **thunar**. Download thunar by typing;

    $ pacman -S thunar
    
But in order to get more functonlaity from thunar we need to install some more packages too. For example if we want to extract packages directly inside file viewer than we need to install [**Thunar Archive Plugin**](https://docs.xfce.org/xfce/thunar/archive). This plugin is only GUI for extisted packages so we can support it with [**File Roller**](https://wiki.gnome.org/Apps/FileRoller).  Download thunar archive plugin and file roller by typing;

    $ pacman -S thunar-archive-plugin file-roller

As I said thunar is super custimuziable so we can add more plugins to extend it's capablity. One of them can be thumb icons of images and videos. Xfce has a plugin for this called [**tumbler**](https://gitlab.xfce.org/xfce/tumbler) we can download this plugin by typing;

    $ pacman -S tumbler

And finaly don't forget to install file system because if installed, Thunar will show the trash can, removable media, and remote filesystems. Install Gnome Virtual File System by typing

    $ pacman -S gvfs

### Reboot
So, finally we install some cruical packages for our system. Now we can reboot to our newly installed system. To do this first we need to exit from `chroot` enviroment. Type;

    $ exit

to exit chroot and then reboot your system with;

    $ reboot

You should see something like this after rebooting your system,
![Login Screen](https://raw.githubusercontent.com/nizamsaltan/arch-linux-for-desktop-users/main/images/boot_after_fresh_install.png)
Enter your user name and password to login.

## Starting i3
We need configure window manager to perfectly use tools we installed. But first let's run i3 and see what we did so far. Start X by typing

    $ startx /usr/bin/i3

And finally we can see our beatifull GUI like so;

![i3 First Start](https://raw.githubusercontent.com/nizamsaltan/arch-linux-for-desktop-users/main/images/i3_start.png)

You can see a message shows on our dock/bar `Error: status_command not found or is missing a library dependecy`. This is not an important issue for now and we will get those in dock section.

In next chapter we will discuss configuring our system to make all packages work with each other.

### TODO: add link to dock section and next chapter

# 5. Configuring System

## Configuring i3
### Shortcuts for i3
### Launching apps / running commands with custom shortcuts

## Configuring Rofi

## System Docks/Bars
### i3bar
### Polybar

### Configuring i3bar
### Configuring Polybar

