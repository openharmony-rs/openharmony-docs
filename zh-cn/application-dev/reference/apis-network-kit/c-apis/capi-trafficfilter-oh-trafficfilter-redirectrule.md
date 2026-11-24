# OH_TrafficFilter_RedirectRule

```c
typedef struct OH_TrafficFilter_RedirectRule {...} OH_TrafficFilter_RedirectRule
```

## 概述

流量重定向规则。定义TCP流量重定向规则，将匹配的流量重定向到指定的代理服务器。 <br>初始化规则：调用[OH_TrafficFilter_AddRedirectRule](capi-net-trafficfilter-h.md#oh_trafficfilter_addredirectrule)之前，调用者必须将该结构体清零（例如使用memset）， 然后将[size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md)设置为调用者分配的结构体实际大小，通常为sizeof(OH_TrafficFilter_RedirectRule)。 <br>二进制兼容规则（ABI，即应用程序二进制接口， 保证新旧版本编译的代码能互相识别结构体布局）：系统通过[size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md)来确定哪些字段可以被安全读取。 如果[size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md)小于当前接口所需的最小大小，接口将返回[OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode)。 如果[size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md)大于系统已知的大小，多余的字段将被忽略。 <br>失败规则：如果[OH_TrafficFilter_AddRedirectRule](capi-net-trafficfilter-h.md#oh_trafficfilter_addredirectrule)返回错误，不保证规则已被添加或生效。 调用者应在假设规则生效之前检查返回值。

<!--Device-struct OH_TrafficFilter_RedirectRule {...}--><!--Device-struct OH_TrafficFilter_RedirectRule {...}-End-->

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

**起始版本：** 26.0.0

**相关模块：** [TrafficFilter](capi-network-kit-trafficfilter.md)

**所在头文件：** [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint32_t size | 调用者分配的结构体实际大小。<br>**起始版本：** 26.0.0<br><!--Device-uint32_t size--><!--Device-uint32_t size-End--> |
| uint32_t priority | 优先级（数值越小优先级越高，规则与报文过滤器相同）。<br>**起始版本：** 26.0.0<br><!--Device-uint32_t priority--><!--Device-uint32_t priority-End--> |
| [OH_TrafficFilter_HookPoint](capi-net-trafficfilter-type-h.md#oh_trafficfilter_hookpoint) hookPoint | 钩子点，指定规则在网络协议栈中生效的位置（仅支持PREROUTING和OUTPUT）。<br>**起始版本：** 26.0.0<br><!--Device-OH_TrafficFilter_HookPoint hookPoint--><!--Device-OH_TrafficFilter_HookPoint hookPoint-End--> |
| uint8_t protocol | 协议（固定为TCP=6）。<br>**起始版本：** 26.0.0<br><!--Device-uint8_t protocol--><!--Device-uint8_t protocol-End--> |
| [OH_TrafficFilter_IPMatch](capi-trafficfilter-oh-trafficfilter-ipmatch.md) srcIp | 源IP匹配条件。<br>**起始版本：** 26.0.0<br><!--Device-OH_TrafficFilter_IPMatch srcIp--><!--Device-OH_TrafficFilter_IPMatch srcIp-End--> |
| [OH_TrafficFilter_PortMatch](capi-trafficfilter-oh-trafficfilter-portmatch.md) srcPort | 源端口匹配条件。<br>**起始版本：** 26.0.0<br><!--Device-OH_TrafficFilter_PortMatch srcPort--><!--Device-OH_TrafficFilter_PortMatch srcPort-End--> |
| [OH_TrafficFilter_IPMatch](capi-trafficfilter-oh-trafficfilter-ipmatch.md) dstIp | 目的IP匹配条件。<br>**起始版本：** 26.0.0<br><!--Device-OH_TrafficFilter_IPMatch dstIp--><!--Device-OH_TrafficFilter_IPMatch dstIp-End--> |
| [OH_TrafficFilter_PortMatch](capi-trafficfilter-oh-trafficfilter-portmatch.md) dstPort | 目的端口匹配条件。<br>**起始版本：** 26.0.0<br><!--Device-OH_TrafficFilter_PortMatch dstPort--><!--Device-OH_TrafficFilter_PortMatch dstPort-End--> |
| [OH_TrafficFilter_InterfaceMatch](capi-trafficfilter-oh-trafficfilter-interfacematch.md) inInterface | 入接口匹配条件。<br>**起始版本：** 26.0.0<br><!--Device-OH_TrafficFilter_InterfaceMatch inInterface--><!--Device-OH_TrafficFilter_InterfaceMatch inInterface-End--> |
| [OH_TrafficFilter_InterfaceMatch](capi-trafficfilter-oh-trafficfilter-interfacematch.md) outInterface | 出接口匹配条件。<br>**起始版本：** 26.0.0<br><!--Device-OH_TrafficFilter_InterfaceMatch outInterface--><!--Device-OH_TrafficFilter_InterfaceMatch outInterface-End--> |
| uint32_t uidStart | 应用UID范围起始值，有效范围：[0, UINT32_MAX]。 如需匹配任意UID，将uidStart和uidEnd都设置为UINT32_MAX。 如果uidStart > uidEnd，规则设置接口返回[OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode)。 零初始化后，uidStart=0且uidEnd=0，仅匹配UID 0。<br>**起始版本：** 26.0.0<br><!--Device-uint32_t uidStart--><!--Device-uint32_t uidStart-End--> |
| uint32_t uidEnd | 应用UID范围结束值，有效范围：[0, UINT32_MAX]，使用详情参见uidStart。<br>**起始版本：** 26.0.0<br><!--Device-uint32_t uidEnd--><!--Device-uint32_t uidEnd-End--> |
| [OH_TrafficFilter_IPAddress](capi-trafficfilter-oh-trafficfilter-ipaddress.md) proxyIp | 代理服务器IP地址（支持IPv4和IPv6）。<br>**起始版本：** 26.0.0<br><!--Device-OH_TrafficFilter_IPAddress proxyIp--><!--Device-OH_TrafficFilter_IPAddress proxyIp-End--> |
| uint16_t proxyPort | 代理服务器端口。<br>**起始版本：** 26.0.0<br><!--Device-uint16_t proxyPort--><!--Device-uint16_t proxyPort-End--> |


