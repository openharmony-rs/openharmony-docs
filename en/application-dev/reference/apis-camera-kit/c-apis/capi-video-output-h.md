# video_output.h

## Overview

The file declares the video output concepts.

**Library**: libohcamera.so

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 11

**Related module**: [OH_Camera](capi-oh-camera.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [VideoOutput_Callbacks](capi-oh-camera-videooutput-callbacks.md) | VideoOutput_Callbacks | The struct describes the callbacks related to video output. |
| [Camera_VideoOutput](capi-oh-camera-camera-videooutput.md) | Camera_VideoOutput | The struct describes the video output object. |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef void (\*OH_VideoOutput_OnFrameStart)(Camera_VideoOutput* videoOutput)](#oh_videooutput_onframestart) | OH_VideoOutput_OnFrameStart | Defines the callback defined in the [VideoOutput_Callbacks](capi-oh-camera-videooutput-callbacks.md) struct and used to report video output frame start events. |
| [typedef void (\*OH_VideoOutput_OnFrameEnd)(Camera_VideoOutput* videoOutput, int32_t frameCount)](#oh_videooutput_onframeend) | OH_VideoOutput_OnFrameEnd | Defines the callback defined in the [VideoOutput_Callbacks](capi-oh-camera-videooutput-callbacks.md) struct and used to report video output frame end events. |
| [typedef void (\*OH_VideoOutput_OnError)(Camera_VideoOutput* videoOutput, Camera_ErrorCode errorCode)](#oh_videooutput_onerror) | OH_VideoOutput_OnError | Defines the callback defined in the [VideoOutput_Callbacks](capi-oh-camera-videooutput-callbacks.md) struct and used to report video output errors. |
| [Camera_ErrorCode OH_VideoOutput_RegisterCallback(Camera_VideoOutput* videoOutput, VideoOutput_Callbacks* callback)](#oh_videooutput_registercallback) | - | Registers a callback to listen for video output events. |
| [Camera_ErrorCode OH_VideoOutput_UnregisterCallback(Camera_VideoOutput* videoOutput, VideoOutput_Callbacks* callback)](#oh_videooutput_unregistercallback) | - | Unregisters the callback used to listen for video output events. |
| [Camera_ErrorCode OH_VideoOutput_Start(Camera_VideoOutput* videoOutput)](#oh_videooutput_start) | - | Starts video output. |
| [Camera_ErrorCode OH_VideoOutput_Stop(Camera_VideoOutput* videoOutput)](#oh_videooutput_stop) | - | Stops video output. |
| [Camera_ErrorCode OH_VideoOutput_Release(Camera_VideoOutput* videoOutput)](#oh_videooutput_release) | - | Releases a VideoOutput instance. |
| [Camera_ErrorCode OH_VideoOutput_GetActiveProfile(Camera_VideoOutput* videoOutput, Camera_VideoProfile** profile)](#oh_videooutput_getactiveprofile) | - | Obtains the profile of a VideoOutput instance. |
| [Camera_ErrorCode OH_VideoOutput_DeleteProfile(Camera_VideoProfile* profile)](#oh_videooutput_deleteprofile) | - | Deletes the profile of a VideoOutput instance. |
| [Camera_ErrorCode OH_VideoOutput_IsMirrorSupported(Camera_VideoOutput* videoOutput, bool* isSupported)](#oh_videooutput_ismirrorsupported) | - | Check whether mirror mode is supported for videoOutput |
| [Camera_ErrorCode OH_VideoOutput_EnableMirror(Camera_VideoOutput* videoOutput, bool mirrorMode)](#oh_videooutput_enablemirror) | - | Enable or disable mirror mode for videoOutput |
| [Camera_ErrorCode OH_VideoOutput_GetVideoRotation(Camera_VideoOutput* videoOutput, int deviceDegree, Camera_ImageRotation* imageRotation)](#oh_videooutput_getvideorotation) | - | Obtains the rotation angle of a video. |
| [Camera_ErrorCode OH_VideoOutput_GetVideoRotationWithoutDeviceDegree(Camera_VideoOutput* videoOutput, Camera_ImageRotation* imageRotation)](#oh_videooutput_getvideorotationwithoutdevicedegree) | - | Obtains the rotation angle of a video. |
| [Camera_ErrorCode OH_VideoOutput_GetSupportedFrameRates(Camera_VideoOutput* videoOutput, Camera_FrameRateRange** frameRateRange, uint32_t* size)](#oh_videooutput_getsupportedframerates) | - | Obtains the list of frame rates supported by a VideoOutput instance. |
| [Camera_ErrorCode OH_VideoOutput_DeleteFrameRates(Camera_VideoOutput* videoOutput, Camera_FrameRateRange* frameRateRange)](#oh_videooutput_deleteframerates) | - | Deletes the frame rate list. |
| [Camera_ErrorCode OH_VideoOutput_SetFrameRate(Camera_VideoOutput* videoOutput, int32_t minFps, int32_t maxFps)](#oh_videooutput_setframerate) | - | Sets the frame rates for a VideoOutput instance. |
| [Camera_ErrorCode OH_VideoOutput_GetActiveFrameRate(Camera_VideoOutput* videoOutput, Camera_FrameRateRange* frameRateRange)](#oh_videooutput_getactiveframerate) | - | Obtains the active frame rates of a VideoOutput instance. |

### Variable

| Name | Description |
| -- | -- |
| void (*OH_VideoOutput_OnFrameStart)(Camera_VideoOutput* videoOutput) | Defines the callback defined in the [VideoOutput_Callbacks](capi-oh-camera-videooutput-callbacks.md) struct and used to report video output frame start events.<br>**Since**: 11 |
| void (*OH_VideoOutput_OnFrameEnd)(Camera_VideoOutput* videoOutput, int32_t frameCount) | Defines the callback defined in the [VideoOutput_Callbacks](capi-oh-camera-videooutput-callbacks.md) struct and used to report video output frame end events.<br>**Since**: 11 |
| void (*OH_VideoOutput_OnError)(Camera_VideoOutput* videoOutput, Camera_ErrorCode errorCode) | Defines the callback defined in the [VideoOutput_Callbacks](capi-oh-camera-videooutput-callbacks.md) struct and used to report video output errors.<br>**Since**: 11 |

## Function description

### OH_VideoOutput_OnFrameStart()

```c
typedef void (*OH_VideoOutput_OnFrameStart)(Camera_VideoOutput* videoOutput)
```

**Description**

Defines the callback defined in the [VideoOutput_Callbacks](capi-oh-camera-videooutput-callbacks.md) struct and used to report video output frame start events.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_VideoOutput](capi-oh-camera-camera-videooutput.md)\* videoOutput | Pointer to the VideoOutput instance that transfers the callback. |

### OH_VideoOutput_OnFrameEnd()

```c
typedef void (*OH_VideoOutput_OnFrameEnd)(Camera_VideoOutput* videoOutput, int32_t frameCount)
```

**Description**

Defines the callback defined in the [VideoOutput_Callbacks](capi-oh-camera-videooutput-callbacks.md) struct and used to report video output frame end events.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_VideoOutput](capi-oh-camera-camera-videooutput.md)\* videoOutput | Pointer to the VideoOutput instance that transfers the callback. |
| int32_t frameCount | Number of frames to be included in the callback. |

### OH_VideoOutput_OnError()

```c
typedef void (*OH_VideoOutput_OnError)(Camera_VideoOutput* videoOutput, Camera_ErrorCode errorCode)
```

**Description**

Defines the callback defined in the [VideoOutput_Callbacks](capi-oh-camera-videooutput-callbacks.md) struct and used to report video output errors.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_VideoOutput](capi-oh-camera-camera-videooutput.md)\* videoOutput | Pointer to the VideoOutput instance that transfers the callback. |
| Camera_ErrorCode errorCode | Error code reported during video output. |

**Reference**:

CAMERA_SERVICE_FATAL_ERROR


### OH_VideoOutput_RegisterCallback()

```c
Camera_ErrorCode OH_VideoOutput_RegisterCallback(Camera_VideoOutput* videoOutput, VideoOutput_Callbacks* callback)
```

**Description**

Registers a callback to listen for video output events.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_VideoOutput](capi-oh-camera-camera-videooutput.md)* videoOutput | Pointer to the target VideoOutput instance. |
| [VideoOutput_Callbacks](capi-oh-camera-videooutput-callbacks.md)* callback | Pointer to the target callback. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_VideoOutput_UnregisterCallback()

```c
Camera_ErrorCode OH_VideoOutput_UnregisterCallback(Camera_VideoOutput* videoOutput, VideoOutput_Callbacks* callback)
```

**Description**

Unregisters the callback used to listen for video output events.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_VideoOutput](capi-oh-camera-camera-videooutput.md)* videoOutput | Pointer to the target VideoOutput instance. |
| [VideoOutput_Callbacks](capi-oh-camera-videooutput-callbacks.md)* callback | Pointer to the target callback. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_VideoOutput_Start()

```c
Camera_ErrorCode OH_VideoOutput_Start(Camera_VideoOutput* videoOutput)
```

**Description**

Starts video output.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_VideoOutput](capi-oh-camera-camera-videooutput.md)* videoOutput | Pointer to the VideoOutput instance to start. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SESSION_NOT_CONFIG: The capture session is not configured.      <br>CAMERA_SERVICE_FATAL_ERROR: The camera service is abnormal. |

### OH_VideoOutput_Stop()

```c
Camera_ErrorCode OH_VideoOutput_Stop(Camera_VideoOutput* videoOutput)
```

**Description**

Stops video output.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_VideoOutput](capi-oh-camera-camera-videooutput.md)* videoOutput | Pointer to the VideoOutput instance to stop. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SERVICE_FATAL_ERROR: The camera service is abnormal. |

### OH_VideoOutput_Release()

```c
Camera_ErrorCode OH_VideoOutput_Release(Camera_VideoOutput* videoOutput)
```

**Description**

Releases a VideoOutput instance.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_VideoOutput](capi-oh-camera-camera-videooutput.md)* videoOutput | Pointer to the VideoOutput instance to release. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SERVICE_FATAL_ERROR: The camera service is abnormal. |

### OH_VideoOutput_GetActiveProfile()

```c
Camera_ErrorCode OH_VideoOutput_GetActiveProfile(Camera_VideoOutput* videoOutput, Camera_VideoProfile** profile)
```

**Description**

Obtains the profile of a VideoOutput instance.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_VideoOutput](capi-oh-camera-camera-videooutput.md)* videoOutput | Pointer to the VideoOutput instance for which the profile is to be obtained. |
| Camera_VideoProfile** profile | Double pointer to the video output profile obtained. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SERVICE_FATAL_ERROR: The camera service is abnormal. |

### OH_VideoOutput_DeleteProfile()

```c
Camera_ErrorCode OH_VideoOutput_DeleteProfile(Camera_VideoProfile* profile)
```

**Description**

Deletes the profile of a VideoOutput instance.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| Camera_VideoProfile* profile | Pointer to the profile to delete. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_VideoOutput_IsMirrorSupported()

```c
Camera_ErrorCode OH_VideoOutput_IsMirrorSupported(Camera_VideoOutput* videoOutput, bool* isSupported)
```

**Description**

Check whether mirror mode is supported for videoOutput

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_VideoOutput](capi-oh-camera-camera-videooutput.md)* videoOutput | the [Camera_VideoOutput](capi-oh-camera-camera-videooutput.md) instance |
| bool* isSupported | the result of whether mirror mode supported. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | {@link #CAMERA_OK} if the method call succeeds.<br>        {@link #CAMERA_INVALID_ARGUMENT} if parameter missing or parameter type incorrect.<br>        {@link #CAMERA_SERVICE_FATAL_ERROR} if camera service fatal error. |

### OH_VideoOutput_EnableMirror()

```c
Camera_ErrorCode OH_VideoOutput_EnableMirror(Camera_VideoOutput* videoOutput, bool mirrorMode)
```

**Description**

Enable or disable mirror mode for videoOutput

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_VideoOutput](capi-oh-camera-camera-videooutput.md)* videoOutput | the [Camera_VideoOutput](capi-oh-camera-camera-videooutput.md) instance |
| bool mirrorMode | enable mirror mode if mirrorMode is TRUE, otherwise disable |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | {@link #CAMERA_OK} if the method call succeeds.<br>        {@link #CAMERA_INVALID_ARGUMENT} if parameter missing or parameter type incorrect.<br>        {@link #CAMERA_SERVICE_FATAL_ERROR} if camera service fatal error. |

### OH_VideoOutput_GetVideoRotation()

```c
Camera_ErrorCode OH_VideoOutput_GetVideoRotation(Camera_VideoOutput* videoOutput, int deviceDegree, Camera_ImageRotation* imageRotation)
```

**Description**

Obtains the rotation angle of a video.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_VideoOutput](capi-oh-camera-camera-videooutput.md)* videoOutput | Pointer to the target VideoOutput instance. |
| int deviceDegree | Clockwise rotation angle of the device relative to the natural direction (the charging port faces downward). |
| Camera_ImageRotation* imageRotation | Pointer to the rotation angle of the video output. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SERVICE_FATAL_ERROR: The camera service is abnormal. |

### OH_VideoOutput_GetVideoRotationWithoutDeviceDegree()

```c
Camera_ErrorCode OH_VideoOutput_GetVideoRotationWithoutDeviceDegree(Camera_VideoOutput* videoOutput, Camera_ImageRotation* imageRotation)
```

**Description**

Obtains the rotation angle of a video.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_VideoOutput](capi-oh-camera-camera-videooutput.md)* videoOutput | Pointer to the target VideoOutput instance. |
| Camera_ImageRotation* imageRotation | Pointer to the rotation angle of the video output. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SERVICE_FATAL_ERROR: The camera service is abnormal. |

### OH_VideoOutput_GetSupportedFrameRates()

```c
Camera_ErrorCode OH_VideoOutput_GetSupportedFrameRates(Camera_VideoOutput* videoOutput, Camera_FrameRateRange** frameRateRange, uint32_t* size)
```

**Description**

Obtains the list of frame rates supported by a VideoOutput instance.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_VideoOutput](capi-oh-camera-camera-videooutput.md)* videoOutput | Pointer to the target VideoOutput instance. |
| Camera_FrameRateRange** frameRateRange | Double pointer to the list of frame rates, if the function is successfully called. |
| uint32_t* size | Pointer to the size of the list of frame rates. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SERVICE_FATAL_ERROR: The camera service is abnormal. |

### OH_VideoOutput_DeleteFrameRates()

```c
Camera_ErrorCode OH_VideoOutput_DeleteFrameRates(Camera_VideoOutput* videoOutput, Camera_FrameRateRange* frameRateRange)
```

**Description**

Deletes the frame rate list.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_VideoOutput](capi-oh-camera-camera-videooutput.md)* videoOutput | Pointer to the target VideoOutput instance. |
| Camera_FrameRateRange* frameRateRange | Pointer to the list of frame rates to delete. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_VideoOutput_SetFrameRate()

```c
Camera_ErrorCode OH_VideoOutput_SetFrameRate(Camera_VideoOutput* videoOutput, int32_t minFps, int32_t maxFps)
```

**Description**

Sets the frame rates for a VideoOutput instance.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_VideoOutput](capi-oh-camera-camera-videooutput.md)* videoOutput | Pointer to the VideoOutput instance for which the frame rates are to be set. |
| int32_t minFps | Minimum frame rate. |
| int32_t maxFps | Maximum frame rate. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect. |

### OH_VideoOutput_GetActiveFrameRate()

```c
Camera_ErrorCode OH_VideoOutput_GetActiveFrameRate(Camera_VideoOutput* videoOutput, Camera_FrameRateRange* frameRateRange)
```

**Description**

Obtains the active frame rates of a VideoOutput instance.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Camera_VideoOutput](capi-oh-camera-camera-videooutput.md)* videoOutput | Pointer to the target VideoOutput instance. |
| Camera_FrameRateRange* frameRateRange | Pointer to the frame rate range, if the function is successfully called. |

**Returns**:

| Type | Description |
| -- | -- |
| Camera_ErrorCode | CAMERA_OK: The operation is successful.      <br>CAMERA_INVALID_ARGUMENT: A parameter is missing or the parameter type is incorrect.      <br>CAMERA_SERVICE_FATAL_ERROR: The camera service is abnormal. |


