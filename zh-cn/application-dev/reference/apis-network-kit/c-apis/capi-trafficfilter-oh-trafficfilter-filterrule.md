# OH_TrafficFilter_FilterRule

```c
typedef struct OH_TrafficFilter_FilterRule {...} OH_TrafficFilter_FilterRule
```

## 概述

报文过滤规则定义报文匹配条件。1. **初始化约定（调用方）**：- 调用者必须在使用前将整个结构体**零初始化**（例如通过`memset`）。- `size`字段**必须**显式设置为`sizeof(OH_TrafficFilter_FilterRule)`。- 如果`size`小于`sizeof(OH_TrafficFilter_FilterRule)`，实现将仅读取截至`size`的稳定前缀字段，忽略后续字节。2. **读取约定（实现方）**：- 实现严格根据`size`值确定有效字段范围。- 如果`size` < `sizeof(OH_TrafficFilter_FilterRule)`，实现将其视为旧版本，仅读取与该大小兼容的前缀字段。- 如果`size`为0或指针为NULL，实现必须返回错误。

**起始版本：** 26.1.0

**相关模块：** [TrafficFilter](capi-trafficfilter.md)

**所在头文件：** [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint32_t size | 调用者必须将其设置为`sizeof(OH_TrafficFilter_FilterRule)`。调用者需要先零初始化结构体，然后设置此字段。实现使用此值来确定有效数据范围，以实现二进制兼容。<br>**起始版本：** 26.1.0 |
| uint32_t priority | 优先级（数值越小优先级越高）<br>**起始版本：** 26.1.0 |
| [OH_TrafficFilter_HookPoint](capi-net-trafficfilter-type-h.md#oh_trafficfilter_hookpoint) hookPoint | 钩子点<br>**起始版本：** 26.1.0 |
| uint8_t protocol | 协议（0=任意，6=TCP，17=UDP）<br>**起始版本：** 26.1.0 |
| [OH_TrafficFilter_IPMatch](capi-trafficfilter-oh-trafficfilter-ipmatch.md) srcIp | 源IP匹配条件<br>**起始版本：** 26.1.0 |
| [OH_TrafficFilter_PortMatch](capi-trafficfilter-oh-trafficfilter-portmatch.md) srcPort | 源端口匹配条件<br>**起始版本：** 26.1.0 |
| [OH_TrafficFilter_IPMatch](capi-trafficfilter-oh-trafficfilter-ipmatch.md) dstIp | 目的IP匹配条件<br>**起始版本：** 26.1.0 |
| [OH_TrafficFilter_PortMatch](capi-trafficfilter-oh-trafficfilter-portmatch.md) dstPort | 目的端口匹配条件<br>**起始版本：** 26.1.0 |
| [OH_TrafficFilter_InterfaceMatch](capi-trafficfilter-oh-trafficfilter-interfacematch.md) inInterface | 入接口匹配条件<br>**起始版本：** 26.1.0 |
| [OH_TrafficFilter_InterfaceMatch](capi-trafficfilter-oh-trafficfilter-interfacematch.md) outInterface | 出接口匹配条件<br>**起始版本：** 26.1.0 |
| uint32_t uidStart | 应用UID范围起始值（包含）。有效范围：0到UINT32_MAX。要匹配任意UID，将uidStart和uidEnd都设置为UINT32_MAX。如果uidStart > uidEnd，规则设置接口返回OH_TRAFFICFILTER_ERROR_INVALID_PARAM。零初始化后，uidStart=0且uidEnd=0，仅匹配UID 0。<br>**起始版本：** 26.1.0 |
| uint32_t uidEnd | 应用UID范围结束值（包含）。有效范围：0到UINT32_MAX。使用详情参见uidStart。<br>**起始版本：** 26.1.0 |
| [OH_TrafficFilter_MACMatch](capi-trafficfilter-oh-trafficfilter-macmatch.md) macMatch | MAC地址匹配条件（仅源MAC）<br>**起始版本：** 26.1.0 |
| [OH_TrafficFilter_TCPFlagsMatch](capi-trafficfilter-oh-trafficfilter-tcpflagsmatch.md) tcpFlagsMatch | TCP标志匹配条件（仅对TCP协议有效）<br>**起始版本：** 26.1.0 |
| [OH_TrafficFilter_ConntrackMatch](capi-trafficfilter-oh-trafficfilter-conntrackmatch.md) conntrackMatch | 连接跟踪匹配条件<br>**起始版本：** 26.1.0 |


