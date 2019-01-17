# FileSystems - Useful issues about File Systems
## Use MHDDFS tool to mount more than one fs into a single one.
1. Install MHDDFS Tool 
   apt install mhddfs
2. Create files with zero
   dd if=/dev/zero of=1G bs=1000000 count=1000
   dd if=/dev/zero of=2G bs=1000000 count=2000
3. Configure loop devices
   losetup /dev/loop0 1G
   losetup /dev/loop1 2G
4. Format loop devices
   mkfs.btrfs /dev/loop0
   mkfs.btrfs /dev/loop1
5. Create dirs and mount loop devices on them
   mkdir a b c
   mount /dev/loop0 a
   mount /dev/loop1 b
6. Mount mhddfs to /c unioning /a and /b
   mhddfs a/ b/ c/
7. Umount all, Remove all
   umount /c /a /b
   losetup -d /dev/loop0
   losetup -d /dev/loop1
