# WindowManager_MainWindowInfo

<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @fei_1007-->
<!--Designer: @gcw_sPCsris4-->
<!--Tester: @jingbotao-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=494f31a35d1b25179fe202754d9ee44d527d8ab6 translatedAt=2026-10-15T10:39:24.216Z pushedAt=2026-10-16T02:30:12.636Z -->

```c
typedef struct {...} WindowManager_MainWindowInfo
```

## Overview

Describes the main window information.

**Since**: 21

**Related module**: [WindowManager](capi-windowmanager.md)

**Header file**: [oh_window_comm.h](capi-oh-window-comm-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint64_t displayId | ID of the display to which the main window belongs.|
| int32_t windowId | ID of the main window.|
| bool showing | Foreground/Background status of the main window. **true** if the main window is in the foreground, **false** otherwise.|
| const char* label | Pointer to the task name of the main window.|