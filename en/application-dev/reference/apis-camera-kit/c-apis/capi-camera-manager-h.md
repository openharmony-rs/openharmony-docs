# camera_manager.h

## Overview

The file declares the camera manager concepts.

**Library**: libohcamera.so

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 11

**Related module**: [OH_Camera](capi-oh-camera.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [CameraManager_Callbacks](capi-oh-camera-cameramanager-callbacks.md) | CameraManager_Callbacks | The struct describes the callbacks used to listen for camera status changes. |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef void (\*OH_CameraManager_StatusCallback)(Camera_Manager* cameraManager, Camera_StatusInfo* status)](#oh_cameramanager_statuscallback) | OH_CameraManager_StatusCallback | Defines the callback defined in the [CameraManager_Callbacks](capi-oh-camera-cameramanager-callbacks.md) struct and used to report the camera manager status. |
| [typedef void (\*OH_CameraManager_TorchStatusCallback)(Camera_Manager* cameraManager, Camera_TorchStatusInfo* status)](#oh_cameramanager_torchstatuscallback) | OH_CameraManager_TorchStatusCallback | Defines the callback to listen for flashlight status changes. |
| [typedef void (\*OH_CameraManager_OnFoldStatusInfoChange)(Camera_Manager* cameraManager, Camera_FoldStatusInfo* foldStatusInfo)](#oh_cameramanager_onfoldstatusinfochange) | OH_CameraManager_OnFoldStatusInfoChange | Defines the callback to listen for fold status changes of the camera manager. |
| [Camera_ErrorCode OH_CameraManager_RegisterCallback(Camera_Manager* cameraManager, CameraManager_Callbacks* callback)](#oh_cameramanager_registercallback) | - | Registers a callback to listen for camera status changes. |
| [Camera_ErrorCode OH_CameraManager_UnregisterCallback(Camera_Manager* cameraManager, CameraManager_Callbacks* callback)](#oh_cameramanager_unregistercallback) | - | Unregisters the callback used to listen for camera status changes. |
| [Camera_ErrorCode OH_CameraManager_RegisterTorchStatusCallback(Camera_Manager* cameraManager, OH_CameraManager_TorchStatusCallback torchStatusCallback)](#oh_cameramanager_registertorchstatuscallback) | - | Registers a callback to listen for flashlight status changes. |
| [Camera_ErrorCode OH_CameraManager_UnregisterTorchStatusCallback(Camera_Manager* cameraManager, OH_CameraManager_TorchStatusCallback torchStatusCallback)](#oh_cameramanager_unregistertorchstatuscallback) | - | Unregisters the callback used to listen for flashlight status changes. |
| [Camera_ErrorCode OH_CameraManager_RegisterFoldStatusInfoCallback(Camera_Manager* cameraManager, OH_CameraManager_OnFoldStatusInfoChange foldStatusInfoCallback)](#oh_cameramanager_registerfoldstatusinfocallback) | - | Registers a callback to listen for fold status changes. |
| [Camera_ErrorCode OH_CameraManager_UnregisterFoldStatusInfoCallback(Camera_Manager* cameraManager, OH_CameraManager_OnFoldStatusInfoChange foldStatusInfoCallback)](#oh_cameramanager_unregisterfoldstatusinfocallback) | - | Unregisters the callback used to listen for fold status changes. |
| [Camera_ErrorCode OH_CameraManager_GetSupportedCameras(Camera_Manager* cameraManager, Camera_Device** cameras, uint32_t* size)](#oh_cameramanager_getsupportedcameras) | - | Obtains the supported cameras. |
| [Camera_ErrorCode OH_CameraManager_DeleteSupportedCameras(Camera_Manager* cameraManager, Camera_Device* cameras, uint32_t size)](#oh_cameramanager_deletesupportedcameras) | - | Deletes supported cameras. |
| [Camera_ErrorCode OH_CameraManager_GetSupportedCameraOutputCapability(Camera_Manager* cameraManager, const Camera_Device* camera, Camera_OutputCapability** cameraOutputCapability)](#oh_cameramanager_getsupportedcameraoutputcapability) | - | Obtains the output capability supported by a camera. |
| [Camera_ErrorCode OH_CameraManager_GetSupportedCameraOutputCapabilityWithSceneMode(Camera_Manager* cameraManager, const Camera_Device* camera, Camera_SceneMode sceneMode, Camera_OutputCapability** cameraOutputCapability)](#oh_cameramanager_getsupportedcameraoutputcapabilitywithscenemode) | - | Obtains the output capability supported by a camera in the specified mode. |
| [Camera_ErrorCode OH_CameraManager_GetSupportedFullCameraOutputCapabilityWithSceneMode(Camera_Manager* cameraManager, const Camera_Device* camera, Camera_SceneMode sceneMode, Camera_OutputCapability** cameraOutputCapability)](#oh_cameramanager_getsupportedfullcameraoutputcapabilitywithscenemode) | - | Obtains the complete output capabilities supported by a specified camera in a specified mode, including YUV, HEIF, and HDR. Before using YUV, HEIF, or HDR, you need to explicitly call this method to ensure that the complete output capabilities are obtained. |
| [Camera_ErrorCode OH_CameraManager_DeleteSupportedCameraOutputCapability(Camera_Manager* cameraManager, Camera_OutputCapability* cameraOutputCapability)](#oh_cameramanager_deletesupportedcameraoutputcapability) | - | Deletes the output capability supported by a camera. |
| [Camera_ErrorCode OH_CameraManager_IsCameraMuted(Camera_Manager* cameraManager, bool* isCameraMuted)](#oh_cameramanager_iscameramuted) | - | Checks whether a camera is muted. |
| [Camera_ErrorCode OH_CameraManager_CreateCaptureSession(Camera_Manager* cameraManager, Camera_CaptureSession** captureSession)](#oh_cameramanager_createcapturesession) | - | Creates a **CaptureSession** instance. |
| [Camera_ErrorCode OH_CameraManager_CreateCameraInput(Camera_Manager* cameraManager, const Camera_Device* camera, Camera_Input** cameraInput)](#oh_cameramanager_createcamerainput) | - | Creates a **Camera_Input** instance. |
| [Camera_ErrorCode OH_CameraManager_CreateCameraInput_WithPositionAndType(Camera_Manager* cameraManager, Camera_Position position, Camera_Type type, Camera_Input** cameraInput)](#oh_cameramanager_createcamerainput_withpositionandtype) | - | Creates a **Camera_Input** instance with the specified camera position and type. |
| [Camera_ErrorCode OH_CameraManager_CreatePreviewOutput(Camera_Manager* cameraManager, const Camera_Profile* profile, const char* surfaceId, Camera_PreviewOutput** previewOutput)](#oh_cameramanager_createpreviewoutput) | - | Creates a **PreviewOutput** instance. |
| [Camera_ErrorCode OH_CameraManager_CreatePreviewOutputUsedInPreconfig(Camera_Manager* cameraManager, const char* surfaceId, Camera_PreviewOutput** previewOutput)](#oh_cameramanager_createpreviewoutputusedinpreconfig) | - | Creates a **PreviewOutput** instance to be used in a preconfiguration stream. |
| [Camera_ErrorCode OH_CameraManager_CreateDeferredPreviewOutput(const Camera_Manager* cameraManager, const Camera_Profile* profile, Camera_PreviewOutput** previewOutput)](#oh_cameramanager_createdeferredpreviewoutput) | - | Create a defer preview output instance.The caller must call [OH_PreviewOutput_Release](capi-preview-output-h.md#oh_previewoutput_release) to free the memory of the output. |
| [Camera_ErrorCode OH_CameraManager_CreatePhotoOutput(Camera_Manager* cameraManager, const Camera_Profile* profile, const char* surfaceId, Camera_PhotoOutput** photoOutput)](#oh_cameramanager_createphotooutput) | - | Creates a **PhotoOutput** instance. This API can only be used to create a **PhotoOutput** object in JPEG format. |
| [Camera_ErrorCode OH_CameraManager_CreatePhotoOutputUsedInPreconfig(Camera_Manager* cameraManager, const char* surfaceId, Camera_PhotoOutput** photoOutput)](#oh_cameramanager_createphotooutputusedinpreconfig) | - | Creates a **PhotoOutput** instance to be used in a preconfiguration stream. |
| [Camera_ErrorCode OH_CameraManager_CreatePhotoOutputWithoutSurface(Camera_Manager *cameraManager, const Camera_Profile *profile, Camera_PhotoOutput **photoOutput)](#oh_cameramanager_createphotooutputwithoutsurface) | - | Creates a **PhotoOutput** instance. **surfaceId** is not required in this function. |
| [Camera_ErrorCode OH_CameraManager_CreateVideoOutput(Camera_Manager* cameraManager, const Camera_VideoProfile* profile, const char* surfaceId, Camera_VideoOutput** videoOutput)](#oh_cameramanager_createvideooutput) | - | Creates a **VideoOutput** instance. |
| [Camera_ErrorCode OH_CameraManager_CreateVideoOutputUsedInPreconfig(Camera_Manager* cameraManager, const char* surfaceId, Camera_VideoOutput** videoOutput)](#oh_cameramanager_createvideooutputusedinpreconfig) | - | Creates a **VideoOutput** instance to be used in a preconfiguration stream. |
| [Camera_ErrorCode OH_CameraManager_CreateMetadataOutput(Camera_Manager* cameraManager, const Camera_MetadataObjectType* profile, Camera_MetadataOutput** metadataOutput)](#oh_cameramanager_createmetadataoutput) | - | Creates a **MetadataOutput** instance. |
| [Camera_ErrorCode OH_CameraManager_CreateMetadataOutputWithObjectTypes(Camera_Manager* cameraManager, const Camera_MetadataObjectType* metadataObjectTypes, uint32_t size, Camera_MetadataOutput** metadataOutput)](#oh_cameramanager_createmetadataoutputwithobjecttypes) | - | Creates a **metadataOutput** instance using an array of metadata object types. |
| [Camera_ErrorCode OH_CameraManager_GetSupportedSceneModes(Camera_Device* camera, Camera_SceneMode** sceneModes, uint32_t* size)](#oh_cameramanager_getsupportedscenemodes) | - | Obtains the scene modes supported by a camera. |
| [Camera_ErrorCode OH_CameraManager_DeleteSceneModes(Camera_Manager* cameraManager, Camera_SceneMode* sceneModes)](#oh_cameramanager_deletescenemodes) | - | Deletes scene modes. |
| [Camera_ErrorCode OH_CameraManager_IsTorchSupported(Camera_Manager* cameraManager, bool* isTorchSupported)](#oh_cameramanager_istorchsupported) | - | Checks whether the device supports the flashlight. |
| [Camera_ErrorCode OH_CameraManager_IsTorchSupportedByTorchMode(Camera_Manager* cameraManager, Camera_TorchMode torchMode, bool* isTorchSupported)](#oh_cameramanager_istorchsupportedbytorchmode) | - | Checks whether the device supports the specified flashlight mode. |
| [Camera_ErrorCode OH_CameraManager_SetTorchMode(Camera_Manager* cameraManager, Camera_TorchMode torchMode)](#oh_cameramanager_settorchmode) | - | Sets a flashlight mode. |
| [Camera_ErrorCode OH_CameraManager_IsTorchLevelControlSupported(const Camera_Manager* cameraManager, bool* isTorchLevelControlSupported)](#oh_cameramanager_istorchlevelcontrolsupported) | - | Checks whether the device supports flashlight brightness control. |
| [Camera_ErrorCode OH_CameraManager_SetTorchModeOnWithLevel(Camera_Manager* cameraManager, double torchLevel)](#oh_cameramanager_settorchmodeonwithlevel) | - | Turns on the flashlight and sets the brightness level. |
| [Camera_ErrorCode OH_CameraManager_GetCameraDevice(Camera_Manager* cameraManager, Camera_Position position, Camera_Type type, Camera_Device* camera)](#oh_cameramanager_getcameradevice) | - | Queries a specified device based on position and type. |
| [Camera_ErrorCode OH_CameraManager_GetCameraDevices(Camera_Manager* cameraManager, Camera_DeviceQueryInfo* deviceQueryInfo, uint32_t* cameraSize, Camera_Device** cameras)](#oh_cameramanager_getcameradevices) | - | Obtains the list of cameras that meet the search criteria based on the camera position, camera types, and connection type. |
| [Camera_ErrorCode OH_CameraManager_DeleteCameraDevices(Camera_Manager* cameraManager, Camera_Device* cameras)](#oh_cameramanager_deletecameradevices) | - | Deletes the specified camera. |
| [Camera_ErrorCode OH_CameraManager_GetCameraConcurrentInfos(Camera_Manager* cameraManager, const Camera_Device* camera, uint32_t deviceSize, Camera_ConcurrentInfo** cameraConcurrentInfo, uint32_t* infoSize)](#oh_cameramanager_getcameraconcurrentinfos) | - | Obtains the concurrent information of specified cameras, the empty return means concurrency is not supported. |

### Variable

| Name | Description |
| -- | -- |
| void (*OH_CameraManager_StatusCallback)(Camera_Manager* cameraManager, Camera_StatusInfo* status) | Defines the callback defined in the [CameraManager_Callbacks](capi-oh-camera-cameramanager-callbacks.md) struct and used to report the camera manager status.<br>**Since**: 11 |
| void (*OH_CameraManager_TorchStatusCallback)(Camera_Manager* cameraManager, Camera_TorchStatusInfo* status) | Defines the callback to listen for flashlight status changes.<br>**Since**: 12 |
| void (*OH_CameraManager_OnFoldStatusInfoChange)(Camera_Manager* cameraManager, Camera_FoldStatusInfo* foldStatusInfo) | Defines the callback to listen for fold status changes of the camera manager.<br>**Since**: 13 |

## Function description

### OH_CameraManager_StatusCallback()

```c
typedef void (*OH_CameraManager_StatusCallback)(Camera_Manager* cameraManager, Camera_StatusInfo* status)
```

**Description**

Defines the callback defined in the [CameraManager_Callbacks](capi-oh-camera-cameramanager-callbacks.md) struct and used to report the camera manager status.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| Camera_Manager\* cameraManager | Pointer to the **Camera_Manager** instance that transfers the callback. |
| Camera_StatusInfo\* status | Pointer to the status information of each camera. |

### OH_CameraManager_TorchStatusCallback()

```c
typedef void (*OH_CameraManager_TorchStatusCallback)(Camera_Manager* cameraManager, Camera_TorchStatusInfo* status)
```

**Description**

Defines the callback to listen for flashlight status changes.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| Camera_Manager\* cameraManager | Pointer to the **Camera_Manager** instance that transfers the callback. |
| Camera_TorchStatusInfo\* status | Pointer to the flashlight status information. |

### OH_CameraManager_OnFoldStatusInfoChange()

```c
typedef void (*OH_CameraManager_OnFoldStatusInfoChange)(Camera_Manager* cameraManager, Camera_FoldStatusInfo* foldStatusInfo)
```

**Description**

Defines the callback to listen for fold status changes of the camera manager.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| Camera_Manager\* cameraManager | Pointer to the **Camera_Manager** instance that transfers the callback. |
| Camera_FoldStatusInfo\* foldStatusInfo | Pointer to the fold status information of the device. |

### OH_CameraManager_RegisterCallback()

```c
Camera_ErrorCode OH_CameraManager_RegisterCallback(Camera_Manager* cameraManager, CameraManager_Callbacks* callback)
```

**Description**

Registers a callback to listen for camera status changes.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| Camera_Manager* cameraManager | Pointer to the **Camera_Manager** instance. |
| [CameraManager_Callbacks](capi-oh-camera-cameramanager-callbacks.md)* callback | Pointer to the target callback. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_CameraManager_UnregisterCallback()

```c
Camera_ErrorCode OH_CameraManager_UnregisterCallback(Camera_Manager* cameraManager, CameraManager_Callbacks* callback)
```

**Description**

Unregisters the callback used to listen for camera status changes.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| Camera_Manager* cameraManager | Pointer to the **Camera_Manager** instance. |
| [CameraManager_Callbacks](capi-oh-camera-cameramanager-callbacks.md)* callback | Pointer to the target callback. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_CameraManager_RegisterTorchStatusCallback()

```c
Camera_ErrorCode OH_CameraManager_RegisterTorchStatusCallback(Camera_Manager* cameraManager, OH_CameraManager_TorchStatusCallback torchStatusCallback)
```

**Description**

Registers a callback to listen for flashlight status changes.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| Camera_Manager* cameraManager | Pointer to the **Camera_Manager** instance. |
| [OH_CameraManager_TorchStatusCallback](capi-camera-manager-h.md#oh_cameramanager_torchstatuscallback) torchStatusCallback | Target callback. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_CameraManager_UnregisterTorchStatusCallback()

```c
Camera_ErrorCode OH_CameraManager_UnregisterTorchStatusCallback(Camera_Manager* cameraManager, OH_CameraManager_TorchStatusCallback torchStatusCallback)
```

**Description**

Unregisters the callback used to listen for flashlight status changes.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| Camera_Manager* cameraManager | Pointer to the **Camera_Manager** instance. |
| [OH_CameraManager_TorchStatusCallback](capi-camera-manager-h.md#oh_cameramanager_torchstatuscallback) torchStatusCallback | Target callback. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_CameraManager_RegisterFoldStatusInfoCallback()

```c
Camera_ErrorCode OH_CameraManager_RegisterFoldStatusInfoCallback(Camera_Manager* cameraManager, OH_CameraManager_OnFoldStatusInfoChange foldStatusInfoCallback)
```

**Description**

Registers a callback to listen for fold status changes.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| Camera_Manager* cameraManager | Pointer to the **Camera_Manager** instance. |
| [OH_CameraManager_OnFoldStatusInfoChange](capi-camera-manager-h.md#oh_cameramanager_onfoldstatusinfochange) foldStatusInfoCallback | Target callback. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_CameraManager_UnregisterFoldStatusInfoCallback()

```c
Camera_ErrorCode OH_CameraManager_UnregisterFoldStatusInfoCallback(Camera_Manager* cameraManager, OH_CameraManager_OnFoldStatusInfoChange foldStatusInfoCallback)
```

**Description**

Unregisters the callback used to listen for fold status changes.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| Camera_Manager* cameraManager | Pointer to the **Camera_Manager** instance. |
| [OH_CameraManager_OnFoldStatusInfoChange](capi-camera-manager-h.md#oh_cameramanager_onfoldstatusinfochange) foldStatusInfoCallback | Target callback. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_CameraManager_GetSupportedCameras()

```c
Camera_ErrorCode OH_CameraManager_GetSupportedCameras(Camera_Manager* cameraManager, Camera_Device** cameras, uint32_t* size)
```

**Description**

Obtains the supported cameras.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| Camera_Manager* cameraManager | Pointer to the **Camera_Manager** instance. |
| Camera_Device** cameras | Double pointer to the list of cameras, which are defined in the Camera_Device struct, if the function is successfully called. |
| uint32_t* size | Pointer to the size of the list of cameras. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_CameraManager_DeleteSupportedCameras()

```c
Camera_ErrorCode OH_CameraManager_DeleteSupportedCameras(Camera_Manager* cameraManager, Camera_Device* cameras, uint32_t size)
```

**Description**

Deletes supported cameras.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| Camera_Manager* cameraManager | Pointer to the **Camera_Manager** instance. |
| Camera_Device* cameras | Pointer to a list of cameras, which are defined in the Camera_Device struct. |
| uint32_t size | The size of the list of cameras. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_CameraManager_GetSupportedCameraOutputCapability()

```c
Camera_ErrorCode OH_CameraManager_GetSupportedCameraOutputCapability(Camera_Manager* cameraManager, const Camera_Device* camera, Camera_OutputCapability** cameraOutputCapability)
```

**Description**

Obtains the output capability supported by a camera.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| Camera_Manager* cameraManager | Pointer to the **Camera_Manager** instance. |
| cameras | the [Camera_Device](capi-oh-camera-camera-device.md) to be queried. |
| Camera_OutputCapability** cameraOutputCapability | Double pointer to the output capability, which is defined in the Camera_OutputCapability struct, if the function is successfully called. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_CameraManager_GetSupportedCameraOutputCapabilityWithSceneMode()

```c
Camera_ErrorCode OH_CameraManager_GetSupportedCameraOutputCapabilityWithSceneMode(Camera_Manager* cameraManager, const Camera_Device* camera, Camera_SceneMode sceneMode, Camera_OutputCapability** cameraOutputCapability)
```

**Description**

Obtains the output capability supported by a camera in the specified mode.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| Camera_Manager* cameraManager | Pointer to the **Camera_Manager** instance. |
| const Camera_Device* camera | Pointer to the **Camera_Device** instance. |
| Camera_SceneMode sceneMode | Scene mode. |
| Camera_OutputCapability** cameraOutputCapability | Double pointer to output capability, which is defined in the **Camera_OutputCapability*<br> struct, if the function is successfully called. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SERVICE_FATAL_ERROR: The camera service is abnormal. |

### OH_CameraManager_GetSupportedFullCameraOutputCapabilityWithSceneMode()

```c
Camera_ErrorCode OH_CameraManager_GetSupportedFullCameraOutputCapabilityWithSceneMode(Camera_Manager* cameraManager, const Camera_Device* camera, Camera_SceneMode sceneMode, Camera_OutputCapability** cameraOutputCapability)
```

**Description**

Obtains the complete output capabilities supported by a specified camera in a specified mode, including YUV, HEIF, and HDR. Before using YUV, HEIF, or HDR, you need to explicitly call this method to ensure that the complete output capabilities are obtained.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| Camera_Manager* cameraManager | Pointer to the **Camera_Manager** instance. |
| const Camera_Device* camera | Pointer to the **Camera_Device** instance. |
| Camera_SceneMode sceneMode | Scene mode. |
| Camera_OutputCapability** cameraOutputCapability | Double pointer to output capability, which is defined in the **Camera_OutputCapability*<br> struct, if the function is successfully called. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SERVICE_FATAL_ERROR: The camera service is abnormal. |

### OH_CameraManager_DeleteSupportedCameraOutputCapability()

```c
Camera_ErrorCode OH_CameraManager_DeleteSupportedCameraOutputCapability(Camera_Manager* cameraManager, Camera_OutputCapability* cameraOutputCapability)
```

**Description**

Deletes the output capability supported by a camera.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| Camera_Manager* cameraManager | Pointer to the **Camera_Manager** instance. |
| Camera_OutputCapability* cameraOutputCapability | Pointer to the output capability, which is defined in the **Camera_OutputCapability**<br>struct. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_CameraManager_IsCameraMuted()

```c
Camera_ErrorCode OH_CameraManager_IsCameraMuted(Camera_Manager* cameraManager, bool* isCameraMuted)
```

**Description**

Checks whether a camera is muted.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| Camera_Manager* cameraManager | Pointer to the **Camera_Manager** instance. |
| bool* isCameraMuted | Pointer to the check result for whether the camera is muted, if the function is successfully called. **true** if muted, **false** otherwise. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_CameraManager_CreateCaptureSession()

```c
Camera_ErrorCode OH_CameraManager_CreateCaptureSession(Camera_Manager* cameraManager, Camera_CaptureSession** captureSession)
```

**Description**

Creates a **CaptureSession** instance.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| Camera_Manager* cameraManager | Pointer to the **Camera_Manager** instance. |
| Camera_CaptureSession** captureSession | Double pointer to the **Camera_CaptureSession** instance created, if the function is successfully called. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SERVICE_FATAL_ERROR: The camera service is abnormal. |

### OH_CameraManager_CreateCameraInput()

```c
Camera_ErrorCode OH_CameraManager_CreateCameraInput(Camera_Manager* cameraManager, const Camera_Device* camera, Camera_Input** cameraInput)
```

**Description**

Creates a **Camera_Input** instance.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Required permission**: ohos.permission.CAMERA

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| Camera_Manager* cameraManager | Pointer to the **Camera_Manager** instance. |
| const Camera_Device* camera | Pointer to the **Camera_Device** instance. |
| Camera_Input** cameraInput | Double pointer to the **Camera_Input** instance created, if the function is successfully called. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SERVICE_FATAL_ERROR: The camera service is abnormal. |

### OH_CameraManager_CreateCameraInput_WithPositionAndType()

```c
Camera_ErrorCode OH_CameraManager_CreateCameraInput_WithPositionAndType(Camera_Manager* cameraManager, Camera_Position position, Camera_Type type, Camera_Input** cameraInput)
```

**Description**

Creates a **Camera_Input** instance with the specified camera position and type.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Required permission**: ohos.permission.CAMERA

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| Camera_Manager* cameraManager | Pointer to the **Camera_Manager** instance. |
| Camera_Position position | Camera position. |
| Camera_Type type | Camera type. |
| Camera_Input** cameraInput | Double pointer to the **Camera_Input** instance created, if the function is successfully called. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SERVICE_FATAL_ERROR: The camera service is abnormal. |

### OH_CameraManager_CreatePreviewOutput()

```c
Camera_ErrorCode OH_CameraManager_CreatePreviewOutput(Camera_Manager* cameraManager, const Camera_Profile* profile, const char* surfaceId, Camera_PreviewOutput** previewOutput)
```

**Description**

Creates a **PreviewOutput** instance.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| Camera_Manager* cameraManager | Pointer to the **Camera_Manager** instance. |
| const Camera_Profile* profile | Pointer to the profile used for creating the **Camera_PreviewOutput** instance. |
| const char* surfaceId | Pointer to the surface ID used for creating the **Camera_PreviewOutput** instance. |
| Camera_PreviewOutput** previewOutput | Double pointer to the **Camera_PreviewOutput** instance created, if the function is successfully called. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SERVICE_FATAL_ERROR: The camera service is abnormal. |

### OH_CameraManager_CreatePreviewOutputUsedInPreconfig()

```c
Camera_ErrorCode OH_CameraManager_CreatePreviewOutputUsedInPreconfig(Camera_Manager* cameraManager, const char* surfaceId, Camera_PreviewOutput** previewOutput)
```

**Description**

Creates a **PreviewOutput** instance to be used in a preconfiguration stream.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| Camera_Manager* cameraManager | Pointer to the **Camera_Manager** instance. |
| const char* surfaceId | Pointer to the surface ID used for creating the **Camera_PreviewOutput** instance. |
| Camera_PreviewOutput** previewOutput | Double pointer to the **Camera_PreviewOutput** instance created, if the function is successfully called. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SERVICE_FATAL_ERROR: The camera service is abnormal. |

### OH_CameraManager_CreateDeferredPreviewOutput()

```c
Camera_ErrorCode OH_CameraManager_CreateDeferredPreviewOutput(const Camera_Manager* cameraManager, const Camera_Profile* profile, Camera_PreviewOutput** previewOutput)
```

**Description**

Create a defer preview output instance.The caller must call [OH_PreviewOutput_Release](capi-preview-output-h.md#oh_previewoutput_release) to free the memory of the output.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| const Camera_Manager* cameraManager | the [Camera_Manager](capi-oh-camera-camera-manager.md) instance. |
| const Camera_Profile* profile | the [Camera_Profile](capi-oh-camera-camera-profile.md) to create [Camera_PreviewOutput](capi-oh-camera-camera-previewoutput.md). |
| Camera_PreviewOutput** previewOutput | the [Camera_PreviewOutput](capi-oh-camera-camera-previewoutput.md) will be created if the method call succeeds. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | [CAMERA_OK](capi-camera-h.md#camera_errorcode) if the method call succeeds.          [CAMERA_INVALID_ARGUMENT](capi-camera-h.md#camera_errorcode) if parameter missing or parameter type incorrect.          [CAMERA_SERVICE_FATAL_ERROR](capi-camera-h.md#camera_errorcode) if camera service fatal error. |

### OH_CameraManager_CreatePhotoOutput()

```c
Camera_ErrorCode OH_CameraManager_CreatePhotoOutput(Camera_Manager* cameraManager, const Camera_Profile* profile, const char* surfaceId, Camera_PhotoOutput** photoOutput)
```

**Description**

Creates a **PhotoOutput** instance. This API can only be used to create a **PhotoOutput** object in JPEG format.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| Camera_Manager* cameraManager | Pointer to the **Camera_Manager** instance. |
| const Camera_Profile* profile | Pointer to the profile used for creating the **Camera_PhotoOutput** instance. |
| const char* surfaceId | Pointer to the surface ID used for creating the **Camera_PhotoOutput** instance. |
| Camera_PhotoOutput** photoOutput | Double pointer to the **Camera_PhotoOutput** instance created, if the function is successfully called. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SERVICE_FATAL_ERROR: The camera service is abnormal. |

### OH_CameraManager_CreatePhotoOutputUsedInPreconfig()

```c
Camera_ErrorCode OH_CameraManager_CreatePhotoOutputUsedInPreconfig(Camera_Manager* cameraManager, const char* surfaceId, Camera_PhotoOutput** photoOutput)
```

**Description**

Creates a **PhotoOutput** instance to be used in a preconfiguration stream.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| Camera_Manager* cameraManager | Pointer to the **Camera_Manager** instance. |
| const char* surfaceId | Pointer to the surface ID used for creating the **Camera_PhotoOutput** instance. |
| Camera_PhotoOutput** photoOutput | Double pointer to the **Camera_PhotoOutput** instance created, if the function is successfully called. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SERVICE_FATAL_ERROR: The camera service is abnormal. |

### OH_CameraManager_CreatePhotoOutputWithoutSurface()

```c
Camera_ErrorCode OH_CameraManager_CreatePhotoOutputWithoutSurface(Camera_Manager *cameraManager, const Camera_Profile *profile, Camera_PhotoOutput **photoOutput)
```

**Description**

Creates a **PhotoOutput** instance. **surfaceId** is not required in this function.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| Camera_Manager *cameraManager | Pointer to the **Camera_Manager** instance. |
| const Camera_Profile *profile | Pointer to the profile used for creating the **Camera_PhotoOutput** instance. |
| Camera_PhotoOutput **photoOutput | Double pointer to the **Camera_PhotoOutput** instance created, if the function is successfully called. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SERVICE_FATAL_ERROR: The camera service is abnormal. |

### OH_CameraManager_CreateVideoOutput()

```c
Camera_ErrorCode OH_CameraManager_CreateVideoOutput(Camera_Manager* cameraManager, const Camera_VideoProfile* profile, const char* surfaceId, Camera_VideoOutput** videoOutput)
```

**Description**

Creates a **VideoOutput** instance.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| Camera_Manager* cameraManager | Pointer to the **Camera_Manager** instance. |
| const Camera_VideoProfile* profile | Pointer to the profile for creating the **Camera_VideoOutput** instance. |
| const char* surfaceId | Pointer to the surface ID used for creating the **Camera_VideoOutput** instance. |
| Camera_VideoOutput** videoOutput | Double pointer to the **Camera_VideoOutput** instance created, if the function is successfully called. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SERVICE_FATAL_ERROR: The camera service is abnormal. |

### OH_CameraManager_CreateVideoOutputUsedInPreconfig()

```c
Camera_ErrorCode OH_CameraManager_CreateVideoOutputUsedInPreconfig(Camera_Manager* cameraManager, const char* surfaceId, Camera_VideoOutput** videoOutput)
```

**Description**

Creates a **VideoOutput** instance to be used in a preconfiguration stream.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| Camera_Manager* cameraManager | Pointer to the **Camera_Manager** instance. |
| const char* surfaceId | Pointer to the surface ID used for creating the **Camera_VideoOutput** instance. |
| Camera_VideoOutput** videoOutput | Double pointer to the **Camera_VideoOutput** instance created, if the function is successfully called. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SERVICE_FATAL_ERROR: The camera service is abnormal. |

### OH_CameraManager_CreateMetadataOutput()

```c
Camera_ErrorCode OH_CameraManager_CreateMetadataOutput(Camera_Manager* cameraManager, const Camera_MetadataObjectType* profile, Camera_MetadataOutput** metadataOutput)
```

**Description**

Creates a **MetadataOutput** instance.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| Camera_Manager* cameraManager | Pointer to the **Camera_Manager** instance. |
| const Camera_MetadataObjectType* profile | Pointer to the metadata object type used for creating the **Camera_MetadataOutput** instance. |
| Camera_MetadataOutput** metadataOutput | Double pointer to the **Camera_MetadataOutput** instance created, if the function is successfully called. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SERVICE_FATAL_ERROR: The camera service is abnormal. |

### OH_CameraManager_CreateMetadataOutputWithObjectTypes()

```c
Camera_ErrorCode OH_CameraManager_CreateMetadataOutputWithObjectTypes(Camera_Manager* cameraManager, const Camera_MetadataObjectType* metadataObjectTypes, uint32_t size, Camera_MetadataOutput** metadataOutput)
```

**Description**

Creates a **metadataOutput** instance using an array of metadata object types.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| Camera_Manager* cameraManager | Pointer to the **Camera_Manager** instance. |
| const Camera_MetadataObjectType* metadataObjectTypes | Pointer to the metadata object types used for creating the **Camera_MetadataOutput**<br>instance. |
| uint32_t size | Length of the metadata object type array. |
| Camera_MetadataOutput** metadataOutput | Double pointer to the **Camera_MetadataOutput** instance created, if the function is successfully called. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SERVICE_FATAL_ERROR: The camera service is abnormal. |

### OH_CameraManager_GetSupportedSceneModes()

```c
Camera_ErrorCode OH_CameraManager_GetSupportedSceneModes(Camera_Device* camera, Camera_SceneMode** sceneModes, uint32_t* size)
```

**Description**

Obtains the scene modes supported by a camera.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| Camera_Device* camera | Pointer to the **Camera_Device** instance. |
| Camera_SceneMode** sceneModes | Double pointer to the list of scene modes, which are defined in the Camera_SceneMode struct, if the function is successfully called. |
| uint32_t* size | Pointer to the size of the list of scene modes. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SERVICE_FATAL_ERROR: The camera service is abnormal. |

### OH_CameraManager_DeleteSceneModes()

```c
Camera_ErrorCode OH_CameraManager_DeleteSceneModes(Camera_Manager* cameraManager, Camera_SceneMode* sceneModes)
```

**Description**

Deletes scene modes.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| Camera_Manager* cameraManager | Pointer to the **Camera_Manager** instance. |
| Camera_SceneMode* sceneModes | Pointer to the list of scene modes to delete. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_CameraManager_IsTorchSupported()

```c
Camera_ErrorCode OH_CameraManager_IsTorchSupported(Camera_Manager* cameraManager, bool* isTorchSupported)
```

**Description**

Checks whether the device supports the flashlight.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| Camera_Manager* cameraManager | Pointer to the **Camera_Manager** instance. |
| bool* isTorchSupported | Pointer to the check result for the support of the flashlight. **true** if supported, **<br>false** otherwise. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_CameraManager_IsTorchSupportedByTorchMode()

```c
Camera_ErrorCode OH_CameraManager_IsTorchSupportedByTorchMode(Camera_Manager* cameraManager, Camera_TorchMode torchMode, bool* isTorchSupported)
```

**Description**

Checks whether the device supports the specified flashlight mode.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| Camera_Manager* cameraManager | Pointer to the **Camera_Manager** instance. |
| Camera_TorchMode torchMode | Flashlight mode to check. |
| bool* isTorchSupported | Pointer to the check result for the support of the flashlight mode. **true** if supported, **<br>false** otherwise. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SERVICE_FATAL_ERROR: The camera service is abnormal. |

### OH_CameraManager_SetTorchMode()

```c
Camera_ErrorCode OH_CameraManager_SetTorchMode(Camera_Manager* cameraManager, Camera_TorchMode torchMode)
```

**Description**

Sets a flashlight mode.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| Camera_Manager* cameraManager | Pointer to the **Camera_Manager** instance. |
| Camera_TorchMode torchMode | Flashlight mode to set. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SERVICE_FATAL_ERROR: The camera service is abnormal. |

### OH_CameraManager_IsTorchLevelControlSupported()

```c
Camera_ErrorCode OH_CameraManager_IsTorchLevelControlSupported(const Camera_Manager* cameraManager, bool* isTorchLevelControlSupported)
```

**Description**

Checks whether the device supports flashlight brightness control.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| const Camera_Manager* cameraManager | Pointer to the **Camera_Manager** instance. |
| bool* isTorchLevelControlSupported | Whether the device supports flashlight brightness control. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SERVICE_FATAL_ERROR: The camera service is abnormal. |

### OH_CameraManager_SetTorchModeOnWithLevel()

```c
Camera_ErrorCode OH_CameraManager_SetTorchModeOnWithLevel(Camera_Manager* cameraManager, double torchLevel)
```

**Description**

Turns on the flashlight and sets the brightness level.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| Camera_Manager* cameraManager | Pointer to the **Camera_Manager** instance. |
| double torchLevel | Target brightness level. The value range is [0.0, 1.0]. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SERVICE_FATAL_ERROR: The camera service is abnormal. |

### OH_CameraManager_GetCameraDevice()

```c
Camera_ErrorCode OH_CameraManager_GetCameraDevice(Camera_Manager* cameraManager, Camera_Position position, Camera_Type type, Camera_Device* camera)
```

**Description**

Queries a specified device based on position and type.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| Camera_Manager* cameraManager | the [Camera_Manager](capi-oh-camera-camera-manager.md) instance. |
| Camera_Position position | the [Camera_Position](capi-camera-h.md#camera_position) instance. |
| Camera_Type type | the [Camera_Type](capi-camera-h.md#camera_type) instance. |
| Camera_Device* camera | the [Camera_Device](capi-oh-camera-camera-device.md) to be set. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | [CAMERA_OK](capi-camera-h.md#camera_errorcode) if the method call succeeds.          [CAMERA_INVALID_ARGUMENT](capi-camera-h.md#camera_errorcode) if parameter missing or parameter type incorrect.          [CAMERA_SERVICE_FATAL_ERROR](capi-camera-h.md#camera_errorcode) if camera service fatal error. |

### OH_CameraManager_GetCameraDevices()

```c
Camera_ErrorCode OH_CameraManager_GetCameraDevices(Camera_Manager* cameraManager, Camera_DeviceQueryInfo* deviceQueryInfo, uint32_t* cameraSize, Camera_Device** cameras)
```

**Description**

Obtains the list of cameras that meet the search criteria based on the camera position, camera types, and connection type.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| Camera_Manager* cameraManager | Pointer to the **Camera_Manager** instance. |
| Camera_DeviceQueryInfo* deviceQueryInfo | Camera device query information instance. |
| uint32_t* cameraSize | Size of the list of supported cameras. |
| Camera_Device** cameras | List of supported cameras. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SERVICE_FATAL_ERROR: The camera service is abnormal. |

### OH_CameraManager_DeleteCameraDevices()

```c
Camera_ErrorCode OH_CameraManager_DeleteCameraDevices(Camera_Manager* cameraManager, Camera_Device* cameras)
```

**Description**

Deletes the specified camera.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| Camera_Manager* cameraManager | Pointer to the **Camera_Manager** instance. |
| Camera_Device* cameras | List of cameras to be deleted. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_CameraManager_GetCameraConcurrentInfos()

```c
Camera_ErrorCode OH_CameraManager_GetCameraConcurrentInfos(Camera_Manager* cameraManager, const Camera_Device* camera, uint32_t deviceSize, Camera_ConcurrentInfo** cameraConcurrentInfo, uint32_t* infoSize)
```

**Description**

Obtains the concurrent information of specified cameras, the empty return means concurrency is not supported.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| Camera_Manager* cameraManager | the [Camera_Manager](capi-oh-camera-camera-manager.md) instance. |
| const Camera_Device* camera | the [Camera_Device](capi-oh-camera-camera-device.md) instance. |
| uint32_t deviceSize | length of the input device array. |
| Camera_ConcurrentInfo** cameraConcurrentInfo | the [Camera_ConcurrentInfo](capi-oh-camera-camera-concurrentinfo.md) to be set. |
| uint32_t* infoSize | length of the returned concurrency information array. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | [CAMERA_OK](capi-camera-h.md#camera_errorcode) if the method call succeeds.          [CAMERA_INVALID_ARGUMENT](capi-camera-h.md#camera_errorcode) if parameter missing or parameter type incorrect.          [CAMERA_SERVICE_FATAL_ERROR](capi-camera-h.md#camera_errorcode) if camera service fatal error. |


