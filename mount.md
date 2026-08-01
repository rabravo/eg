# mount

mount a NTFS device with specific uid/gid

    sudo mount -t ntfs -o umask=0022,gid=33,uid=33 /dev/sdX /media/foldername


mount a USB drive (exfat)

    sudo mount -t exfat /dev/sdX /media/foldername


mount all devices listed in /etc/fstab

    mount -a


mount a remote CIFS/Samba share

    sudo mount //server/share -t cifs -o uid=1001,gid=1001,username=YOURUSER /media/remote


mount a Mac HFS+ drive with read/write

    sudo mount -t hfsplus -o force,rw /dev/sdX /path/to/mountpoint



# Detect Devices

list connected block devices

    ls /dev | grep sd


show partition table and sizes

    sudo fdisk -l


