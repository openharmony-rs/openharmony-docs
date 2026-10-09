# Camera_OcclusionDetectionResult
<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leo_ysl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=df2388ac9ece670e2be6918a776640e250f776ef translatedAt=2026-06-25T02:36:36.965Z pushedAt=2026-06-25T06:57:19.558Z -->

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
| bool isCameraLensDirty | Whether the camera lens is dirty. The value **true** indicates that the camera lens is dirty, and **false** indicates the opposite. |