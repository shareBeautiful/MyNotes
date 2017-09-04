---
title: Linux常用指令
date: 2017-08-28 22:07:27
tags: Linux
categories: Linux
---

## 1.查看目录下有什么文件/目录
    > ls     //list 列出目录的文件信息
    > ls -l或ll  //list -list以详细列表形式 查看目录文件
    > ls -   //list -all查看目录“全部”(隐藏)文件
    > ls -al     //list -all list查看目录“全部”(隐藏)文件详细信息
    > ls 目录  //查看指定目录下有什么文件
    > ls -i      //查看文件的索引号码


## 2.进行目录切换
    > cd dirname     //进行目录切换
    > cd ..          //上一级目录切换
    > cd ~ 或 cd  //直接切换到当前用户对应的家目录


## 3.查看完整的操作位置
    >pwd

## 4.用户切换
    > su -  或 su - root //普通用户切换root用户；
    > exit      //退回到原先的用户
    > su 用户名    //普通用户切换
    多次使用su指令，会造成用户的“叠加”


## 5.查看当前用户是谁
    > whoami


## 6.图形界面 与 命令界面 切换
    root用户可以切换
    ># init 3   //图像界面 切换 命令界面
    ># init 5   //命令界面 切换 图形界面


## 7.查看一个指令对应的执行程序文件在哪
    > which 指令、


## 8.目录相关操作

    1) 创建目录 make directory
    > mkdir 目录名字
    > mkdir -p newdir/newdir/newdir     //创建多个级别关系目录
      //新的多级目录数目如果大于等于2个，就要使用 -p 参数
      mkdir     dir/newdir      //不用 -p 参数
      mkdir     dir/newdir/newdir   //使用 -p 参数

    2) 移动目录(文件和目录) move
    > mv dir1 dir2              //把dir1移动到dir2目录下
    > mv dir1/dir2 dir3         //把dir2移动到dir3目录下
    > mv dir1/dir2 dir3/dir4    //把dir2移动到dir4目录下
    > mv dir1/dir2 ./           //把dir2移动到当前目录下

    3) 改名字
    > mv dir1 newdir            //修改dir1的名字为newdir
    //mv是“移动” 和 “该名字” 合并的指令
    > mv dir1 ./newdir          //dir1移动到当前目录下 并改名为newdir
    > mv dir1/dir2 dir3/newdir  //dir2移动到dir3目录下，并改名为newdir
    > mv dir1/dir2 dir3/dir4    //dir2移动到dir4目录下，并改名为原名
    > mv dir1/dir2 dir3/dir4/newdir /dir2移动到dir4目录下，并改名为newdir

    4) 目录复制(文件和目录)copy
        ①文件的复制
    > cp file1 dir/newfile2     //file1被复制一份到dir目录下并改名字为newfile2
    > cp file1 dir              //file1被复制一份到dir目录下并改名字为原名
    > cp dir1/filea dir2/newfile //filea被复制一份到dir2录下并改名字为newfile
        ②目录的复制(需要设置-r[recursive递归]参数，无视目录的层次)
    > cp -r dir1 dir2               //dir1被复制到dir2目录下，并改名字为原名
    > cp -r dir1/dir2 dir3/newdir   //dir2被复制到dir3目录下，并改名字为newdir;
    > cp -r dir1 ../../newdir       //dir1被复制到上两级目录下，并改名字为newdir

    5）删除(文件和目录)remove
    > rm 文件
    > rm -r 目录          //-r 递归方式删除目录
    > rm -rf 文件/目录      //-r force 递归强制方式删除文件和目录
                            //force强制，不需要额外的提示 rm -rf /
## 9.文件操作
    
    1) 查看文件内容
        cat filename        //打印文件内容到输出终端
        more filename       //通过敲回车的方式逐行查看文件的各个行内容
                            //默认从第一行开始查看  不支持回看 q 退出查看
        less                //通过“上下左右”键查看文件的各个部分内容
                            //支持回看
                            //q 退出查看
        head -n filename    //n(数字)查看文件的前n行内容
        tail -n filename    //n(数字)查看文件的最末位n行内容
        wc filename         //查看文件的行数

    2) 创建文件
        > touch dir1/filename
        > touch filename

    3) 给文件追加内容  //如果文件不存在会创建文件
        > echo "内容" > 文件名称      //把“内容”以覆盖写方式追加给"文件"
        > echo 内容 >> 文件名称           //把"内容" 以追加的形式写给 "文件"

## 10.用户的操作

    配置文件: /etc/passwd
    1) 创建用户 user add
        ># useradd
        ># useradd liming           //创建一个liming用户 的 同时会创建一个同名组
        ># useradd -g 组别编号 username     //把用户的组别设置好，避免创建同名的组出来
        ># useradd -g 组编号 -u 用户编号 -d 家目录 username

    2) 修改用户 user modify
        ># usermod -g 组编号 -u 用户编号 -d 家目录 -l 新名字 username
        （修改家目录时需要手动创建之）

    3) 删除用户 user delete
        ># userdel username             //删除用户，不删除家目录
        ># userdel -r username          //删除用户同时删除家目录

    4）给用户设置密码，使其登陆系统
        > passwd username

