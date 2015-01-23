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

*``BIOS``:*
- Basic Input/Output System
- First thing which loads once you power on your machine
- CPU looks out into ROM for further instruction.
- ROM contains JUMP function in the form of instruction which tells the CPU to bring up the BIOS
- performs integrity check
- BIOS searches the Boot loader program in Disk Drive,SD Card,CD/DVD ROM,Hard Disk
- determine all the list of bootable devices available in the system
- loads and execute the Boot loader (tries to boot from hard disk where the MBR contains primary boot loader)

*``Boot Loader``:*
``MBR``:
- Master Boot Record
- first sector of the Hard Disk (less than 512 bytes) usually /dev/hda or /dev/sda
- primary boot loader (434-446 bytes), partition table (64 bytes), MBR validation timestamp (6 bytes)
- cannot load the kernel directly ,GRUB does
- contains info about GRUB..(loads and executes GRUB)

``GRUB``:
- Grand Unified Boot Loader
- 