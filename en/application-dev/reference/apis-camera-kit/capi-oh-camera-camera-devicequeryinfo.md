# Camera_DeviceQueryInfo
<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leo_ysl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=132342cdd19e09e8d1c7a964e48a57b6cf30fc8d translatedAt=2026-10-12T12:01:01.405Z pushedAt=2026-10-13T04:58:00.897Z -->

```c
typedef struct Camera_DeviceQueryInfo {...} Camera_DeviceQueryInfo
```

## Overview

Camera device query information.

**Since**: 23

**Related module**: [OH_Camera](capi-oh-camera.md)

**Header file**: [camera.h](capi-camera-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| Camera_Type* cameraType | List of camera types.|
| uint32_t cameraTypeSize | Size of the camera type list.|
| [Camera_Position](capi-camera-h.md#camera_position) cameraPosition | Camera position.|
| [Camera_Connection](capi-camera-h.md#camera_connection) connectionType | Camera connection type.|