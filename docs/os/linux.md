# Linux 通用的问题

## 查看系统依赖库
- `ldconfig -v`

## 查看二进制文件依赖

- `ldd` 

## /etc/fstab
```
UUID=9be2de0e-ef44-4288-9c88-58a9d87e06e0 /mnt/Data ext4 defaults 0 0
<fs spec> <fs file> <fs vfstype> <fs mntops> <fs freq> <fs passno>
<fs spec>：分区定位，可以给UUID或LABEL，例如：UUID=6E9ADAC29ADA85CD或LABEL=software 也可以用 device /dev/sda1
<fs file>：具体挂载点的位置，例如：/data<fs vfstype>：挂载磁盘类型,linux 分区一般为 ext4，windows 分区一般为 ntfs
<fs mntops>：挂载参数，一般为defaults
<fs freq>：磁盘检查，默认为 0 开机不检查磁盘 1 表示开机检查磁盘
<fs passno>：磁盘检查，默认为0，不需要检查

第一个叫fs_freq,用来决定哪一个文件系统需要执行dump操作，0就是不需要；
第二个叫fs_passno,是系统重启时fsck程序检测磁盘的顺序号 1 是root文件系统，2 是别的文件系统。fsck按序号检测磁盘，0表示该文件系统不被检测 dump 执行ext2的文件系统的备份操作 fsck 检测和修复文件系统
```

[Arch Linux Wiki fstab](https://wiki.archlinux.org/title/Fstab_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87)#.E8.87.AA.E5.8A.A8.E6.8C.82.E8.BD.BD)