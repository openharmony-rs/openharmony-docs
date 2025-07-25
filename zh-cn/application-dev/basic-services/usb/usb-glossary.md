# USB服务开发术语

## B

### Baud Rate（波特率）

波特率表示串口设备每秒传输的符号数（符号即二进制位，包括数据位、起始位、停止位、校验位），单位为Baud（波特），例如9600 Baud表示每秒传输9600个符号。收发双方必须使用相同的波特率，否则数据无法正确解析。

### Bulk Transfer（批量传输）

一种USB服务的单向数据传输模式，适用于大数据量的传输场景。在传输过程中使用批量事务（IN/OUT令牌包、数据包、握手包）处理方式提高总体传输量，并通过错误检测和重传机制保证数据传输的可靠性，但批量传输在几种USB传输模式中优先级最低。其主要应用于U盘、打印机、扫描仪等对实时性要求低但需要高可靠性的设备。

## C

### Control Transfer（控制传输）

一种USB服务的双向传输模式，适用于设备配置、状态查询和命令传输场景。在传输过程中包含三个阶段：建立阶段（SETUP事务）、数据阶段（可选批量事务）和状态阶段（握手确认）。其主要应用于设备枚举（如读取描述符）、初始化配置、固件升级等基础控制操作的场景。

## D

### Data Bit（数据位）

数据位表示每个数据包中实际传输的有效二进制位数，决定了单个字符的数据容量。常见的取值包括5位、6位、7位和8位。数据位决定单次传输的信息量，数据位越多，单次传输信息量越大，但需更多时间同步。

### Device（设备）

Device（设备）指连接到Host（主机）的外设，负责执行特定功能（如存储、输入输出等），被动响应Host的指令。例如U盘、鼠标、打印机等均属于Device（设备）。

## E

### Endpoint（端点）

端点是设备（Device）与主机（Host）之间进行数据传输的逻辑终点，是USB通信的基本单元。每个端点具有唯一的地址和方向（IN表示设备（Device）到主机（Host），OUT表示主机（Host）到设备（Device））。每个端点代表一个单向或双向的数据传输通道。

## H

### Host（主机）

Host是指具有USB主机功能的设备。Host是控制和管理USB总线的设备，它负责管理总线上的连接设备，并协调数据传输和通信。Host通常是计算机或其他主机，如PC机、智能手机、平板等。Host可以连接和控制多个设备，通过USB端口与设备相连，提供数据传输和充电的功能。

## I

### Interface（接口）

Interface（接口）是USB设备中功能模块的逻辑抽象，代表设备的一种独立功能（如音频、存储或通信功能）。每个接口包含一组端点（Endpoint），并通过配置（USBConfiguration）管理其激活状态。通过接口的灵活配置，USB设备能够实现多功能复用和动态功能切换，这是USB协议支持即插即用和复杂外设的核心机制。

### Interrupt Transfer（中断传输）

一种USB服务的单向数据传输模式，主机周期性轮询设备（如1ms~255ms），保证实时性和正确性。事务结构与批量传输类似，但优先级更高。适用于键盘、鼠标、游戏手柄等需要低延迟响应的输入设备。

### Isochronous Transfer（实时传输）

一种USB服务的单向数据传输模式，无握手包，通过固定带宽保证实时性但允许数据丢失。事务仅包含令牌和数据阶段，适合流媒体传输。适用于摄像头、USB音响、视频会议设备等对连续性要求高、容错性强的场景。

## P

### Parity Bit（校验位）

校验位是附加在数据帧中的1位二进制值，根据数据位的内容按特定规则生成。常见的有，奇校验（Odd）数据位+校验位中“1”的总数为奇数，偶校验（Even）数据位+校验位中“1”的总数为偶数，无校验（None）不添加校验位。校验位通过验证数据位中“1”的数量，判断数据在传输过程中是否发生位翻转、噪声干扰等错误，增加校验位会略微降低传输效率，但能提高容错性。

### Pipe（管道）

Pipe（管道） 是主机（Host）与设备端点（Endpoint）之间的逻辑通信通道，用于数据传输。Pipe并非物理连接，而是主机（Host）与设备端点（Endpoint）之间的抽象通信路径。每个Pipe对应设备的一个特定端点（Endpoint）。Pipe是单向的，方向由端点决定（例如IN端点对应主机接收数据的Pipe，OUT端点对应主机发送数据的Pipe）。
  
## S

### Stop Bit（停止位）

停止位位于数据帧末尾，是逻辑高电平信号，用于标识一个字符（数据包）传输的结束。典型长度有1位和2位（实际开发中1位最常用，2位多用于抗干扰场景）。其核心作用是为接收端提供时序同步容错空间，并确保数据完整性。

## U

### USBConfiguration（配置）

USBConfiguration表示USB设备的一种功能集合。一个USB设备可以支持多个配置，但同一时间只能激活一个配置。每个USBConfiguration包含多个Interface（接口），每个接口代表一种独立功能（如数据传输、音频输出等）。每个Interface下又包含多个Endpoint（端点），用于实际的数据传输（如控制传输、批量传输等）。
