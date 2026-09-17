# Camera_FoldStatusInfo

```c
typedef struct Camera_FoldStatusInfo {...} Camera_FoldStatusInfo
```

## Overview

The struct describes the fold status information of the camera.

**Since**: 13

**Related module**: [OH_Camera](capi-oh-camera.md)

**Header file**: [camera.h](capi-camera-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [Camera_Device**](capi-oh-camera-camera-device.md) supportedCameras | Double pointer to the camera list. |
| uint32_t cameraSize | Number of cameras in the list. |
| [Camera_FoldStatus](capi-camera-h.md#camera_foldstatus) foldStatus | Current fold status. |


