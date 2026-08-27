# OH_TrafficFilter_InterfaceMatch

```c
typedef struct OH_TrafficFilter_InterfaceMatch {...} OH_TrafficFilter_InterfaceMatch
```

## 概述

接口匹配条件。

**起始版本：** 26.0.0

**相关模块：** [TrafficFilter](capi-trafficfilter.md)

**所在头文件：** [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| bool enabled | 是否启用接口匹配。<br>**起始版本：** 26.0.0 |
| bool invert | 是否反转匹配结果。<br>**起始版本：** 26.0.0 |
| bool isPrefix | 是否按前缀匹配接口名称。<br>**起始版本：** 26.0.0 |
| char ifName[OH_TRAFFICFILTER_IFNAMSIZ] | 接口名称。该字符串必须以UTF-8编码，且必须以NUL结尾。该缓冲区的容量为{@link OH_TRAFFICFILTER_IFNAMSIZ}字节，包含结尾的NUL字符。因此，接口名称的最大长度为{@link OH_TRAFFICFILTER_IFNAMSIZ} - 1字节，不包含结尾的NUL字符。如果{@link enabled}为true，该字符串不能为空。如果该字符串在{@link OH_TRAFFICFILTER_IFNAMSIZ}字节内没有以NUL结尾，或者其长度超过{@link OH_TRAFFICFILTER_IFNAMSIZ} - 1字节，使用该结构体的接口将返回[OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode)。如果{@link enabled}为false，该字段将被忽略。建议在禁用接口匹配时将该缓冲区全部置零。<br>**起始版本：** 26.0.0 |


