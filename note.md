## Linux下软件的安装

```bash
sudo apt install netease-cloud-music
sudo apt install mpv
sudo apt install vlc
# 删除多余的软件包
sudo apt autoremove
# 安装deb软件
sudo dpkg -i softname.deb
# 卸载deb软件
sudo dpkg -r softname.deb
# 利用URL语法在命令行方式下工作的开源文件传输工具
sudo apt install curl
sudo npm install gitbook-cli -g
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
- [wps-office](http://wps-community.org/download.html)
- htop：一个比较漂亮的查看当前进程排名的软件
- Fontmatrix/font-manager/Unity Tweak Tool 字体安装管理

### Sublime的安装

官方安装教程：https://www.sublimetext.com/docs/3/linux_repositories.html

```bash
wget -qO - https://download.sublimetext.com/sublimehq-pub.gpg | sudo apt-key add -
# 稳定版
echo "deb https://download.sublimetext.com/ apt/stable/" | sudo tee /etc/apt/sources.list.d/sublime-text.list
sudo apt update
sudo apt install sublime-text
```

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

http://wps-community.org/download.html

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

字体缺失解决方案：http://community.wps.cn/wiki/No_necessary_symbol_fonts

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

### nodejs

https://nodejs.org/en/download/package-manager/

```bash
curl -sL https://deb.nodesource.com/setup_8.x | sudo -E bash -
sudo apt-get install -y nodejs
```

### calibre-ebook

https://calibre-ebook.com/download_linux

```bash
sudo -v && wget -nv -O- https://download.calibre-ebook.com/linux-installer.py | sudo python -c "import sys; main=lambda:sys.stderr.write('Download failed\n'); exec(sys.stdin.read()); main()"
```

### xmind

http://blog.csdn.net/faryang/article/details/70238326

https://askubuntu.com/questions/869848/how-to-install-run-xmind-v-8-in-ubuntu-16-04

```bash
unzip xmind-8-update7-linux.zip -d xmind
sudo ./setup.sh
# 然后直接打开XMind_amd64下的XMind
```

### [Fontmatrix](https://github.com/fontmatrix/fontmatrix)

安装字体，http://wiki.ubuntu.org.cn/%E5%AD%97%E4%BD%93

```bash
sudo mkfontscale
sudo mkfontdir
sudo fc-cache -fv
```

## Ubuntu下Git的安装与使用

http://www.linuxidc.com/Linux/2016-09/135527.htm

## MPlayer的安装

源码下载：http://www.mplayerhq.hu/MPlayer/releases/

## Systemd

Systemd 是 Linux 系统工具，用来启动[守护进程](http://www.ruanyifeng.com/blog/2016/02/linux-daemon.html)，已成为大多数发行版的标准配置。

http://www.ruanyifeng.com/blog/2016/03/systemd-tutorial-commands.html

## Ubuntu屏幕亮度无法调节的问题

安装显卡驱动后即可调节屏幕亮度：系统设置->软件和更新->附加驱动

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
# 查看网卡驱动是否加载
lsmod
# 加载网卡驱动
modprobe
# 开启网络管理器
service NetworkManager start
```

## 分辨率变化，密码正确无法进入桌面

安装显卡驱动，http://blog.csdn.net/jacktangyao/article/details/78239249

```bash
sudo apt update
sudo apt upgrade
# 注：装那个版本的需要根据自己的显卡型号等实际情况而定！
sudo apt-get install nvidia-384
sudo dpkg-reconfigure nvidia-384
sudo reboot
```

## 常用快捷键

| 快捷键             | 功能说明               |
| ------------------ | ---------------------- |
| Ctrl+L             | 清屏快捷               |
| Ctrl + Alt + T     | 打开终端               |
| Ctrl + shift + =   | 放大终端窗口的字体显示 |
| Ctrl + -           | 缩小终端窗口的字体显示 |
| Ctrl + h           | 显示隐藏文件或文件夹   |
| Ctrl + Alt + F2~F6 | 切换到命令行界面       |
| Ctrl + Alt + F7    | 切换到桌面界面         |

#### Shutter

截图快捷键Ctrl+Alt+A

1. 里面的快捷键命令用：shutter -s 或者shutter –select
2. 截取当前活动窗口：shutter -a （a表示active）
3. 截取拖拉区域：shutter -s （s是select之意），拖拉出矩形区域后按Enter。

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

## Wget

wget是一个命令行工具——是历史上最快的单线程传输工具，用于下载网站/批量文件，支持HTTP和FTP。 它的任务就是获取互联网。

https://www.cnblogs.com/wuheng1991/p/5332764.html
