# OH_SwapfsSwapOutRequest (系统接口)
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @wangke25; @gsl_1234; @wuchengjun5-->
<!--Designer: @gsl_1234; @wangke25-->
<!--Tester: @zsyztt; @yue-ye2; @juxiaopang-->
<!--Adviser: @jinqiuheng-->

```c
typedef struct OH_SwapfsSwapOutRequest {...} OH_SwapfsSwapOutRequest
```

## 概述

换出操作的请求参数。用于在应用需要释放内存时，主动触发数据换出到交换分区的场景，例如内存紧张时将部分数据临时换出。

**起始版本：** 26.0.0

**相关模块：** [Swapfs](capi-swapfs-sys.md)

**所在头文件：** [oh_swapfs.h (系统接口)](capi-oh-swapfs-h-sys.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| const void *buffer | 指向待换出数据缓冲区的指针。不可为空指针。传入空指针时返回错误码[SWAPFS_E_INVAL](capi-swapfs-errcode-h-sys.md#oh_swapfs_errcode)。<br>**起始版本：** 26.0.0 |
| uint64_t bufferSize | 待换出数据缓冲区的大小，单位：Byte。必须大于0。传入0时返回错误码[SWAPFS_E_INVAL](capi-swapfs-errcode-h-sys.md#oh_swapfs_errcode)。<br>**起始版本：** 26.0.0 |


