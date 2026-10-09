# OH_SwapfsManager (系统接口)
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @wangke25; @gsl_1234; @wuchengjun5-->
<!--Designer: @gsl_1234; @wangke25-->
<!--Tester: @zsyztt; @yue-ye2; @juxiaopang-->
<!--Adviser: @jinqiuheng-->

```c
typedef struct OH_SwapfsManager OH_SwapfsManager
```

## 概述

该结构体用于执行与swapfs管理器交互相关的操作。使用前需通过[OH_Swapfs_CreateManager](capi-oh-swapfs-h-sys.md#oh_swapfs_createmanager)函数创建有效的管理器实例。<br> 该结构体用于管理swapfs的生命周期和配置，提供交换分区的创建、销毁、扩展等管理能力。

**起始版本：** 26.0.0

**相关模块：** [Swapfs](capi-swapfs-sys.md)

**所在头文件：** [oh_swapfs.h (系统接口)](capi-oh-swapfs-h-sys.md)

