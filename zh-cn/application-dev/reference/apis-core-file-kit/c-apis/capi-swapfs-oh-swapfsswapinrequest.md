# OH_SwapfsSwapInRequest

```c
typedef struct OH_SwapfsSwapInRequest {...} OH_SwapfsSwapInRequest
```

## 概述

换入操作的请求参数。

**起始版本：** 26.0.0

**相关模块：** [Swapfs](capi-swapfs.md)

**所在头文件：** [oh_swapfs.h](capi-oh-swapfs-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint64_t keyId | 上一次换出操作返回的keyId。<br>**起始版本：** 26.0.0 |
| void *buffer | 接收换入数据的缓冲区指针。不能为NULL。DIO模式下，buffer地址和大小必须对齐SWAPFS_DIO_ALIGNMENT。且bufferSize必须大于等于OccupiedSize。在缓冲模式下，bufferSize必须大于等于dataSize。<br>**起始版本：** 26.0.0 |
| uint64_t bufferSize | 接收缓冲区大小，以字节为单位。<br>**起始版本：** 26.0.0 |


