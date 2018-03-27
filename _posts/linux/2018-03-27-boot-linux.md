---
title: Linux Boot process - Bit explained
category: Linux
layout: post
---
It is important to understand booting process of Linux systems. The entire process is consist of 6 phases as follows,
  1. BIOS [ *Basic input output system* ]
  2. MBR [ *Master Boot Record* ]
  3. LILO - [ *Linux Loader* ] **or** GRUB - [ *Grand Unified Loader* ]
  4. Kernel - [ *Central Core of the Operating System* ]
  5. Init **or** Systemd - [ *First Process which is started* ]
  6. Runlevels - [ *Tell me the mode* ]

  > Bios performs **POST** [ *power on self test* ] to make sure hardwares all are working fine and also retrieve the informations such as date, time etc from **CMOS** [ *Complementary Metal-Oxide Semiconductor* ]. It will then look for valid MBR and execute portion *sector0* which is the first *512 bytes* of partitioned data storage such as *Hard Disk* or *CD-ROM* etc.

  >>>>>>>>>>>>>>>>>&darr;

  > MBR stands for
