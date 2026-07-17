# OH_SwapfsStats

```c
typedef struct OH_SwapfsStats {...} OH_SwapfsStats
```

## 概述

当前swapfs管理器的统计信息。

**起始版本：** 26.0.0

**相关模块：** [Swapfs](capi-swapfs.md)

**所在头文件：** [oh_swapfs.h](capi-oh-swapfs-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint64_t totalKeys | 管理器中的活动Key总数。<br>**起始版本：** 26.0.0 |
| uint64_t totalDataSize | 所有Key的原始数据总大小，以字节为单位。<br>**起始版本：** 26.0.0 |
| uint64_t totalOccupiedSize | 所有Key的总对齐文件大小（以字节为单位）。<br>**起始版本：** 26.0.0 |
| uint64_t spaceLimitBytes | 配置的交换空间限制（以字节为单位）。<br>**起始版本：** 26.0.0 |
| bool featureEnabled | 当前是否启用了换出。当设备空间低于5GB或控制策略禁用该功能。<br>**起始版本：** 26.0.0 |
| [OH_SwapfsDisableReason](capi-oh-swapfs-h.md#oh_swapfsdisablereason) disableReason | 功能关闭的原因。<br>**起始版本：** 26.0.0 |
| uint64_t accumulatedWriteBytes | 成功的换出操作写入的累计字节数。<br>**起始版本：** 26.0.0 |
| int64_t lastSpaceCheckTime | 上次设备空间检查的时间戳（Unix epoch，以毫秒为单位）。<br>**起始版本：** 26.0.0 |
| uint64_t availableDeviceSpace | 上次检查时缓存的可用设备存储空间（以字节为单位）。<br>**起始版本：** 26.0.0 |


