# WindowManager_MainWindowInfo

<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @waterwin-->
<!--Designer: @nyankomiya-->
<!--Tester: @qinliwen0417-->
<!--Adviser: @ge-yafang-->

## Overview

The struct describes the main window information.

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
