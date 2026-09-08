# OH_TrafficFilter_PacketCallback

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->

```c
typedef OH_TrafficFilter_PacketDecision (*OH_TrafficFilter_PacketCallback)(
    const OH_TrafficFilter_PacketDesc* packet,
    void* userData
)
```

## 概述

报文回调函数类型。

**起始版本：** 26.1.0

**相关模块：** [TrafficFilter](capi-trafficfilter.md)

**所在头文件：** [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## 汇总

### 参数

| 名称 | 描述 |
| -- | -- |
| [const OH_TrafficFilter_PacketDesc](capi-trafficfilter-oh-trafficfilter-packetdesc.md)* packet | 报文描述符。 |
| void* userData | 用户数据。 |

### 返回

| 类型 | 说明 |
| -- | -- |
| [OH_TrafficFilter_PacketDecision](capi-trafficfilter-oh-trafficfilter-packetdecision.md) | 报文处理决策（接受或丢弃）。 |
