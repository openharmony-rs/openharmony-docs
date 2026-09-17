# OH_TrafficFilter_Config

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->

```c
typedef struct OH_TrafficFilter_Config {...} OH_TrafficFilter_Config
```

## 概述

NFQueue（Netfilter 框架里的一个“数据包排队通道”）配置结构体。

初始化规则：调用[OH_TrafficFilter_CreatePacketController](capi-net-trafficfilter-h.md#oh_trafficfilter_createpacketcontroller)之前，调用者必须将该结构体清零（例如使用memset），然后将[size](#成员变量)设置为调用者分配的结构体实际大小，通常为sizeof(OH_TrafficFilter_Config)。

二进制兼容规则（ABI，即应用程序二进制接口，保证新旧版本编译的代码能互相识别结构体布局）：系统通过[size](#成员变量)来确定哪些字段可以被安全读取。如果[size](#成员变量)小于当前接口所需的最小大小，接口将返回[OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode)。如果[size](#成员变量)大于系统已知的大小，多余的字段将被忽略。

**起始版本：** 26.1.0

**相关模块：** [TrafficFilter](capi-trafficfilter.md)

**所在头文件：** [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint32_t size | 调用者分配的结构体实际大小。 |
| uint32_t packetCopyMode | 报文拷贝模式，请参考[OH_TrafficFilter_PacketCopyMode](capi-trafficfilter-oh-trafficfilter-packetcopymode.md)。默认值为2。 |
| uint32_t packetCopyLen | NFQueue报文拷贝长度（字节），取值范围为[0, 0xFFFF]，0xFFFF表示复制整个报文，其他值复制指定长度的报文头部。默认值为0xFFFF。 |
| uint32_t nfqueueMaxlen | NFQueue最大队列长度（报文数量），0表示使用系统默认值（1024）。 |
| uint32_t nfqueueFlags | NFQueue队列标志，参见[OH_TRAFFICFILTER_NFQUEUE_FLAG_FAIL_OPEN](capi-net-trafficfilter-type-h.md#宏定义)。默认值为0x1。 |
