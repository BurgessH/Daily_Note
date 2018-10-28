基础操作：
  - 1、命令行和图形化界面之间的切换：ctrl + alt + fx;  
  - 2.关闭提示的声音：modprobe -r pcspkr;  
  - ls -alsh/ctrl + l(clear);  
  - cal 6 2018;   （查询时间）  
  - bc scale=4 quit;  （计算器）  
  - history:默认记录1000命令，以便方便查询；！+ 序号（执行命令）  
  - ctrl + i/e(开头、结尾)
  - 按esc键后按.键，调用之前命令的参数； 
  
帮助文档：  
  - whatis ls: 说明命令由什么作用；  
  - ls --help  
  - man passwd(/words n:从上往下查找；N：从下往上查找;查询命令的用法)；  
  - man -k clock(查找部分内容clock);  
  
编辑器：
  - gedit  
  - nano file
  
关机：
  - 数据同步写入磁盘：sync  
  - shutdown  
  - reboot  
  - poweroff  
  - 运行7个级别：不同的运行级别的时候，运行不同的服务级别；（文件夹包含了所有的服务）(/etc/init.d)/(/etc/rc.d/init.d); rc.d文件下运行的七个级别；
  - runlevel: 查看运行级别；
  - init 3(切换运行级别，不同的运行级别下运行着不同服务比如：界面服务)；  
  - level 0: 关机  
  - level 1：单用户模式（windows 安全模式）    
  - level 2: 单NEFS  
  - level 3: 纯文本模式（stsrtx）  
  - level 4: 未定义  
  - level 5: 图形化界面  
  - level 6: 重启  
注意：不同的级别下都对应七个控制台，其中级别三中图形化界面服务默认没运行；
开机过程中的问题排解：
  - 文件系统错误的问题
  - 忘记root密码5.3
  
6.linux的文件权限与目录配置
  - 用户与用户组：etc/passwd（用户）; /etc/shadow(passwd)、/etc/group(group)
  - linux文件权限概念
    - -/d/b/c/l(文件类型)；  ---user ---group ---other
    - chmod u+x,g+w,o-r filename(r=4 w=2 x=1)
    - chmod ug-rw/a=r
    - chmod 743
    - chown/grp filname 
6.2目录的配置
  - boot系统启动文件   
  - dev设备文件（硬盘、tty）  
  - home(用户的家目录)  
  - lib(链接库文件)  
  - media(系统自动挂载点，插入U盘时自动挂载)  
  - mnt（挂载点）  
  - opt（源码安装时指定到opt目录下的某个文件）  
  - proc(内核参数)  
  - root(root用户)  
  - sbin(二进制文件系统管理所能执行的命令)  
  - tmp(临时文件)  
  - usr(默认装载usr)  
  -  var(日志、log文件记录)  
  
