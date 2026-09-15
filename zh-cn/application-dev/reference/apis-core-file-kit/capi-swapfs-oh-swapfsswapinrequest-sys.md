# OH_SwapfsSwapInRequest (系统接口)
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @wangke25; @gsl_1234; @wuchengjun5-->
<!--Designer: @gsl_1234; @wangke25-->
<!--Tester: @zsyztt; @yue-ye2; @juxiaopang-->
<!--Adviser: @jinqiuheng-->

```c
typedef struct OH_SwapfsSwapInRequest {...} OH_SwapfsSwapInRequest
```

## 概述

换入操作的请求参数。该结构体用于描述换入操作所需的参数，包括换出时返回的keyId、接收换入数据的缓冲区及其大小。<br> 开发者需通过[OH_Swapfs_SwapOut](capi-oh-swapfs-h-sys.md#oh_swapfs_swapout)获取keyId，再使用本结构体中的参数调用换入接口将数据换入内存。

**起始版本：** 26.0.0

**相关模块：** [Swapfs](capi-swapfs-sys.md)

**所在头文件：** [oh_swapfs.h (系统接口)](capi-oh-swapfs-h-sys.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint64_t keyId | 由先前[OH_Swapfs_SwapOut](capi-oh-swapfs-h-sys.md#oh_swapfs_swapout)返回的keyId。用于唯一标识需要换入的数据。<br>**起始版本：** 26.0.0 |
| void *buffer | 指向接收换入数据的缓冲区指针。不可为空指针。<br> 在Direct I/O模式下，缓冲区地址和大小必须对齐到SWAPFS_DIO_ALIGNMENT，且bufferSize必须大于等于occupiedSize。<br> 在缓冲模式下，bufferSize必须大于等于dataSize。<br> Direct I/O模式直接读写磁盘，不经过系统缓存；缓冲模式使用系统缓存。occupiedSize表示数据实际占用的存储大小，dataSize表示数据的逻辑大小。<br>**起始版本：** 26.0.0 |
| uint64_t bufferSize | 接收缓冲区的大小，单位：Byte。<br> 在Direct I/O模式下必须大于等于occupiedSize且对齐到SWAPFS_DIO_ALIGNMENT。<br> 在缓冲模式下必须大于等于dataSize。建议根据实际数据大小设置合适的缓冲区大小以提升性能。<br> 取值范围：大于等于换入数据的大小，且必须大于0。超出范围或传入无效值时接口返回错误。<br>**起始版本：** 26.0.0 |


