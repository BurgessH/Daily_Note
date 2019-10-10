# Ubuntu16.04上网配置：  
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
# APT下载工具：  
  - （实现软件自动下载、配置、安装二进制或者源码的功能；使用APT工具下载或者更新软件的时候，首先会在下载列表中与本机对比，看一下需要下载哪些软件、或者升级哪些软件、默认情况下APT会下载最新的软件包）
  - 
  1.更新本地数据库
  

