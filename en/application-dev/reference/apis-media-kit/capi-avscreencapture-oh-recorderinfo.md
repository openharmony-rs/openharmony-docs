# OH_RecorderInfo
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @chenkun613227-->
<!--Designer: @yxc2-->
<!--Tester: @xdlinc-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=4b1a2f751fcd33c52248528ed8c23a9b2935126b translatedAt=2026-06-23T01:06:36.526Z pushedAt=2026-06-23T06:12:23.714Z -->

```c
typedef struct OH_RecorderInfo {...} OH_RecorderInfo
```

## Overview

The struct describes the recording file information.

**Since**: 10

**Related module**: [AVScreenCapture](capi-avscreencapture.md)

**Header file**: [native_avscreen_capture_base.h](capi-native-avscreen-capture-base-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| char* url | Pointer to the URL of the recording file.|
| uint32_t urlLen | Length of the URL of the recording file.|
| [OH_ContainerFormatType](capi-native-avscreen-capture-base-h.md#oh_containerformattype) fileFormat | Format of the recording file.|