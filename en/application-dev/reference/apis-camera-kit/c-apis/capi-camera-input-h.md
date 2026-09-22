# camera_input.h

## Overview

The file declares the camera input concepts.

**Library**: libohcamera.so

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 11

**Related module**: [OH_Camera](capi-oh-camera.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [CameraInput_Callbacks](capi-oh-camera-camerainput-callbacks.md) | CameraInput_Callbacks | The struct describes the callbacks used to listen for camera input errors. |
| [Camera_Input](capi-oh-camera-camera-input.md) | Camera_Input | The struct describes the camera input object. |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef void (\*OH_CameraInput_OnError)(const Camera_Input* cameraInput, Camera_ErrorCode errorCode)](#oh_camerainput_onerror) | OH_CameraInput_OnError | Defines the callback defined in the [CameraInput_Callbacks](capi-oh-camera-camerainput-callbacks.md) struct and used to report camera input errors. |
| [Camera_ErrorCode OH_CameraInput_RegisterCallback(Camera_Input* cameraInput, CameraInput_Callbacks* callback)](#oh_camerainput_registercallback) | - | Registers a callback to listen for camera input events. |
| [Camera_ErrorCode OH_CameraInput_UnregisterCallback(Camera_Input* cameraInput, CameraInput_Callbacks* callback)](#oh_camerainput_unregistercallback) | - | Unregisters the callback used to listen for camera input events. |
| [Camera_ErrorCode OH_CameraInput_Open(Camera_Input* cameraInput)](#oh_camerainput_open) | - | Opens a camera. |
| [Camera_ErrorCode OH_CameraInput_OpenSecureCamera(Camera_Input* cameraInput, uint64_t* secureSeqId)](#oh_camerainput_opensecurecamera) | - | Opens a camera in secure mode. |
| [Camera_ErrorCode OH_CameraInput_Close(Camera_Input* cameraInput)](#oh_camerainput_close) | - | Closes a camera. |
| [Camera_ErrorCode OH_CameraInput_Release(Camera_Input* cameraInput)](#oh_camerainput_release) | - | Releases a Camera_Input instance. Either this function or [OH_CameraInput_Close](capi-camera-input-h.md#oh_camerainput_close) needs to be called. |
| [Camera_ErrorCode OH_CameraInput_IsPhysicalCameraOrientationVariable(Camera_Input* cameraInput, bool* isVariable)](#oh_camerainput_isphysicalcameraorientationvariable) | - | Checks whether the physical camera orientation is adjustable in different fold states of the device. |
| [Camera_ErrorCode OH_CameraInput_GetPhysicalCameraOrientation(Camera_Input* cameraInput, uint32_t* orientation)](#oh_camerainput_getphysicalcameraorientation) | - | Obtains the physical camera orientation in the current fold state of the device. |
| [Camera_ErrorCode OH_CameraInput_UsePhysicalCameraOrientation(Camera_Input* cameraInput, bool isUsed)](#oh_camerainput_usephysicalcameraorientation) | - | Enables or disables the use of the physical camera orientation. |
| [typedef void (\*OH_CameraInput_OnOcclusionDetectionCallback)(const Camera_Input* cameraInput, Camera_OcclusionDetectionResult occlusionDetectionResult)](#oh_camerainput_onocclusiondetectioncallback) | OH_CameraInput_OnOcclusionDetectionCallback | Defines a callback used to return the check result for whether a camera lens is blocked or dirty. |
| [Camera_ErrorCode OH_CameraInput_RegisterOcclusionDetectionCallback(Camera_Input* cameraInput, OH_CameraInput_OnOcclusionDetectionCallback occlusionDetectionCallback)](#oh_camerainput_registerocclusiondetectioncallback) | - | Registers a callback used to check whether a camera lens is blocked or dirty. |
| [Camera_ErrorCode OH_CameraInput_UnregisterOcclusionDetectionCallback(Camera_Input* cameraInput, OH_CameraInput_OnOcclusionDetectionCallback occlusionDetectionCallback)](#oh_camerainput_unregisterocclusiondetectioncallback) | - | Unregisters the callback used to check whether a camera lens is blocked or dirty. |
| [Camera_ErrorCode OH_CameraInput_OpenConcurrentCameras(Camera_Input* cameraInput, Camera_ConcurrentType type)](#oh_camerainput_openconcurrentcameras) | - | Opens the camera based on the specified concurrency type. |

### Variable

| Name | Description |
| -- | -- |
| void (*OH_CameraInput_OnError)(const Camera_Input* cameraInput, Camera_ErrorCode errorCode) | Defines the callback defined in the [CameraInput_Callbacks](capi-oh-camera-camerainput-callbacks.md) struct and used to report camera input errors.<br>**Since**: 11 |
| void (*OH_CameraInput_OnOcclusionDetectionCallback)(const Camera_Input* cameraInput, Camera_OcclusionDetectionResult occlusionDetectionResult) | Defines a callback used to return the check result for whether a camera lens is blocked or dirty.<br>**Since**: 23 |

## Function description

### OH_CameraInput_OnError()

```c
typedef void (*OH_CameraInput_OnError)(const Camera_Input* cameraInput, Camera_ErrorCode errorCode)
```

**Description**

Defines the callback defined in the [CameraInput_Callbacks](capi-oh-camera-camerainput-callbacks.md) struct and used to report camera input errors.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const Camera_Input](capi-oh-camera-camera-input.md)\* cameraInput | Pointer to the target Camera_Input instance. |
| Camera_ErrorCode errorCode | Error code reported during camera input and defined in the Camera_ErrorCode struct. |

**Reference**:

[CAMERA_CONFLICT_CAMERA](capi-camera-h.md#camera_errorcode)
[CAMERA_DEVICE_DISABLED](capi-camera-h.md#camera_errorcode)
[CAMERA_DEVICE_PREEMPTED](capi-camera-h.md#camera_errorcode)
[CAMERA_SERVICE_FATAL_ERROR](capi-camera-h.md#camera_errorcode)


### OH_CameraInput_RegisterCallback()

```c
Camera_ErrorCode OH_CameraInput_RegisterCallback(Camera_Input* cameraInput, CameraInput_Callbacks* callback)
```

**Description**

Registers a callback to listen for camera input events.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_Input](capi-oh-camera-camera-input.md)* cameraInput | Pointer to the target Camera_Input instance. |
| [CameraInput_Callbacks](capi-oh-camera-camerainput-callbacks.md)* callback | Pointer to the target callback. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_CameraInput_UnregisterCallback()

```c
Camera_ErrorCode OH_CameraInput_UnregisterCallback(Camera_Input* cameraInput, CameraInput_Callbacks* callback)
```

**Description**

Unregisters the callback used to listen for camera input events.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_Input](capi-oh-camera-camera-input.md)* cameraInput | Pointer to the target Camera_Input instance. |
| [CameraInput_Callbacks](capi-oh-camera-camerainput-callbacks.md)* callback | Pointer to the target callback. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_CameraInput_Open()

```c
Camera_ErrorCode OH_CameraInput_Open(Camera_Input* cameraInput)
```

**Description**

Opens a camera.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_Input](capi-oh-camera-camera-input.md)* cameraInput | Pointer to the target Camera_Input instance. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_CONFLICT_CAMERA: The camera cannot be used due to a conflict.      <br>CAMERA_DEVICE_DISABLED: The camera is disabled due to security reasons.      <br>CAMERA_SERVICE_FATAL_ERROR: The camera service is abnormal. |

### OH_CameraInput_OpenSecureCamera()

```c
Camera_ErrorCode OH_CameraInput_OpenSecureCamera(Camera_Input* cameraInput, uint64_t* secureSeqId)
```

**Description**

Opens a camera in secure mode.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_Input](capi-oh-camera-camera-input.md)* cameraInput | Pointer to the target Camera_Input instance. |
| uint64_t* secureSeqId | Pointer to the sequence ID of the camera. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_CONFLICT_CAMERA: The camera cannot be used due to a conflict.      <br>CAMERA_DEVICE_DISABLED: The camera is disabled due to security reasons.      <br>CAMERA_SERVICE_FATAL_ERROR: The camera service is abnormal. |

### OH_CameraInput_Close()

```c
Camera_ErrorCode OH_CameraInput_Close(Camera_Input* cameraInput)
```

**Description**

Closes a camera.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_Input](capi-oh-camera-camera-input.md)* cameraInput | Pointer to the target Camera_Input instance. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SERVICE_FATAL_ERROR: The camera service is abnormal. |

### OH_CameraInput_Release()

```c
Camera_ErrorCode OH_CameraInput_Release(Camera_Input* cameraInput)
```

**Description**

Releases a Camera_Input instance. Either this function or [OH_CameraInput_Close](capi-camera-input-h.md#oh_camerainput_close) needs to be called.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_Input](capi-oh-camera-camera-input.md)* cameraInput | Pointer to the target Camera_Input instance. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SERVICE_FATAL_ERROR: The camera service is abnormal. |

### OH_CameraInput_IsPhysicalCameraOrientationVariable()

```c
Camera_ErrorCode OH_CameraInput_IsPhysicalCameraOrientationVariable(Camera_Input* cameraInput, bool* isVariable)
```

**Description**

Checks whether the physical camera orientation is adjustable in different fold states of the device.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| {CameraInput} | cameraInput the [Camera_Input](capi-oh-camera-camera-input.md) instance. |
| {bool} | isVariable the result of whether physical camera orientation is variable. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_CameraInput_GetPhysicalCameraOrientation()

```c
Camera_ErrorCode OH_CameraInput_GetPhysicalCameraOrientation(Camera_Input* cameraInput, uint32_t* orientation)
```

**Description**

Obtains the physical camera orientation in the current fold state of the device.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_Input](capi-oh-camera-camera-input.md)* cameraInput | Pointer to the target Camera_Input instance. |
| uint32_t* orientation | Pointer to the physical camera orientation if the operation is successful. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_CameraInput_UsePhysicalCameraOrientation()

```c
Camera_ErrorCode OH_CameraInput_UsePhysicalCameraOrientation(Camera_Input* cameraInput, bool isUsed)
```

**Description**

Enables or disables the use of the physical camera orientation.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_Input](capi-oh-camera-camera-input.md)* cameraInput | Pointer to the target Camera_Input instance. |
| bool isUsed | Whether to enable the use of the physical camera orientation. **true** to enable, **false** otherwise. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_OPERATION_NOT_ALLOWED: The operation is not allowed.      <br>CAMERA_SERVICE_FATAL_ERROR: The camera service is abnormal. |

### OH_CameraInput_OnOcclusionDetectionCallback()

```c
typedef void (*OH_CameraInput_OnOcclusionDetectionCallback)(const Camera_Input* cameraInput, Camera_OcclusionDetectionResult occlusionDetectionResult)
```

**Description**

Defines a callback used to return the check result for whether a camera lens is blocked or dirty.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const Camera_Input](capi-oh-camera-camera-input.md)\* cameraInput | Pointer to the target Camera_Input instance. |
| Camera_OcclusionDetectionResult occlusionDetectionResult | Check result for whether a camera lens is blocked or dirty. |

### OH_CameraInput_RegisterOcclusionDetectionCallback()

```c
Camera_ErrorCode OH_CameraInput_RegisterOcclusionDetectionCallback(Camera_Input* cameraInput, OH_CameraInput_OnOcclusionDetectionCallback occlusionDetectionCallback)
```

**Description**

Registers a callback used to check whether a camera lens is blocked or dirty.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_Input](capi-oh-camera-camera-input.md)* cameraInput | Pointer to the target Camera_Input instance. |
| [OH_CameraInput_OnOcclusionDetectionCallback](capi-camera-input-h.md#oh_camerainput_onocclusiondetectioncallback) occlusionDetectionCallback | Callback used to check whether a camera lens is blocked or dirty. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_CameraInput_UnregisterOcclusionDetectionCallback()

```c
Camera_ErrorCode OH_CameraInput_UnregisterOcclusionDetectionCallback(Camera_Input* cameraInput, OH_CameraInput_OnOcclusionDetectionCallback occlusionDetectionCallback)
```

**Description**

Unregisters the callback used to check whether a camera lens is blocked or dirty.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_Input](capi-oh-camera-camera-input.md)* cameraInput | Pointer to the target Camera_Input instance. |
| [OH_CameraInput_OnOcclusionDetectionCallback](capi-camera-input-h.md#oh_camerainput_onocclusiondetectioncallback) occlusionDetectionCallback | Callback used to check whether a camera lens is blocked or dirty. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_CameraInput_OpenConcurrentCameras()

```c
Camera_ErrorCode OH_CameraInput_OpenConcurrentCameras(Camera_Input* cameraInput, Camera_ConcurrentType type)
```

**Description**

Opens the camera based on the specified concurrency type.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_Input](capi-oh-camera-camera-input.md)* cameraInput | Pointer to the target Camera_Input instance. |
| Camera_ConcurrentType type | Concurrency type. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_CONFLICT_CAMERA: The camera cannot be used due to a conflict.      <br>CAMERA_DEVICE_DISABLED: The camera is disabled due to security reasons.      <br>CAMERA_SERVICE_FATAL_ERROR: The camera service is abnormal. |


