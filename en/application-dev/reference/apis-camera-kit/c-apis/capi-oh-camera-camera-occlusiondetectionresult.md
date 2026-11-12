# Camera_OcclusionDetectionResult

```c
typedef struct Camera_OcclusionDetectionResult {...} Camera_OcclusionDetectionResult
```

## Overview

Provides the check result for whether a camera lens is blocked or dirty.

<!--Device-struct Camera_OcclusionDetectionResult {...}--><!--Device-struct Camera_OcclusionDetectionResult {...}-End-->

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 23

**Related module**: [OH_Camera](capi-camera-kit-oh-camera.md)

**Header file**: [camera.h](capi-camera-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| bool isCameraOccluded | Checks whether the camera lens is blocked. The value **true** indicates that the camera lens is blocked, and **<br>false** indicates the opposite. |
| bool isCameraLensDirty | Checks whether the camera lens is dirty. The value **true** indicates that the camera lens is dirty, and **false*<br> indicates the opposite. |


