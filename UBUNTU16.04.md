# 一、Ubuntu16.04上网配置：  
  - 1.NET方式： 
    - 选择NET网络连接方式;    
    - 打开配置文件：vim /etc/network/interfaces;      
    - 配置网络参数：iface ens33 inet dhcp    
    - 重启网卡： /etc/init.d/networking restart    
  - 2.桥接方式：
    - 选择桥接网络连接方式;  
    - 桥接到无线网卡上wireless;  
    - 打开配置文件：vim /etc/network/interfaces    
    - 配置网络参数：DHCP、ID、MASK、GATE    
    - 重启网卡：/etc/init.d/networking restart    
  - 3.Host方式：
  
# 二、更换ubuntu源为清华（自带的镜像源服务器默认配置在国外，更新和下载软件速度慢）  
  - 1.https://mirrors.tuna.tsinghua.edu.cn/help/ubuntu/（URL）  
  - 2.备份系统自带更新源配置文件：/etc/apt/sources.list  
  - 3.打开gedit  source.list更换1复制的内容保存退出；  
  - 4.apt updata(更新源)   
  
# 三、Ubuntu16.04添加sogo输入法：  
  - 1.官网下载与Linux系统适应的版本；    
  - 2.sudo apt-get install -f  
  - 3.sudo dpkg -i sogoXXX_amd.deb  
  - 4.system-setting(将默认的ibus设置为fcitx)后，注销重新登录；然后点击输入图标设置选项，点击添加并将只显示勾选去掉即可；  
  
# APT下载工具：  
  - （实现软件自动下载、配置、安装二进制或者源码的功能；使用APT工具下载或者更新软件的时候，首先会在下载列表中与本机对比，看一下需要下载哪些软件、或者升级哪些软件、默认情况下APT会下载最新的软件包）
  - 
  1.更新本地数据库
  
## I、使用过程中出现的问题：  
  - 1.sudo apt-get install vim报告  
    - E: Could not get lock /var/lib/dpkg/lock-frontend - open (11: Resource temporarily unavialable)  
    - E: Unable to acquire the dpkg fronted lock (/var/lib/dpkg/lock-frontend), is another process using it?  
 - 原因：可能是另外个程序正在使用，导致资源被锁不可用；而导致资源被锁不可用的原因是，上次运行安装或者更新时没有正常完成，才导致这个问题出现；  
 - 解决：根据报告信息（sudo rm /var/lib/dpkg/lock-frontend）  
