# OH_TrafficFilter_TCPFlagsMatch

```c
typedef struct OH_TrafficFilter_TCPFlagsMatch {...} OH_TrafficFilter_TCPFlagsMatch
```

## 概述

TCP标志位匹配条件。仅对TCP协议有效。

<!--Device-struct OH_TrafficFilter_TCPFlagsMatch {...}--><!--Device-struct OH_TrafficFilter_TCPFlagsMatch {...}-End-->

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

**起始版本：** 26.0.1

**相关模块：** [TrafficFilter](capi-network-kit-trafficfilter.md)

**所在头文件：** [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| bool enable | 是否启用TCP标志位匹配，true表示启用TCP标志位匹配，false表示不启用TCP标志位匹配。<br>**起始版本：** 26.0.1<br><!--Device-bool enable--><!--Device-bool enable-End--> |
| uint8_t flagMask | 标志位掩码（指定要检查的标志，使用OH_TRAFFICFILTER_TCP_FLAG_*常量）。<br>**起始版本：** 26.0.1<br><!--Device-uint8_t flagMask--><!--Device-uint8_t flagMask-End--> |
| uint8_t flagComp | 标志位比较值（指定必须设置的标志）。<br>**起始版本：** 26.0.1<br><!--Device-uint8_t flagComp--><!--Device-uint8_t flagComp-End--> |


