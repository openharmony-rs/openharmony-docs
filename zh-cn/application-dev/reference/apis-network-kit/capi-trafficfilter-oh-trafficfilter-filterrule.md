# OH_TrafficFilter_FilterRule

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->

```c
typedef struct OH_TrafficFilter_FilterRule {...} OH_TrafficFilter_FilterRule
```

## 概述

报文过滤规则。单个OH_TrafficFilter_FilterRule结构内的条件为逻辑与关系，添加到同一OH_TrafficFilter_PacketController的多个规则为逻辑或关系。

初始化规则：调用[OH_TrafficFilter_AddPacketRule](capi-net-trafficfilter-h.md#oh_trafficfilter_addpacketrule)之前，调用者必须将该结构体清零（例如使用memset），然后将[size](#成员变量)设置为调用者分配的结构体实际大小，通常为sizeof(OH_TrafficFilter_FilterRule)。

二进制兼容规则（ABI，即应用程序二进制接口，保证新旧版本编译的代码能互相识别结构体布局）：系统通过[size](#成员变量)来确定哪些字段可以被安全读取。如果[size](#成员变量)小于当前接口所需的最小大小，接口将返回[OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode)。如果[size](#成员变量)大于系统已知的大小，多余的字段将被忽略。

失败规则：如果[OH_TrafficFilter_AddPacketRule](capi-net-trafficfilter-h.md#oh_trafficfilter_addpacketrule)返回错误，不保证规则已被添加或生效。调用者应在假设规则生效之前检查返回值。

**起始版本：** 26.1.0

**相关模块：** [TrafficFilter](capi-trafficfilter.md)

**所在头文件：** [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint32_t size | 调用者分配的结构体实际大小。 |
| uint32_t priority | 优先级（数值越小优先级越高）。 |
| [OH_TrafficFilter_HookPoint](capi-net-trafficfilter-type-h.md#oh_trafficfilter_hookpoint) hookPoint | 钩子点（添加规则到不同钩子点的链上）。 |
| uint8_t protocol | 协议类型（0=不限制，6=TCP，17=UDP）。 |
| [OH_TrafficFilter_IPMatch](capi-trafficfilter-oh-trafficfilter-ipmatch.md) srcIp | 源IP匹配条件。 |
| [OH_TrafficFilter_PortMatch](capi-trafficfilter-oh-trafficfilter-portmatch.md) srcPort | 源端口匹配条件。 |
| [OH_TrafficFilter_IPMatch](capi-trafficfilter-oh-trafficfilter-ipmatch.md) dstIp | 目的IP匹配条件。 |
| [OH_TrafficFilter_PortMatch](capi-trafficfilter-oh-trafficfilter-portmatch.md) dstPort | 目的端口匹配条件。 |
| [OH_TrafficFilter_InterfaceMatch](capi-trafficfilter-oh-trafficfilter-interfacematch.md) inInterface | 入接口匹配条件。 |
| [OH_TrafficFilter_InterfaceMatch](capi-trafficfilter-oh-trafficfilter-interfacematch.md) outInterface | 出接口匹配条件。 |
| uint32_t uidStart | 应用UID范围起始值（UINT32_MAX表示任意）。 |
| uint32_t uidEnd | 应用UID范围结束值（UINT32_MAX表示任意）。 |
| [OH_TrafficFilter_MACMatch](capi-trafficfilter-oh-trafficfilter-macmatch.md) macMatch | MAC地址匹配条件（仅源MAC地址）。 |
| [OH_TrafficFilter_TCPFlagsMatch](capi-trafficfilter-oh-trafficfilter-tcpflagsmatch.md) tcpFlagsMatch | TCP标志位匹配条件（仅对TCP协议有效）。 |
| [OH_TrafficFilter_ConntrackMatch](capi-trafficfilter-oh-trafficfilter-conntrackmatch.md) conntrackMatch | 连接跟踪匹配条件。 |
