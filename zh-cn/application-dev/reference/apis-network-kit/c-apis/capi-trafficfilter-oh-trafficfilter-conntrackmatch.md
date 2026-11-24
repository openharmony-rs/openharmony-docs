# OH_TrafficFilter_ConntrackMatch

```c
typedef struct OH_TrafficFilter_ConntrackMatch {...} OH_TrafficFilter_ConntrackMatch
```

## 概述

连接跟踪（Connection Tracking）匹配条件。

<!--Device-struct OH_TrafficFilter_ConntrackMatch {...}--><!--Device-struct OH_TrafficFilter_ConntrackMatch {...}-End-->

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

**起始版本：** 26.0.1

**相关模块：** [TrafficFilter](capi-network-kit-trafficfilter.md)

**所在头文件：** [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| bool enable | 是否启用连接跟踪匹配，true表示启用连接跟踪匹配，false表示不启用连接跟踪匹配。<br>**起始版本：** 26.0.1<br><!--Device-bool enable--><!--Device-bool enable-End--> |
| uint8_t stateMask | 连接状态（使用OH_TRAFFICFILTER_CT_STATE_*位图）。<br>**起始版本：** 26.0.1<br><!--Device-uint8_t stateMask--><!--Device-uint8_t stateMask-End--> |


