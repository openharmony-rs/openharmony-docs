# OH_TrafficFilter_TCPFlagsMatch

```c
typedef struct OH_TrafficFilter_TCPFlagsMatch {...} OH_TrafficFilter_TCPFlagsMatch
```

## 概述

TCP标志匹配条件基于TCP标志设置匹配TCP报文

**起始版本：** 26.1.0

**相关模块：** [TrafficFilter](capi-trafficfilter.md)

**所在头文件：** [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| bool enable | 启用TCP标志匹配<br>**起始版本：** 26.1.0 |
| uint8_t flagMask | 标志掩码（指定要检查的标志，使用OH_TRAFFICFILTER_TCP_FLAG_*常量）<br>**起始版本：** 26.1.0 |
| uint8_t flagComp | 比较标志（指定必须设置的标志）<br>**起始版本：** 26.1.0 |


