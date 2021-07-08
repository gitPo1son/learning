# 修改 rhel-guest-image 的默认密码
```
# rhel: yum -y install guestfish
        yum install libguestfs libguestfs-tools 
        yum install '*guestf*'
        
        
# fedora: yum -y install libguestfs-tools

1.生成密码
# openssl passwd -1 redhat
$1$QiSwNHrs$uID6S6qOifSNZKzfXsmQG1

2.修改密码
# guestfish --rw -a ./rhel-guest-image-7.1-20150224.0.x86_64.qcow2
><fs> run
><fs> list-filesystems
><fs> mount /dev/sda1 /
><fs> vi /etc/shadow

NOTE: after you perform the following steps you use "quit" to exit. 
DO NOT EXIT NOW, proceed with the following steps
```

# 根目录 / 扩容
```
1.查看VG情况
# vgdisplay

2.扩容
# lvextend -l +100%FREE /dev/mapper/master--vg-root

3.查看实际磁盘大小
# df -h

4.查看文件系统格式
# blkid

5.同步磁盘空间
# resize2fs /dev/mapper/master--vg-root (针对ext 文件系统)
# xfs_growfs  /dev/mapper/master--vg-root  (针对xfs文件系统)

6.查看实际磁盘空间
# df -h
```

