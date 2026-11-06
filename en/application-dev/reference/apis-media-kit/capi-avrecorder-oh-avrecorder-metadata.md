# OH_AVRecorder_Metadata
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @gcw_dyOv3Sds-->
<!--Designer: @chris2981-->
<!--Tester: @xdlinc-->
<!--Adviser: @zzs911-->
<!-- md-trans-meta sourceCommit=f7deae3962affdf9350cd46c72e652967c8034c7 translatedAt=2026-09-15T16:32:22.495Z pushedAt=2026-09-18T09:07:30.191Z -->

```c
typedef struct OH_AVRecorder_Metadata {...} OH_AVRecorder_Metadata
```

## Overview

Defines the metadata structure for recording, which is used to describe the genre, video rotation angle, geographical location, and custom parameters of media resources. This struct is applicable to scenarios where media metadata needs to be carried or read during recording.

**Since**: 18

**Related module**: [AVRecorder](capi-avrecorder.md)

**Header file**: [avrecorder_base.h](capi-avrecorder-base-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| char *genre | Genre of a media resource. If this parameter is not set, the genre information is not carried. |
| char *videoOrientation | Video orientation, in degrees (°). Only the following angle values are supported: **0°**: no rotation, the video remains in the original orientation; **90°**: rotates 90° clockwise; **180°**: rotates 180°; **270°**: rotates 270° clockwise. If this parameter is not specified, the default value **0°** is used. If an unsupported angle is passed, the setting fails. |
| [OH_AVRecorder_Location](capi-avrecorder-oh-avrecorder-location.md) location | Geographical location information of a media asset, including the latitude and longitude. The value range of latitude is [–90, 90], and that of longitude is [–180, 180]. The unit is degree (°). If the input value is out of the value range, the setting fails. If this parameter is not specified, geographical location information is not carried. |
| [OH_AVRecorder_MetadataTemplate](capi-avrecorder-oh-avrecorder-metadatatemplate.md) customInfo | Custom parameter key-value mapping written to **moov.meta.list**. Both the key and value are of the string type. This parameter is used to carry the metadata tag customized by the app during recording, for example, adding a service ID or extended attribute. If this parameter is not specified, custom metadata information is not carried. |


