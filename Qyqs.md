## 
  - QYQS：提供的一个系统集成工具，该工具可用于搭建复杂的嵌入式系统，搭建完成的系统将作为后续软件开发的硬件基础。用户可以通过QYQS来调用官方所提供的IP核，从而加速系统设计；也可以利用QYQS来制作自己的IP核，定制符合需求的硬件系统。    
  - 过程步骤：  
    - 1.新建Quartus工程；  
    - 2.创建Qsys,添加以及rename IP核；  
    - 3.连接时钟信号和复位信号等等；  
    
    - 4.设置NiOS II IP核的复位地址和异常地址，双击NiOS II（勾选Hardware divide,复位地址和异常地址）;   
    - 5.基地址分配system->assign base address;  
    - 6.生成Qsys系统，保存在hardware;  
    
    - 7.添加.qip文件，Qsys生产的后缀名为.qip文件，assignment-settings;工程的一些配置，assignment-device :Category unuse as input tri-state  
    - 8.Dual-purpose pins -use as regular I/o  
    - 9.引脚分配；  
    
    
    - 10.软件设计：【Toos】→【Nios II SBT for Eclipse】，存放空间software，
  
