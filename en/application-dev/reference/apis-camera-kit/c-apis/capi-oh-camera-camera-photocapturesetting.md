# Camera_PhotoCaptureSetting

```c
typedef struct Camera_PhotoCaptureSetting {...} Camera_PhotoCaptureSetting
```

## Overview

The struct describes the parameters related to photo capture.

<!--Device-struct Camera_PhotoCaptureSetting {...}--><!--Device-struct Camera_PhotoCaptureSetting {...}-End-->

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 11

**Related module**: [OH_Camera](capi-camera-kit-oh-camera.md)

**Header file**: [camera.h](capi-camera-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [Camera_QualityLevel](capi-camera-h.md#camera_qualitylevel) quality | Quality of the photo.<br><!--Device-Camera_QualityLevel quality--><!--Device-Camera_QualityLevel quality-End--> |
| [Camera_ImageRotation](capi-camera-h.md#camera_imagerotation) rotation | Rotation angle.<br><!--Device-Camera_ImageRotation rotation--><!--Device-Camera_ImageRotation rotation-End--> |
| [Camera_Location*](capi-oh-camera-camera-location.md) location | Pointer to the location where the photo is taken.<br><!--Device-Camera_Location* location--><!--Device-Camera_Location* location-End--> |
| bool mirror | Whether mirroring is enabled.<br> **true** if enabled, **false** otherwise. The default value is **false**.<br><!--Device-bool mirror--><!--Device-bool mirror-End--> |


