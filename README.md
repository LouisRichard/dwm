# DWM
Dynamic Window Manager  
Along with some more stuff just not in this repo

# I archived this repo as it is not kept up to date with Suckless' version and I went back to a regular DE. I have no need for it anymore.

## Dependencies
* make  
* gcc  
* libx11-dev  
* libxft-dev  
* libxinerama-dev  
* xorg (obviously)  
* xsetroot  
* [Nerd Fonts](https://github.com/ryanoasis/nerd-fonts)  

If you are using a discreet GPU, make sure to install the necessary drivers beforehand 
(looking at you nVidia)

My install includes the following :
* dwm/dwm     - Dynamic window manager (this repo, no need to download it)
* st/st       - simple terminal
* tools/dmenu - dynamic menu
* tools/slock - x display locker, recommended if you wanna lock your screen in an office environment

all available with wget on https://dl.suckless.org/

## Installation
Extract the other archives using 
```bash
tar -xvf PACKAGE.tar.gz
```

Edit config.mk to match your local setup (dwm is installed into the /usr/local namespace by default).

Afterwards enter the following command to build and install dwm (as root) :
```bash
make clean install
```

## Running dwm
Add the following line to your ~/.xinitrc to start dwm using startx:
```bash
exec dwm
```
In order to connect dwm to a specific display, make sure that
the DISPLAY environment variable is set correctly, e.g.:
```bash
DISPLAY=foo.bar:1 exec dwm
```
(This will start dwm on display :1 of the host foo.bar.)

In order to display status info in the bar, you can do something
like this in your .xinitrc:
```bash
while xsetroot -name "`date` `uptime | sed 's/.*,//'`"
do
    sleep 1
done &
exec dwm
```
(For that, you'll have to make sure `xsetroot` is installed)  
But I, ofc, have a .xinitrc in this repo you can take if you want to.  
It is currently optimised for my laptop with a battery indicator and all.  
A desktop version will come.  
If you want to use mine, juste copy or move it to your home directory and remove the `.laptop` or `.desktop` from the filename.  
IE : `mv .xinitrc.laptop ~/.xinitrc`

If you wish to use my .xinitrc file, make sure you have the following installed :
* awk - Data extraction from the datas in xsetroot  
* feh - Change the wallpaper  

You can put a custom wallpaper in `~/.wp/wp.png`  
Or you can edit the file, idc  

## Configuration
The configuration of dwm is done by creating a custom config.h
and (re)compiling the source code.  
Here, you'll be playing with my config but you can modify it at your will.

The modifications I've done include :
* Using different fonts  
* Having media keys working  
  * Volume keys made to work with Pulseaudio and Alsa  
* Change the color  
* The custom .xinitrc  

## Source
https://git.suckless.org/dwm/
