# Install Alpine linux on a single partition.

## Steps :

1. Partition Preparation.
2. Format and mount partition.
3. Choose mirror or repository.
4. Install system.
5. Mount filsesystem and chroot.
6. Set root password.
7. Set hostname.
8. Set time Zone.
9. Install grup and update grub.
10. Exit and unmount filesystem.
11. Grub appearance.
12. Login.
<br>

1. Partition Preparation.

If you already prepare one unallocated partition, you can skip this step.

<br>

2. Format and mount partition.

Format partition and then mount it to /mnt.

Command :

> \# mkfs.ext4 /dev/sda1

> \# mount /dev/sda1 /mnt

![Format and Mount](https://github.com/lidgnulinux/Alpine-linux-single-partition/blob/main/Dokumentasi/02.format-dan-mount.png "Format and Mount")

<br>

3. Choose mirror or repository.

Choose your desired mirror.

Command :

> \# setup-apkrepos

NB : Just choose number 1, it works anyway.

![Choose Mirror](https://github.com/lidgnulinux/Alpine-linux-single-partition/blob/main/Dokumentasi/03.Pilih-Repo.png "Choose Mirror")

<br>

4. Install system.

Install alpine linux system to /mnt, we choose "sys" mode, and for BOOTLOADER, we choose "grub".

Command :

> \# export BOOTLOADER=grub

> \# setup-disk -m sys /mnt

![Install System](https://github.com/lidgnulinux/Alpine-linux-single-partition/blob/main/Dokumentasi/04.Install-system-1.png "Install System")


![Install System](https://github.com/lidgnulinux/Alpine-linux-single-partition/blob/main/Dokumentasi/04.Install-system-2.png "Install System")

<br>

5. Mount filsesystem and chroot.

Before we perform chroot, we need to mount some filesystems (dev, sys, proc) first.

> \# cd /mnt

> \# mount -o bind /dev dev/

> \# mount -o bind /sys sys/

> \# mount -t proc none proc

> \# chroot /mnt /bin/ash -l

![Mount Filesystem and chroot](https://github.com/lidgnulinux/Alpine-linux-single-partition/blob/main/Dokumentasi/05.mount-fs-chroot.png "Mount Filesystem and chroot")
<br>

6. Set root password.

We need to set root passwd.

Command :

> \# passwd

![Set password root](https://github.com/lidgnulinux/Alpine-linux-single-partition/blob/main/Dokumentasi/06.set-password.png "Set password root")

<br>

7. Set hostname.

We need to set hostname.

Command :

> \# echo "your hostname" > /etc/hosname

![Set hostname](https://github.com/lidgnulinux/Alpine-linux-single-partition/blob/main/Dokumentasi/07.set-hostname.png "Set hostname")

<br>

8. Set time Zone.

We need to set time Zone.

Command :

> \# setup-timezone

![Set time Zone](https://github.com/lidgnulinux/Alpine-linux-single-partition/blob/main/Dokumentasi/08.set-timezone.png "Set time Zone")

<br>

9. Install grup and update grub.

Install grub to hardisk and update grub.

Command :

> \# grub-install /dev/sda

> \# grub-mkconfig -o /boot/grub/grub.cfg

![Install grup and update grub](https://github.com/lidgnulinux/Alpine-linux-single-partition/blob/main/Dokumentasi/09.install-grub-update-grub.png "Install grup and update grub")

<br>

10. Exit and unmount filesystem.

After we feel sure, we can exit from chroot and unmount filesystem.

Command :

> \# exit 

> \# cd /mnt

> \# umount dev

> \# umount sys

> \# umount proc

> \# cd /

> \# umount /mnt

![Exit and unmount filesystem](https://github.com/lidgnulinux/Alpine-linux-single-partition/blob/main/Dokumentasi/10.exit-umount.png "Exit and unmount filesystem")

<br>

11. Grub appearance.

If we are lucky, we will face GRUB, after we reboot.

![GRUB](https://github.com/lidgnulinux/Alpine-linux-single-partition/blob/main/Dokumentasi/11.grub.png "GRUB")

<br>

12. Login.

If we are lucky, we will face login prompt.

![Login](https://github.com/lidgnulinux/Alpine-linux-single-partition/blob/main/Dokumentasi/12.login.png "Login")