## 11.组别的操作

    配置文件：/etc/group
    1) 创建组 group add
        ># groupadd music
        ># groupadd php
        ># groupadd movice
        ># groupadd -g 组编号

    2) 修改组 group modify
        ># groupmod -g gid -n 新名字 groupname

    3) 删除组 group delete
        ># groupdel groupname           //如果组别下有用户存在，禁止删除

## 12.查看指令可设置的参数
    > man 指令

## 13.给文件设置权限
    1） 字母相对方式设置权限   
    // 针对一个组别设置权限，其他组别权限没有变化，称为 “相对方式” 权限设置  
    chmod指令
    chmod u+rwx filename                //给filename文件的主人增加 “读、写、执行” 权限
    chmod g-rx filename                 //给filename文件的同组用户 去掉 “读、执行”权限

    chmod u+/-rwx,g+/-rwx,o+/-rwx filename
    说明：
    ① 每个单元"+" "-"只能使用一个
    ② 可以同时给一个或多个组设置权限，组别之间使用","分割
    ③ 每个单元的权限可以是"rwx"中的一个或多个
    > chmod u+w,g-rx,o+rw filename      //给filename文件主人增加 写 权限，同组删除 读、执行 权限，
                                        //其他用户组增加 读、写 权限
    > chmod u+w,u-x filename            //给filename文件的主人 “增加写权限” 同时 “删除执行权限”

    > chmod +/-rwx filename             //无视具体组别，统一给全部的组设置权限
    > chmod +rw filename                //给filename用户全部增加 读，写 权限

    2) 数字绝对方式设置权限
    r读:4        w写:2    x执行:1
    0: 没有权限
    1：执行
    2：写
    3：写，执行
    4：读
    5：读，执行
    6：读，写
    7：读，写，执行

    chmod ABC filename              //ABC分别代表主人，同组，其他组用户的权限
    > chmod 753 filename            //主人rwx;同组rx,其他组wx

    问：字母相对 和 数字绝对 方式权限设置取舍？
    修改的权限相对比较少的时候使用 "字母相对" 方式
    修改的权限相对比较多的时候使用 "数字绝对" 方式


## 14. 在文件中查找内容
    grep 被搜寻内容 文件
    > grep hello passwd             //在passwd文件中搜索hello内容，
                                    //会把hello所在行的内容都打印到终端显示

## 15. 计算文件占用磁盘空间大小
    > ps -A                         //查看系统活跃进程progress
    > kill -9 pid                   //杀死指定 pid进程号 的进程
    > du -h 目标(file/dir)            //以K,M,G为单位显示文件或目录占据磁盘空间的大小(4k)

## 16. 设置系统时间
    > date                          //查看时间
    > date -s "2016-07-27 23:59:59" //给系统设置 指定 时间
## 17. 查看系统分区
    > df -lh                        //查看系统分区情况

## 18.文件查找
    find 查找目录 选项 选项值 选项 选项值 ...
    1） -name选项 根据名字进行查找
        > find / -name passwd[完整名字]     //'递归遍历'/ 全部目录最浅极其内部深层目录，寻找passwd文件
        > find / -name "pas*"[模糊查找] //在系统全部目录中模糊查找一个文件名字是pas开始的文件
        > find / -name "*er*"           //文件名字有出现er即可，不要求位置

    2） 限制查找的目录层次 -maxdepth -mindepth
        -maxdepth 限制查找的最深目录
        -mindepth 限制查找的最浅目录
        > find / -maxdepth 4 -name passwd   //查找 / 全部目录 最深为4的passwd文件
        > find / -mindepth 3 -maxdepth 5 -name passwd   // 查找 / 全部目录最浅 3 最深 5 的passwd文件

    3） 根据大小为条件进行文件查找
        -size +/-数字
            + : 表示大小大于某个范围
            - : 表示大小小于某个范围
        大小单位：
            -size 5         //单位是512字节 5*512字节
            -size 10c       //单位是 字节  10字节
            -size 3k        //单位是 千字节 3*1024字节
            -size 6M        //单位是 1024*千字节 6M字节 
        > find ./ -size 14c     //在当前目录查找大小等于14字节的文件
        > find ./ -size +50M    //在系统全部目录里边查找大小大于50M的文件
    4） 根据文件权限查找
        > find ./ -perm 764     //查找权限为764的文件
    5)  根据文件类型查找(f/d)
        > find ./ -type f       //查找当前类型为 文件 的
        > find ./ -type d       //查找当前类型为 目录 的
    6） 根据文件的 "主人" 或 "组别" 来查找
        > find ./ -user zhou        //查找当前 主人为zhou 的文件和目录
        > find ./ -group music       //查找当前 组别为 music 的文件和目录

