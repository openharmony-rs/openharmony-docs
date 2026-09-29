# OH_TrafficFilter_ProcessInfo

```c
struct OH_TrafficFilter_ProcessInfo {...}
```

## 概述

进程信息结构体。存储OH_TrafficFilter_QueryProcess返回的进程信息。<br>初始化规则：调用OH_TrafficFilter_QueryProcess之前， 调用者必须将该结构体清零（例如使用memset），然后将[size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md)设置为调用者分配的结构体实际大小，通常为sizeof(OH_TrafficFilter_ProcessInfo)。<br>二进制兼容规则（ABI， 即应用程序二进制接口，保证新旧版本编译的代码能互相识别结构体布局）：系统通过[size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md)来确定哪些输出字段可以被安全写入。只有被[size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md)完全覆盖的字段才会被系统写入。如果[size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md)小于读取 [size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md)字段本身所需的最小大小，接口将返回[OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode)。如果[size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md)大于系统已知的大小，多余的字段将被忽略。<br> 输出有效性规则：当OH_TrafficFilter_QueryProcess返回[OH_TRAFFICFILTER_OK](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode)时，被[size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md)覆盖的字段包含有效的输出值。当接口返回错误时， 调用者不应依赖[size](capi-trafficfilter-oh-trafficfilter-connectioninfo.md)以外的输出字段的值。

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

**起始版本：** 26.0.0

**相关模块：** [TrafficFilter](capi-trafficfilter.md)

**所在头文件：** [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint32_t size | 调用者分配的结构体实际大小。<br>**起始版本：** 26.0.0 |
| uint32_t pid | 进程ID。<br>**起始版本：** 26.0.0 |
| uint32_t uid | 用户ID。<br>**起始版本：** 26.0.0 |


