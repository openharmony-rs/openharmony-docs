# WindowManager_Rect
<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @fei_1007-->
<!--Designer: @gcw_sPCsris4-->
<!--Tester: @qinliwen0417-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=cbeab3efe78496eefe7f99a9dc945e61d5d3c1bd translatedAt=2026-08-29T09:15:58.253Z pushedAt=2026-08-31T01:40:45.599Z -->

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


