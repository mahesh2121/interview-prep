1. How to reduce the file system in Linux or Linux LVM? Can FS reduction happen online or not?

Answer:
Reducing a file system size in Linux or Linux LVM involves several steps and cannot be done online. The general process is:

    Backup Data: Always backup data before resizing the file system.
    Unmount the File System: You need to unmount the file system to resize it.

    bash

umount /dev/mapper/vgname-lvname

Check the File System: Check the file system for errors.

bash

e2fsck -f /dev/mapper/vgname-lvname

Resize the File System: Use resize2fs to resize the file system.

bash

resize2fs /dev/mapper/vgname-lvname SIZE

Reduce the Logical Volume: Use lvreduce to reduce the logical volume.

bash

lvreduce -L SIZE /dev/mapper/vgname-lvname

Remount the File System: Remount the file system.

bash

    mount /dev/mapper/vgname-lvname /mountpoint

2. How to delete a log whose ownership changed in the last 45 minutes from root to splunk?

Answer:
You can use the find command with the -mmin option to find files whose status was last changed in the last 45 minutes, and then delete them if their ownership is splunk.

bash

find /path/to/logs -type f -mmin -45 -user splunk -exec rm -f {} \;

3. How to scan the disk in Linux without restarting the server?

Answer:
To scan a new disk without restarting the server, you can use the partprobe or rescan-scsi-bus.sh command.

bash

# Using partprobe
partprobe

# Using rescan-scsi-bus.sh (part of sg3_utils package)
rescan-scsi-bus.sh

4. How to clear the inode, page cache, and dentries in Linux?

Answer:
To clear the inode, page cache, and dentries, you can use the sync command followed by echo commands to write to /proc/sys/vm/drop_caches.

bash

# Clear PageCache only

sync; echo 1 > /proc/sys/vm/drop_caches

# Clear dentries and inodes

sync; echo 2 > /proc/sys/vm/drop_caches


# Clear PageCache, dentries, and inodes

sync; echo 3 > /proc/sys/vm/drop_caches

5. What is the purpose of the /etc/fstab file in Linux? How many fields are there in the /etc/fstab file and what do they mean?

Answer:
The /etc/fstab file in Linux is used to define how disk partitions, various other block devices, and remote file systems should be mounted and integrated into the filesystem structure.

The /etc/fstab file contains six fields:

    File System: The device or remote filesystem to be mounted.
    Mount Point: The directory where the file system will be mounted.
    File System Type: The type of file system (e.g., ext4, xfs, nfs).
    Options: Mount options such as rw, auto, noauto, user, etc.
    Dump: A number indicating whether the file system should be dumped (backed up) by the dump command (0 or 1).
    Pass: A number indicating the order in which file systems should be checked by fsck at boot time. 0 means the file system is not checked.

Example entry in /etc/fstab:

bash

    /dev/sda1   /       ext4    defaults    1   1
