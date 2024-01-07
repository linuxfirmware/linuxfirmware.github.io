# 在树莓派4B上运行Lineage OS 16

***警告：下载过程需要连接外网才能进行。翻墙后果自负！***

首先，下载以下文件:  
从 <https://konstakang.com/devices/rpi4/LineageOS16.0> 下载Lineage OS For RPI

先解压下载好的lineageos镜像，然后把SD卡插入电脑，使用命令
```
dd if=lineage镜像名.img of=/dev/$DEVICEID bs=1M
```
这里的lineage镜像名.img替换为你下载的镜像名称，$DEVICEID替换为你的SD卡的设备ID。等待命令完成，然后运行
```
sync
```
来同步内存中的数据到SD卡。执行完成后，运行命令
```
cfdisk /dev/$DEVICEID
```
先把除了Free Space之外的最后一个分区选中，用上下左右键选择resize，按两次回车  
再选择save，按回车，输入yes，按回车  
最后选择quit，按回车
然后再次输入sync。移除SD卡，插入树莓派，开机，我们就成功地在树莓派上安装了Lineage OS 16。
