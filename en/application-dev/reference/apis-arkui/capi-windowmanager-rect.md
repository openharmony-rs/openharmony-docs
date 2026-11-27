# WindowManager_Rect
<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @fei_1007-->
<!--Designer: @gcw_sPCsris4-->
<!--Tester: @jingbotao-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=494f31a35d1b25179fe202754d9ee44d527d8ab6 translatedAt=2026-11-25T10:53:07.383Z pushedAt=2026-11-26T07:47:13.636Z nl=1 -->

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


