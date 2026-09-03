# OH_SwapfsDataInfo (系统接口)
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @wangke25; @gsl_1234; @wuchengjun5-->
<!--Designer: @gsl_1234; @wangke25-->
<!--Tester: @zsyztt; @yue-ye2; @juxiaopang-->
<!--Adviser: @jinqiuheng-->

```c
typedef struct OH_SwapfsDataInfo {...} OH_SwapfsDataInfo
```

## 概述

单个key的信息。用于在应用需要精确管理换出数据条目的元信息时（如查询换出状态、监控换出大小等）。

**起始版本：** 26.0.0

**相关模块：** [Swapfs](capi-swapfs-sys.md)

**所在头文件：** [oh_swapfs.h (系统接口)](capi-oh-swapfs-h-sys.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint64_t keyId | 交换数据条目的标识符，用于唯一标识交换数据，不同keyId对应不同的数据条目。<br>**起始版本：** 26.0.0 |
| uint64_t dataSize | 换出时调用方提供的原始数据大小，单位：Byte。该大小决定了数据占用的空间和读取时的性能表现。<br>**起始版本：** 26.0.0 |
| uint64_t occupiedSize | 磁盘上占用的文件大小，单位：Byte。<br> 在Direct I/O模式下为dataSize向上对齐到SWAPFS_DIO_ALIGNMENT的值；在缓冲模式下等于dataSize。<br>**起始版本：** 26.0.0 |
| int64_t createTime | key创建时的时间戳（Unix纪元，单位为ms）。该时间戳用于记录数据创建时间，可用于数据排序、过期策略判断等。<br>**起始版本：** 26.0.0 |
| [OH_SwapfsKeyStatus](capi-oh-swapfs-h-sys.md#oh_swapfskeystatus) status | key的当前状态。不同状态值表示key的不同使用阶段，如是否可用、是否正在交换中、是否已删除等。<br>**起始版本：** 26.0.0 |
| bool canSwapIn | 该key是否可被换入。<br> 如果key的[OH_SwapfsKeyStatus](capi-oh-swapfs-h-sys.md#oh_swapfskeystatus)状态处于OH_SWAPFS_KEY_STATUS_REMOVING则为false，若key活跃未被清理则为true。<br>**起始版本：** 26.0.0 |


