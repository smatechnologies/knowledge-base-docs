---
sidebar_label: 'AIX System/Symitar Upgrade Preparation for OpCon'
hide_title: 'true'
---

## AIX System/Symitar Upgrade Preparation for OpCon

Use this document if performing one of the following functions:

* AIX upgrades
* Applying firmware updates
* Setting up a backup or failover system
* Applying a Symitar Upgrade

### Overview 

Perform the following procedures for each Symitar box you are upgrading.

:::warning 

Installing AIX completely replaces the operating system, including the `/(root)` file system in addition to `/usr`, `/var`, and `/opt`. You will need to reinstall any software placed in these file systems by third parties (including software by third-party web developers) that was not obtained through Symitar. If you do not copy the `/ops/bin` and `/usr/local/lsam` directories into an area saved by the AIX install (e.g., `/SY</OP` or a home directory), you will need to reinstall RSJ and 
the LSAM software to your host before attempting to run OpCon jobs on the upgraded server.

:::

:::warning 

Simply performing a rcp copy will not properly install and configure SMA’s software. Failure to follow proper procedures will result in downtime.

:::

#### Validate sufficient space is available in all mounted partitions

1. Log on to the old host as root.
2. Issue the following command in a command window (telnet session): df
3. Validate that all entries in the `%Used` and `%Iused` are less than 90%. If any partition is more that 90% used in free space or free inodes, then files will need to be deleted by Symitar before proceeding. An alternative solution is to increase the size of the partition(s). A common symptom of insufficient space is that tar will give a premature end of file (EOD) message.

### Validate Symbolic link to LSAM

1. Issue the following commands in a command window: `cd /usr/local`
2. `ls -l` Then, press Enter.
3. Make note of **WHERE** the link of the LSAM is pointing. It should appear similar to the following: `lsam -> /usr/local/lsam_<version>`

### Validate the LSAM Port in Enterprise Manager

:::info Note 

The default Port (Socket Number) for the OpCon LSAM is 3100. In some cases, you may have the LSAM on a different Port. This document assumes Port 3100. If your Port does not match, replace all commands for 3100 with the Port specified in Enterprise Manager for your LSAM.

:::

1. Open Enterprise Manager.
2. Under the Administration topic, double-click Machines.
3. Under Select Machine, select the UNIX Machine to be upgraded from the drop-down list.
4. Under General Settings, make note of the Socket Number specified.
 
### To save SAM OpCon/xps Files located in /ops/bin and /usr/local/lsam

:::info Note 

UNIX is case-sensitive. Please enter all commands in the case presented.

:::

1. Disable Job Starts to the machine.
2. Wait for all jobs to finish for that machine.
3. Mark the AIX machine down in OpCon/xps.
4. Log on to the old host as **root**.
5. Issue the following commands in a command window :
6. `cd /usr/local/lsam` (or where your LSAM is located).
7. `bin/lsam3100 stop`
8. `cd /`
9. `tar -cvf /tmp/sma_ops.tar ops`
10. `cd /usr`
11. `tar -cvf /tmp/sma_local.tar local`
12. Re-validate that sufficient space exists in all disk partitions and that no premature end of file (EOF) messages were received during the tar process.
13. From a PC, transfer the files `/tmp/sma_ops.tar` and `/tmp/sma_local.tar` via FTP to the PC in binary mode. 

:::warning

Failure to transfer the files in binary mode will cause corruption to the tar files.

:::

### To restore SMA Files

1. In binary mode, transfer the file `sma_ops.tar` and `sma_local.tar` to `/tmp` on the Symitar box. Failure to transfer the files in binary mode will cause corruption to the tar files.
2. Issue the following commands in a command window :
3. `cd /`
4. `tar -xvf /tmp/sma_ops.tar`
5. Verify files exist in ops/bin by entering the following: ls –l /ops/bin
6. `cd /usr`
7. `tar -xvf /tmp/sma_local.tar`
8. Verify files exist in usr/local/lsam/bin by entering the following : ls –la /usr/local/lsam/bin
9. Run the following command to insure that the agent will start automatically when the host is rebooted: 
10. `cd /usr/local/lsam`
11. then enter: `bin/install_lsam_service `pwd` 3100`
 
:::info Note 

The ``` around pwd is a tick not a single quote. This symbol is located above the left-hand Tab key.

:::

1. If the procedure above does not work, run the following command:
2. `cd /usr/local/lsam`
3. then enter: `./bin/install_lsam_service `pwd` 3100`
4. Start your UNIX LSAM then enter the following in a command window:  
5. `cd /usr/local/lsam` 
6. then enter: `bin/lsam3100 start`
7. Start Communication for the UNIX machine in OpCon using the following steps:
8. Open Enterprise Manager.
9. Under the Administration topic, double-click Machines.
10. Under Select Machine, select the UNIX Machine to be started.
11. Under Communication Status, right-click over the graphic to enable the menu, then click Start Communication.