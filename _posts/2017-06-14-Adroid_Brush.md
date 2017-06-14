
# Android刷机
 
## 刷recovery

1.有BL的手机需要去手机官网申请解锁, 用解锁工具解锁手机

2.按音量减+开机键直到出现logo

3.手机连接到电脑

4.显示设备:
```sh
fastboot devices
```

5.刷入recovery：
```sh
fastboot flash recovery recovery包名
fastboot boot recovery包名
````

## ROOT
刷入第三方recovery后进入recovery安装supersu

安装re文件管理器，进入/system/app下可删除系统app

## 线刷
1.安装adb和fastboot

arch下运行:
```sh
pacman -S android-tools
```

2.线刷
进入手机的recovery，一般是开机键+音量上，进入sideload模式，等待发送zip包

运行:
```sh
adb device
```
会显示连接的设备，否则需要安装驱动


运行:
```sh
adb sideload 线刷包名
```

线刷过程中出现如下错误
error: insufficient permissions for device
解决方法：
```sh
su - root
adb kill-server
adb start-server
```

但每次切换终端或者重启之后还是要重新kill一下，可以通过以下方法永久解决：
```sh
chmod a+s adb路径
```
