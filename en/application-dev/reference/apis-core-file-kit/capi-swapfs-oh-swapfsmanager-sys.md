# OH_SwapfsManager (System API)
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @wangke25; @gsl_1234; @wuchengjun5-->
<!--Designer: @gsl_1234; @wangke25-->
<!--Tester: @zsyztt; @yue-ye2; @juxiaopang-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=c3dac3338f135feeca4a02be08f92e9afb1fc0fc translatedAt=2026-11-03T03:58:09.561Z pushedAt=2026-11-04T03:11:33.484Z nl=1 -->

```c
typedef struct OH_SwapfsManager OH_SwapfsManager
```

## Overview

This structure is used to perform operations related to interacting with the swapfs manager. Before use, you need to create a valid manager instance through the [OH_Swapfs_CreateManager](capi-oh-swapfs-h-sys.md#oh_swapfs_createmanager) function.<br> This structure is used to manage the lifecycle and configuration of swapfs, providing management capabilities such as creating, destroying, and expanding swap partitions.

**Since**: 26.0.0

**Related Modules:** [Swapfs](capi-swapfs-sys.md)

**Header File:** [oh_swapfs.h (System API)](capi-oh-swapfs-h-sys.md)

