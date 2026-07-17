# OH_SwapfsSwapOutRequest

```c
typedef struct OH_SwapfsSwapOutRequest {...} OH_SwapfsSwapOutRequest
```

## 概述

换出操作请求参数。

**起始版本：** 26.0.0

**相关模块：** [Swapfs](capi-swapfs.md)

**所在头文件：** [oh_swapfs.h](capi-oh-swapfs-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| const void *buffer | 指向要换出的数据缓冲区的指针。不能为NULL。<br>**起始版本：** 26.0.0 |
| uint64_t bufferSize | 数据缓冲区的大小，以字节为单位。必须大于0。<br>**起始版本：** 26.0.0 |


