## Linux常用指令

```bash
1. 查看目录下有什么文件/目录
    > ls            //list列出目录的文件信息
    > ls  -l        //list -list以“详细信息”查看目录文件
    > ls  -a        //list  -all查看目录“全部”(包括隐藏文件)文件
    > ls  -al       //list  -all list 查看目录“全部”(包括隐藏文件)文件,以“详细信息”展示
    > ls  目录      //查看指定目录下有什么文件

2. 进行目录切换
    > cd  dirname       //进行目录切换
    > cd  ..            //向上级目录切换
    > cd  ~    或 cd     //直接切换到当前用户对应的家目录

3. 查看完整的操作位置
    > pwd

4. 用户切换
    > su -  或  su - root       //向root用户切换
    > exit          //退回到原用户
    
    > su 用户名     //普通用户切换

    多次使用su指令，会造成用户的“叠加”：
    (su和exit最好匹配使用)
    jinnan--->root--->jinnan--->root--->jinnan

5. 查看当前用户是谁
    > whoami

6. 图形界面 与 命令界面 切换
    root用户可以切换
    ># init 3
    ># init 5

7. 查看一个指令对应的执行程序文件在哪
    > which  指令


8. 目录相关操作
    1) 创建目录 make directory
    > mkdir  目录名字
    > mkdir -p newdir/newdir/newdir       //递归方式创建多个连续目录
      
      //新的多级目录数目如果大于等于2个，就要使用-p参数
      mkdir      dir/newdir                //不用-p参数
      mkdir  -p  dir/newdir/newdir         //使用-p参数
      mkdir  -p  newdir/newdir/newdir      //使用-p参数

    2) 移动目录(文件和目录)  move
    > mv  dir1  dir2            //把dir1移动到dir2目录下
    > mv  dir1/dir2  dir3       //把dir2移动到dir3目录下
    > mv  dir1/dir2  dir3/dir4  //把dir2移动到dir4目录下
    > mv  dir1/dir2  ./         //把dir2移动到当前目录下

    3) 改名字  (文件和目录)
    > mv  dir1  newdir          //修改dir1的名字为newdir
    
    mv是“移动” 和 “改名字” 合并的指令
    > mv  dir1  ./newdir            //dir1移动到当前目录下 并改名字为newdir
    > mv  dir1/dir2  dir3           //dir2移动到dir3目录下， 并改名字为“原名”
    > mv  dir1/dir2  dir3/newdir    //dir2移动到dir3目录下，并改名字为“newdir”
    > mv  dir1/dir2  dir3/dir4      //dir2移动到dir4目录下， 并改名字为“原名”
    > mv  dir1/dir2  dir3/dir4/newdir   //dir2移动到dir4目录下， 并改名字为“newdir”

    4) 复制(改名字)(文件和目录) copy
    ① 文件的复制
    > cp  file1  dir/newfile2         //file1被复制一份到dir目录下，并改名字为“newfile2”
    > cp  file1  dir               //file1被复制一份到dir目录下，并改名字为“原名”
    > cp  dir1/filea  dir2/newfile  //filea被复制一份到dir2目录下，并改名字为“newfile”
    ② 目录的复制(需要设置-r[recursive递归]参数，无视目录的层次)
    > cp -r dir1   dir2             //dir1被复制到dir2目录下,并改名字为"原名"
    > cp -r  dir1/dir2  dir3/newdir  //dir2被复制到dir3目录下,并改名字为"newdir"
    > cp -r  dir1/dir2  dir3/dir4   //dir2被复制到dir4目录下,并改名字为"原名"
    > cp -r  dir1/dir2  dir3/dir4/newdir   //dir2被复制到dir4目录下,并改名字为"newdir"
    > cp -r  dir1  ../../newdir     //dir1被复制到上两级目录下,并改名字为"newdir"

    ⑤ 删除(文件和目录)remove
    > rm  文件
    > rm -r  目录           //-r[recursive递归]递归方式删除目录
    > rm -rf  文件/目录     //-r force  递归强制方式删除文件
                            force强制，不需要额外的提示
      rm  -rf  /

9. 文件操作
    1) 查看文件内容
        cat  filename       //打印文件内容到输出终端
        more  filename      //通过敲回车方式逐行查看文件的各个行内容
                            //默认从第一行开始查看
                            //不支持回看
                            //q 退出查看
        
        less                //通过“上下左右”键查看文件的各个部分内容
                            //支持回看
                            //q 退出查看
        
        head -n filename    //查看文件的前n行内容
        tail -n filename    //查看文件的最末尾n行内容
        
        wc filename         //查看文件的行数

    2) 创建文件
        > touch  dir1/filename
        > touch  filename
    3) 给文件追加内容
        > echo 内容 > 文件名称      //把“内容”以[覆盖写]方式追加给“文件”
        > echo 内容 >>  文件名称    //把“内容”以[追加]形式写给“文件”
        (如果文件不存在会创建文件)

10. 用户操作
    配置文件：/etc/passwd
    1) 创建用户 user add
    ># useradd
    ># useradd  liming          //创建liming用户，同时会创建一个同名的组出来
    ># useradd  -g 组别编号  username   //把用户的组别设置好，避免创建同名的组出来
    ># useradd  -g 组编号  -u 用户编号  -d 家目录   username

    2) 修改用户 user modify
    ># usermod  -g 组编号  -u 用户编号  -d 家目录  -l 新名字  username
    (修改家目录时需要手动创建之)

    3) 删除用户 user delete
    ># userdel  username
    ># userdel -r  username    //删除用户同时删除其家目录


    4) 给用户设置密码，使其登录系统
    > passwd  用户名

11. 组别操作
    配置文件： /etc/group
    1) 创建组 group add
    ># groupadd  music
    ># groupadd  movie
    ># groupadd  php

    2) 修改组 group modify
    ># groupmod  -g gid  -n 新名字  groupname

    3) 删除组 group delete
    ># groupdel  groupname    //组下边如果有用户存在，就禁止删除

12. 查看指令可设置的参数
    > man 指令
```

