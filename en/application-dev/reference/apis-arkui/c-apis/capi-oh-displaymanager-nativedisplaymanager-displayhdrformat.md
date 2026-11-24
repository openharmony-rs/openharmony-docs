# NativeDisplayManager_DisplayHdrFormat

```c
typedef struct NativeDisplayManager_DisplayHdrFormat {...} NativeDisplayManager_DisplayHdrFormat
```

## Overview

The struct describes all the HDR formats supported by a display.

<!--Device-typedef struct NativeDisplayManager_DisplayHdrFormat {...} NativeDisplayManager_DisplayHdrFormat--><!--Device-typedef struct NativeDisplayManager_DisplayHdrFormat {...} NativeDisplayManager_DisplayHdrFormat-End-->

**System capability**: SystemCapability.WindowManager.WindowManager.Core

**Since**: 14

**Related module**: [OH_DisplayManager](capi-arkui-oh-displaymanager.md)

**Header file**: [oh_display_info.h](capi-oh-display-info-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t hdrFormatLength | Number of HDR formats supported by the display.<br><!--Device-uint32_t hdrFormatLength--><!--Device-uint32_t hdrFormatLength-End--> |
| uint32_t *hdrFormats | Data of the HDR formats supported by the display.<br><!--Device-uint32_t *hdrFormats--><!--Device-uint32_t *hdrFormats-End--> |


