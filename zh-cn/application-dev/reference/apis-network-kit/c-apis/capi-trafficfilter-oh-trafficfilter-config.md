# OH_TrafficFilter_Config

```c
typedef struct OH_TrafficFilter_Config {...} OH_TrafficFilter_Config
```

## 概述

NFQueue配置结构体- 如果`config`为**NULL**，实现将应用以下默认值：- `packetCopyLen` = 0xFFFF（拷贝整个报文）- `nfqueueMaxlen` = 0 （使用系统默认值，即1024）- `nfqueueFlags` = OH_TRAFFICFILTER_NFQUEUE_FLAG_FAIL_OPEN- 如果`config`为**非NULL**，调用者**必须**：1. 将整个结构体零初始化（例如`memset(&cfg, 0, sizeof(cfg))`）。2. 设置`size` = `sizeof(OH_TrafficFilter_Config)`。3. 将所有其他字段设置为定义范围内的有效值（见下文）。- **未遵守**此约定（例如`size`不正确、字段值超出范围）将导致接口返回`OH_TRAFFICFILTER_ERROR_INVALID_PARAM`。

**起始版本：** 26.1.0

**相关模块：** [TrafficFilter](capi-trafficfilter.md)

**所在头文件：** [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint32_t size | 调用者必须将其设置为`sizeof(OH_TrafficFilter_Config)`。调用者需要先零初始化结构体，然后设置此字段。实现使用此值来确定有效数据范围，以实现二进制兼容。<br>**起始版本：** 26.1.0 |
| uint32_t packetCopyMode | NFQueue报文拷贝模式，参见OH_TrafficFilter_PacketCopyMode<br>**起始版本：** 26.1.0 |
| uint32_t packetCopyLen | NFQueue报文拷贝长度（字节），0xFFFF表示拷贝整个报文，较小的值仅拷贝报文头<br>**起始版本：** 26.1.0 |
| uint32_t nfqueueMaxlen | NFQueue最大队列长度（报文数量），0表示系统默认值（1024）<br>**起始版本：** 26.1.0 |
| uint32_t nfqueueFlags | NFQueue队列标志，参见OH_TRAFFICFILTER_NFQUEUE_FLAG_*定义<br>**起始版本：** 26.1.0 |


