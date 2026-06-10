# Camera_OcclusionDetectionResult

<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leo_ysl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=d0c7a5fb2bc1f1b1c7630c4a5886ec88f6136925 translatedAt=2026-06-09T10:28:15.775Z pushedAt=2026-06-10T01:59:42.652Z -->

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
| bool isCameraOccluded | Whether the camera lens is blocked. The value **true** indicates that the camera lens is blocked, and **false** indicates the opposite.|
| bool isCameraLensDirty | Whether the camera lens is dirty. The value **true** indicates that the camera lens is dirty, and **false** indicates the opposite. |