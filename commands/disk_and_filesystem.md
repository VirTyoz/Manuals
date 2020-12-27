# Disks and partitions
View
```
fdisk -l
lsblk -o NAME,SIZE,FSTYPE,TYPE,MOUNTPOINT
lsblk -f
findmnt
mount | column -t
```

Tell the Linux kernel about the presence and numbering of on-disk partitions, update the specified partitions
```
partx -u /dev/sda
```

Inform the OS of partition table changes
```
partprobe
```

Re-scan disk
```
find /sys -iname 'scan'
echo 1>/sys/class/block/sda/device/rescan
```

* SCSI
```
echo "- - -" > /sys/class/scsi_host/hostX/scan
```

Copy partition
```
dd if=/dev/sda of=/dev/sdb
```

Copy partition table
MBR
```
sfdisk -d /dev/sda | sfdisk /dev/sdb
```

GPT sda to sdb
```
sgdisk -R=/dev/sdb /dev/sda
```

Formatting
```
mkfs.ext4 /dev/sda
```

Partition synchronization
```
rsync -avzr /var/log/ /mnt/
```

What kind of process working with partition
```
lsof | grep '/var/log'
```

Show information of dick
```
hdparm -I /dev/sda
```

## Dd

Burn the image
```
sudo dd oflag=direct status=progress if=image.iso of=/dev/sd* bs=1M; sync
```

dd with status
```
pv -tpreb /dev/sdb | dd of=~/sdb.img bs=1M
```

Make emty files with size
```
dd if=/dev/zero of=output.dat  bs=24M  count=1
dd if=/dev/zero of=output.dat  bs=1M  count=24
```

Copy cd-rom
```
dd if=/dev/cdrom of=/opt/cd.iso bs=1M
```

Create image
```
dd if=/dev/sdc of=flash.img bs=512
ddrescue /dev/sdc flash.img /tmp/flash.log
dcfldd if=/dev/sda1 hash=md5 of=/media/forensic_disk_image.dd bs=512 noerror
```

Ignore Errors
```
dd if=/dev/sdc of=flash.img bs=1M conv=noerror
```

## S.M.A.R.T
View
```
smartctl -a /dev/sda
```

File system resize
```
resize2fs /dev/sda
```

## Raid
Information
```
cat /proc/mdstat
```

Add disk
```
mdadm --manage /dev/md_number --add /dev/sda
```

Create the raid with one disk
```
mdadm --create --verbose /dev/md_number --level=1 --raid-devices=1 /dev/sda
```

Change number of disks
```
mdadm --grow /dev/m_number --raid-devices=2
```

## Check and repair the file system
### e2fsprogs
The defragmentation check ext4 partition
```
e4defrag -c /dev/sda
```
Defragmentation ext4 partition
```
e4defrag /dev/sda
```

Check the result ⩽0.3% non-contiguous
```
fsck -n /dev/sda
```

### Fsck
Check the file system
```
fsck -CMn /dev/sda1
```

Force check the file system
```
fsck -CMnf /dev/sda1
```

Repair the file system
```
fsck -p /dev/sda1
```

Repair superblocks
* View backup superblocks
```
mkfs -t ext4 -n /dev/sda1
```

* Recovery
```
fsck -b "superblocks" /dev/sda1
```

Find badblocks
```
fsck -c /dev/sda1
```

### XFS_check
```
Check the partition
xfs_check /dev/sdb1
```

### XFS_repair
Check the partition
```
xfs_repair -n /dev/sdb1
```

Repair the file system
```
xfs_repair /dev/sdb1
```

Force Log Zeroing
```
xfs_repair -L  /dev/sdb1
```

### XFSsdump

### XFS_copy
