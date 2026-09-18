# NativeDisplayManager_DisplaysInfo

```c
typedef struct NativeDisplayManager_DisplaysInfo {...} NativeDisplayManager_DisplaysInfo
```

## Overview

The struct describes the information about displays of a device with multiple screens.

**Since**: 14

**Related module**: [OH_DisplayManager](capi-oh-displaymanager.md)

**Header file**: [oh_display_info.h](capi-oh-display-info-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t displaysLength | Number of displays of a device with multiple screens. |
| [NativeDisplayManager_DisplayInfo](capi-oh-displaymanager-nativedisplaymanager-displayinfo.md) *displaysInfo | An array of NativeDisplayManager_DisplayInfo structs, each containing information about a display. |


