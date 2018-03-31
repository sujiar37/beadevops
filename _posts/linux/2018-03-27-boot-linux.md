---
title: Linux Boot process - An Overview
category: Linux
layout: post
---
It is important to understand the booting process of Linux systems. The entire process is consist of 6 phases as follows,
  1. BIOS [ *Basic input output system* ]
  2. MBR [ *Master Boot Record* ]
  3. LILO - [ *Linux Loader* ] **or** GRUB - [ *Grand Unified Loader* ]
  4. Kernel - [ *Central Core of the Operating System* ]
  5. Init **or** Systemd - [ *First Process which is started* ]
  6. Runlevels - [ *Tell me the mode* ]

  > BIOS performs **POST** [ *power on self test* ] to make sure that all hardwares are working fine, and also retrieve the informations such as date, time etc from **CMOS** [ *Complementary Metal-Oxide Semiconductor* ]. It will then look for valid MBR and execute the portion *sector0*, which is the first *512 bytes* of the partitioned data storage such as *Hard Disk* or *CD-ROM* etc.

  <center><h1>&darr;</h1></center>

  > MBR is stands for Master Boot Record which meants they are in size of **512 bytes** and it holds the information of **boot loaders** ( *LILO* or *GRUB*) and partition tables

  <center><h1>&darr;</h1></center>

  > *LILO* / *GRUB* both are Linux boot loaders to serve the operating system by passing control to the respective Kernel. Grub has more in feature than Lilo as it supports different OS, booting from network, interactive command interface to manage *'n'* number of boot entries and differnet boot options etc.

  ```bash
    [root@beadevops ~]# cat /boot/grub/grub.conf
    # Sample GRUB Config File ~ BeaDevOps

    default=1
    timeout=0
    title CentOS Linux 7 Rescue 756b4531ac954206ae4481f54d40d1d5 (3.10.0-693.17.1.el7.x86_64)
        root (hd0)
        kernel /boot/vmlinuz-0-rescue-756b4531ac954206ae4481f54d40d1d5 ro root=UUID=e64899eb-665e-41a9-b7da-ed5781a8b3aa console=hvc0 LANG=en_US.UTF-8
        initrd /boot/initramfs-0-rescue-756b4531ac954206ae4481f54d40d1d5.img
  ``` 

  <center><h1>&darr;</h1></center>

  > Kernel is the heart. It initialize the devices and load initrd.img from boot loader file, also mounts root file systems.

  <center><h1>&darr;</h1></center>

  > *systemd* / *init* are the first process (*pid 1* ) run through kernel to execute the targeted runlevel of an Operating System. Init is replaced with Systemd in the latest version of linux releases today. 

  ```bash
      [root@beadevops ~]# cat /etc/inittab
      # Sample Inittab file ~ BeaDevOps

      # inittab is only used by upstart for the default runlevel.
      # Default runlevel. The runlevels used are:
      #   0 - halt (Do NOT set initdefault to this)
      #   1 - Single user mode
      #   2 - Multiuser, without NFS (The same as 3, if you do not have networking)
      #   3 - Full multiuser mode
      #   4 - unused
      #   5 - X11
      #   6 - reboot (Do NOT set initdefault to this)
      #
      id:3:initdefault:
  ```

  ```bash
      [root@beadevops ~]# cat /etc/systemd/system/default.target
      # Sample Systemd file ~ BeaDevOps

      #  This file is part of systemd.
      #
      #  systemd is free software; you can redistribute it and/or modify it
      #  under the terms of the GNU Lesser General Public License as published by
      #  the Free Software Foundation; either version 2.1 of the License, or
      #  (at your option) any later version.

      [Unit]
      Description=Multi-User System
      Documentation=man:systemd.special(7)
      Requires=basic.target
      Conflicts=rescue.service rescue.target
      After=basic.target rescue.service rescue.target
      AllowIsolate=yes
  ```
  <center><h1>&darr;</h1></center>

  > There are 7 run levels in total and we can opt any one of those as per our needs. Most linux systems runs on run level 3 which is the full multi user mode without GUI. 

  ```text
     0 - Halt / Poweroff
     1 - Single User / Rescue mode
     2 - Multiuser withoy NFS( No Networking )
     3 - Full multiuser mode with Networking ( No GUI )
     4 - Unused / User-Definable mode
     5 - As run level 3 + GUI
     6 - Reboot
  ```

{% include site-subscribe.html %}