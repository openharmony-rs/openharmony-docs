# OH_TrafficFilter_PacketCopyMode

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->

```c
typedef enum OH_TrafficFilter_PacketCopyMode {...} OH_TrafficFilter_PacketCopyMode
```

## 概述

报文复制模式枚举。

**起始版本：** 26.1.0

**相关模块：** [TrafficFilter](capi-trafficfilter.md)

**所在头文件：** [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## 汇总

### 枚举项

| 名称 | 说明 |
| -- | -- |
| OH_TRAFFICFILTER_COPY_MODE_META = 0 | 仅复制元数据（不复制报文数据）。 |
| OH_TRAFFICFILTER_COPY_MODE_HEADER = 1 | 仅复制报文头部（由packetCopyLen指定）。 |
| OH_TRAFFICFILTER_COPY_MODE_FULL = 2 | 复制整个报文。 |
| OH_TRAFFICFILTER_COPY_MODE_MAXLEN = 3 | 复制指定最大长度的报文。 |
