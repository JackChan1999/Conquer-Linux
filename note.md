## Linux下软件的安装

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

http://blog.csdn.net/u011982340/article/details/45843413

```
sudo add-apt-repository ppa:webupd8team/sublime-text-3
sudo apt-get update
sudo apt-get install sublime-text-installer
```

### 安装Linux版Typora

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

### 播放器

- smplayer
- vlc
- mplayer

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

```
sudo update-grub
```

- 重启电脑

## Ubuntu自动断网的问题

将/etc/ppp/options 文件中的 lcp-echo-failure 4 改为 lcp-echo-failure 40

或执行命令 sudo /etc/init.d/networking restart

## 常用快捷键

| 快捷键              | 功能说明        |
| ---------------- | ----------- |
| Ctrl+L           | 清屏快捷        |
| Ctrl + Alt + T   | 打开终端        |
| ctrl + shift + = | 放大终端窗口的字体显示 |
| ctrl + -         | 缩小终端窗口的字体显示 |
|                  |             |
|                  |             |
|                  |             |
|                  |             |
|                  |             |

