# OH_SwapfsConfig (系统接口)
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @wangke25; @gsl_1234; @wuchengjun5-->
<!--Designer: @gsl_1234; @wangke25-->
<!--Tester: @zsyztt; @yue-ye2; @juxiaopang-->
<!--Adviser: @jinqiuheng-->

```c
typedef struct OH_SwapfsConfig {...} OH_SwapfsConfig
```

## 概述

用于配置swapfs管理器的初始化参数，包括数据存储路径、空间限制和IO方式等。

**起始版本：** 26.0.0

**相关模块：** [Swapfs](capi-swapfs-sys.md)

**所在头文件：** [oh_swapfs.h (系统接口)](capi-oh-swapfs-h-sys.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| const char *swapRootPath | 存储换出数据的根路径。设置不同的根路径会影响swapfs数据的存储位置和访问性能，确保路径具有足够的存储空间和读写权限。<br> swapfs使用固定的 “swapfs” 子目录。当为空指针或空字符串时，使用应用沙箱下的默认临时根路径 “/data/storage/el2/base/temp/swapfs”。<br>**起始版本：** 26.0.0 |
| uint64_t spaceLimitBytes | 最大换出空间，单位：Byte。当spaceLimitBytes为0时，默认限制为1,073,741,824 Bytes（即1GB）。<br>**起始版本：** 26.0.0 |
| bool useDirectIo | 是否对换出操作强制使用Direct I/O。为false时使用缓冲IO；为true时使用Direct I/O，将对缓冲区进行强制对齐，未对齐的缓冲区将导致错误。<br>**起始版本：** 26.0.0 |


