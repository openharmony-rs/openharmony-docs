# OH_SwapfsDataInfo

```c
typedef struct OH_SwapfsDataInfo {...} OH_SwapfsDataInfo
```

## 概述

单个swap key的信息。

**起始版本：** 26.0.0

**相关模块：** [Swapfs](capi-swapfs.md)

**所在头文件：** [oh_swapfs.h](capi-oh-swapfs-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint64_t keyId | 标识此交换数据条目的keyId。<br>**起始版本：** 26.0.0 |
| uint64_t dataSize | 在换出期间由调用方提供的原始数据大小（以字节为单位）。<br>**起始版本：** 26.0.0 |
| uint64_t occupiedSize | 磁盘上占用的文件大小（以字节为单位）。在DIO模式下，这是将dataSize对齐到SWAPFS_DIO_ALIGNMENT；在缓冲模式下，它等于dataSize。<br>**起始版本：** 26.0.0 |
| int64_t createTime | 创建Key时的时间戳（Unix epoch，以毫秒为单位）。<br>**起始版本：** 26.0.0 |
| [OH_SwapfsKeyStatus](capi-oh-swapfs-h.md#oh_swapfskeystatus) status | key的当前状态。<br>**起始版本：** 26.0.0 |
| bool canSwapIn | key对应的数据是否可以换入。如果Key处于删除状态，则为False。<br>**起始版本：** 26.0.0 |


