# OH_SwapfsConfig

```c
typedef struct OH_SwapfsConfig {...} OH_SwapfsConfig
```

## 概述

创建swapfs管理器的配置。

**起始版本：** 26.0.0

**相关模块：** [Swapfs](capi-swapfs.md)

**所在头文件：** [oh_swapfs.h](capi-oh-swapfs-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| const char *swapRootPath | 交换数据存储的根路径。当为NULL或为空时，使用应用沙箱下默认的临时目录。<br>**起始版本：** 26.0.0 |
| uint64_t spaceLimitBytes | 最大交换空间（以字节为单位）。为0时，默认限制为1GB (1073741824)。<br>**起始版本：** 26.0.0 |
| bool useDirectIo | 是否为换出操作强制实施直接IO。如果为false，则使用缓冲IO；如果为true，使用直接IO，未对齐的缓冲区将导致错误。<br>**起始版本：** 26.0.0 |