7.1linux文件与目录管理
  - ~用户家目录：cd －(回到之前所在的目录下)
  - mkdir -p mk/xx  
  - rmdir -p mk/xx  
  - 命令执行完整的路径:   $echo PATH  
    - cp /etc/tmp /mnt -p(默认的复制文件不会改变文件的属性信息，-p为默认创建新文件)    
    - cp(复制的是源文件的符号链接文件时，实质拷贝的是源文件本身cp -d(拷贝的是符号链接))    
    - mv(文件的移动)  
    - rm -rf(强制删除文件)  
    
  - 文件内容查阅
    - cat -n (从头查看)查看小文件  
    - tac （倒行显示）  
    - nl(查看文件里的内容列出行号)     
    - more(分屏显示：回车一行一行显示，空格按页显示，只能往下查看)    
    - less (前后都可以查看，pageup/down home开头end末尾)    
    - head -n 3(查看文件的头几行10)  
    - tail -n 3(查看文件的尾几行)  
    - tail -f /var/log/massge()  
    - od/strings  
    
  - 创建文件
    - touch filename(后面创建的文件如果存在的则将文件改为当前时间，不存在则创建文件)
    - touch -t   
  - 默认文件权限  
    - umask（权限过滤符）对文件来说：并不是简单的减去umask的值；对目录来说：等于减去umask的值；  
    - umask -S（查看文件权限）  
  - 文件隐藏属性    
    - chattr +/-a home/aa(某个文件夹下只能添加文件不能删除)    
    - chattr +/-i home/bb(添加和删除都不能)  
    - lsattr(查看文件隐藏属性)  
    
  - 文件特殊权限    
    - SUID(chmod u+s xx:表示其他也具有执行者的权限)    
    - SGID（）    
    - echo "xxx `hostname`/$(hostname) xxx"(需要在某些地方需要执行我们的命令时使用反引号或者$（）的方式)    
    - chgrp astonnhm rhce/ touch rhce/aa chmod g+s rhce(在该目录下创建的所有文件都会具有所属组的属性)    
    - ls -l `which passwd`       
    - SBIT（只能分配给目录的Other所对应的权限上）    
      - chmod o+t rhce(初了所有者和root用户其他用户都不能删除)  
      - chmod 4/2/1(usr/grp/othr)644 yy  
      
  - 命令与文件目录查询  
    - which ls  
    - whereis -b/-m ls(可执行二进制文件的目录、manpage)  
    - locate -i
    - find 目录 -属性 值（find / -iname root）
    
8.linux磁盘与文件系统管理  
  - 认识EXT2文件系统  
  - 硬盘组成与分区（boot section + super block + inode +block） 
    - ls -i filename(查询文件记录的inode信息)  
    - filefrag -v filename(查看文件分布在哪些block)  
    - dumpe2fs filename(查看superblock inode信息)  
  - 文件系统  
    - linux的EXT2文件系统与目录树的关系  
    - EXT2/EXT3文件访问与日志文件系统的功能  
  - 挂载点的意义  
  - 其他linux支持的文件系统与VFS  
    - df -hT(已挂载文件大小，文件类型)
    - du -sh filename(查看文件的大小)  
    - ln -s aa aa1(软连接)    
    - ln aa bb(硬链接:同一个文件有几个名字inode) 
  - 8.2磁盘分区操作  
    - fdisk -l（查看所有的分区信息）  
    - fdisk /dev/sda(对硬盘分区的不是分区的分区)
  - 文件系统简单操作  
  - 磁盘与目录容量  
  
  - 9.linux系统常见的压缩命令    
    - compress -v filename  /uncompress filename
    - compress -v -c service > service.Z（源文件存在）  
    
    - gzip(gzip filename压缩文件源文件不存在了)  
    - zcat filename(查看压缩文件的内容)    
    - gzip -d filename(解压压缩文件)  
    - gzip -c host > host.gzip(源文件存在)  
    
    - bzip2 filename(压缩文件)  
    - bzip2 -d filename(解压文件)  
    - bzip2 -c host > host.bz2(源文件存在压缩文件)  
    - bzcat filename(查看压缩文件内容)  
    
    - zip host.zip host(指定文件（host）压缩为host.zip)  
    - unzip filename(解压)
    
  - 打包归档命令  
    - tar cvf host.tar host/--remove-files(创建一个文件并显示创建过程且指明创建的文件名称)/（不保留源文件）  
    - tar tvf host.tar(不解档查看文件的内容)    
    
    - tar xvf host.tar(解档文件当前文件夹)    
    - tar xvf host.tar -C pathname/（解档到指定的文件中去） 
    - tar xvf host.tar host(只解压出其中的host文件)  
    
    - tar zcvf host.tar.gz host--remove-files (c/z文件使用时具有打包和压缩的功能)  
    - tar zxvf host.tar.gz(解档和解压文件)  
    - tar jcvf host.tar.biz2 host(压缩并打包文件host)  
    - tar jxvf host.tar.biz2(解压)
    