## 19. 创建软/硬连接
        > ln -s 源文件 软连接
        > ln -s /home/zhou/animat.txt /var/ani.txt      //使用绝对路径来创建有效
        > ln -d 源文件 硬链接// -d 可以没有
        > ln -d animat.txt app.txt                      //创建animat.txt 的硬链接app.txt
                                //硬链接只能文件，不能目录
## 20.文件主人，组别设置
        > chown 主人 filename
        > chown 主人.组别 filename
        > chown .组别 filename
        > chown -R 主人.组别 dir        //通过递归方式设置目录的属组信息
        > chmod -R 765 dir              //通过递归方式设置目录的权限
        > service network restart/stop/star         //重启网络

## 21.光驱挂载
        mount 硬件 挂载点目录(普通目录)        //挂载动作
            > mount /dev/cdrom /home/zhou/rom       //把光驱挂载到rom目录
        umount 硬件或挂载点                       //卸载动作
            > umount /dev/cdrom                     //(硬件)卸载光驱
            > umount /home/zhou/rom                 //(挂载点)卸载光驱
            > eject                                 //弹出光盘

## 22.ftp软件以及gcc软件安装
        1) ftp安装
        rpm方式安装（vsftpd）软件
            > rpm -ivh 软件包全名                //安装软件
            > rpm -q 软件包全名(完整)          //query查看软件是否有安装
            > rpm -e 软件包全名(完整)          //卸载软件
            > rpm -qa                           //query all 查看系统里面全部rpm方式安装的软件
            > rpm -qa | grep ftpd(部分名字)     //模糊查找指定软件ftpd是否有安装
            软件包全名 = 软件包名 + 软件版本 + 支持的系统 + 支持的cpu型号 + 文件后缀
        2) ftp使用
        启动ftp服务：
            > service vsftpd start/shop/restart //控制ftp服务 启动/停止/重启
            >ps -A | grep ftp                   //查看ftp相关服务进程
        3) 关闭linux防火墙(执行指令 > setup)
            > setup
            1>//首次连接 错误 
            > vi/det/selinux/config //把enforcing改为disabled

            2> //对使用ftp用户的限制
            // /etc/vsftpd/user_list
            // /etc/vsftpd/ftpusers
            //限制普通用户只访问自己的家目录
             /etc/vsftpd/vsftpd.conf     第97行和99行
             //创建chroot_list文件做限制访问家目录的用户的设置 输入限制用户名
        4) 安装gcc软件：
            1.gcc-4.4...
            2.gcc-c++
            3.gcc-java
            //软件依赖
                gcc-4.4.7.. --> cloog-ppl和cpp -->ppl(libppl.so.7和libppl_c.so.2)
                                功能依赖：cpp -->libmpfr.so.1(mpfr)
                gcc-c++..  --> libstdc++-devel

## 23.源码编译方式安装软件
        1) zlib 软件安装
            1>> zlib 可以对许多其他软件的编译代码起着 优化、压缩 的作用
            a.解压压缩包：
                >tar.gz -------> tar zxvf               压缩包tar.gz
                >.tar.bz2 --------> tar jxvf            压缩包tar.bz2
            b.源码编译方式安装
                源码状态--->二进制码状态--->复制到系统指定目录
                ① ./configure                   //在解压软件目录内执行
                相关 参数配置，软件 安装位置，依赖软件设置，软件依赖检查等
                例如--prefix 是设置软件的安装位置
                    > ./configure --help        //查看当前软件可以设置的各种参数
                ② make                          //编译，根据configure的配置信息生成“二进制文件”
                ③ make install                  //把生成的二进制文件复制到系统指定的目录(本质与rpm安装类似)

        2） appache安装
            ./configure --prefix=/usr/local/http2 \
            --enable-modules=all \
            --enable-mods-shared=all \                  //模块共享型  
                                                            要把全部的功能模块代码内容都编译到apache 本身软件 内部
                                                            特点：apache本身软件会稍显臃肿但是再调用相关模块的时候速度会很快

                                                            相对应类型：static 静态类型
                                                            apache内部要被编译进行许多模块代码，其它模块代码都
                                                            独立存在，需要什么模块，就立即include引用之
                                                            特点：apache软件本身会非常小巧，器运行速度会很快
            --enable-so             //可以识别so模块文件
        3） 启动apache服务
            > /usr/local/http2/bin/apachectl start/stop/restart

## 24.开机自动启动服务
        1）配置文件路径：vi /etc/rc.d/rc.local在文件中增加
        /usr/local/http2/bin/apachectl start
        /usr/local/mysql/bin/mysqld_safe --user=mysql &
        service vsftpd start







