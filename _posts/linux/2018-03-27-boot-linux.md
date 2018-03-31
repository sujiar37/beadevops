---
title: Linux Boot process - Bit explained
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

  > *LILO* / *GRUB* both are Linux boot loaders to serve the operating system by passing control to the respective Kernel. Grub has more in feature than Lilo as it supports booting from network, interactive command interface to manage *'n'* number of boot entries and differnet boot options etc

  ` [root@beadevops web]# cat /boot/grub/grub.conf
    default=1
    timeout=0
    title CentOS Linux 7 Rescue 756b4531ac954206ae4481f54d40d1d5 (3.10.0-693.17.1.el7.x86_64)
        root (hd0)
        kernel /boot/vmlinuz-0-rescue-756b4531ac954206ae4481f54d40d1d5 ro root=UUID=e64899eb-665e-41a9-b7da-ed5781a8b3aa console=hvc0 LANG=en_US.UTF-8
        initrd /boot/initramfs-0-rescue-756b4531ac954206ae4481f54d40d1d5.img `


  <center><h1>&darr;</h1></center>

  > Kernel is the heart. It initialize the devices and load initrd.img from boot loader file, also mounts root file systems.

  <center><h1>&darr;</h1></center>




