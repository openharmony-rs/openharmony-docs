# Camera_OcclusionDetectionResult
<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leo_ysl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct {...} Camera_OcclusionDetectionResult
```

## Overview

Provides the check result for whether a camera lens is blocked or dirty.

**Since**: 23

**Related module**: [OH_Camera](capi-oh-camera.md)

**Header file**: [camera.h](capi-camera-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| bool isCameraOccluded | Checks whether the camera lens is blocked. The value **true** indicates that the camera lens is blocked, and **false** indicates the opposite.|
| bool isCameraLensDirty | Checks whether the camera lens is dirty. The value **true** indicates that the camera lens is dirty, and **false** indicates the opposite.|
