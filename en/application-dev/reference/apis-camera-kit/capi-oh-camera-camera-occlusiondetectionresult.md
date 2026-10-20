# Camera_OcclusionDetectionResult
<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leo_ysl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=132342cdd19e09e8d1c7a964e48a57b6cf30fc8d translatedAt=2026-10-12T12:01:21.326Z pushedAt=2026-10-13T04:58:00.902Z -->

```c
typedef struct Camera_OcclusionDetectionResult {...} Camera_OcclusionDetectionResult
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
