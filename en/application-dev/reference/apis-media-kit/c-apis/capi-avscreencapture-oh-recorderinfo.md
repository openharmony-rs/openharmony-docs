# OH_RecorderInfo

```c
typedef struct OH_RecorderInfo {...} OH_RecorderInfo
```

## Overview

The struct describes the recording file information.

<!--Device-struct OH_RecorderInfo {...}--><!--Device-struct OH_RecorderInfo {...}-End-->

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 10

**Related module**: [AVScreenCapture](capi-media-kit-avscreencapture.md)

**Header file**: [native_avscreen_capture_base.h](capi-native-avscreen-capture-base-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| char *url | Recorder file url<br><!--Device-char *url--><!--Device-char *url-End--> |
| uint32_t urlLen | Recorder file url length<br><!--Device-uint32_t urlLen--><!--Device-uint32_t urlLen-End--> |
| [OH_ContainerFormatType](capi-native-avscreen-capture-base-h.md#oh_containerformattype) fileFormat | Recorder file format<br><!--Device-OH_ContainerFormatType fileFormat--><!--Device-OH_ContainerFormatType fileFormat-End--> |


