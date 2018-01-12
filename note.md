## 安装Linux版Typora

http://support.typora.io/Typora-on-Linux/

```
# optional, but recommended
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys BA300B7755AFCFAE

# add Typora's repository
sudo add-apt-repository 'deb https://typora.io ./linux/'
sudo apt-get update

# install typora
sudo apt-get install typora

# upgrade all packages include Typora
sudo apt-get upgrade
```

## Ubuntu下Git的安装与使用

http://www.linuxidc.com/Linux/2016-09/135527.htm

## MPlayer的安装

源码下载：http://www.mplayerhq.hu/MPlayer/releases/

## Systemd

Systemd 是 Linux 系统工具，用来启动[守护进程](http://www.ruanyifeng.com/blog/2016/02/linux-daemon.html)，已成为大多数发行版的标准配置。

http://www.ruanyifeng.com/blog/2016/03/systemd-tutorial-commands.html

## Ubuntu屏幕亮度无法调节的问题

试了很多其他的方法，都没有用，可能是跟具体的笔记本品牌有关，以下的方法仅适用于华硕笔记本

可以正常使用Fn+F5调暗，Fn+F6调亮，或者直接在系统设置中的亮度和锁屏设置亮度

- 修改/etc/default/目录下文件grub

将15~16行内容

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```

修改为如下内容

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux"
GRUB_CMDLINE_LINUX="acpi_backlight=asus"
```

- 在终端输入命令 

```
sudo update-grub
```

- 重启电脑