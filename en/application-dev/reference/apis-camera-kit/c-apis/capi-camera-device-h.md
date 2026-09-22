# camera_device.h

## Overview

Defines the basic APIs of the camera device.

**Library**: libohcamera.so

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 11

**Related module**: [OH_Camera](capi-oh-camera.md)

## Summary

### Function

| Name | Description |
| -- | -- |
| [Camera_ErrorCode OH_CameraDevice_GetCameraOrientation(Camera_Device* camera, uint32_t* orientation)](#oh_cameradevice_getcameraorientation) | Obtains the sensor direction of a camera device. |
| [Camera_ErrorCode OH_CameraDevice_GetHostDeviceName(Camera_Device* camera, char** hostDeviceName)](#oh_cameradevice_gethostdevicename) | Obtains the name of a remote device. |
| [Camera_ErrorCode OH_CameraDevice_GetHostDeviceType(Camera_Device* camera, Camera_HostDeviceType* hostDeviceType)](#oh_cameradevice_gethostdevicetype) | Obtains the type of a remote device. |
| [Camera_ErrorCode OH_CameraDevice_GetLensEquivalentFocalLengths(const Camera_Device* camera, uint32_t** equivalentFocalLengths, uint32_t* size)](#oh_cameradevice_getlensequivalentfocallengths) | Gets the equivalent focal lengths of a camera device. |
| [Camera_ErrorCode OH_CameraDevice_IsLogicalCamera(const Camera_Device* camera, bool* isLogicalCamera)](#oh_cameradevice_islogicalcamera) | Checks if a camera device is a logical camera. |
| [Camera_ErrorCode OH_CameraDevice_GetLogicalCameraConstituentCameraDevices(const Camera_Device* logicalCamera, Camera_Device** constituentCameras, uint32_t* size)](#oh_cameradevice_getlogicalcameraconstituentcameradevices) | Gets the constituent camera devices of a logical camera. Release resources of the constituent cameras by calling [OH_CameraDevice_DeleteConstituentCameraDevices](capi-camera-device-h.md#oh_cameradevice_deleteconstituentcameradevices) . |
| [Camera_ErrorCode OH_CameraDevice_DeleteConstituentCameraDevices(const Camera_Device* logicalCamera, Camera_Device* constituentCameras, uint32_t size)](#oh_cameradevice_deleteconstituentcameradevices) | delete the constituent cameras of logicalCamera. |
| [Camera_ErrorCode OH_CameraDevice_GetLensFocalLength(const Camera_Device* camera, float* lensFocalLength)](#oh_cameradevice_getlensfocallength) | Gets the focal length of a camera lens. |
| [Camera_ErrorCode OH_CameraDevice_GetMinimumFocusDistance(const Camera_Device* camera, float* minimumFocusDistance)](#oh_cameradevice_getminimumfocusdistance) | Gets the minimum focus distance of a camera device. |
| [Camera_ErrorCode OH_CameraDevice_GetLensDistortion(const Camera_Device* camera, float** lens, uint32_t* size)](#oh_cameradevice_getlensdistortion) | Gets the lens distortion parameters of a camera device. |
| [Camera_ErrorCode OH_CameraDevice_GetIntrinsicCalibration(const Camera_Device* camera, float** intrinsicCalibration, uint32_t* size)](#oh_cameradevice_getintrinsiccalibration) | Gets the intrinsic calibration parameters of a camera device. |
| [Camera_ErrorCode OH_CameraDevice_GetSensorPhysicalSize(const Camera_Device* camera, float* width, float* height)](#oh_cameradevice_getsensorphysicalsize) | Gets the physical size of a camera sensor. |
| [Camera_ErrorCode OH_CameraDevice_GetSensorPixelArraySize(const Camera_Device* camera, uint32_t* width, uint32_t* height)](#oh_cameradevice_getsensorpixelarraysize) | Gets the pixel array size of a camera sensor. |
| [Camera_ErrorCode OH_CameraDevice_GetSensorColorFilterArrangement(const Camera_Device* camera, OH_Camera_SensorColorFilterArrangement* sensorCFA)](#oh_cameradevice_getsensorcolorfilterarrangement) | Gets the color filter arrangement of a camera sensor. |
| [Camera_ErrorCode OH_CameraDevice_GetAutomotiveCameraPosition(const Camera_Device* camera, OH_Camera_AutomotiveCameraPosition* automotiveCameraPosition)](#oh_cameradevice_getautomotivecameraposition) | Gets the automotive position of a camera sensor. |

## Function description

### OH_CameraDevice_GetCameraOrientation()

```c
Camera_ErrorCode OH_CameraDevice_GetCameraOrientation(Camera_Device* camera, uint32_t* orientation)
```

**Description**

Obtains the sensor direction of a camera device.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| Camera_Device* camera | Pointer to the camera device. |
| uint32_t* orientation | Pointer to the sensor direction obtained. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SERVICE_FATAL_ERROR: The camera service is abnormal. |

### OH_CameraDevice_GetHostDeviceName()

```c
Camera_ErrorCode OH_CameraDevice_GetHostDeviceName(Camera_Device* camera, char** hostDeviceName)
```

**Description**

Obtains the name of a remote device.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| Camera_Device* camera | Pointer to the camera device. |
| char** hostDeviceName | Double pointer to the name of the remote device. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful, and the remote device name is returned.      <br>CAMERA_CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SERVICE_FATAL_ERROR: The camera service is abnormal. |

### OH_CameraDevice_GetHostDeviceType()

```c
Camera_ErrorCode OH_CameraDevice_GetHostDeviceType(Camera_Device* camera, Camera_HostDeviceType* hostDeviceType)
```

**Description**

Obtains the type of a remote device.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| Camera_Device* camera | Pointer to the camera device. |
| Camera_HostDeviceType* hostDeviceType | Pointer to the type of the remote device. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful, and the remote device name is returned.      <br>CAMERA_CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SERVICE_FATAL_ERROR: The camera service is abnormal. |

### OH_CameraDevice_GetLensEquivalentFocalLengths()

```c
Camera_ErrorCode OH_CameraDevice_GetLensEquivalentFocalLengths(const Camera_Device* camera, uint32_t** equivalentFocalLengths, uint32_t* size)
```

**Description**

Gets the equivalent focal lengths of a camera device.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| const Camera_Device* camera | Pointer to the Camera_Device used to retrieve attributes. |
| uint32_t** equivalentFocalLengths | Output parameter, returns equivalent focal lengths array. |
| uint32_t* size | Output parameter, returns array size. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | [CAMERA_OK](capi-camera-h.md#camera_errorcode) if successful          [CAMERA_INVALID_ARGUMENT](capi-camera-h.md#camera_errorcode) if parameter missing or type incorrect          [CAMERA_SERVICE_FATAL_ERROR](capi-camera-h.md#camera_errorcode) if camera service fatal error |

### OH_CameraDevice_IsLogicalCamera()

```c
Camera_ErrorCode OH_CameraDevice_IsLogicalCamera(const Camera_Device* camera, bool* isLogicalCamera)
```

**Description**

Checks if a camera device is a logical camera.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| const Camera_Device* camera | Pointer to the Camera_Device used to retrieve attributes. |
| bool* isLogicalCamera | Output parameter, returns boolean indicating if it's a logical camera. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | [CAMERA_OK](capi-camera-h.md#camera_errorcode) if successful          [CAMERA_INVALID_ARGUMENT](capi-camera-h.md#camera_errorcode) if parameter missing or type incorrect          [CAMERA_SERVICE_FATAL_ERROR](capi-camera-h.md#camera_errorcode) if camera service fatal error |

### OH_CameraDevice_GetLogicalCameraConstituentCameraDevices()

```c
Camera_ErrorCode OH_CameraDevice_GetLogicalCameraConstituentCameraDevices(const Camera_Device* logicalCamera, Camera_Device** constituentCameras, uint32_t* size)
```

**Description**

Gets the constituent camera devices of a logical camera. Release resources of the constituent cameras by calling [OH_CameraDevice_DeleteConstituentCameraDevices](capi-camera-device-h.md#oh_cameradevice_deleteconstituentcameradevices) .

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| const Camera_Device* logicalCamera | Pointer to the logical Camera_Device. |
| Camera_Device** constituentCameras | returns array of constituent camera devices. |
| uint32_t* size | the size of constituentCameras. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | [CAMERA_OK](capi-camera-h.md#camera_errorcode) if successful          [CAMERA_INVALID_ARGUMENT](capi-camera-h.md#camera_errorcode) if parameter missing or type incorrect          [CAMERA_SERVICE_FATAL_ERROR](capi-camera-h.md#camera_errorcode) if camera service fatal error |

### OH_CameraDevice_DeleteConstituentCameraDevices()

```c
Camera_ErrorCode OH_CameraDevice_DeleteConstituentCameraDevices(const Camera_Device* logicalCamera, Camera_Device* constituentCameras, uint32_t size)
```

**Description**

delete the constituent cameras of logicalCamera.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| const Camera_Device* logicalCamera | Pointer to the logical Camera_Device. |
| Camera_Device* constituentCameras | the constituent cameras to be released. |
| uint32_t size | The size of the constituent cameras array. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | [CAMERA_OK](capi-camera-h.md#camera_errorcode) if the method call succeeds.          [CAMERA_INVALID_ARGUMENT](capi-camera-h.md#camera_errorcode) if parameter missing or parameter type incorrect. |

### OH_CameraDevice_GetLensFocalLength()

```c
Camera_ErrorCode OH_CameraDevice_GetLensFocalLength(const Camera_Device* camera, float* lensFocalLength)
```

**Description**

Gets the focal length of a camera lens.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| const Camera_Device* camera | Pointer to the Camera_Device used to retrieve attributes. |
| float* lensFocalLength | Output parameter, returns lens focal length value. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | [CAMERA_OK](capi-camera-h.md#camera_errorcode) if successful          [CAMERA_INVALID_ARGUMENT](capi-camera-h.md#camera_errorcode) if parameter missing or type incorrect          [CAMERA_SERVICE_FATAL_ERROR](capi-camera-h.md#camera_errorcode) if camera service fatal error |

### OH_CameraDevice_GetMinimumFocusDistance()

```c
Camera_ErrorCode OH_CameraDevice_GetMinimumFocusDistance(const Camera_Device* camera, float* minimumFocusDistance)
```

**Description**

Gets the minimum focus distance of a camera device.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| const Camera_Device* camera | Pointer to the Camera_Device used to retrieve attributes. |
| float* minimumFocusDistance | Output parameter, returns the minimum focus distance. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | [CAMERA_OK](capi-camera-h.md#camera_errorcode) if the operation succeeds          [CAMERA_INVALID_ARGUMENT](capi-camera-h.md#camera_errorcode) if parameter is missing or invalid          [CAMERA_SERVICE_FATAL_ERROR](capi-camera-h.md#camera_errorcode) if camera service fails |

### OH_CameraDevice_GetLensDistortion()

```c
Camera_ErrorCode OH_CameraDevice_GetLensDistortion(const Camera_Device* camera, float** lens, uint32_t* size)
```

**Description**

Gets the lens distortion parameters of a camera device.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| const Camera_Device* camera | Pointer to the Camera_Device used to retrieve attributes. |
| float** lens | Output parameter, returns the lens distortion parameters array. |
| uint32_t* size | Output parameter, returns the size of the array. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | [CAMERA_OK](capi-camera-h.md#camera_errorcode) if the operation succeeds          [CAMERA_INVALID_ARGUMENT](capi-camera-h.md#camera_errorcode) if parameter is missing or invalid          [CAMERA_SERVICE_FATAL_ERROR](capi-camera-h.md#camera_errorcode) if camera service fails |

### OH_CameraDevice_GetIntrinsicCalibration()

```c
Camera_ErrorCode OH_CameraDevice_GetIntrinsicCalibration(const Camera_Device* camera, float** intrinsicCalibration, uint32_t* size)
```

**Description**

Gets the intrinsic calibration parameters of a camera device.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| const Camera_Device* camera | Pointer to the Camera_Device used to retrieve attributes. |
| float** intrinsicCalibration | Output parameter, returns the intrinsic calibration parameters array. |
| uint32_t* size | Output parameter, returns the size of the array. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | [CAMERA_OK](capi-camera-h.md#camera_errorcode) if the operation succeeds          [CAMERA_INVALID_ARGUMENT](capi-camera-h.md#camera_errorcode) if parameter is missing or invalid          [CAMERA_SERVICE_FATAL_ERROR](capi-camera-h.md#camera_errorcode) if camera service fails |

### OH_CameraDevice_GetSensorPhysicalSize()

```c
Camera_ErrorCode OH_CameraDevice_GetSensorPhysicalSize(const Camera_Device* camera, float* width, float* height)
```

**Description**

Gets the physical size of a camera sensor.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| const Camera_Device* camera | Pointer to the Camera_Device used to retrieve attributes. |
| float* width | Output parameter, returns the sensor width in millimeters. |
| float* height | Output parameter, returns the sensor height in millimeters. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | [CAMERA_OK](capi-camera-h.md#camera_errorcode) if the operation succeeds          [CAMERA_INVALID_ARGUMENT](capi-camera-h.md#camera_errorcode) if parameter is missing or invalid          [CAMERA_SERVICE_FATAL_ERROR](capi-camera-h.md#camera_errorcode) if camera service fails |

### OH_CameraDevice_GetSensorPixelArraySize()

```c
Camera_ErrorCode OH_CameraDevice_GetSensorPixelArraySize(const Camera_Device* camera, uint32_t* width, uint32_t* height)
```

**Description**

Gets the pixel array size of a camera sensor.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| const Camera_Device* camera | Pointer to the Camera_Device used to retrieve attributes. |
| uint32_t* width | Output parameter, returns the pixel array width in pixels. |
| uint32_t* height | Output parameter, returns the pixel array height in pixels. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | [CAMERA_OK](capi-camera-h.md#camera_errorcode) if the operation succeeds          [CAMERA_INVALID_ARGUMENT](capi-camera-h.md#camera_errorcode) if parameter is missing or invalid          [CAMERA_SERVICE_FATAL_ERROR](capi-camera-h.md#camera_errorcode) if camera service fails |

### OH_CameraDevice_GetSensorColorFilterArrangement()

```c
Camera_ErrorCode OH_CameraDevice_GetSensorColorFilterArrangement(const Camera_Device* camera, OH_Camera_SensorColorFilterArrangement* sensorCFA)
```

**Description**

Gets the color filter arrangement of a camera sensor.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| const Camera_Device* camera | Pointer to the Camera_Device used to retrieve attributes. |
| OH_Camera_SensorColorFilterArrangement* sensorCFA | Output parameter, returns the sensor color filter arrangement enum value. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | [CAMERA_OK](capi-camera-h.md#camera_errorcode) if the operation succeeds          [CAMERA_INVALID_ARGUMENT](capi-camera-h.md#camera_errorcode) if parameter is missing or invalid          [CAMERA_SERVICE_FATAL_ERROR](capi-camera-h.md#camera_errorcode) if camera service fails |

### OH_CameraDevice_GetAutomotiveCameraPosition()

```c
Camera_ErrorCode OH_CameraDevice_GetAutomotiveCameraPosition(const Camera_Device* camera, OH_Camera_AutomotiveCameraPosition* automotiveCameraPosition)
```

**Description**

Gets the automotive position of a camera sensor.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| const Camera_Device* camera | Pointer to the Camera_Device used to retrieve attributes. |
| OH_Camera_AutomotiveCameraPosition* automotiveCameraPosition | Output parameter, returns the automotive camera position enum value. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | [CAMERA_OK](capi-camera-h.md#camera_errorcode) if the operation succeeds          [CAMERA_INVALID_ARGUMENT](capi-camera-h.md#camera_errorcode) if parameter is missing or invalid          [CAMERA_SERVICE_FATAL_ERROR](capi-camera-h.md#camera_errorcode) if camera service fails |


