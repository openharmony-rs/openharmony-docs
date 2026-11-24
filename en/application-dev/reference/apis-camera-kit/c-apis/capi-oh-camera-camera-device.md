# Camera_Device

```c
typedef struct Camera_Device {...} Camera_Device
```

## Overview

The struct describes the camera device.

<!--Device-struct Camera_Device {...}--><!--Device-struct Camera_Device {...}-End-->

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 11

**Related module**: [OH_Camera](capi-camera-kit-oh-camera.md)

**Header file**: [camera.h](capi-camera-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| char* cameraId | Pointer to the camera ID.<br><!--Device-char* cameraId--><!--Device-char* cameraId-End--> |
| [Camera_Position](capi-camera-h.md#camera_position) cameraPosition | Camera position.<br><!--Device-Camera_Position cameraPosition--><!--Device-Camera_Position cameraPosition-End--> |
| [Camera_Type](capi-camera-h.md#camera_type) cameraType | Camera type.<br><!--Device-Camera_Type cameraType--><!--Device-Camera_Type cameraType-End--> |
| [Camera_Connection](capi-camera-h.md#camera_connection) connectionType | Camera connection type.<br><!--Device-Camera_Connection connectionType--><!--Device-Camera_Connection connectionType-End--> |


