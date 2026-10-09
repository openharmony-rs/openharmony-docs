# OH_SwapfsStats (系统接口)
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @wangke25; @gsl_1234; @wuchengjun5-->
<!--Designer: @gsl_1234; @wangke25-->
<!--Tester: @zsyztt; @yue-ye2; @juxiaopang-->
<!--Adviser: @jinqiuheng-->

```c
typedef struct OH_SwapfsStats {...} OH_SwapfsStats
```

## 概述

OH_SwapfsStats用于获取swapfs管理器的统计信息，包括活跃key数量、数据大小、空间使用情况等。<br> 适用于需要监控swapfs状态、分析存储使用情况的场景，帮助开发者了解系统的交换空间使用情况。

**起始版本：** 26.0.0

**相关模块：** [Swapfs](capi-swapfs-sys.md)

**所在头文件：** [oh_swapfs.h (系统接口)](capi-oh-swapfs-h-sys.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint64_t totalKeys | 管理器中活跃key的总数。<br>**起始版本：** 26.0.0 |
| uint64_t totalDataSize | 所有key的原始数据总大小，单位：Byte。<br>**起始版本：** 26.0.0 |
| uint64_t totalOccupiedSize | 所有key的对齐后文件总大小，单位：Byte。<br>**起始版本：** 26.0.0 |
| uint64_t spaceLimitBytes | 配置的交换空间上限，单位：Byte。<br>**起始版本：** 26.0.0 |
| bool featureEnabled | 换出功能是否已启用。当设备空间低于5GB或控制策略禁用该功能时为false。<br>**起始版本：** 26.0.0 |
| [OH_SwapfsDisableReason](capi-oh-swapfs-h-sys.md#oh_swapfsdisablereason) disableReason | 换出功能被禁用的原因。仅在featureEnabled为false时有效。<br>**起始版本：** 26.0.0 |
| uint64_t accumulatedWriteBytes | 成功换出操作累计写入量，单位：Byte。<br>**起始版本：** 26.0.0 |
| int64_t lastSpaceCheckTime | 最近一次检查设备空间的时间戳（Unix纪元，单位为ms）。<br>**起始版本：** 26.0.0 |
| uint64_t availableDeviceSpace | 最近一次检查时缓存设备的可用存储空间，单位：Byte。<br>**起始版本：** 26.0.0 |


