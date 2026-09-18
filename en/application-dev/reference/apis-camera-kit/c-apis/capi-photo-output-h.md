# photo_output.h

## Overview

The file declares the photo output concepts.

**Library**: libohcamera.so

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 11

**Related module**: [OH_Camera](capi-oh-camera.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [PhotoOutput_Callbacks](capi-oh-camera-photooutput-callbacks.md) | PhotoOutput_Callbacks | The struct describes the callbacks related to photo output. |
| [Camera_PhotoOutput](capi-oh-camera-camera-photooutput.md) | Camera_PhotoOutput | The struct describes the photo output object. |
| [OH_Camera_PhotoCaptureSettingExt](capi-oh-camera-oh-camera-photocapturesettingext.md) | OH_Camera_PhotoCaptureSettingExt | The struct describes the photo capture setting ext. |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef void (\*OH_PhotoOutput_OnFrameStart)(Camera_PhotoOutput* photoOutput)](#oh_photooutput_onframestart) | OH_PhotoOutput_OnFrameStart | Defines the callback defined in the [PhotoOutput_Callbacks](capi-oh-camera-photooutput-callbacks.md) struct and used to report photo output frame start events. |
| [typedef void (\*OH_PhotoOutput_OnFrameShutter)(Camera_PhotoOutput* photoOutput, Camera_FrameShutterInfo* info)](#oh_photooutput_onframeshutter) | OH_PhotoOutput_OnFrameShutter | Defines the callback defined in the [PhotoOutput_Callbacks](capi-oh-camera-photooutput-callbacks.md) struct and used to report frame shutter events. |
| [typedef void (\*OH_PhotoOutput_OnFrameEnd)(Camera_PhotoOutput* photoOutput, int32_t frameCount)](#oh_photooutput_onframeend) | OH_PhotoOutput_OnFrameEnd | Defines the callback defined in the [PhotoOutput_Callbacks](capi-oh-camera-photooutput-callbacks.md) struct and used to report photo output frame end events. |
| [typedef void (\*OH_PhotoOutput_OnError)(Camera_PhotoOutput* photoOutput, Camera_ErrorCode errorCode)](#oh_photooutput_onerror) | OH_PhotoOutput_OnError | Defines the callback defined in the [PhotoOutput_Callbacks](capi-oh-camera-photooutput-callbacks.md) struct and used to report photo output errors. |
| [typedef void (\*OH_PhotoOutput_CaptureEnd)(Camera_PhotoOutput* photoOutput, int32_t frameCount)](#oh_photooutput_captureend) | OH_PhotoOutput_CaptureEnd | Defines the callback invoked when the capture ends. |
| [typedef void (\*OH_PhotoOutput_CaptureStartWithInfo)(Camera_PhotoOutput* photoOutput, Camera_CaptureStartInfo* Info)](#oh_photooutput_capturestartwithinfo) | OH_PhotoOutput_CaptureStartWithInfo | Defines the callback invoked when the capture starts. |
| [typedef void (\*OH_PhotoOutput_OnFrameShutterEnd)(Camera_PhotoOutput* photoOutput, Camera_FrameShutterInfo* Info)](#oh_photooutput_onframeshutterend) | OH_PhotoOutput_OnFrameShutterEnd | Defines the callback invoked when frame shutter ends. |
| [typedef void (\*OH_PhotoOutput_CaptureReady)(Camera_PhotoOutput* photoOutput)](#oh_photooutput_captureready) | OH_PhotoOutput_CaptureReady | Defines the callback invoked when the camera is ready to take photos. When the callback is received, the next capture can be performed. |
| [typedef void (\*OH_PhotoOutput_EstimatedCaptureDuration)(Camera_PhotoOutput* photoOutput, int64_t duration)](#oh_photooutput_estimatedcaptureduration) | OH_PhotoOutput_EstimatedCaptureDuration | Defines the callback for the estimated capture duration. |
| [typedef void (\*OH_PhotoOutput_PhotoAvailable)(Camera_PhotoOutput* photoOutput, OH_PhotoNative* photo)](#oh_photooutput_photoavailable) | OH_PhotoOutput_PhotoAvailable | Defines the callback invoked when a high-resolution photo is available. |
| [typedef void (\*OH_PhotoOutput_PhotoAssetAvailable)(Camera_PhotoOutput* photoOutput, OH_MediaAsset* photoAsset)](#oh_photooutput_photoassetavailable) | OH_PhotoOutput_PhotoAssetAvailable | Defines the callback invoked when a photo asset is available. |
| [Camera_ErrorCode OH_PhotoOutput_RegisterCallback(Camera_PhotoOutput* photoOutput, PhotoOutput_Callbacks* callback)](#oh_photooutput_registercallback) | - | Registers a callback to listen for photo output events. |
| [Camera_ErrorCode OH_PhotoOutput_UnregisterCallback(Camera_PhotoOutput* photoOutput, PhotoOutput_Callbacks* callback)](#oh_photooutput_unregistercallback) | - | Unregisters the callback used to listen for photo output events. |
| [Camera_ErrorCode OH_PhotoOutput_RegisterCaptureStartWithInfoCallback(Camera_PhotoOutput* photoOutput, OH_PhotoOutput_CaptureStartWithInfo callback)](#oh_photooutput_registercapturestartwithinfocallback) | - | Registers a callback to listen for capture start events. |
| [Camera_ErrorCode OH_PhotoOutput_GetPhotoRotation(Camera_PhotoOutput* photoOutput, int deviceDegree, Camera_ImageRotation* imageRotation)](#oh_photooutput_getphotorotation) | - | Obtains the photo rotation angle. |
| [Camera_ErrorCode OH_PhotoOutput_GetPhotoRotationWithoutDeviceDegree(Camera_PhotoOutput* photoOutput, Camera_ImageRotation* imageRotation)](#oh_photooutput_getphotorotationwithoutdevicedegree) | - | Obtains the photo rotation angle. |
| [Camera_ErrorCode OH_PhotoOutput_UnregisterCaptureStartWithInfoCallback(Camera_PhotoOutput* photoOutput, OH_PhotoOutput_CaptureStartWithInfo callback)](#oh_photooutput_unregistercapturestartwithinfocallback) | - | Unregisters the callback used to listen for capture start events. |
| [Camera_ErrorCode OH_PhotoOutput_RegisterCaptureEndCallback(Camera_PhotoOutput* photoOutput, OH_PhotoOutput_CaptureEnd callback)](#oh_photooutput_registercaptureendcallback) | - | Registers a callback to listen for capture end events. |
| [Camera_ErrorCode OH_PhotoOutput_UnregisterCaptureEndCallback(Camera_PhotoOutput* photoOutput, OH_PhotoOutput_CaptureEnd callback)](#oh_photooutput_unregistercaptureendcallback) | - | Unregisters the callback used to listen for capture end events. |
| [Camera_ErrorCode OH_PhotoOutput_RegisterFrameShutterEndCallback(Camera_PhotoOutput* photoOutput, OH_PhotoOutput_OnFrameShutterEnd callback)](#oh_photooutput_registerframeshutterendcallback) | - | Registers a callback to listen for frame shutter end events. |
| [Camera_ErrorCode OH_PhotoOutput_UnregisterFrameShutterEndCallback(Camera_PhotoOutput* photoOutput, OH_PhotoOutput_OnFrameShutterEnd callback)](#oh_photooutput_unregisterframeshutterendcallback) | - | Unregisters the callback used to listen for frame shutter end events. |
| [Camera_ErrorCode OH_PhotoOutput_RegisterCaptureReadyCallback(Camera_PhotoOutput* photoOutput, OH_PhotoOutput_CaptureReady callback)](#oh_photooutput_registercapturereadycallback) | - | Registers a callback to listen for camera ready events. When the callback is received, the next capture can be performed. |
| [Camera_ErrorCode OH_PhotoOutput_UnregisterCaptureReadyCallback(Camera_PhotoOutput* photoOutput, OH_PhotoOutput_CaptureReady callback)](#oh_photooutput_unregistercapturereadycallback) | - | Unregisters the callback used to listen for camera ready events. |
| [Camera_ErrorCode OH_PhotoOutput_RegisterEstimatedCaptureDurationCallback(Camera_PhotoOutput* photoOutput, OH_PhotoOutput_EstimatedCaptureDuration callback)](#oh_photooutput_registerestimatedcapturedurationcallback) | - | Registers a callback to listen for estimated capture duration events. |
| [Camera_ErrorCode OH_PhotoOutput_UnregisterEstimatedCaptureDurationCallback(Camera_PhotoOutput* photoOutput, OH_PhotoOutput_EstimatedCaptureDuration callback)](#oh_photooutput_unregisterestimatedcapturedurationcallback) | - | Unregisters the callback used to listen for estimated capture duration events. |
| [Camera_ErrorCode OH_PhotoOutput_RegisterPhotoAvailableCallback(Camera_PhotoOutput* photoOutput, OH_PhotoOutput_PhotoAvailable callback)](#oh_photooutput_registerphotoavailablecallback) | - | Registers a callback to listen for photo availability events. |
| [Camera_ErrorCode OH_PhotoOutput_UnregisterPhotoAvailableCallback(Camera_PhotoOutput* photoOutput, OH_PhotoOutput_PhotoAvailable callback)](#oh_photooutput_unregisterphotoavailablecallback) | - | Unregisters the callback used to listen for photo availability events. |
| [Camera_ErrorCode OH_PhotoOutput_RegisterPhotoAssetAvailableCallback(Camera_PhotoOutput* photoOutput, OH_PhotoOutput_PhotoAssetAvailable callback)](#oh_photooutput_registerphotoassetavailablecallback) | - | Registers a callback to listen for photo asset availability events. |
| [Camera_ErrorCode OH_PhotoOutput_UnregisterPhotoAssetAvailableCallback(Camera_PhotoOutput* photoOutput, OH_PhotoOutput_PhotoAssetAvailable callback)](#oh_photooutput_unregisterphotoassetavailablecallback) | - | Unregisters the callback used to listen for photo asset availability events. |
| [Camera_ErrorCode OH_PhotoOutput_Capture(Camera_PhotoOutput* photoOutput)](#oh_photooutput_capture) | - | Captures a photo. This function must be called in prior to {@link OH_PreviewOutput_Release}. Otherwise, photo capture fails. |
| [Camera_ErrorCode OH_PhotoOutput_Capture_WithCaptureSetting(Camera_PhotoOutput* photoOutput, Camera_PhotoCaptureSetting setting)](#oh_photooutput_capture_withcapturesetting) | - | Captures a photo with photographing parameters. |
| [Camera_ErrorCode OH_PhotoOutput_Release(Camera_PhotoOutput* photoOutput)](#oh_photooutput_release) | - | Releases a PhotoOutput instance. |
| [Camera_ErrorCode OH_PhotoOutput_IsMirrorSupported(Camera_PhotoOutput* photoOutput, bool* isSupported)](#oh_photooutput_ismirrorsupported) | - | Checks whether mirroring is supported. |
| [Camera_ErrorCode OH_PhotoOutput_EnableMirror(Camera_PhotoOutput* photoOutput, bool enabled)](#oh_photooutput_enablemirror) | - | Enables dynamic photo capture. |
| [Camera_ErrorCode OH_PhotoOutput_GetActiveProfile(Camera_PhotoOutput* photoOutput, Camera_Profile** profile)](#oh_photooutput_getactiveprofile) | - | Obtains the profile of a PhotoOutput instance. |
| [Camera_ErrorCode OH_PhotoOutput_DeleteProfile(Camera_Profile* profile)](#oh_photooutput_deleteprofile) | - | Deletes the profile of a PhotoOutput instance. |
| [Camera_ErrorCode OH_PhotoOutput_IsMovingPhotoSupported(Camera_PhotoOutput* photoOutput, bool* isSupported)](#oh_photooutput_ismovingphotosupported) | - | Checks whether moving photos are supported. |
| [Camera_ErrorCode OH_PhotoOutput_EnableMovingPhoto(Camera_PhotoOutput* photoOutput, bool enabled)](#oh_photooutput_enablemovingphoto) | - | Enables or disables moving photos. |
| [Camera_ErrorCode OH_PhotoOutput_IsPhotoQualityPrioritizationSupported(Camera_PhotoOutput* photoOutput, Camera_PhotoQualityPrioritization qualityPrioritization, bool* isSupported)](#oh_photooutput_isphotoqualityprioritizationsupported) | - | Checks whether the specified photo quality prioritization strategy is supported. |
| [Camera_ErrorCode OH_PhotoOutput_SetPhotoQualityPrioritization(Camera_PhotoOutput* photoOutput, Camera_PhotoQualityPrioritization qualityPrioritization)](#oh_photooutput_setphotoqualityprioritization) | - | Sets the photo quality prioritization strategy. |
| [Camera_ErrorCode OH_PhotoOutput_Capture_WithCaptureSettingExt(Camera_PhotoOutput* photoOutput, OH_Camera_PhotoCaptureSettingExt* setting)](#oh_photooutput_capture_withcapturesettingext) | - | Captures a photo with photo capture setting extension. |
| [Camera_ErrorCode OH_PhotoOutput_CreatePhotoCaptureSettingExt(Camera_PhotoOutput* photoOutput, OH_Camera_PhotoCaptureSettingExt** setting)](#oh_photooutput_createphotocapturesettingext) | - | Creates a **OH_Camera_PhotoCaptureSettingExt** instance. Release the photo capture setting ext memory by calling [OH_PhotoOutput_DestroyPhotoCaptureSettingExt](capi-photo-output-h.md#oh_photooutput_destroyphotocapturesettingext). |
| [Camera_ErrorCode OH_PhotoCaptureSettingExt_SetCompressionQuality(OH_Camera_PhotoCaptureSettingExt* photoCaptureSettingExt, uint8_t compressionQuality)](#oh_photocapturesettingext_setcompressionquality) | - | Sets the image compression quality for the photo capture extension configuration. |
| [Camera_ErrorCode OH_PhotoCaptureSettingExt_SetImageRotation(OH_Camera_PhotoCaptureSettingExt* photoCaptureSettingExt, Camera_ImageRotation rotation)](#oh_photocapturesettingext_setimagerotation) | - | Sets the image rotation for the photo capture extension configuration. |
| [Camera_ErrorCode OH_PhotoCaptureSettingExt_SetMirror(OH_Camera_PhotoCaptureSettingExt* photoCaptureSettingExt, bool mirror)](#oh_photocapturesettingext_setmirror) | - | Sets the image mirror for the photo capture extension configuration. |
| [Camera_ErrorCode OH_PhotoOutput_DestroyPhotoCaptureSettingExt(OH_Camera_PhotoCaptureSettingExt* setting)](#oh_photooutput_destroyphotocapturesettingext) | - | Destroy the photo capture setting ext. |
| [Camera_ErrorCode OH_PhotoCaptureSettingExt_SetLocation(OH_Camera_PhotoCaptureSettingExt* photoCaptureSettingExt, Camera_Location location)](#oh_photocapturesettingext_setlocation) | - | Sets the image location for the photo capture extension configuration. |
| [Camera_ErrorCode OH_PhotoOutput_EnableAutoExtendedGainmapDelivery(Camera_PhotoOutput* photoOutput, bool enabled)](#oh_photooutput_enableautoextendedgainmapdelivery) | - | Enables auto extended gainmap delivery. |
| [bool OH_PhotoOutput_IsAutoExtendedGainmapDeliverySupported(const Camera_PhotoOutput* photoOutput)](#oh_photooutput_isautoextendedgainmapdeliverysupported) | - | Checks whether the auto extended gainmap delivery is supported. |

### Variable

| Name | Description |
| -- | -- |
| void (*OH_PhotoOutput_OnFrameStart)(Camera_PhotoOutput* photoOutput) | Defines the callback defined in the [PhotoOutput_Callbacks](capi-oh-camera-photooutput-callbacks.md) struct and used to report photo output frame start events.<br>**Since**: 11 |
| void (*OH_PhotoOutput_OnFrameShutter)(Camera_PhotoOutput* photoOutput, Camera_FrameShutterInfo* info) | Defines the callback defined in the [PhotoOutput_Callbacks](capi-oh-camera-photooutput-callbacks.md) struct and used to report frame shutter events.<br>**Since**: 11 |
| void (*OH_PhotoOutput_OnFrameEnd)(Camera_PhotoOutput* photoOutput, int32_t frameCount) | Defines the callback defined in the [PhotoOutput_Callbacks](capi-oh-camera-photooutput-callbacks.md) struct and used to report photo output frame end events.<br>**Since**: 11 |
| void (*OH_PhotoOutput_OnError)(Camera_PhotoOutput* photoOutput, Camera_ErrorCode errorCode) | Defines the callback defined in the [PhotoOutput_Callbacks](capi-oh-camera-photooutput-callbacks.md) struct and used to report photo output errors.<br>**Since**: 11 |
| void (*OH_PhotoOutput_CaptureEnd) (Camera_PhotoOutput* photoOutput, int32_t frameCount) | Defines the callback invoked when the capture ends.<br>**Since**: 12 |
| void (*OH_PhotoOutput_CaptureStartWithInfo) (Camera_PhotoOutput* photoOutput, Camera_CaptureStartInfo* Info) | Defines the callback invoked when the capture starts.<br>**Since**: 12 |
| void (*OH_PhotoOutput_OnFrameShutterEnd) (Camera_PhotoOutput* photoOutput, Camera_FrameShutterInfo* Info) | Defines the callback invoked when frame shutter ends.<br>**Since**: 12 |
| void (*OH_PhotoOutput_CaptureReady) (Camera_PhotoOutput* photoOutput) | Defines the callback invoked when the camera is ready to take photos. When the callback is received, the next capture can be performed.<br>**Since**: 12 |
| void (*OH_PhotoOutput_EstimatedCaptureDuration) (Camera_PhotoOutput* photoOutput, int64_t duration) | Defines the callback for the estimated capture duration.<br>**Since**: 12 |
| void (*OH_PhotoOutput_PhotoAvailable)(Camera_PhotoOutput* photoOutput, OH_PhotoNative* photo) | Defines the callback invoked when a high-resolution photo is available.<br>**Since**: 12 |
| void (*OH_PhotoOutput_PhotoAssetAvailable)(Camera_PhotoOutput* photoOutput, OH_MediaAsset* photoAsset) | Defines the callback invoked when a photo asset is available.<br>**Since**: 12 |

## Function description

### OH_PhotoOutput_OnFrameStart()

```c
typedef void (*OH_PhotoOutput_OnFrameStart)(Camera_PhotoOutput* photoOutput)
```

**Description**

Defines the callback defined in the [PhotoOutput_Callbacks](capi-oh-camera-photooutput-callbacks.md) struct and used to report photo output frame start events.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_PhotoOutput](capi-oh-camera-camera-photooutput.md)\* photoOutput | Pointer to the PhotoOutput instance that transfers the callback. |

### OH_PhotoOutput_OnFrameShutter()

```c
typedef void (*OH_PhotoOutput_OnFrameShutter)(Camera_PhotoOutput* photoOutput, Camera_FrameShutterInfo* info)
```

**Description**

Defines the callback defined in the [PhotoOutput_Callbacks](capi-oh-camera-photooutput-callbacks.md) struct and used to report frame shutter events.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_PhotoOutput](capi-oh-camera-camera-photooutput.md)\* photoOutput | Pointer to the PhotoOutput instance that transfers the callback. |
| Camera_FrameShutterInfo\* info | Pointer to the frame shutter information. |

### OH_PhotoOutput_OnFrameEnd()

```c
typedef void (*OH_PhotoOutput_OnFrameEnd)(Camera_PhotoOutput* photoOutput, int32_t frameCount)
```

**Description**

Defines the callback defined in the [PhotoOutput_Callbacks](capi-oh-camera-photooutput-callbacks.md) struct and used to report photo output frame end events.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_PhotoOutput](capi-oh-camera-camera-photooutput.md)\* photoOutput | Pointer to the PhotoOutput instance that transfers the callback. |
| int32_t frameCount | Number of frames to be included in the callback. |

### OH_PhotoOutput_OnError()

```c
typedef void (*OH_PhotoOutput_OnError)(Camera_PhotoOutput* photoOutput, Camera_ErrorCode errorCode)
```

**Description**

Defines the callback defined in the [PhotoOutput_Callbacks](capi-oh-camera-photooutput-callbacks.md) struct and used to report photo output errors.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_PhotoOutput](capi-oh-camera-camera-photooutput.md)\* photoOutput | Pointer to the PhotoOutput instance that transfers the callback. |
| Camera_ErrorCode errorCode | Error code reported during photo output. |

**Reference**:

CAMERA_SERVICE_FATAL_ERROR


### OH_PhotoOutput_CaptureEnd()

```c
typedef void (*OH_PhotoOutput_CaptureEnd)(Camera_PhotoOutput* photoOutput, int32_t frameCount)
```

**Description**

Defines the callback invoked when the capture ends.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_PhotoOutput](capi-oh-camera-camera-photooutput.md)\* photoOutput | Pointer to the PhotoOutput instance that transfers the callback. |
| int32_t frameCount | Number of frames to be included in the callback. |

### OH_PhotoOutput_CaptureStartWithInfo()

```c
typedef void (*OH_PhotoOutput_CaptureStartWithInfo)(Camera_PhotoOutput* photoOutput, Camera_CaptureStartInfo* Info)
```

**Description**

Defines the callback invoked when the capture starts.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_PhotoOutput](capi-oh-camera-camera-photooutput.md)\* photoOutput | Pointer to the PhotoOutput instance that transfers the callback. |
| info | the {@link Camera_CaptureStartInfo} which is delivered by the callback. |

### OH_PhotoOutput_OnFrameShutterEnd()

```c
typedef void (*OH_PhotoOutput_OnFrameShutterEnd)(Camera_PhotoOutput* photoOutput, Camera_FrameShutterInfo* Info)
```

**Description**

Defines the callback invoked when frame shutter ends.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_PhotoOutput](capi-oh-camera-camera-photooutput.md)\* photoOutput | Pointer to the PhotoOutput instance that transfers the callback. |
| info | the {@link Camera_CaptureStartInfo} which is delivered by the callback. |

### OH_PhotoOutput_CaptureReady()

```c
typedef void (*OH_PhotoOutput_CaptureReady)(Camera_PhotoOutput* photoOutput)
```

**Description**

Defines the callback invoked when the camera is ready to take photos. When the callback is received, the next capture can be performed.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_PhotoOutput](capi-oh-camera-camera-photooutput.md)\* photoOutput | Pointer to the PhotoOutput instance that transfers the callback. |

### OH_PhotoOutput_EstimatedCaptureDuration()

```c
typedef void (*OH_PhotoOutput_EstimatedCaptureDuration)(Camera_PhotoOutput* photoOutput, int64_t duration)
```

**Description**

Defines the callback for the estimated capture duration.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_PhotoOutput](capi-oh-camera-camera-photooutput.md)\* photoOutput | Pointer to the PhotoOutput instance that transfers the callback. |
| int64_t duration | Estimated capture duration passed by the callback, measured in milliseconds. |

### OH_PhotoOutput_PhotoAvailable()

```c
typedef void (*OH_PhotoOutput_PhotoAvailable)(Camera_PhotoOutput* photoOutput, OH_PhotoNative* photo)
```

**Description**

Defines the callback invoked when a high-resolution photo is available.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_PhotoOutput](capi-oh-camera-camera-photooutput.md)\* photoOutput | Pointer to the PhotoOutput instance that transfers the callback. |
| OH_PhotoNative\* photo | Pointer to OH_PhotoNative passed by the callback. |

### OH_PhotoOutput_PhotoAssetAvailable()

```c
typedef void (*OH_PhotoOutput_PhotoAssetAvailable)(Camera_PhotoOutput* photoOutput, OH_MediaAsset* photoAsset)
```

**Description**

Defines the callback invoked when a photo asset is available.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_PhotoOutput](capi-oh-camera-camera-photooutput.md)\* photoOutput | Pointer to the PhotoOutput instance that transfers the callback. |
| OH_MediaAsset\* photoAsset | Pointer to the media asset passed by the callback. |

### OH_PhotoOutput_RegisterCallback()

```c
Camera_ErrorCode OH_PhotoOutput_RegisterCallback(Camera_PhotoOutput* photoOutput, PhotoOutput_Callbacks* callback)
```

**Description**

Registers a callback to listen for photo output events.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_PhotoOutput](capi-oh-camera-camera-photooutput.md)* photoOutput | Pointer to the target PhotoOutput instance. |
| [PhotoOutput_Callbacks](capi-oh-camera-photooutput-callbacks.md)* callback | Pointer to the target callback. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_PhotoOutput_UnregisterCallback()

```c
Camera_ErrorCode OH_PhotoOutput_UnregisterCallback(Camera_PhotoOutput* photoOutput, PhotoOutput_Callbacks* callback)
```

**Description**

Unregisters the callback used to listen for photo output events.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_PhotoOutput](capi-oh-camera-camera-photooutput.md)* photoOutput | Pointer to the target PhotoOutput instance. |
| [PhotoOutput_Callbacks](capi-oh-camera-photooutput-callbacks.md)* callback | Pointer to the target callback. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_PhotoOutput_RegisterCaptureStartWithInfoCallback()

```c
Camera_ErrorCode OH_PhotoOutput_RegisterCaptureStartWithInfoCallback(Camera_PhotoOutput* photoOutput, OH_PhotoOutput_CaptureStartWithInfo callback)
```

**Description**

Registers a callback to listen for capture start events.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_PhotoOutput](capi-oh-camera-camera-photooutput.md)* photoOutput | Pointer to the target PhotoOutput instance. |
| [OH_PhotoOutput_CaptureStartWithInfo](capi-photo-output-h.md#oh_photooutput_capturestartwithinfo) callback | Target callback. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_PhotoOutput_GetPhotoRotation()

```c
Camera_ErrorCode OH_PhotoOutput_GetPhotoRotation(Camera_PhotoOutput* photoOutput, int deviceDegree, Camera_ImageRotation* imageRotation)
```

**Description**

Obtains the photo rotation angle.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_PhotoOutput](capi-oh-camera-camera-photooutput.md)* photoOutput | Pointer to the target PhotoOutput instance. |
| int deviceDegree | Rotation angle of the device. |
| Camera_ImageRotation* imageRotation | Pointer to the rotation angle of the photo. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.  CAMERA_SERVICE_FATAL_ERROR: The camera service is abnormal. |

### OH_PhotoOutput_GetPhotoRotationWithoutDeviceDegree()

```c
Camera_ErrorCode OH_PhotoOutput_GetPhotoRotationWithoutDeviceDegree(Camera_PhotoOutput* photoOutput, Camera_ImageRotation* imageRotation)
```

**Description**

Obtains the photo rotation angle.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_PhotoOutput](capi-oh-camera-camera-photooutput.md)* photoOutput | Pointer to the target PhotoOutput instance. |
| Camera_ImageRotation* imageRotation | Pointer to the rotation angle of the photo. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SERVICE_FATAL_ERROR: The camera service is abnormal. |

### OH_PhotoOutput_UnregisterCaptureStartWithInfoCallback()

```c
Camera_ErrorCode OH_PhotoOutput_UnregisterCaptureStartWithInfoCallback(Camera_PhotoOutput* photoOutput, OH_PhotoOutput_CaptureStartWithInfo callback)
```

**Description**

Unregisters the callback used to listen for capture start events.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_PhotoOutput](capi-oh-camera-camera-photooutput.md)* photoOutput | Pointer to the target PhotoOutput instance. |
| [OH_PhotoOutput_CaptureStartWithInfo](capi-photo-output-h.md#oh_photooutput_capturestartwithinfo) callback | Target callback. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_PhotoOutput_RegisterCaptureEndCallback()

```c
Camera_ErrorCode OH_PhotoOutput_RegisterCaptureEndCallback(Camera_PhotoOutput* photoOutput, OH_PhotoOutput_CaptureEnd callback)
```

**Description**

Registers a callback to listen for capture end events.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_PhotoOutput](capi-oh-camera-camera-photooutput.md)* photoOutput | Pointer to the target PhotoOutput instance. |
| [OH_PhotoOutput_CaptureEnd](capi-photo-output-h.md#oh_photooutput_captureend) callback | Target callback. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_PhotoOutput_UnregisterCaptureEndCallback()

```c
Camera_ErrorCode OH_PhotoOutput_UnregisterCaptureEndCallback(Camera_PhotoOutput* photoOutput, OH_PhotoOutput_CaptureEnd callback)
```

**Description**

Unregisters the callback used to listen for capture end events.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_PhotoOutput](capi-oh-camera-camera-photooutput.md)* photoOutput | Pointer to the target PhotoOutput instance. |
| [OH_PhotoOutput_CaptureEnd](capi-photo-output-h.md#oh_photooutput_captureend) callback | Target callback. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_PhotoOutput_RegisterFrameShutterEndCallback()

```c
Camera_ErrorCode OH_PhotoOutput_RegisterFrameShutterEndCallback(Camera_PhotoOutput* photoOutput, OH_PhotoOutput_OnFrameShutterEnd callback)
```

**Description**

Registers a callback to listen for frame shutter end events.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_PhotoOutput](capi-oh-camera-camera-photooutput.md)* photoOutput | Pointer to the target PhotoOutput instance. |
| [OH_PhotoOutput_OnFrameShutterEnd](capi-photo-output-h.md#oh_photooutput_onframeshutterend) callback | Target callback. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_PhotoOutput_UnregisterFrameShutterEndCallback()

```c
Camera_ErrorCode OH_PhotoOutput_UnregisterFrameShutterEndCallback(Camera_PhotoOutput* photoOutput, OH_PhotoOutput_OnFrameShutterEnd callback)
```

**Description**

Unregisters the callback used to listen for frame shutter end events.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_PhotoOutput](capi-oh-camera-camera-photooutput.md)* photoOutput | Pointer to the target PhotoOutput instance. |
| [OH_PhotoOutput_OnFrameShutterEnd](capi-photo-output-h.md#oh_photooutput_onframeshutterend) callback | Target callback. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_PhotoOutput_RegisterCaptureReadyCallback()

```c
Camera_ErrorCode OH_PhotoOutput_RegisterCaptureReadyCallback(Camera_PhotoOutput* photoOutput, OH_PhotoOutput_CaptureReady callback)
```

**Description**

Registers a callback to listen for camera ready events. When the callback is received, the next capture can be performed.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_PhotoOutput](capi-oh-camera-camera-photooutput.md)* photoOutput | Pointer to the target PhotoOutput instance. |
| [OH_PhotoOutput_CaptureReady](capi-photo-output-h.md#oh_photooutput_captureready) callback | Target callback. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_PhotoOutput_UnregisterCaptureReadyCallback()

```c
Camera_ErrorCode OH_PhotoOutput_UnregisterCaptureReadyCallback(Camera_PhotoOutput* photoOutput, OH_PhotoOutput_CaptureReady callback)
```

**Description**

Unregisters the callback used to listen for camera ready events.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_PhotoOutput](capi-oh-camera-camera-photooutput.md)* photoOutput | Pointer to the target PhotoOutput instance. |
| [OH_PhotoOutput_CaptureReady](capi-photo-output-h.md#oh_photooutput_captureready) callback | Target callback. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_PhotoOutput_RegisterEstimatedCaptureDurationCallback()

```c
Camera_ErrorCode OH_PhotoOutput_RegisterEstimatedCaptureDurationCallback(Camera_PhotoOutput* photoOutput, OH_PhotoOutput_EstimatedCaptureDuration callback)
```

**Description**

Registers a callback to listen for estimated capture duration events.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_PhotoOutput](capi-oh-camera-camera-photooutput.md)* photoOutput | Pointer to the target PhotoOutput instance. |
| [OH_PhotoOutput_EstimatedCaptureDuration](capi-photo-output-h.md#oh_photooutput_estimatedcaptureduration) callback | Target callback. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_PhotoOutput_UnregisterEstimatedCaptureDurationCallback()

```c
Camera_ErrorCode OH_PhotoOutput_UnregisterEstimatedCaptureDurationCallback(Camera_PhotoOutput* photoOutput, OH_PhotoOutput_EstimatedCaptureDuration callback)
```

**Description**

Unregisters the callback used to listen for estimated capture duration events.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_PhotoOutput](capi-oh-camera-camera-photooutput.md)* photoOutput | Pointer to the target PhotoOutput instance. |
| [OH_PhotoOutput_EstimatedCaptureDuration](capi-photo-output-h.md#oh_photooutput_estimatedcaptureduration) callback | Target callback. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_PhotoOutput_RegisterPhotoAvailableCallback()

```c
Camera_ErrorCode OH_PhotoOutput_RegisterPhotoAvailableCallback(Camera_PhotoOutput* photoOutput, OH_PhotoOutput_PhotoAvailable callback)
```

**Description**

Registers a callback to listen for photo availability events.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_PhotoOutput](capi-oh-camera-camera-photooutput.md)* photoOutput | Pointer to the target PhotoOutput instance. |
| [OH_PhotoOutput_PhotoAvailable](capi-photo-output-h.md#oh_photooutput_photoavailable) callback | Target callback. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SERVICE_FATAL_ERROR: The camera service is abnormal. |

### OH_PhotoOutput_UnregisterPhotoAvailableCallback()

```c
Camera_ErrorCode OH_PhotoOutput_UnregisterPhotoAvailableCallback(Camera_PhotoOutput* photoOutput, OH_PhotoOutput_PhotoAvailable callback)
```

**Description**

Unregisters the callback used to listen for photo availability events.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_PhotoOutput](capi-oh-camera-camera-photooutput.md)* photoOutput | Pointer to the target PhotoOutput instance. |
| [OH_PhotoOutput_PhotoAvailable](capi-photo-output-h.md#oh_photooutput_photoavailable) callback | Target callback. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SERVICE_FATAL_ERROR: The camera service is abnormal. |

### OH_PhotoOutput_RegisterPhotoAssetAvailableCallback()

```c
Camera_ErrorCode OH_PhotoOutput_RegisterPhotoAssetAvailableCallback(Camera_PhotoOutput* photoOutput, OH_PhotoOutput_PhotoAssetAvailable callback)
```

**Description**

Registers a callback to listen for photo asset availability events.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_PhotoOutput](capi-oh-camera-camera-photooutput.md)* photoOutput | Pointer to the target PhotoOutput instance. |
| [OH_PhotoOutput_PhotoAssetAvailable](capi-photo-output-h.md#oh_photooutput_photoassetavailable) callback | Target callback. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_PhotoOutput_UnregisterPhotoAssetAvailableCallback()

```c
Camera_ErrorCode OH_PhotoOutput_UnregisterPhotoAssetAvailableCallback(Camera_PhotoOutput* photoOutput, OH_PhotoOutput_PhotoAssetAvailable callback)
```

**Description**

Unregisters the callback used to listen for photo asset availability events.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_PhotoOutput](capi-oh-camera-camera-photooutput.md)* photoOutput | Pointer to the target PhotoOutput instance. |
| [OH_PhotoOutput_PhotoAssetAvailable](capi-photo-output-h.md#oh_photooutput_photoassetavailable) callback | Target callback. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_PhotoOutput_Capture()

```c
Camera_ErrorCode OH_PhotoOutput_Capture(Camera_PhotoOutput* photoOutput)
```

**Description**

Captures a photo. This function must be called in prior to {@link OH_PreviewOutput_Release}. Otherwise, photo capture fails.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_PhotoOutput](capi-oh-camera-camera-photooutput.md)* photoOutput | Pointer to the target PhotoOutput instance. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SESSION_NOT_RUNNING: The capture session is not running.      <br>CAMERA_SERVICE_FATAL_ERROR: The camera service is abnormal. |

### OH_PhotoOutput_Capture_WithCaptureSetting()

```c
Camera_ErrorCode OH_PhotoOutput_Capture_WithCaptureSetting(Camera_PhotoOutput* photoOutput, Camera_PhotoCaptureSetting setting)
```

**Description**

Captures a photo with photographing parameters.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_PhotoOutput](capi-oh-camera-camera-photooutput.md)* photoOutput | Pointer to the target PhotoOutput instance. |
| Camera_PhotoCaptureSetting setting | Photographing parameters, which are defined in the {@link Camera_PhotoCaptureSetting} struct. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SESSION_NOT_RUNNING: The capture session is not running.      <br>CAMERA_SERVICE_FATAL_ERROR: The camera service is abnormal. |

### OH_PhotoOutput_Release()

```c
Camera_ErrorCode OH_PhotoOutput_Release(Camera_PhotoOutput* photoOutput)
```

**Description**

Releases a PhotoOutput instance.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_PhotoOutput](capi-oh-camera-camera-photooutput.md)* photoOutput | Pointer to the target PhotoOutput instance. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SERVICE_FATAL_ERROR: The camera service is abnormal. |

### OH_PhotoOutput_IsMirrorSupported()

```c
Camera_ErrorCode OH_PhotoOutput_IsMirrorSupported(Camera_PhotoOutput* photoOutput, bool* isSupported)
```

**Description**

Checks whether mirroring is supported.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_PhotoOutput](capi-oh-camera-camera-photooutput.md)* photoOutput | Pointer to the target PhotoOutput instance. |
| bool* isSupported | Pointer to the check result for the support of mirroring. **true** if supported, **false**<br>otherwise. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SERVICE_FATAL_ERROR: The camera service is abnormal. |

### OH_PhotoOutput_EnableMirror()

```c
Camera_ErrorCode OH_PhotoOutput_EnableMirror(Camera_PhotoOutput* photoOutput, bool enabled)
```

**Description**

Enables dynamic photo capture.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_PhotoOutput](capi-oh-camera-camera-photooutput.md)* photoOutput | Pointer to the target PhotoOutput instance. |
| bool enabled | Whether to enable or disable dynamic photo capture. **true** to enable, **false** otherwise. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SERVICE_FATAL_ERROR: The camera service is abnormal. |

### OH_PhotoOutput_GetActiveProfile()

```c
Camera_ErrorCode OH_PhotoOutput_GetActiveProfile(Camera_PhotoOutput* photoOutput, Camera_Profile** profile)
```

**Description**

Obtains the profile of a PhotoOutput instance.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_PhotoOutput](capi-oh-camera-camera-photooutput.md)* photoOutput | Pointer to the target PhotoOutput instance. |
| Camera_Profile** profile | Double pointer to the photo output profile obtained. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SERVICE_FATAL_ERROR: The camera service is abnormal. |

### OH_PhotoOutput_DeleteProfile()

```c
Camera_ErrorCode OH_PhotoOutput_DeleteProfile(Camera_Profile* profile)
```

**Description**

Deletes the profile of a PhotoOutput instance.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| Camera_Profile* profile | Pointer to the target PhotoOutput instance. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_PhotoOutput_IsMovingPhotoSupported()

```c
Camera_ErrorCode OH_PhotoOutput_IsMovingPhotoSupported(Camera_PhotoOutput* photoOutput, bool* isSupported)
```

**Description**

Checks whether moving photos are supported.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_PhotoOutput](capi-oh-camera-camera-photooutput.md)* photoOutput | Pointer to the target PhotoOutput instance. |
| bool* isSupported | Pointer to the check result for the support of moving photos. **true** if supported, **false**<br>otherwise. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SERVICE_FATAL_ERROR: The camera service is abnormal. |

### OH_PhotoOutput_EnableMovingPhoto()

```c
Camera_ErrorCode OH_PhotoOutput_EnableMovingPhoto(Camera_PhotoOutput* photoOutput, bool enabled)
```

**Description**

Enables or disables moving photos.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_PhotoOutput](capi-oh-camera-camera-photooutput.md)* photoOutput | Pointer to the target PhotoOutput instance. |
| bool enabled | Whether to enable moving photos. **true** to enable, **false** otherwise. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SERVICE_FATAL_ERROR: The camera service is abnormal. |

### OH_PhotoOutput_IsPhotoQualityPrioritizationSupported()

```c
Camera_ErrorCode OH_PhotoOutput_IsPhotoQualityPrioritizationSupported(Camera_PhotoOutput* photoOutput, Camera_PhotoQualityPrioritization qualityPrioritization, bool* isSupported)
```

**Description**

Checks whether the specified photo quality prioritization strategy is supported.

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_PhotoOutput](capi-oh-camera-camera-photooutput.md)* photoOutput | Pointer to the target PhotoOutput instance. |
| Camera_PhotoQualityPrioritization qualityPrioritization | Photo quality prioritization strategy. |
| bool* isSupported | Pointer to the check result for the support of the specified photo quality prioritization strategy. **true** if supported, **false** otherwise. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SERVICE_FATAL_ERROR: The camera service is abnormal. |

### OH_PhotoOutput_SetPhotoQualityPrioritization()

```c
Camera_ErrorCode OH_PhotoOutput_SetPhotoQualityPrioritization(Camera_PhotoOutput* photoOutput, Camera_PhotoQualityPrioritization qualityPrioritization)
```

**Description**

Sets the photo quality prioritization strategy.

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_PhotoOutput](capi-oh-camera-camera-photooutput.md)* photoOutput | Pointer to the target PhotoOutput instance. |
| Camera_PhotoQualityPrioritization qualityPrioritization | Photo quality prioritization strategy. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_OPERATION_NOT_ALLOWED: The operation is not allowed.      <br>CAMERA_SERVICE_FATAL_ERROR: The camera service is abnormal. |

### OH_PhotoOutput_Capture_WithCaptureSettingExt()

```c
Camera_ErrorCode OH_PhotoOutput_Capture_WithCaptureSettingExt(Camera_PhotoOutput* photoOutput, OH_Camera_PhotoCaptureSettingExt* setting)
```

**Description**

Captures a photo with photo capture setting extension.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_PhotoOutput](capi-oh-camera-camera-photooutput.md)* photoOutput | Pointer to the target PhotoOutput instance. |
| [OH_Camera_PhotoCaptureSettingExt](capi-oh-camera-oh-camera-photocapturesettingext.md)* setting | Pointer to the target OH_Camera_PhotoCaptureSettingExt instance.. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SESSION_NOT_RUNNING: The capture session is not running.      <br>CAMERA_SERVICE_FATAL_ERROR: The camera service is abnormal. |

### OH_PhotoOutput_CreatePhotoCaptureSettingExt()

```c
Camera_ErrorCode OH_PhotoOutput_CreatePhotoCaptureSettingExt(Camera_PhotoOutput* photoOutput, OH_Camera_PhotoCaptureSettingExt** setting)
```

**Description**

Creates a **OH_Camera_PhotoCaptureSettingExt** instance. Release the photo capture setting ext memory by calling [OH_PhotoOutput_DestroyPhotoCaptureSettingExt](capi-photo-output-h.md#oh_photooutput_destroyphotocapturesettingext).

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_PhotoOutput](capi-oh-camera-camera-photooutput.md)* photoOutput | Pointer to the target PhotoOutput instance. |
| [OH_Camera_PhotoCaptureSettingExt](capi-oh-camera-oh-camera-photocapturesettingext.md)** setting | Double pointer to the **OH_Camera_PhotoCaptureSettingExt** instance created, if the function is successfully called. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SERVICE_FATAL_ERROR: The camera service is abnormal. |

### OH_PhotoCaptureSettingExt_SetCompressionQuality()

```c
Camera_ErrorCode OH_PhotoCaptureSettingExt_SetCompressionQuality(OH_Camera_PhotoCaptureSettingExt* photoCaptureSettingExt, uint8_t compressionQuality)
```

**Description**

Sets the image compression quality for the photo capture extension configuration.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Camera_PhotoCaptureSettingExt](capi-oh-camera-oh-camera-photocapturesettingext.md)* photoCaptureSettingExt | Pointer to the photo capture extension settings object. |
| uint8_t compressionQuality | Image compression quality. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | <ul>          <li>CAMERA_OK: The operation is successful.</li>          <li>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.</li>          </ul> |

### OH_PhotoCaptureSettingExt_SetImageRotation()

```c
Camera_ErrorCode OH_PhotoCaptureSettingExt_SetImageRotation(OH_Camera_PhotoCaptureSettingExt* photoCaptureSettingExt, Camera_ImageRotation rotation)
```

**Description**

Sets the image rotation for the photo capture extension configuration.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Camera_PhotoCaptureSettingExt](capi-oh-camera-oh-camera-photocapturesettingext.md)* photoCaptureSettingExt | Pointer to the photo capture extension settings object. |
| Camera_ImageRotation rotation | Image rotation, defined in the Camera_ImageRotation enumeration. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | <ul>          <li>CAMERA_OK: The operation is successful.</li>          <li>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.</li>          </ul> |

### OH_PhotoCaptureSettingExt_SetMirror()

```c
Camera_ErrorCode OH_PhotoCaptureSettingExt_SetMirror(OH_Camera_PhotoCaptureSettingExt* photoCaptureSettingExt, bool mirror)
```

**Description**

Sets the image mirror for the photo capture extension configuration.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Camera_PhotoCaptureSettingExt](capi-oh-camera-oh-camera-photocapturesettingext.md)* photoCaptureSettingExt | Pointer to the photo capture extension settings object. |
| bool mirror | The switch of the mirror effect. **true** for enabled, **false** for disabled. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | <ul>          <li>CAMERA_OK: The operation is successful.</li>          <li>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.</li>          </ul> |

### OH_PhotoOutput_DestroyPhotoCaptureSettingExt()

```c
Camera_ErrorCode OH_PhotoOutput_DestroyPhotoCaptureSettingExt(OH_Camera_PhotoCaptureSettingExt* setting)
```

**Description**

Destroy the photo capture setting ext.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Camera_PhotoCaptureSettingExt](capi-oh-camera-oh-camera-photocapturesettingext.md)* setting | The target [OH_Camera_PhotoCaptureSettingExt](capi-oh-camera-oh-camera-photocapturesettingext.md) list to be destoryed if the method call succeeds. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_PhotoCaptureSettingExt_SetLocation()

```c
Camera_ErrorCode OH_PhotoCaptureSettingExt_SetLocation(OH_Camera_PhotoCaptureSettingExt* photoCaptureSettingExt, Camera_Location location)
```

**Description**

Sets the image location for the photo capture extension configuration.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Camera_PhotoCaptureSettingExt](capi-oh-camera-oh-camera-photocapturesettingext.md)* photoCaptureSettingExt | Pointer to the photo capture extension settings object. |
| Camera_Location location | Image location, defined in the Camera_Location enumeration. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | <ul>          <li>CAMERA_OK: The operation is successful.</li>          <li>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.</li>          </ul> |

### OH_PhotoOutput_EnableAutoExtendedGainmapDelivery()

```c
Camera_ErrorCode OH_PhotoOutput_EnableAutoExtendedGainmapDelivery(Camera_PhotoOutput* photoOutput, bool enabled)
```

**Description**

Enables auto extended gainmap delivery.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_PhotoOutput](capi-oh-camera-camera-photooutput.md)* photoOutput | Pointer to the target PhotoOutput instance. |
| bool enabled | Whether to enable or disable auto extended gainmap delivery. **true** to enable, **false** otherwise. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful. <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. <br>CAMERA_OPERATION_NOT_ALLOWED: The operation is not allowed. <br>CAMERA_SESSION_NOT_CONFIG: The capture session is not configured. <br>CAMERA_SERVICE_FATAL_ERROR: The camera service is abnormal. |

### OH_PhotoOutput_IsAutoExtendedGainmapDeliverySupported()

```c
bool OH_PhotoOutput_IsAutoExtendedGainmapDeliverySupported(const Camera_PhotoOutput* photoOutput)
```

**Description**

Checks whether the auto extended gainmap delivery is supported.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const Camera_PhotoOutput](capi-oh-camera-camera-photooutput.md)* photoOutput | Pointer to the target PhotoOutput instance. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | true if supported, false otherwise. |


