title: 双系统重装Windows修复引导grub2
date: 2016-05-15 00:24:50
tags: [双系统, grub2]
---

###### OS：openSuSE Leap-42.1 Win8

　　双系统openSUSE42.1和Win7，想要把Win7换成Win8，安装Win8，会覆盖grub2引导。于是现在U盘上装了openSUSE42.1做启动盘，以便安装完win8后修复。
　　主要做法是，先挂载root，再把其他分区挂载到root下面，swap无须挂载。例如：

```bash
#root
mount /dev/sdax /mnt

#boot
mount /dev/sday /mnt/boot

#home
mount /dev/sday /mnt/home
```

　　我用的是LVM，其实做法差不多，只不过应该在/dev/mapper下找对应分区。而boot分区并不在LVM中，所以boot挂载和上面一样。

```bash
#root
mount /dev/mapper/XX-root /mnt

#home
mount /dev/mapper/XX-home /mnt/home
```

　　之后执行：

```bash
mount -t proc proc /mnt.proc
mount --rebind sys /mnt/sys
mount --rebind dev /mnt/dev

chroot /mnt /bin/bash
```

　　生成grub2文件：

```bash
grub2-mkconfig -o /boot/grub2/grub.cfg

grub2-install /dev/sda

exit
reboot
```