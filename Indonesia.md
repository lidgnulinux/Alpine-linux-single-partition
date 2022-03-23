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
<br>
Langkah ini bisa dilewati jika anda sudah punya satu partisi unalocated.

<br>

2. Format dan mount partisi.

Format partisi ke ext4 dan mount ke /mnt.
Perinntah :

> \# mkfs.ext4 /dev/sda1
> \# mount /dev/sda1 /mnt

3. Mem
