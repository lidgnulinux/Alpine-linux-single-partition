# Memasang alpine linux dengan partisi tunggal.

## Langkah langkah :

1. Persiapan Partisi.
2. Format dan mount partisi.
3. Memilih mirror atau repositori.
4. Memasang system.
5. Mount filsesystem dan chroot.
6. Set password root.
7. Set hostname.
8. Set zona waktu.
9. Memasang grup dan update grub.
10. Keluar dan meng-unmount filesystem.
11. Tampilan grub.
12. Login.
<br>

1. Persiapan Partisi.

Untuk yang sudah menyiapkan satu partisi unalocated, mungkin bisa dilewati.

<br>

2. Format dan mount partisi.

Format partisi kita lalu mount ke /mnt.

Perintah :

> \# mkfs.ext4 /dev/sda1

> \# mount /dev/sda1 /mnt

![Format dan Mount](https://github.com/lidgnulinux/Alpine-linux-single-partition/blob/main/Dokumentasi/02.format-dan-mount.png "Format dan Mount")

<br>

3. Memilih mirror atau repositori.

Pilih mirror yang kita inginkan.

Perintah :

> \# setup-apkrepos

NB : Pilih nomor 1 saja, agar lebih cepat.

![Memilih Mirror](https://github.com/lidgnulinux/Alpine-linux-single-partition/blob/main/Dokumentasi/03.Pilih-Repo.png "Memilih Mirror")

<br>

4. Memasang system.

Kita pasang system alpine linux ke /mnt, kita memilih mode "sys", dan untuk BOOTLOADER, kita memilih "grub"

Perintah :

> \# export BOOTLOADER=grub

> \# setup-disk -m sys /mnt

![Install System](https://github.com/lidgnulinux/Alpine-linux-single-partition/blob/main/Dokumentasi/04.Install-system-1.png "Install System")

![Install System](https://github.com/lidgnulinux/Alpine-linux-single-partition/blob/main/Dokumentasi/04.Install-system-2.png "Install System")

<br>

5. Mount filsesystem dan chroot.

Sebelum kita melaukan chroot, kita perlu mount beberapa filesystem (dev, sys, proc)  terlebih dahulu.

> \# cd /mnt

> \# mount -o bind /dev dev/

> \# mount -o bind /sys sys/

> \# mount -t proc none proc

> \# chroot /mnt /bin/ash -l

![Mount Filesystem dan chroot](https://github.com/lidgnulinux/Alpine-linux-single-partition/blob/main/Dokumentasi/05.mount-fs-chroot.png "Mount Filesystem dan chroot")
<br>

6. Set password root.

Kita perlu mengatur passwd root.

Perintah :

> \# passwd

![Set password root](https://github.com/lidgnulinux/Alpine-linux-single-partition/blob/main/Dokumentasi/06.set-password.png "Set password root")

<br>

7. Set hostname.

Kita perlu mengatur hostname.

Perintah :

> \# echo "nama hostname" > /etc/hosname

<br>

8. Set zona waktu.

Kita perlu mengatur zona waktu.

Perintah :

> \# setup-timezone

<br>

9. Memasang grup dan update grub.

Memasang grub ke hardisk dan mengupdate-nya.

Perintah :

> \# grub-install /dev/sda

> \# grub-mkconfig -o /boot/grub/grub.cfg

<br>

10. Keluar dan meng-unmount filesystem.

Setelah dirasa cukup, kita bisa keluar dari chroot dan meng-unmount filesystem.

Perintah :

> \# cd /mnt

> \# umount dev

> \# umount sys

> \# umount proc

> \# cd /

> \# umount /mnt

<br>

11. Tampilan grub.

12. Login.
