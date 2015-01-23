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

*BIOS

    stands for Basic Input/Output System
    Searches,loads and executes the boot loader program
    
*Boot Loader
    MBR

        Master Boot Record
        Located in the first sector of bootable disk
        loads and execute GRUB
    GRUB

        Grand Unified Boot Loader
        selects particular kernel image
        has knowledge of file system
        loads and execute kernel and Init rd
*Kernel

    mounts the root file system
    executes the init program located in /sbin/init

*Init
    
    first program
    has pid #1 run "ps -ef | grep init"
    decides runlevel

*Runlevel:
     
     executes startup scripts






