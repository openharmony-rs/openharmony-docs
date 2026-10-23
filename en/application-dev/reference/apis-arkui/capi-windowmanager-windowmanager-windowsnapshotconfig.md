# WindowManager_WindowSnapshotConfig

<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @fei_1007-->
<!--Designer: @gcw_sPCsris4-->
<!--Tester: @jingbotao-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=494f31a35d1b25179fe202754d9ee44d527d8ab6 translatedAt=2026-10-15T10:39:33.079Z pushedAt=2026-10-16T02:30:28.156Z -->

```c
typedef struct {...} WindowManager_WindowSnapshotConfig
```

## Overview

Describes the configuration of the main window screenshot.

**Since**: 21

**Related module**: [WindowManager](capi-windowmanager.md)

**Header file**: [oh_window_comm.h](capi-oh-window-comm-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| bool useCache | Whether the existing screenshot of the main window should be used. The default value is **true**. When it is set to **true**, the system uses the existing screenshot of the main window, or captures the latest screenshot if no existing screenshot is saved. When it is set to **false**, the system captures the latest screenshot of the main window.|