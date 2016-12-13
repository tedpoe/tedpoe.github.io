---
layout: post
title: "Background and OS Selection"
date: 2016-12-12
---
For the project that I'm working on, I may have need to run numerous instances of EnergyPlus on a regular basis.  
I was attracted to [Jon Hand's](https://www.linkedin.com/pulse/energyplus-esp-r-distributions-disk-image-raspberry-pi-jon-hand) 
build of EnergyPlus on Raspberry Pi, so I looked at what OSes could run on RPi.

I've looked at:

* Ubuntu (since the RPi runs Raspbian)
* Alpine Linux
* coreOS
* Snappy Ubuntu Core - supports Docker too; there is no longer a traditional Ubuntu Core

In order to build up to running an RPi cluster, I wanted to start using an OS that could be run in VirtualBox, could support more than a command-line interface for development, and provided a clear and distinct Python 3.x since part of my work will use the [eppy](https://pypi.python.org/pypi/eppy) package.

## Snappy Ubuntu Core

Snappy provides little to address my requirements so it fell off of the list.  It is definitely targeted at Internet of Things devices. 

## coreOS

Similarly, coreOS did not meet all of my requirements.  That left a Ubuntu variant and Alpine Linux.

## Alpine Linux

Alpine Linux is really lightweight and it can run XFCE4.  It has numerous packages including VirtualBox support as well as Python3.  The only drawback is that is it built against mucl libc and not glibc.  The downloadable EnergyPlus for Linux is built against libc, so I tried Alpine Linux's chroot approach.  Using chroot, one can run libc programs by adding the archlinux glibc package.  However, EnergyPlus also requires: libstdc++, libgcc, libdm, libm, libpthread, and ld-linux-x86-64.  I stopped without trying to add from archlinux all of these other packages.

## Ubuntu

Since the RPi's Raspbian and Ubuntu share the same Debian upstream source, this appears to be the build of choice to satisfy my requirements: glibc, desktop, Python.  It's only the weight of the system that's a concern.  Trying to run multiple simultaneous VirtualBox images will start to tax my poor little laptop.

## Still to be considered

[DietPi](http://dietpi.com/) provides builds for both RPi as well as an x86-64 VirtualBox image.  I'll have to look at the packages that might be available.  It does provide MATE and XFCE desktops.

[Minibian](https://minibianpi.wordpress.com/).  Latest release 12 Mar 2016.

