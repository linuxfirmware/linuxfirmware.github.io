# 在树莓派4B上安装Android 14

***警告：下载过程需要连接外网才能进行。翻墙后果自负！***

首先，准备好U盘并下载以下文件:  
从 <https://drive.google.com/file/d/1oby4-GwvaXnSA2Pu4xfjvMqf8lgaWzme> 下载Android 14 For Raspberry Pi

先解压下载好的Android镜像，然后把U盘插入电脑，使用命令
```
dd if=镜像名.img of=/dev/$DEVICEID bs=1M
```
这里的 镜像名.img 替换为你下载的镜像名称，$DEVICEID替换为你的U盘的设备ID，后面出现$DEVICEID也是这样。等待命令完成，然后运行
```
sync
```
来同步内存中的数据到U盘。执行完成后，运行命令
```
cfdisk /dev/$DEVICEID
```
先把除了Free Space之外的最后一个分区选中，用上下左右键选择resize，按两次回车  
再选择save，按回车，输入yes，按回车  
最后选择quit，按回车
然后再次输入sync。

输入命令
```
su -
#这里输入root密码
mount /dev/$DEVICEID1 /mnt
#比如这里我的设备ID是sdb，就是mount /dev/sdb1 /mnt
cd /mnt
echo "dtoverlay=android-usb" >> config.txt
```
移除U盘，插入树莓派，开机，我们就成功地在树莓派上安装了Android 14。
