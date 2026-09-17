# Camera_DeviceQueryInfo

```c
typedef struct Camera_DeviceQueryInfo {...} Camera_DeviceQueryInfo
```

## Overview

Camera device query information.

**Since**: 23

**Related module**: [OH_Camera](capi-oh-camera.md)

**Header file**: [camera.h](capi-camera-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| Camera_Type* cameraType | List of camera types. |
| uint32_t cameraTypeSize | Size of the camera type list. |
| [Camera_Position](capi-camera-h.md#camera_position) cameraPosition | Camera position. |
| [Camera_Connection](capi-camera-h.md#camera_connection) connectionType | Camera connection type. |


