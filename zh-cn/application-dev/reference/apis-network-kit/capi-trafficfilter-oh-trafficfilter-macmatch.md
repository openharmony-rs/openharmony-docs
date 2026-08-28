# OH_TrafficFilter_MACMatch

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->

```c
typedef struct OH_TrafficFilter_MACMatch {...} OH_TrafficFilter_MACMatch
```

## 概述

MAC地址匹配条件。

**起始版本：** 26.1.0

**相关模块：** [TrafficFilter](capi-trafficfilter.md)

**所在头文件：** [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| bool enable | 是否启用MAC地址匹配，true表示启用MAC地址匹配，false表示不启用MAC地址匹配。 |
| bool invert | 是否反转匹配结果。true表示反转匹配结果，false表示不反转匹配结果。 |
| char srcMac[OH_TRAFFICFILTER_MAC_ADDRSTRLEN] | 源MAC地址（XX:XX:XX:XX:XX:XX格式）。 |
