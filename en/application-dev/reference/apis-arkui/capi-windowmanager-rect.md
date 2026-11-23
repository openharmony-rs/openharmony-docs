# WindowManager_Rect
<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @fei_1007-->
<!--Designer: @gcw_sPCsris4-->
<!--Tester: @jingbotao-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=b5bac46b123c8ef772e6a1f04f3d13c5b3c45368 translatedAt=2026-11-18T09:25:49.200Z pushedAt=2026-11-20T06:05:20.366Z nl=1 -->

```c
typedef struct {...} WindowManager_Rect
```

## Overview

Describes the window rectangle, including the window position, width, and height.

**Since**: 15

**Related module**: [WindowManager](capi-windowmanager.md)

**Header file**: [oh_window_comm.h](capi-oh-window-comm-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| int32_t posX | X-coordinate of the window, in px. The value is an integer. |
| int32_t posY | Y-coordinate of the window, in px. The value is an integer. |
| uint32_t width | Window width, in px. The value is an integer.|
| uint32_t height | Window height, in px. The value is an integer.|


