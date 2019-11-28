---
layout: post
title: "kali(vm虚拟机)在NET模式下不能联网的解决办法"
date: 2019-11-28
description: "kali(vm虚拟机)在NET模式下不能联网的解决办法"
tag: kali
---

### 检查网卡状态
首先`ifconfig`，可以看到没有在工作的网卡。然后`ifconfig -a`，可以看到`eth0`这块网卡并没有消失，只是罢工了。
接下来打开并且编辑`interfaces`配置文件。

```
leafpad /etc/network/interfaces
```

[![AHDS6.md.png](https://cdn.img.wenhairu.com/images/2019/11/28/AHDS6.md.png)](https://img.wenhairu.com/image/AHDS6)

可以看到`eth0`并未配置，这就是kali Net模式下不能上网的原因。找到问题关键后，我们现在就可以进行解决问题了。

[![AHWWp.md.png](https://cdn.img.wenhairu.com/images/2019/11/28/AHWWp.md.png)](https://img.wenhairu.com/image/AHWWp)

在配置文件后面加上
```
auto eth0
iface eth0 inet dhcp
```
保存，最后初始化网络
```
/etc/init.d/networking restart
```
重启网络之后，使得刚才的配置文件生效，done。

到此kali就可以上网了

<img src="https://miao.su/images/2019/08/09/9150e4e5gy1g0sab5n1uej2043037weba662a.jpg" height="100" alt="点个赞再走呗">

### 欢迎转载、留言

转载请注明出处：[小志博客](http://xiaozhi-chen.github.io) » [点击阅读原文](http://pengjuchen.tk/kali(vm虚拟机)在NET模式下不能联网的解决办法/)
<font face="黑体" color="red">**欢迎留言**</font>

<img src="https://miao.su/images/2019/08/09/6af89bc8gw1f8qnullt9ij20140140sibd843.jpg" height="100" alt="今天我也是一个小可爱">
