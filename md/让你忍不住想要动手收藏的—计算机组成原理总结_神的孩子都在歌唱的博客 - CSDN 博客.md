> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [blog.csdn.net](https://blog.csdn.net/weixin_46654114/article/details/105812651)

[这是我观看了 b 站 up 做的笔记](https://www.bilibili.com/video/BV1WW411Q7PF?p=41)

> 还会持续更新  
> 转载说明：务必注明来源，附带本人 CSDN 博客连接。  
> 关注公众号：**神的孩子都在歌唱** 回复：**组成原理** 获取 pdf 电子版

### [计算机组成原理](https://so.csdn.net/so/search?q=%E8%AE%A1%E7%AE%97%E6%9C%BA%E7%BB%84%E6%88%90%E5%8E%9F%E7%90%86&spm=1001.2101.3001.7020)笔记总结

*   *   [第 1 章：计算机的系统](#1_7)
    *   [第 3 章：系统总线](#3_36)
    *   [第 4 章：存储器](#4_89)
    *   *   [一. 概述](#__90)
        *   [二. 主存储器](#_101)
        *   *   [1. 概述](#1_102)
            *   [2. 半导体储存芯片](#2__111)
            *   [3. 随机存储器（RAM）](#3RAM_125)
            *   [4. 只读存储器（ROM）](#4ROM_139)
            *   [5. 存储器与 CPU 的连接](#5CPU_148)
            *   [6. 存储器校验](#6_171)
            *   [7. 提高访存速度的措施](#7_176)
        *   [三. 高速缓冲存储器（cache）](#cache_180)
        *   *   [1. 概述](#1_181)
            *   [2.Cache-- 主存地址映射和替换策略](#2Cache_217)
        *   [四. 辅助存储器（外部存储器）](#_230)
    *   [第 5 章：输入输出系统](#5_237)
    *   *   [一. 发展情况，了解历史](#_251)
        *   [二. 系统组成](#_270)
        *   [三. I/O 设备与主机的联系方式](#IO_286)
        *   [四. I/O 设备与主机信息传送的控制方式](#IO_304)

第 1 章：计算机的系统
------------

硬件：指计算机实体部分。（看得见摸得着的）  
软件：通过编译具有各类特殊功能的程序组成（看不见摸不着）

> 冯. 诺依曼计算机：以运算器为中心  
> 现代计算机：以存储器为中心

1. 计算机由运算器，存储器，控制器，输入，输出设备过构成。  
2. 现代计算机三大组成：CPU，I/O 设备，主存储器  
3. 工作步骤：（1）建立数学模型 （2）确定计算方法（3）编制解题程序  
4. 存储容量 = 存储单元个数（MAR 1k=1024=2^10）x 存储字长（MDR 1M=2 ^20）  
![](https://img-blog.csdnimg.cn/20200407220608734.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjY1NDExNA==,size_16,color_FFFFFF,t_70)  
**ax^2+bx+c 在计算机中的运行过程**  
![](https://img-blog.csdnimg.cn/20200407222113612.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjY1NDExNA==,size_16,color_FFFFFF,t_70)  
**各种英文代号解释**

> CPU:（Central Processing Unit) 中央处理器  
> I/O 设备：（Input/Output Equip-ment）输入，输出设备  
> MM: （Main Memory) 主存储器  
> ALU: （Arithmetic Logic Unit）算数逻辑单元  
> ACC：（Accumulator）累加器  
> MQ：（Multiplier-Quotient Register）乘商寄存器  
> X：操作数寄存器  
> PC：（Program Counter）程序计数器  
> IR：（Instruction Register）指令寄存器  
> CU：（Control Unit）控制单元  
> MAR：（Memory Address Register）存储器地址寄存器，反映单元个数  
> MDR：（Memory Data Register）存储器数据寄存器，反映字长

第 3 章：系统总线
----------

总线是信号的公共传输线，是连接多个部件的信息传输线，是各部件共享的传输介质。

**发展过程：**

1.  面向 CPU 的双总线：这种结构在 I/O 设备与主存交换信息是仍然要占用 CPU，因此还会影响 CPU 的工作效率。
2.  单总线结构（系统总线）：只有一组总线，当都要占用总线时，就会发生冲突。
3.  以存储器为中心的双总线结构：由单总线基础上，在 CPU 与主存之间连接一条存储总线。

**分类：**

1.  片内总线：芯片内部的线。
2.  系统总线：计算机各部件之间的信息传输线。  
    （1）数据总线（双向）：传输数据信息。**位数**与机器字长，存储字长有关，是衡量性能重要参数。  
    （2）地址总线（单向）：指出在数据总线上数据在主存单元或 I/O 设备的地址，地址线的位数与存储单元的个数有关  
    （3）控制总线（单向，双向）：发出各种控制信号，监视各部件状态。
3.  通信总线：用于计算机系统之间或计算机系统与其他系统（外部系统） 传输方式：串行通信，并行通信

**特性：**

1.  机器特性
2.  电气特性
3.  功能特性
4.  时间特性

**性能指标：**

1.  总线宽度：指数据总线的根数，用 bit（位）表示，如 8 位（8 根）。
2.  总线带宽 (数据传输速率)：既单位时间内总线上传输数据的位数，用每秒传输信息的字节数来衡量，单位用 MBps(兆字节每秒)。
3.  时钟同步 / 异步：数据与时钟。
4.  总线复用：地址线和数据线的复用。
5.  信号总线：三种总线的总和。

**判优控制**

1.  主设备对总线有控制权，从设备只能响应从设备发来的总线命令
2.  判优控制可分为集中式和分布式。

集中控制优先权仲裁方式：  
（1）链式查询：控制线少，对电路故障敏感，优先级低的设备难请求  
（2）计数器定时查询：控制复制  
（3）独立请求方式：响应快，优先次序控制灵活

**通信控制**

1.  总线周期：完成一次总线操作的时间。
2.  目的：解决通信双方如何协调配合。
3.  方式：  
    （1）同步通信：通信双方由统一时标。  
    （2）异步通信：采用应答方式，没有公共时钟标准。  
    （3）半同步通信：同步，异步结合。  
    （4）分离式通信：充分挖掘系统总线每个瞬间的潜力。

第 4 章：存储器
---------

### 一. 概述

分类：  
![](https://img-blog.csdnimg.cn/20200409114028338.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjY1NDExNA==,size_16,color_FFFFFF,t_70)  
层次结构：

1.  性能指标：速度，容量，位价（每位价格）。  
    ![](https://img-blog.csdnimg.cn/20200409143028217.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjY1NDExNA==,size_16,color_FFFFFF,t_70)
2.  存储层次结构：  
    （1）缓存 - 主存层次：解决 CPU 和主存速度不匹配问题。  
    （2）主存 - 辅存层次：解决容量问题。

![](https://img-blog.csdnimg.cn/20200409141740984.png)

### 二. 主存储器

#### 1. 概述

1.  **基本组成：** 存储体（大楼）–存储单元（房间）–存储元件（床位）-- 0 / 1（无人 / 有人）。
2.  **主存中存储单元地址的分配：** 主存个存储单元的空间位置是由单元地址号来表示，地址总线是指出储存单元地址号，由地址号可以读出写入一个储存字。
3.  **技术指标：**  
    （1）存储容量 ：指主存能存放二进制代码的总位数，也可用字节总数 来表示。  
    存储容量 = 存储单元个数 x 存储字长  
    存储容量 = 存储单元个数 x 存储字长 / 8  
    （2）存储速度 ：由存取时间和存储周期来表示。

#### 2. 半导体储存芯片

基本结构：  
![](https://img-blog.csdnimg.cn/2020041316541957.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjY1NDExNA==,size_16,color_FFFFFF,t_70)  
**容量**：由地址线（单向）和数据线（双向）的位数共同反应。  
列：

<table><thead><tr><th>地址线</th><th>数据线</th><th>容量</th></tr></thead><tbody><tr><td>10</td><td>4</td><td>2^10(1k)*4</td></tr><tr><td>14</td><td>1</td><td>2^14(16k)*1</td></tr><tr><td>13</td><td>8</td><td>2^13(8k)*8</td></tr></tbody></table>

**控制线**：  
（1）读写控制线：决定芯片进行读写操作。  
（2）片选线：用来选择储存芯片。  
**译码驱动方式**：线选法和重合法

#### 3. 随机存储器（RAM）

> DRAM(动态)：用在主存  
> SRAM(静态)：用在缓存

<table><thead><tr><th></th><th>DRAM(动态)</th><th>SRAM(静态)</th></tr></thead><tbody><tr><td>存储原理</td><td>容量</td><td>触发器</td></tr><tr><td>集成度</td><td>高</td><td>低</td></tr><tr><td>芯片引脚</td><td>少</td><td>多</td></tr><tr><td>功耗</td><td>小</td><td>大</td></tr><tr><td>价格</td><td>低</td><td>高</td></tr><tr><td>速度</td><td>慢</td><td>快</td></tr><tr><td>刷新</td><td>有</td><td>无</td></tr></tbody></table>

#### 4. 只读存储器（ROM）

> 定义： 一般保存系统程序或系统的配置信息  
> 半导体 ROM 基本器件：MOS 型和 TTL 型。

1.  MROM: 用户不发改变原始状态。
2.  PROM：可以改变一次（一次性）。
3.  EPROM：（多次性编程）。
4.  EEPROM：既可局部，也可全部。
5.  闪速存储器：快擦型存储器

#### 5. 存储器与 CPU 的连接

1.  **存储容量的扩展**

> CS （片选线 ）：连接芯片  
> WE：读，写

（1）位扩展 ： 指增加存储字长（就是增加数据线）。  
（2）字扩展 ：指增加存储器字的数量，也称存储单元（就是增加地址线）  
（3）字，位扩展 ：两个都增。

2.  **存储器与 CPU 连接**  
    （1）地址线连接：通常将 CPU 地址线的低位与存储芯片的地址线相连（CPU 地址线多于存储芯片地址线）。  
    （2）数据线连接 : 若存储芯片与 CPU 的数据线不相等，就对存储芯片进行扩位（使他们数据位数相等）。  
    （3）读 / 写命令线连接 ：高电平为读，低电平为写。  
    （4）片选线连接 ：是 CPU 与存储芯片正确工作的关键。片选有效信号与 CPU 的访存信号 MREQ（低电平有效，有效时，这次访问的地址才在存储器当中）有关。  
    （5）合理选择存储芯片 ：ROM 存放系统程序，RAM 为用户编程设计。

> 解题步骤  
> （1）写出对应的二进制地址码  
> （2）确定芯片数量及类型  
> （3）分配地址线  
> （4）确定片选信号  
> （5）确定片选逻辑

#### 6. 存储器校验

1.  汉明码：1950 年提出，具有以为纠错能力。
2.  汉明码的分组是一种非划分方式。
3.  校验位： 指对一组数据进行效验，不和其他组共有。

#### 7. 提高访存速度的措施

目的：提高主存的存取速度  
多体并行系统：采用多体模块组成的存储器。

### 三. 高速缓冲存储器（cache）

#### 1. 概述

> 主要作用：解决主存与 CPU 速度不匹配的问题。

#mermaid-svg-UlsliJbBBbe7aQ2x .label{font-family:'trebuchet ms', verdana, arial;font-family:var(--mermaid-font-family);fill:#333;color:#333}#mermaid-svg-UlsliJbBBbe7aQ2x .label text{fill:#333}#mermaid-svg-UlsliJbBBbe7aQ2x .node rect,#mermaid-svg-UlsliJbBBbe7aQ2x .node circle,#mermaid-svg-UlsliJbBBbe7aQ2x .node ellipse,#mermaid-svg-UlsliJbBBbe7aQ2x .node polygon,#mermaid-svg-UlsliJbBBbe7aQ2x .node path{fill:#ECECFF;stroke:#9370db;stroke-width:1px}#mermaid-svg-UlsliJbBBbe7aQ2x .node .label{text-align:center;fill:#333}#mermaid-svg-UlsliJbBBbe7aQ2x .node.clickable{cursor:pointer}#mermaid-svg-UlsliJbBBbe7aQ2x .arrowheadPath{fill:#333}#mermaid-svg-UlsliJbBBbe7aQ2x .edgePath .path{stroke:#333;stroke-width:1.5px}#mermaid-svg-UlsliJbBBbe7aQ2x .flowchart-link{stroke:#333;fill:none}#mermaid-svg-UlsliJbBBbe7aQ2x .edgeLabel{background-color:#e8e8e8;text-align:center}#mermaid-svg-UlsliJbBBbe7aQ2x .edgeLabel rect{opacity:0.9}#mermaid-svg-UlsliJbBBbe7aQ2x .edgeLabel span{color:#333}#mermaid-svg-UlsliJbBBbe7aQ2x .cluster rect{fill:#ffffde;stroke:#aa3;stroke-width:1px}#mermaid-svg-UlsliJbBBbe7aQ2x .cluster text{fill:#333}#mermaid-svg-UlsliJbBBbe7aQ2x div.mermaidTooltip{position:absolute;text-align:center;max-width:200px;padding:2px;font-family:'trebuchet ms', verdana, arial;font-family:var(--mermaid-font-family);font-size:12px;background:#ffffde;border:1px solid #aa3;border-radius:2px;pointer-events:none;z-index:100}#mermaid-svg-UlsliJbBBbe7aQ2x .actor{stroke:#ccf;fill:#ECECFF}#mermaid-svg-UlsliJbBBbe7aQ2x text.actor>tspan{fill:#000;stroke:none}#mermaid-svg-UlsliJbBBbe7aQ2x .actor-line{stroke:grey}#mermaid-svg-UlsliJbBBbe7aQ2x .messageLine0{stroke-width:1.5;stroke-dasharray:none;stroke:#333}#mermaid-svg-UlsliJbBBbe7aQ2x .messageLine1{stroke-width:1.5;stroke-dasharray:2, 2;stroke:#333}#mermaid-svg-UlsliJbBBbe7aQ2x #arrowhead path{fill:#333;stroke:#333}#mermaid-svg-UlsliJbBBbe7aQ2x .sequenceNumber{fill:#fff}#mermaid-svg-UlsliJbBBbe7aQ2x #sequencenumber{fill:#333}#mermaid-svg-UlsliJbBBbe7aQ2x #crosshead path{fill:#333;stroke:#333}#mermaid-svg-UlsliJbBBbe7aQ2x .messageText{fill:#333;stroke:#333}#mermaid-svg-UlsliJbBBbe7aQ2x .labelBox{stroke:#ccf;fill:#ECECFF}#mermaid-svg-UlsliJbBBbe7aQ2x .labelText,#mermaid-svg-UlsliJbBBbe7aQ2x .labelText>tspan{fill:#000;stroke:none}#mermaid-svg-UlsliJbBBbe7aQ2x .loopText,#mermaid-svg-UlsliJbBBbe7aQ2x .loopText>tspan{fill:#000;stroke:none}#mermaid-svg-UlsliJbBBbe7aQ2x .loopLine{stroke-width:2px;stroke-dasharray:2, 2;stroke:#ccf;fill:#ccf}#mermaid-svg-UlsliJbBBbe7aQ2x .note{stroke:#aa3;fill:#fff5ad}#mermaid-svg-UlsliJbBBbe7aQ2x .noteText,#mermaid-svg-UlsliJbBBbe7aQ2x .noteText>tspan{fill:#000;stroke:none}#mermaid-svg-UlsliJbBBbe7aQ2x .activation0{fill:#f4f4f4;stroke:#666}#mermaid-svg-UlsliJbBBbe7aQ2x .activation1{fill:#f4f4f4;stroke:#666}#mermaid-svg-UlsliJbBBbe7aQ2x .activation2{fill:#f4f4f4;stroke:#666}#mermaid-svg-UlsliJbBBbe7aQ2x .mermaid-main-font{font-family:"trebuchet ms", verdana, arial;font-family:var(--mermaid-font-family)}#mermaid-svg-UlsliJbBBbe7aQ2x .section{stroke:none;opacity:0.2}#mermaid-svg-UlsliJbBBbe7aQ2x .section0{fill:rgba(102,102,255,0.49)}#mermaid-svg-UlsliJbBBbe7aQ2x .section2{fill:#fff400}#mermaid-svg-UlsliJbBBbe7aQ2x .section1,#mermaid-svg-UlsliJbBBbe7aQ2x .section3{fill:#fff;opacity:0.2}#mermaid-svg-UlsliJbBBbe7aQ2x .sectionTitle0{fill:#333}#mermaid-svg-UlsliJbBBbe7aQ2x .sectionTitle1{fill:#333}#mermaid-svg-UlsliJbBBbe7aQ2x .sectionTitle2{fill:#333}#mermaid-svg-UlsliJbBBbe7aQ2x .sectionTitle3{fill:#333}#mermaid-svg-UlsliJbBBbe7aQ2x .sectionTitle{text-anchor:start;font-size:11px;text-height:14px;font-family:'trebuchet ms', verdana, arial;font-family:var(--mermaid-font-family)}#mermaid-svg-UlsliJbBBbe7aQ2x .grid .tick{stroke:#d3d3d3;opacity:0.8;shape-rendering:crispEdges}#mermaid-svg-UlsliJbBBbe7aQ2x .grid .tick text{font-family:'trebuchet ms', verdana, arial;font-family:var(--mermaid-font-family)}#mermaid-svg-UlsliJbBBbe7aQ2x .grid path{stroke-width:0}#mermaid-svg-UlsliJbBBbe7aQ2x .today{fill:none;stroke:red;stroke-width:2px}#mermaid-svg-UlsliJbBBbe7aQ2x .task{stroke-width:2}#mermaid-svg-UlsliJbBBbe7aQ2x .taskText{text-anchor:middle;font-family:'trebuchet ms', verdana, arial;font-family:var(--mermaid-font-family)}#mermaid-svg-UlsliJbBBbe7aQ2x .taskText:not([font-size]){font-size:11px}#mermaid-svg-UlsliJbBBbe7aQ2x .taskTextOutsideRight{fill:#000;text-anchor:start;font-size:11px;font-family:'trebuchet ms', verdana, arial;font-family:var(--mermaid-font-family)}#mermaid-svg-UlsliJbBBbe7aQ2x .taskTextOutsideLeft{fill:#000;text-anchor:end;font-size:11px}#mermaid-svg-UlsliJbBBbe7aQ2x .task.clickable{cursor:pointer}#mermaid-svg-UlsliJbBBbe7aQ2x .taskText.clickable{cursor:pointer;fill:#003163 !important;font-weight:bold}#mermaid-svg-UlsliJbBBbe7aQ2x .taskTextOutsideLeft.clickable{cursor:pointer;fill:#003163 !important;font-weight:bold}#mermaid-svg-UlsliJbBBbe7aQ2x .taskTextOutsideRight.clickable{cursor:pointer;fill:#003163 !important;font-weight:bold}#mermaid-svg-UlsliJbBBbe7aQ2x .taskText0,#mermaid-svg-UlsliJbBBbe7aQ2x .taskText1,#mermaid-svg-UlsliJbBBbe7aQ2x .taskText2,#mermaid-svg-UlsliJbBBbe7aQ2x .taskText3{fill:#fff}#mermaid-svg-UlsliJbBBbe7aQ2x .task0,#mermaid-svg-UlsliJbBBbe7aQ2x .task1,#mermaid-svg-UlsliJbBBbe7aQ2x .task2,#mermaid-svg-UlsliJbBBbe7aQ2x .task3{fill:#8a90dd;stroke:#534fbc}#mermaid-svg-UlsliJbBBbe7aQ2x .taskTextOutside0,#mermaid-svg-UlsliJbBBbe7aQ2x .taskTextOutside2{fill:#000}#mermaid-svg-UlsliJbBBbe7aQ2x .taskTextOutside1,#mermaid-svg-UlsliJbBBbe7aQ2x .taskTextOutside3{fill:#000}#mermaid-svg-UlsliJbBBbe7aQ2x .active0,#mermaid-svg-UlsliJbBBbe7aQ2x .active1,#mermaid-svg-UlsliJbBBbe7aQ2x .active2,#mermaid-svg-UlsliJbBBbe7aQ2x .active3{fill:#bfc7ff;stroke:#534fbc}#mermaid-svg-UlsliJbBBbe7aQ2x .activeText0,#mermaid-svg-UlsliJbBBbe7aQ2x .activeText1,#mermaid-svg-UlsliJbBBbe7aQ2x .activeText2,#mermaid-svg-UlsliJbBBbe7aQ2x .activeText3{fill:#000 !important}#mermaid-svg-UlsliJbBBbe7aQ2x .done0,#mermaid-svg-UlsliJbBBbe7aQ2x .done1,#mermaid-svg-UlsliJbBBbe7aQ2x .done2,#mermaid-svg-UlsliJbBBbe7aQ2x .done3{stroke:grey;fill:#d3d3d3;stroke-width:2}#mermaid-svg-UlsliJbBBbe7aQ2x .doneText0,#mermaid-svg-UlsliJbBBbe7aQ2x .doneText1,#mermaid-svg-UlsliJbBBbe7aQ2x .doneText2,#mermaid-svg-UlsliJbBBbe7aQ2x .doneText3{fill:#000 !important}#mermaid-svg-UlsliJbBBbe7aQ2x .crit0,#mermaid-svg-UlsliJbBBbe7aQ2x .crit1,#mermaid-svg-UlsliJbBBbe7aQ2x .crit2,#mermaid-svg-UlsliJbBBbe7aQ2x .crit3{stroke:#f88;fill:red;stroke-width:2}#mermaid-svg-UlsliJbBBbe7aQ2x .activeCrit0,#mermaid-svg-UlsliJbBBbe7aQ2x .activeCrit1,#mermaid-svg-UlsliJbBBbe7aQ2x .activeCrit2,#mermaid-svg-UlsliJbBBbe7aQ2x .activeCrit3{stroke:#f88;fill:#bfc7ff;stroke-width:2}#mermaid-svg-UlsliJbBBbe7aQ2x .doneCrit0,#mermaid-svg-UlsliJbBBbe7aQ2x .doneCrit1,#mermaid-svg-UlsliJbBBbe7aQ2x .doneCrit2,#mermaid-svg-UlsliJbBBbe7aQ2x .doneCrit3{stroke:#f88;fill:#d3d3d3;stroke-width:2;cursor:pointer;shape-rendering:crispEdges}#mermaid-svg-UlsliJbBBbe7aQ2x .milestone{transform:rotate(45deg) scale(0.8, 0.8)}#mermaid-svg-UlsliJbBBbe7aQ2x .milestoneText{font-style:italic}#mermaid-svg-UlsliJbBBbe7aQ2x .doneCritText0,#mermaid-svg-UlsliJbBBbe7aQ2x .doneCritText1,#mermaid-svg-UlsliJbBBbe7aQ2x .doneCritText2,#mermaid-svg-UlsliJbBBbe7aQ2x .doneCritText3{fill:#000 !important}#mermaid-svg-UlsliJbBBbe7aQ2x .activeCritText0,#mermaid-svg-UlsliJbBBbe7aQ2x .activeCritText1,#mermaid-svg-UlsliJbBBbe7aQ2x .activeCritText2,#mermaid-svg-UlsliJbBBbe7aQ2x .activeCritText3{fill:#000 !important}#mermaid-svg-UlsliJbBBbe7aQ2x .titleText{text-anchor:middle;font-size:18px;fill:#000;font-family:'trebuchet ms', verdana, arial;font-family:var(--mermaid-font-family)}#mermaid-svg-UlsliJbBBbe7aQ2x g.classGroup text{fill:#9370db;stroke:none;font-family:'trebuchet ms', verdana, arial;font-family:var(--mermaid-font-family);font-size:10px}#mermaid-svg-UlsliJbBBbe7aQ2x g.classGroup text .title{font-weight:bolder}#mermaid-svg-UlsliJbBBbe7aQ2x g.clickable{cursor:pointer}#mermaid-svg-UlsliJbBBbe7aQ2x g.classGroup rect{fill:#ECECFF;stroke:#9370db}#mermaid-svg-UlsliJbBBbe7aQ2x g.classGroup line{stroke:#9370db;stroke-width:1}#mermaid-svg-UlsliJbBBbe7aQ2x .classLabel .box{stroke:none;stroke-width:0;fill:#ECECFF;opacity:0.5}#mermaid-svg-UlsliJbBBbe7aQ2x .classLabel .label{fill:#9370db;font-size:10px}#mermaid-svg-UlsliJbBBbe7aQ2x .relation{stroke:#9370db;stroke-width:1;fill:none}#mermaid-svg-UlsliJbBBbe7aQ2x .dashed-line{stroke-dasharray:3}#mermaid-svg-UlsliJbBBbe7aQ2x #compositionStart{fill:#9370db;stroke:#9370db;stroke-width:1}#mermaid-svg-UlsliJbBBbe7aQ2x #compositionEnd{fill:#9370db;stroke:#9370db;stroke-width:1}#mermaid-svg-UlsliJbBBbe7aQ2x #aggregationStart{fill:#ECECFF;stroke:#9370db;stroke-width:1}#mermaid-svg-UlsliJbBBbe7aQ2x #aggregationEnd{fill:#ECECFF;stroke:#9370db;stroke-width:1}#mermaid-svg-UlsliJbBBbe7aQ2x #dependencyStart{fill:#9370db;stroke:#9370db;stroke-width:1}#mermaid-svg-UlsliJbBBbe7aQ2x #dependencyEnd{fill:#9370db;stroke:#9370db;stroke-width:1}#mermaid-svg-UlsliJbBBbe7aQ2x #extensionStart{fill:#9370db;stroke:#9370db;stroke-width:1}#mermaid-svg-UlsliJbBBbe7aQ2x #extensionEnd{fill:#9370db;stroke:#9370db;stroke-width:1}#mermaid-svg-UlsliJbBBbe7aQ2x .commit-id,#mermaid-svg-UlsliJbBBbe7aQ2x .commit-msg,#mermaid-svg-UlsliJbBBbe7aQ2x .branch-label{fill:lightgrey;color:lightgrey;font-family:'trebuchet ms', verdana, arial;font-family:var(--mermaid-font-family)}#mermaid-svg-UlsliJbBBbe7aQ2x .pieTitleText{text-anchor:middle;font-size:25px;fill:#000;font-family:'trebuchet ms', verdana, arial;font-family:var(--mermaid-font-family)}#mermaid-svg-UlsliJbBBbe7aQ2x .slice{font-family:'trebuchet ms', verdana, arial;font-family:var(--mermaid-font-family)}#mermaid-svg-UlsliJbBBbe7aQ2x g.stateGroup text{fill:#9370db;stroke:none;font-size:10px;font-family:'trebuchet ms', verdana, arial;font-family:var(--mermaid-font-family)}#mermaid-svg-UlsliJbBBbe7aQ2x g.stateGroup text{fill:#9370db;fill:#333;stroke:none;font-size:10px}#mermaid-svg-UlsliJbBBbe7aQ2x g.statediagram-cluster .cluster-label text{fill:#333}#mermaid-svg-UlsliJbBBbe7aQ2x g.stateGroup .state-title{font-weight:bolder;fill:#000}#mermaid-svg-UlsliJbBBbe7aQ2x g.stateGroup rect{fill:#ECECFF;stroke:#9370db}#mermaid-svg-UlsliJbBBbe7aQ2x g.stateGroup line{stroke:#9370db;stroke-width:1}#mermaid-svg-UlsliJbBBbe7aQ2x .transition{stroke:#9370db;stroke-width:1;fill:none}#mermaid-svg-UlsliJbBBbe7aQ2x .stateGroup .composit{fill:white;border-bottom:1px}#mermaid-svg-UlsliJbBBbe7aQ2x .stateGroup .alt-composit{fill:#e0e0e0;border-bottom:1px}#mermaid-svg-UlsliJbBBbe7aQ2x .state-note{stroke:#aa3;fill:#fff5ad}#mermaid-svg-UlsliJbBBbe7aQ2x .state-note text{fill:black;stroke:none;font-size:10px}#mermaid-svg-UlsliJbBBbe7aQ2x .stateLabel .box{stroke:none;stroke-width:0;fill:#ECECFF;opacity:0.7}#mermaid-svg-UlsliJbBBbe7aQ2x .edgeLabel text{fill:#333}#mermaid-svg-UlsliJbBBbe7aQ2x .stateLabel text{fill:#000;font-size:10px;font-weight:bold;font-family:'trebuchet ms', verdana, arial;font-family:var(--mermaid-font-family)}#mermaid-svg-UlsliJbBBbe7aQ2x .node circle.state-start{fill:black;stroke:black}#mermaid-svg-UlsliJbBBbe7aQ2x .node circle.state-end{fill:black;stroke:white;stroke-width:1.5}#mermaid-svg-UlsliJbBBbe7aQ2x #statediagram-barbEnd{fill:#9370db}#mermaid-svg-UlsliJbBBbe7aQ2x .statediagram-cluster rect{fill:#ECECFF;stroke:#9370db;stroke-width:1px}#mermaid-svg-UlsliJbBBbe7aQ2x .statediagram-cluster rect.outer{rx:5px;ry:5px}#mermaid-svg-UlsliJbBBbe7aQ2x .statediagram-state .divider{stroke:#9370db}#mermaid-svg-UlsliJbBBbe7aQ2x .statediagram-state .title-state{rx:5px;ry:5px}#mermaid-svg-UlsliJbBBbe7aQ2x .statediagram-cluster.statediagram-cluster .inner{fill:white}#mermaid-svg-UlsliJbBBbe7aQ2x .statediagram-cluster.statediagram-cluster-alt .inner{fill:#e0e0e0}#mermaid-svg-UlsliJbBBbe7aQ2x .statediagram-cluster .inner{rx:0;ry:0}#mermaid-svg-UlsliJbBBbe7aQ2x .statediagram-state rect.basic{rx:5px;ry:5px}#mermaid-svg-UlsliJbBBbe7aQ2x .statediagram-state rect.divider{stroke-dasharray:10,10;fill:#efefef}#mermaid-svg-UlsliJbBBbe7aQ2x .note-edge{stroke-dasharray:5}#mermaid-svg-UlsliJbBBbe7aQ2x .statediagram-note rect{fill:#fff5ad;stroke:#aa3;stroke-width:1px;rx:0;ry:0}:root{--mermaid-font-family: '"trebuchet ms", verdana, arial';--mermaid-font-family:"Comic Sans MS","Comic Sans", cursive}#mermaid-svg-UlsliJbBBbe7aQ2x .error-icon{fill:#522}#mermaid-svg-UlsliJbBBbe7aQ2x .error-text{fill:#522;stroke:#522}#mermaid-svg-UlsliJbBBbe7aQ2x .edge-thickness-normal{stroke-width:2px}#mermaid-svg-UlsliJbBBbe7aQ2x .edge-thickness-thick{stroke-width:3.5px}#mermaid-svg-UlsliJbBBbe7aQ2x .edge-pattern-solid{stroke-dasharray:0}#mermaid-svg-UlsliJbBBbe7aQ2x .edge-pattern-dashed{stroke-dasharray:3}#mermaid-svg-UlsliJbBBbe7aQ2x .edge-pattern-dotted{stroke-dasharray:2}#mermaid-svg-UlsliJbBBbe7aQ2x .marker{fill:#333}#mermaid-svg-UlsliJbBBbe7aQ2x .marker.cross{stroke:#333} :root { --mermaid-font-family: "trebuchet ms", verdana, arial;} #mermaid-svg-UlsliJbBBbe7aQ2x {color: rgba(0, 0, 0, 0.75); font: ; } CPU 缓存 主存

1.  **工作原理**

> 1.  主存由 2^n 个可编译的字组成，每个字有唯一的 n 位地址
> 2.  主存 和 缓存以块 为单位存储。
> 3.  块的大小相同

![](https://img-blog.csdnimg.cn/20200421215744643.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjY1NDExNA==,size_16,color_FFFFFF,t_70)

2.  **CPU 读取主存的字**  
    两种情况（1）所需字已在缓存中，可直接访问 Cache（一次送一个字节）。  
    （2）不在，将改字所在的主存整个字块调到缓存。
3.  **命中率**  
    （1）Cache 容量越大 CPU 命中率越高。  
    （2）命中 Cache：说明主存快已经调入缓存中。  
    （3）未命中：未调入。
4.  **基本结构**  
    （1）Cache 存储体。  
    （2）地址映射变换机构  
    （3）替换机构  
    （4）Cache 的读写操作  
    ![](https://img-blog.csdnimg.cn/20200421220056552.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjY1NDExNA==,size_16,color_FFFFFF,t_70)

#### 2.Cache–主存[地址映射](https://so.csdn.net/so/search?q=%E5%9C%B0%E5%9D%80%E6%98%A0%E5%B0%84&spm=1001.2101.3001.7020)和替换策略

> 映射机构：主存的块可以放到缓存那些块当中。  
> 替换机构：完成了主存当中的一个块在 Cache 当中的查找操作。

1.  直接映射（不灵活）：某一 主存块只能固定映射到某一缓存块。
2.  全相联映射（成本高）：某一主存块能 映射到任一缓存块
3.  组相联映射：某一 主存块只能映射到某一缓存组中的存储块当中

算法：

1.  先进先出（First-In-First-out,FIFO）算法。
2.  近期最少使用（Least Recently Used,LRU）算法。

### 四. 辅助存储器（外部存储器）

> 特点：不直接与 CPU 交换信息  
> 与主存一起组成了存储器系统的主存 - 辅存层次

第 5 章：输入输出系统
------------

你们可能看不懂我的题目，那么接下来跟我一起去了解输入输出系统的学习过程。

![](https://img-blog.csdnimg.cn/20200423222144189.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjY1NDExNA==,size_16,color_FFFFFF,t_70)  
输入输出，通俗话讲就是进去出来（希望能过审）。

它有多牛逼呢？  
它是除了 CPU 和存储器计算机硬件系统第三个关键部分。

### 一. 发展情况，了解历史

1.  早期阶段  
    （1）分散连接  
    （2）CPU 与 I/O 设备串行工作  
    （4）程序查询方式  
    （3）I/O 设备通过 CPU 与主存交换消息  
    ![](https://img-blog.csdnimg.cn/20200424215257650.png)
    
2.  接口模块和 DMA 阶段  
    （1）总线连接  
    （2）CPU 和 I/O 设备并行  
    （3）工作：中断方式，DMA 方式。
    
3.  具有通道结构阶段  
    I/O 设备通过通道与主机交换信息。
    
4.  具有 I/O 处理机的阶段
    

### 二. 系统组成

> 是由 I/O 软件和 I/O 硬件组成的。

1.I/O 软件  
（1）I/O 指令

<table><thead><tr><th>操作码</th><th>命令码</th><th>设备码</th></tr></thead><tbody></tbody></table>

（2）通道指令

*   指出数组的首地址，传送字数，操作命令
*   是通道自身的指令，用来执行 I/O 操作

2.I/O 硬件：包括接口模块和 I/O 设备。

### 三. I/O 设备与主机的联系方式

1.  I/O 设备的编址方式  
    （1）统一编址：将 I/O 地址看做是存储器地址的一部分。  
    （2）不统一编址：指 I/O 地址和存储器地址分开
    
2.  设备寻址：用设备选择电路识别是否被选中。
    
3.  传送方式  
    （1）并行方式（数据同时输送）：传送快，但数据线多  
    （2）串行方式（逐位传送）：速度慢，但只需一根数据线和地址线
    
4.  联络方式  
    （1）立即响应方式  
    （2）异步工作采用应答信号联络  
    （3）同步工作采用同步时标联络
    
5.  连接方式  
    （1）辐射式：增删困难  
    （2）总线式：现代被采用
    

### 四. I/O 设备与主机信息传送的控制方式

1.  程序查询
2.  程序中断（还在努力编写。。。）。
3.  [DMA 方式](https://blog.csdn.net/weixin_46654114/article/details/105725775)

> 作者：RodmaChen  
> 本人博客：https://blog.csdn.net/weixin_46654114  
> 转载说明：务必注明来源，附带本人博客连接。