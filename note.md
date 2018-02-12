## Linux下软件的安装

```bash
sudo apt install netease-cloud-music
sudo apt install mpv
sudo apt install vlc
```

https://www.zhihu.com/question/19811112?sort=created

- 搜狗输入法
- chrome浏览器/Firefox
- 网易云音乐
- 图片处理：GIMP
- 截屏：Shutter
- Xmind
- 翻墙：Shadowsocks
- 远程控制：TeamViewer
- GNOME 桌面环境，窗口管理Gtile

### Sublime的安装

官方安装教程：https://www.sublimetext.com/docs/3/linux_repositories.html

http://blog.csdn.net/u011982340/article/details/45843413

```bash
sudo add-apt-repository ppa:webupd8team/sublime-text-3
sudo apt-get update
sudo apt-get install sublime-text-installer
```

Sublime不能输入中文的问题

```bash
git clone https://github.com/lyfeyaj/sublime-text-imfix.git
cd sublime-text-imfix
./sublime-imfix
```

解决中文显示乱码：

在Sublime Text中，按Ctrl+Shift+P打开命令行模式，输入Install Package关键字，然后点击自动出现的下拉菜单里的第一项：Package Control: Install Package。此时会看到左下角有个等号来回动，稍等一会，会再次在命令行下弹出一个下拉菜单。输入“ConvertToUTF8”和“GBK Encoding Support”，选择匹配项，安装这两个插件。

### 安装Linux版Typora

http://support.typora.io/Typora-on-Linux/

```bash
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

### 播放器

- smplayer
- vlc
- mplayer
- mpv

### WPS的安装

64位安装32位beta版wps需要安装以下兼容库

```bash
# 该命令没有用
sudo apt-get install ia32-libs
# 需要使用下面的命令
sudo apt-get install libglib2.0-0:i386
# 添加对 i386 架构的支持
dpkg --add-architecture i386
# 移除对 i386 架构的支持
dpkg --remove-architecture i386
```

### 开发工具

- C/C++：CodeBlock
- Java：Intellij IDEA
- Python：PyCharm
- Android：Android studio
- 查看Jar包：JD-GUI
- HTML等编辑器：Sublime
- Atom编辑器
- Typora
- C/C++ IDE：Visual Studio Code（VSC）
- StarUML
- 最好用app：终端Terminal

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

```bash
sudo update-grub
```

- 重启电脑

## Ubuntu自动断网的问题

将/etc/ppp/options 文件中的 lcp-echo-failure 4 改为 lcp-echo-failure 40

或执行命令

```bash
# 查看系统网卡信息
ifconfig
# 查看无线连接情况
iwconfig
# 重启网络服务
sudo service networking restart
# 重启网络配置
sudo /etc/init.d/networking restart
sudo service network-manager restart
# 查看网卡的硬件信息
lshw -class network
# 激活网卡
sudo ifconfig 网卡设备名 up
# 查看网卡设备信息
lspci | grep -i net
# 打开硬件开关
rfkill list all
```

## 分辨率变化，密码正确无法进入桌面

http://blog.csdn.net/jacktangyao/article/details/78239249

```bash
sudo apt update
sudo apt upgrade
# 注：装那个版本的需要根据自己的显卡型号等实际情况而定！
sudo apt-get install nvidia-384
sudo dpkg-reconfigure nvidia-384
sudo reboot
```

## 常用快捷键

| 快捷键              | 功能说明        |
| ---------------- | ----------- |
| Ctrl+L           | 清屏快捷        |
| Ctrl + Alt + T   | 打开终端        |
| ctrl + shift + = | 放大终端窗口的字体显示 |
| ctrl + -         | 缩小终端窗口的字体显示 |

## 局域网工作机制和网络地址配置

### IP地址

```bash
ifconfig
# 关闭网卡
ifconfig netname down
# 启动网卡
ifconfig netname up
iwconfig
ping servername
```

### NETMASK

子网掩码：用来判断自己属于那个网段，255.255.255.0

网段的计算：IP地址的二进制 & 子网掩码的二进制 = 网段地址

192.168.33.2 & 255.255.255.0 = 192.168.33.0

### GATEWAY

网关，就是网络的总出口，也就是路由器的地址，路由器/交换机就是一个网关

### DNS

域名解析服务器，就是解析域名成对应的ip地址
填网关地址即可

```bash
# nameserver 192.168.1.1
sudo gedit /etc/resolvconf/resolv.conf.d/base 
```

### hosts文件

配置域名ip映射，ip地址和对应的主机名

## 网络配置
网卡的配置文件/etc/network/interfaces
DNS配置文件/etc/resolvconf/resolv.conf.d/base
```
auto eth0
iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0
gateway 192.168.1.1
```
命令配置网络
```bash
# 修改网卡IP和子网掩码
sudo ifconfig eth0 192.168.1.1 netmask 255.255.255.0

# 查看网关
route -n
# 修改网关
sudo route add default gw 192.168.0.1

sudo stop network-manager
sudo start network-manager
```

## 修复Win10启动项

在ubuntu试用系统下试用boot-repair修复

```bash
sudo -i
sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt update
sudo apt install boot-repair
sudo boot-repair
## 按照弹出框提示，将提示命令复制粘贴到终端，然后点击弹出框的forward按钮
```







