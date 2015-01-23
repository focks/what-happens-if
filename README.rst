What happens if...
=================

This repository is an attempt to learn few things about unix os,to know 
"what happens if a particular command is executed?"
inspired by https://github.com/alex/what-happens-when .

Here we would try to answer the questions in a decent manner,step by step.
(starting from the boot process till the ....)

Understanding OS is not an easy task.Lets make learning a collaborative
process,so dig in and try to help,feel free to send pull request or open 
any issue.


Contents
=========

.. contents::
   :backlinks: none
   :local:

the power button turned "on":boot process
----------------------------------------

As soon as the we press the power button we see a login 
prompt;what happens behind it? Lets find it out..

As soon as the power button is pressed the following 
stages are involved in linux Boot process:-

*The Boot Process:*

- ``BIOS``

- Basic Input/Output System
- First thing which loads once you power on your machine
- CPU looks out into ROM for further instruction.
- ROM contains JUMP function in the form of instruction which tells the CPU to bring up the BIOS
- performs integrity check
- BIOS searches the Boot loader program in Disk Drive,SD Card,CD/DVD ROM,Hard Disk
- determine all the list of bootable devices available in the system
- loads and execute the Boot loader (tries to boot from hard disk where the MBR contains primary boot loader)

- ``Boot Loader``:

- ``MBR``:
- Master Boot Record
- first sector of the Hard Disk (less than 512 bytes) usually /dev/hda or /dev/sda
- primary boot loader (434-446 bytes), partition table (64 bytes), MBR validation timestamp (6 bytes)
- cannot load the kernel directly ,GRUB does
- contains info about GRUB..(loads and executes GRUB)

- ``GRUB``: in short loads and executes kernel
- GRand Unified Boot Loader
- has knowledge of file system
- selects kernel image from multiple images installed
- displays a splash screen and waits for few seconds if nothing is entered loads default kernel image as specified in the GRUB configuration file (/boot/grub/grub.conf)
- this happens in three stages
- ``stage 1``
- the primary boot loader takes up less than 512 bytes of disk space in the MBR which really small space to contain the instructions necessary to load a complex os;
- primary boot loader loads either of the next stages
- ``stage 1.5``
- this stage is taken when the /boot partition is situated beyond the 1024 cylinder head of the hard drive.
- GRUB stage 1.5 is located in the first 30 KB of the Hard Disk immediately after MBR and before the first partition
- This space is utilized to store file system drivers and modules.
- ``stage 2``
- at this stage kernel is loaded from /boot/grub/grub.conf
- Loads GUI interface i.e splash screen located at /grub/splash.xpm.gz

- ``Kernel``:

- one may consider it as the heart of the os responsible for handling all system processes;
- it configures hardware and memory allocated to the system as soon as it is loaded
- uncompresses the initrd image
- Unmounts initrd image and frees up all the memory occupied by the disk image.
- then kernel mounts the root partition as specified in grup.conf
- executes init program -the very first program (/sbin/init)

-``Init``:

- decides Runlevel which inturn dictates startup program

-``