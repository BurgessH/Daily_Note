## 搭建QSYS嵌入式开发环境：  
  - QYQS：提供的一个系统集成工具，该工具可用于搭建复杂的嵌入式系统，搭建完成的系统将作为后续软件开发的硬件基础。用户可以通过QYQS来调用官方所提供的IP核，从而加速系统设计；也可以利用QYQS来制作自己的IP核，定制符合需求的硬件系统。    
  - 过程步骤：  
    - 1.新建Quartus工程；  
    - 2.创建Qsys,添加以及rename IP核；  
    - 3.连接时钟信号和复位信号等等；  
    
    - 4.设置NiOS II IP核的复位地址和异常地址，双击NiOS II（勾选Hardware divide, 复位地址和异常地址）;   
    - 5.基地址分配system->assign base address;  
    - 6.生成Qsys系统，保存在hardware;  
    
    - 7.添加.qip文件，Qsys生产的后缀名为.qip文件，assignment-settings;工程的一些配置，assignment-device :Category unuse as input tri-state  
    - 8.Dual-purpose pins -use as regular I/o  
    - 9.引脚分配；    
    - 10.软件设计：【Toos】→【Nios II SBT for Eclipse】，存放空间software；  
    
  - PIO IP核（parallel input/output:）  
    - PIO的I/O端口可以连接到片内用户逻辑（verilog语言完成的电路部分）也可以连接到与外部器件相连的FPGA引脚。每个PIO核能提供最高32个I/O端口，用户可以在QSYS系统中添加多个PIO核。每一个IP核都有会一个寄存器的描述文件，altera_avalon_pio_regs.h(定义了寄存器的映射，宏定义)
  - PIO IP核寄存器：data数据读写操作, direction方向输出, interrupmask中断使能, edgecapture边沿触发检测, outset置位, outclear清零;   
    
