# OH_TrafficFilter_MACMatch

```c
typedef struct OH_TrafficFilter_MACMatch {...} OH_TrafficFilter_MACMatch
```

## 概述

MAC地址匹配条件基于MAC地址匹配报文仅支持源MAC地址

**起始版本：** 26.1.0

**相关模块：** [TrafficFilter](capi-trafficfilter.md)

**所在头文件：** [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| bool enable | 启用MAC地址匹配<br>**起始版本：** 26.1.0 |
| bool invert | 是否反转匹配结果<br>**起始版本：** 26.1.0 |
| char srcMac[OH_TRAFFICFILTER_MAC_ADDRSTRLEN] | 源MAC地址，格式为"XX:XX:XX:XX:XX:XX"。ASCII/UTF-8编码，必须以null结尾。OH_TRAFFICFILTER_MAC_ADDRSTRLEN包含null终止符；最大有效字符串长度为17个字符。格式无效将导致规则设置接口返回OH_TRAFFICFILTER_ERROR_INVALID_PARAM。<br>**起始版本：** 26.1.0 |


