# OH_TrafficFilter_MACMatch

```c
typedef struct OH_TrafficFilter_MACMatch {...} OH_TrafficFilter_MACMatch
```

## 概述

MAC地址匹配条件。

<!--Device-struct OH_TrafficFilter_MACMatch {...}--><!--Device-struct OH_TrafficFilter_MACMatch {...}-End-->

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

**起始版本：** 26.0.1

**相关模块：** [TrafficFilter](capi-network-kit-trafficfilter.md)

**所在头文件：** [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| bool enable | 是否启用MAC地址匹配，true表示启用MAC地址匹配，false表示不启用MAC地址匹配。<br>**起始版本：** 26.0.1<br><!--Device-bool enable--><!--Device-bool enable-End--> |
| bool invert | 是否反转匹配结果。true表示反转匹配结果，false表示不反转匹配结果。<br>**起始版本：** 26.0.1<br><!--Device-bool invert--><!--Device-bool invert-End--> |
| char srcMac[OH_TRAFFICFILTER_MAC_ADDRSTRLEN] | 源MAC地址，格式为"XX:XX:XX:XX:XX:XX"。 ASCII/UTF-8编码，必须以null结尾。 OH_TRAFFICFILTER_MAC_ADDRSTRLEN包含null终止符； 最大有效字符串长度为17个字符。 格式无效将导致规则设置接口返回[OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode)。<br>**起始版本：** 26.0.1<br><!--Device-char srcMac[OH_TRAFFICFILTER_MAC_ADDRSTRLEN]--><!--Device-char srcMac[OH_TRAFFICFILTER_MAC_ADDRSTRLEN]-End--> |


