# 一、Ubuntu16.04工作环境搭建

## I、Ubuntu16.04上网配置：  
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
  
## II、更换ubuntu源为清华（自带的镜像源服务器默认配置在国外，更新和下载软件速度慢）  
  - 1.https://mirrors.tuna.tsinghua.edu.cn/help/ubuntu/（URL）  
  - 2.备份系统自带更新源配置文件：/etc/apt/sources.list  
  - 3.打开gedit  source.list更换1复制的内容保存退出；  
  - 4.apt updata(更新源)/sudo apt-get update     
  
## III、Ubuntu16.04添加sogo输入法：  
  - 1.官网下载与Linux系统适应的版本；    
  - 2.sudo apt-get install -f  
  - 3.sudo dpkg -i sogoXXX_amd.deb  
  - 4.system-setting(将默认的ibus设置为fcitx)后，注销重新登录；然后点击输入图标设置选项，点击添加并将只显示勾选去掉即可；  
  
## IV、ubuntu16.04 下载编译opencv4.1及Contribute 模块  
  - 1.下载opencv4.1与Contribute的源码文件  
    - https://github.com/opencv/opencv/releases/tag/4.0.1  
    - https://github.com/opencv/opencv_contrib/releases/tag/4.0.1  
    - （建议更换源）
  - 2.安装cmake及依赖环境  
    - sudo apt-get install cmake git libgtk2.0-dev pkg-config libavcodec-dev libavformat-dev libswscale-dev  
    - sudo apt-get install python-dev python-numpy libtbb2 libtbb-dev libjpeg-dev libpng-dev libtiff-dev libjasper-dev libdc1394-22-dev     - sudo apt-get install build-essential qt5-default ccache libv4l-dev libavresample-dev libgphoto2-dev libopenblas-base libopenblas-dev doxygen pylint libvtk6-dev  
  - 3.编译opencv  
    - 新建文件夹，存放下载的opencv压缩包并解压文件:(zip:unzip xxx.zip/tar:tar -zxvf xxx.tar.gz)  
    - 解压完成后，查看该目录下的文件，进入opencv-4.0.1文件夹，新建build文件，用存放编译过程中产生的文件  
    - 在build中输入编译过程需要参数：cmake -D CMAKE_BUILD_TYPE=RELEASE -D CMAKE_INSTALL_PREFIX=/usr/local -D OPENCV_GENERATE_PKGCONFIG=ON -D INSTALL_PYTHON_EXAMPLES=ON -D INSTALL_C_EXAMPLES=ON -D OPENCV_EXTRA_MODULES_PATH= /home/cht/opencv4/opencv_contrib-4.0.1/modules -D OPENCV_EXAMPLES=ON ..
      - CMAKE_INSTALL_PREFIX：该选项为opencv安装的目录，可按实际目录进行修改，一般放在/usr/local目录下
      - OPENCV_GENERATE_PKGCONFIG：打开 pkg-config  
      - OPENCV_EXTRA_MODULES_PATH:该选选项为opencv_contrib模块下module文件夹，按实际目录进行修改，若不编译opencv_contrib模块，该选项可以省略
      - .. ：表示CMakeList.txt在上级目录,命令最后的 .. 不能够省略，否则会出现找不到CMakeList.txt  
  - 4.等待cmake执行完成后，执行sudo make install 进行安装  
  - 5.配置编译环境  
    - 在命令行中输入 gedit ~/.bashrc 打开 ~/.bashrc 文件；在 ~/.bashrc 文件中添加下面一行内容：  
    exportPKG_CONFIG_PATH="/usr/local/lib/pkgconfig:$PKG_CONFIG_PATH"  
    - source ~/.bashrc（使环境变量生效）  
    - sudo ldconfig  
    - 使用 pkg-config 进行测试验证：pkg-config --libs --cflags opencv4  
  - 6.运行openv附带的测试程序  
    - /opencv-4.0.1/samples/cpp/example_cmake   
    - cmake .  
    - make  
    - ./opencv_example  
    
    
    

# APT下载工具：  
  - （实现软件自动下载、配置、安装二进制或者源码的功能；使用APT工具下载或者更新软件的时候，首先会在下载列表中与本机对比，看一下需要下载哪些软件、或者升级哪些软件、默认情况下APT会下载最新的软件包）
  - 
  1.更新本地数据库
  
## 1、使用过程中出现的问题：  
  - 1.sudo apt-get install vim报告  
    - E: Could not get lock /var/lib/dpkg/lock-frontend - open (11: Resource temporarily unavialable)  
    - E: Unable to acquire the dpkg fronted lock (/var/lib/dpkg/lock-frontend), is another process using it?  
 - 原因：可能是另外个程序正在使用，导致资源被锁不可用；而导致资源被锁不可用的原因是，上次运行安装或者更新时没有正常完成，才导致这个问题出现；  
 - 解决：根据报告信息（sudo rm /var/lib/dpkg/lock-frontend）  
