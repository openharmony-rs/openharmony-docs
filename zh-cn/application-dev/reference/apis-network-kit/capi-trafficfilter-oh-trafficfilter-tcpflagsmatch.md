# OH_TrafficFilter_TCPFlagsMatch

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->

```c
typedef struct OH_TrafficFilter_TCPFlagsMatch {...} OH_TrafficFilter_TCPFlagsMatch
```

## 概述

TCP标志位匹配条件。仅对TCP协议有效。

**起始版本：** 26.1.0

**相关模块：** [TrafficFilter](capi-trafficfilter.md)

**所在头文件：** [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| bool enable | 是否启用TCP标志位匹配，true表示启用TCP标志位匹配，false表示不启用TCP标志位匹配。 |
| uint8_t flagMask | 标志位掩码（指定检查的标志位）。 |
| uint8_t flagComp | 标志位比较值（标志位比对值）。 |
