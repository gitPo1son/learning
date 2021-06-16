# 修改 rhel-guest-image 的默认密码
```
# rhel: yum -y install guestfish
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
