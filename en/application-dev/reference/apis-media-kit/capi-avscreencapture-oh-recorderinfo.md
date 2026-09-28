# OH_RecorderInfo
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @chenkun613227-->
<!--Designer: @yxc2-->
<!--Tester: @xdlinc-->
<!--Adviser: @zzs911-->
<!-- md-trans-meta sourceCommit=35a92c7d966df03837a52762f256f37e3433296b translatedAt=2026-09-15T16:56:10.486Z pushedAt=2026-09-20T07:18:07.796Z -->

```c
typedef struct OH_RecorderInfo {...} OH_RecorderInfo
```

## Overview

Describes the recording file information.

This struct is used to store the output information of screen capture files, including the URL, URL length, and format of the recorded file. It is applicable to scenarios where the screen capture output destination and format need to be configured, helping you flexibly specify the storage path and encapsulation format of the recorded file.

**Since**: 10

**Related module**: [AVScreenCapture](capi-avscreencapture.md)

**Header file**: [native_avscreen_capture_base.h](capi-native-avscreen-capture-base-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| char *url | URL of the recorded file, which specifies the output directory of the screen capture file. Only the URL format for local files is supported. This parameter must be used together with **urlLen**. |
| uint32_t urlLen | Length of the URL of the recorded file, in bytes, indicating the length of the character string specified by the **url** parameter (excluding the terminating null character). This parameter must be used together with the **url** parameter. If they do not match, recording exceptions may occur. |
| [OH_ContainerFormatType](capi-native-avscreen-capture-base-h.md#oh_containerformattype) fileFormat | Container encapsulation format of the recorded file, which specifies the encapsulation format of the screen capture output file. The options are **CFT_MPEG_4A** (M4A, applicable to audio only recording) and **CFT_MPEG_4** (MP4, applicable to audio and video recording). For details, see [OH_ContainerFormatType](capi-native-avscreen-capture-base-h.md#oh_containerformattype).|


