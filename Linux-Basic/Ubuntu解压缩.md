## ZIP

zip可能是目前使用得最多的文档压缩格式。它最大的优点就是在不同的操作系统平台，比如Linux， Windows以及Mac OS，上使用。缺点就是支持的压缩率不是很高，而tar.gz和tar.gz2在压缩率方面做得非常好。闲话少说，我们步入正题吧：

我们可以使用下列的命令压缩一个目录：

```bash
# zip -r archive_name.zip directory_to_compress
```

下面是如果解压一个zip文档：

```bash
# unzip archive_name.zip -d unzipdir
```

## TAR

Tar是在Linux中使用得非常广泛的文档打包格式。它的好处就是它只消耗非常少的CPU以及时间去打包文件，他仅仅只是一个打包工具，并不负责压缩。下面是如何打包一个目录：

```bash
# tar -cvf archive_name.tar directory_to_compress
```

如何解包：

```bash
# tar -xvf archive_name.tar.gz
```

上面这个解包命令将会将文档解开在当前目录下面。当然，你也可以用这个命令来捏住解包的路径：

```bash
# tar -xvf archive_name.tar -C /tmp/extract_here/
```

## TAR.GZ

这种格式是我使用得最多的压缩格式。它在压缩时不会占用太多CPU的，而且可以得到一个非常理想的压缩率。使用下面这种格式去压缩一个目录：

```bash
# tar -zcvf archive_name.tar.gz directory_to_compress
```

解压缩：

```bash
# tar -zxvf archive_name.tar.gz
```

上面这个解包命令将会将文档解开在当前目录下面。当然，你也可以用这个命令来捏住解包的路径：

```bash
# tar -zxvf archive_name.tar.gz -C /tmp/extract_here/
```

## TAR.BZ2

这种压缩格式是我们提到的所有方式中压缩率最好的。当然，这也就意味着，它比前面的方式要占用更多的CPU与时间。这个就是你如何使用tar.bz2进行压缩。

```bash
# tar -jcvf archive_name.tar.bz2 directory_to_compress
```

上面这个解包命令将会将文档解开在当前目录下面。当然，你也可以用这个命令来捏住解包的路径：

```bash
# tar -jxvf archive_name.tar.bz2 -C /tmp/extract_here/
```
## tar.xz

```bash
# 把xz解压成tar文件
xz -d filename
```

## RAR

```bash
# 压缩
rar a 生成的压缩文件的名字 压缩的文件或目录
# 解压rar文件，不保存原文件目录结构
rar e filename.rar
# 解压rar文件，保存原文件目录结构
rar x filename.rar
```
## 7z

### 安装方法

```
sudo apt-get install p7zip-full
```

### 解压文件

```
7z x manager.7z -r -o /home/xx
```

解释如下：

- x 代表解压缩文件，并且是按原始目录解压（还有个参数 e 也是解压缩文件，但其会将所有文件都解压到根下，而不是自己原有的文件夹下）manager.7z 是压缩文件，这里大家要换成自己的。如果不在当前目录下要带上完整的目录

- -r 表示递归所有的子文件夹

- -o 是指定解压到的目录，这里大家要注意-o后是没有空格的直接接目录

### 压缩文件

```
7z a -t7z -r manager.7z /home/manager/*
```

解释如下：

- a 代表添加文件／文件夹到压缩包
- -t 是指定压缩类型 一般我们定为7z
- -r 表示递归所有的子文件夹，manager.7z 是压缩好后的压缩包名，/home/manager/* 是要压缩的目录，＊是表示该目录下所有的文件。

## 总结

相同之处：
```
tar/rar/zip  参数  生成的压缩文件的名字   压缩的文件或目录 --- 压缩的时候的语法
tar/rar/unzip 参数 压缩包的名字  参数(rar没有参数)  解压缩目录 -- 解压缩语法
```