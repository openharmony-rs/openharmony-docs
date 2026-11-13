# OH_UDMF_VirtualItem
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @jcwen-->
<!--Designer: @xuexuexuehc-->
<!--Tester: @lj_liujing; @yippo; @logic42-->
<!--Adviser: @ge-yafang-->

```c
typedef struct OH_UDMF_VirtualItem OH_UDMF_VirtualItem
```

## 概述

描述虚拟文件或虚拟目录节点。

单棵虚拟文件树最多4096个节点，包含根节点和全部目录、文件节点。根节点深度为0，子节点深度逐层加1，最大深度为64。

<!--Device-typedef struct OH_UDMF_VirtualItem OH_UDMF_VirtualItem--><!--Device-typedef struct OH_UDMF_VirtualItem OH_UDMF_VirtualItem-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

**起始版本：** 26.1.0

**相关模块：** [UDMF](capi-udmf.md)

**所在头文件：** [uds.h](capi-uds-h.md)

