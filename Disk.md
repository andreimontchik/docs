# Utils
## iotop - IO usage monitor by process
1. Install: `sudo apt install oitop`
1. Run: `sudo iotop`

## iostat - disk utilization monitor for specific disks
1. Install: `sudo apt install sysstat`
1. Identify disk of interest: `sudo lsblk`
1. Monitor the utilization: `iostat -dm 1 nvme0n1 nvme1n1 nvme2n1`    

## nvme - disk health check utility
1. Install: `sudo apt install nvme-cli`
1. Check the overall disk health: `sudo nvme smart-log /dev/nvme0n1`
1. Review the SMART log: `sudo nvme error-log /dev/nvme0n1`

# How to
## Partition and format new Disk
1. Install `fdisk`: `sudo apt install fdisk`.
1. Install the `gdisk` util to create partitions larger than 2TB: `sudo apt install gdisk`.  
1. Identify the disk: `sudo fdisk -l`.
1. Run gdisk for the selected disk: `sudo gdisk /dev/nvme1n1`.
1. Select `n` to create new partition.
1. Accept the default partition number.
1. Accept the default starting and ending sectors.
1. Accept the default partition type.
1. After the partition is created, type p to review it.
1. Type w to write the changes to disk.
1. Confirm that the new partition was created: `lsblk -a`.
1. Format new partition: `sudo mkfs -t ext4 /dev/nvme1n1p1`.
1. Use `sudo lsblk -f` to confirm that the newly created partition is formatted. It should show the `ext4` FSTYPE for it.

## Create Mount
* Create mount:
  1. Create the new mount directory: `sudo mkdir /mnt/ledger`
  1. Check available partitions: `lsblk -a`.
  1. Mount available partition: `sudo mount /dev/nvme0n1p1 /mnt/ledger`
  1. Update the mount directory ownership: `sudo chown sol:sol /mnt/ledger`
  1. Add new mount to `/etc/fstab`: `/dev/nvme0n1p1 /mnt/ledger ext4 defaults 0 2`
  1. Run mounts `sudo mount -a` or restart the server.

## Check the disk speed
1. Format and mount the disk `fdisk -l`.
1. Write: `sudo dd if=/dev/zero of=/mnt/<mount name>/testfile bs=1M count=1000 conv=fdatasync`
1. Read: `sudo dd if=/home/sol/testfile of=/dev/null bs=1M`

# Tuning
## Increase number of allowed open file descriptors
1. Check: `ulimit -n`
1. Add the following to `/etc/security/limits.conf`:
```
*               soft     nofile         1000000 
*               hard     nofile         1000000
```
1. Reboot: `sudo reboot`.

# CLI
* Disks information: `sudo sfdisk -l` or `sudo lsblk -f`
* UUID of the host disks: `sudo blkid`
* Review the currently open files: `sudo lsof +D /dev/shm/` 
* Largest in current mount: `sudo du -a / | sort -n -r | head -n 10`   
* Largest in current directory: `sudo du -Sh * | sort -rh | head -10`   
* Size of all files and subdirs in current directory: `sudo du -ah --max-depth=1`
* Grand total of current directory: `du -sh` 