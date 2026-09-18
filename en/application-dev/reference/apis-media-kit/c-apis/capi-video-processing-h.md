# video_processing.h

## Overview

Declare video processing functions.<br> Provides SDR content processing for videos, including color space conversion, metadata generation and video scaling.

**Library**: libvideo_processing.so

**System capability**: SystemCapability.Multimedia.VideoProcessingEngine

**Since**: 12

**Related module**: [VideoProcessing](capi-videoprocessing.md)

## Summary

### Function

| Name | Description |
| -- | -- |
| [VideoProcessing_ErrorCode OH_VideoProcessing_InitializeEnvironment(void)](#oh_videoprocessing_initializeenvironment) | Initialize global environment for video processing.<br> This function is optional. Typically, this function is called once when the host process is started to initialize the global environment for video processing, which can reduce the time of [OH_VideoProcessing_Create](capi-video-processing-h.md#oh_videoprocessing_create). To deinitialize global environment, call [OH_VideoProcessing_DeinitializeEnvironment](capi-video-processing-h.md#oh_videoprocessing_deinitializeenvironment). |
| [VideoProcessing_ErrorCode OH_VideoProcessing_DeinitializeEnvironment(void)](#oh_videoprocessing_deinitializeenvironment) | Deinitialize global environment for video processing.<br> This function is required if [OH_VideoProcessing_InitializeEnvironment](capi-video-processing-h.md#oh_videoprocessing_initializeenvironment) is called. Typically, this function is called when the host process is about to exit to deinitialize the global environment, which is initialized by calling [OH_VideoProcessing_InitializeEnvironment](capi-video-processing-h.md#oh_videoprocessing_initializeenvironment). If there is some video processing instance existing, this function should not be called. If the [OH_VideoProcessing_InitializeEnvironment](capi-video-processing-h.md#oh_videoprocessing_initializeenvironment) is not called, this function should not be called. |
| [bool OH_VideoProcessing_IsColorSpaceConversionSupported(const VideoProcessing_ColorSpaceInfo* sourceVideoInfo, const VideoProcessing_ColorSpaceInfo* destinationVideoInfo)](#oh_videoprocessing_iscolorspaceconversionsupported) | Query if the video color space conversion is supported. |
| [bool OH_VideoProcessing_IsMetadataGenerationSupported(const VideoProcessing_ColorSpaceInfo* sourceVideoInfo)](#oh_videoprocessing_ismetadatagenerationsupported) | Query if the video metadata generation is supported. |
| [VideoProcessing_ErrorCode OH_VideoProcessing_Create(OH_VideoProcessing** videoProcessor, int type)](#oh_videoprocessing_create) | Create a video processing instance. |
| [VideoProcessing_ErrorCode OH_VideoProcessing_Destroy(OH_VideoProcessing* videoProcessor)](#oh_videoprocessing_destroy) | Destroy the video processing instance.<br> Stop the instance before destroying it. see [OH_VideoProcessing_Stop](capi-video-processing-h.md#oh_videoprocessing_stop). |
| [VideoProcessing_ErrorCode OH_VideoProcessing_RegisterCallback(OH_VideoProcessing* videoProcessor, const VideoProcessing_Callback* callback, void* userData)](#oh_videoprocessing_registercallback) | Register callback object.<br> Register the callback object before starting video processing. |
| [VideoProcessing_ErrorCode OH_VideoProcessing_SetSurface(OH_VideoProcessing* videoProcessor, const OHNativeWindow* window)](#oh_videoprocessing_setsurface) | Set the output surface for video processing.<br> Set the output surface before starting video processing. |
| [VideoProcessing_ErrorCode OH_VideoProcessing_GetSurface(OH_VideoProcessing* videoProcessor, OHNativeWindow** window)](#oh_videoprocessing_getsurface) | Create an input surface.<br> Create the input surface before starting video processing. Call {@link OH_NativeWindow_DestroyNativeWindow} to destroy the input surface. |
| [VideoProcessing_ErrorCode OH_VideoProcessing_SetParameter(OH_VideoProcessing* videoProcessor, const OH_AVFormat* parameter)](#oh_videoprocessing_setparameter) | Set parameter for video processing.<br> Add parameter identified by the specified parameter key. |
| [VideoProcessing_ErrorCode OH_VideoProcessing_GetParameter(OH_VideoProcessing* videoProcessor, OH_AVFormat* parameter)](#oh_videoprocessing_getparameter) | Get parameter of video processing.<br> Get parameter identified by the specified parameter key. |
| [VideoProcessing_ErrorCode OH_VideoProcessing_Start(OH_VideoProcessing* videoProcessor)](#oh_videoprocessing_start) | Start video processing instance.<br> After successfully calling this function, the state {@link VIDEO_PROCESSING_STATE_RUNNING} is reported by callback<br>function {@link OH_VideoProcessingCallback_OnState}. |
| [VideoProcessing_ErrorCode OH_VideoProcessing_Stop(OH_VideoProcessing* videoProcessor)](#oh_videoprocessing_stop) | To stop video processing instance.<br> After the video processing instance is stopped successfully, the state {@link VIDEO_PROCESSING_STATE_STOPPED} is<br>reported by callback function {@link OH_VideoProcessing_OnState}. |
| [VideoProcessing_ErrorCode OH_VideoProcessing_RenderOutputBuffer(OH_VideoProcessing* videoProcessor, uint32_t index)](#oh_videoprocessing_renderoutputbuffer) | Send the output buffer out.<br> If the callback function {@link OH_VideoProcessingCallback_OnNewOutputBuffer} is set, the buffer's index is reported to user by the callback function when an output buffer is ready. |
| [VideoProcessing_ErrorCode OH_VideoProcessingCallback_Create(VideoProcessing_Callback** callback)](#oh_videoprocessingcallback_create) | Create a video processing callback object. |
| [VideoProcessing_ErrorCode OH_VideoProcessingCallback_Destroy(VideoProcessing_Callback* callback)](#oh_videoprocessingcallback_destroy) | Destroy the callback object.<br> The callback object can be destroyed after it is registered to video processing instance. |
| [VideoProcessing_ErrorCode OH_VideoProcessingCallback_BindOnError(VideoProcessing_Callback* callback, OH_VideoProcessingCallback_OnError onError)](#oh_videoprocessingcallback_bindonerror) | Bind the {@link OH_VideoProcessingCallback_OnError} callback function to callback object. |
| [VideoProcessing_ErrorCode OH_VideoProcessingCallback_BindOnState(VideoProcessing_Callback* callback, OH_VideoProcessingCallback_OnState onState)](#oh_videoprocessingcallback_bindonstate) | Bind the {@link OH_VideoProcessingCallback_OnState} callback function to callback object. |
| [VideoProcessing_ErrorCode OH_VideoProcessingCallback_BindOnNewOutputBuffer(VideoProcessing_Callback* callback, OH_VideoProcessingCallback_OnNewOutputBuffer onNewOutputBuffer)](#oh_videoprocessingcallback_bindonnewoutputbuffer) | Bind the {@link OH_VideoProcessingCallback_OnNewOutputBuffer} callback function to callback object. |
| [bool OH_VideoProcessing_IsAutoEffectSupported(uint32_t type)](#oh_videoprocessing_isautoeffectsupported) | Query if the autoeffect is supported. |
| [VideoProcessing_ErrorCode OH_VideoProcessing_UseAutoEffect(uint32_t type, bool enable, const char *name)](#oh_videoprocessing_useautoeffect) | Specifies whether the type effect is required in the XComponent named name that will be created.<br> Records the mapping between type, enable, and name in the internal map. This should be called before [OH_VideoProcessing_SetAutoEffectParam](capi-video-processing-h.md#oh_videoprocessing_setautoeffectparam). |
| [VideoProcessing_ErrorCode OH_VideoProcessing_SetAutoEffectParam(uint32_t type, const char *name, const OH_AVFormat *param)](#oh_videoprocessing_setautoeffectparam) | Sets parameters for the automatic effect associated with the XComponent. Currently, the AutoEffect only takes effect on the last invoked XComponent. |

## Function description

### OH_VideoProcessing_InitializeEnvironment()

```c
VideoProcessing_ErrorCode OH_VideoProcessing_InitializeEnvironment(void)
```

**Description**

Initialize global environment for video processing.<br> This function is optional. Typically, this function is called once when the host process is started to initialize the global environment for video processing, which can reduce the time of [OH_VideoProcessing_Create](capi-video-processing-h.md#oh_videoprocessing_create). To deinitialize global environment, call [OH_VideoProcessing_DeinitializeEnvironment](capi-video-processing-h.md#oh_videoprocessing_deinitializeenvironment).

**Since**: 12

**Returns**:

| Type | Description |
| -- | -- |
| VideoProcessing_ErrorCode | {@link VIDEO_PROCESSING_SUCCESS} if initialization is successful. \n<br>{@link VIDEO_PROCESSING_ERROR_INITIALIZE_FAILED} if initialization is failed. \n  You can check if the device GPU is working properly. |

### OH_VideoProcessing_DeinitializeEnvironment()

```c
VideoProcessing_ErrorCode OH_VideoProcessing_DeinitializeEnvironment(void)
```

**Description**

Deinitialize global environment for video processing.<br> This function is required if [OH_VideoProcessing_InitializeEnvironment](capi-video-processing-h.md#oh_videoprocessing_initializeenvironment) is called. Typically, this function is called when the host process is about to exit to deinitialize the global environment, which is initialized by calling [OH_VideoProcessing_InitializeEnvironment](capi-video-processing-h.md#oh_videoprocessing_initializeenvironment). If there is some video processing instance existing, this function should not be called. If the [OH_VideoProcessing_InitializeEnvironment](capi-video-processing-h.md#oh_videoprocessing_initializeenvironment) is not called, this function should not be called.

**Since**: 12

**Returns**:

| Type | Description |
| -- | -- |
| VideoProcessing_ErrorCode | {@link VIDEO_PROCESSING_SUCCESS} if deinitialization is successful. \n<br>{@link VIDEO_PROCESSING_ERROR_OPERATION_NOT_PERMITTED} if some video processing instance is not destroyed or  [OH_VideoProcessing_InitializeEnvironment](capi-video-processing-h.md#oh_videoprocessing_initializeenvironment) is not called. \n |

### OH_VideoProcessing_IsColorSpaceConversionSupported()

```c
bool OH_VideoProcessing_IsColorSpaceConversionSupported(const VideoProcessing_ColorSpaceInfo* sourceVideoInfo, const VideoProcessing_ColorSpaceInfo* destinationVideoInfo)
```

**Description**

Query if the video color space conversion is supported.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const VideoProcessing_ColorSpaceInfo* sourceVideoInfo | Source video color space information. |
| const VideoProcessing_ColorSpaceInfo* destinationVideoInfo | Destination video color space information. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | <b>true</b> if the video color space conversion is supported. \n  <b>false</b> if the video color space conversion is not supported. |

### OH_VideoProcessing_IsMetadataGenerationSupported()

```c
bool OH_VideoProcessing_IsMetadataGenerationSupported(const VideoProcessing_ColorSpaceInfo* sourceVideoInfo)
```

**Description**

Query if the video metadata generation is supported.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const VideoProcessing_ColorSpaceInfo* sourceVideoInfo | Source video color space information. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | <b>true</b> if the video metadata generation is supported. \n  <b>false</b> if the video metadata generation is not supported. |

### OH_VideoProcessing_Create()

```c
VideoProcessing_ErrorCode OH_VideoProcessing_Create(OH_VideoProcessing** videoProcessor, int type)
```

**Description**

Create a video processing instance.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_VideoProcessing** videoProcessor | Output parameter. The *videoProcessor points to a new video processing object. The *videoProcessor must be null before passed in. |
| int type | Use VIDEO_PROCESSING_TYPE_XXX to specify the processing type. The processing type of the instance can not be changed. |

**Returns**:

| Type | Description |
| -- | -- |
| VideoProcessing_ErrorCode | {@link VIDEO_PROCESSING_SUCCESS} if creating a video processing instance successfully. \n<br>{@link VIDEO_PROCESSING_ERROR_UNSUPPORTED_PROCESSING} if the type is not supported. For example, if metadata<br>generation is not supported by vendor, it returns unsupported processing. \n<br>{@link VIDEO_PROCESSING_ERROR_CREATE_FAILED} if failed to create a video processing instance. \n<br>{@link VIDEO_PROCESSING_ERROR_INVALID_INSTANCE} if instance is null or <b></b>instance is <b>not</b> null. \n<br>{@link VIDEO_PROCESSING_ERROR_INVALID_PARAMETER} if type is invalid. |

### OH_VideoProcessing_Destroy()

```c
VideoProcessing_ErrorCode OH_VideoProcessing_Destroy(OH_VideoProcessing* videoProcessor)
```

**Description**

Destroy the video processing instance.<br> Stop the instance before destroying it. see [OH_VideoProcessing_Stop](capi-video-processing-h.md#oh_videoprocessing_stop).

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_VideoProcessing* videoProcessor | The video processing instance pointer to be destroyed. It is recommended setting the instance pointer to null after the instance is destroyed. |

**Returns**:

| Type | Description |
| -- | -- |
| VideoProcessing_ErrorCode | {@link VIDEO_PROCESSING_SUCCESS} if the instance is destroyed successfully . \n<br>{@link VIDEO_PROCESSING_ERROR_INVALID_INSTANCE} if instance is null or not a video processing instance. \n<br>{@link VIDEO_PROCESSING_ERROR_OPERATION_NOT_PERMITTED} if the instance is still running. |

### OH_VideoProcessing_RegisterCallback()

```c
VideoProcessing_ErrorCode OH_VideoProcessing_RegisterCallback(OH_VideoProcessing* videoProcessor, const VideoProcessing_Callback* callback, void* userData)
```

**Description**

Register callback object.<br> Register the callback object before starting video processing.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_VideoProcessing* videoProcessor | A video processing instance pointer. |
| const VideoProcessing_Callback* callback | Callback pointer to be registered. |
| void* userData | User's custom data pointer. |

**Returns**:

| Type | Description |
| -- | -- |
| VideoProcessing_ErrorCode | {@link VIDEO_PROCESSING_SUCCESS} if callback is registered successfully. \n<br>{@link VIDEO_PROCESSING_ERROR_INVALID_INSTANCE} if instance is null or not a video processing instance. \n<br>{@link VIDEO_PROCESSING_ERROR_INVALID_PARAMETER} if callback is null. \n<br>{@link VIDEO_PROCESSING_ERROR_OPERATION_NOT_PERMITTED} if video processing instance is running. |

### OH_VideoProcessing_SetSurface()

```c
VideoProcessing_ErrorCode OH_VideoProcessing_SetSurface(OH_VideoProcessing* videoProcessor, const OHNativeWindow* window)
```

**Description**

Set the output surface for video processing.<br> Set the output surface before starting video processing.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_VideoProcessing* videoProcessor | A video processing instance pointer. |
| const OHNativeWindow* window | The output surface pointer. |

**Returns**:

| Type | Description |
| -- | -- |
| VideoProcessing_ErrorCode | {@link VIDEO_PROCESSING_SUCCESS} if setting output surface successfully. \n<br>{@link VIDEO_PROCESSING_ERROR_INVALID_INSTANCE} if instance is null or not a video processing instance. \n<br>{@link VIDEO_PROCESSING_ERROR_INVALID_PARAMETER} if window is null. |

### OH_VideoProcessing_GetSurface()

```c
VideoProcessing_ErrorCode OH_VideoProcessing_GetSurface(OH_VideoProcessing* videoProcessor, OHNativeWindow** window)
```

**Description**

Create an input surface.<br> Create the input surface before starting video processing. Call {@link OH_NativeWindow_DestroyNativeWindow} to destroy the input surface.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_VideoProcessing* videoProcessor | A video processing instance pointer. |
| OHNativeWindow** window | The input surface pointer. For example, it is the output surface of a video decoder. |

**Returns**:

| Type | Description |
| -- | -- |
| VideoProcessing_ErrorCode | {@link VIDEO_PROCESSING_SUCCESS} if operation is successful. \n<br>{@link VIDEO_PROCESSING_ERROR_INVALID_INSTANCE} if instance is null or not a video processing instance. \n<br>{@link VIDEO_PROCESSING_ERROR_INVALID_PARAMETER} if window is null or <b></b>window is <b>not</b> null. \n<br>{@link VIDEO_PROCESSING_ERROR_OPERATION_NOT_PERMITTED} if creating surface failed, input surface is already created  or video processing instance is running. |

### OH_VideoProcessing_SetParameter()

```c
VideoProcessing_ErrorCode OH_VideoProcessing_SetParameter(OH_VideoProcessing* videoProcessor, const OH_AVFormat* parameter)
```

**Description**

Set parameter for video processing.<br> Add parameter identified by the specified parameter key.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_VideoProcessing* videoProcessor | An video processing instance pointer. |
| const OH_AVFormat* parameter | The parameter for video processing. |

**Returns**:

| Type | Description |
| -- | -- |
| VideoProcessing_ErrorCode | {@link VIDEO_PROCESSING_SUCCESS} if setting parameter is successful. \n<br>{@link VIDEO_PROCESSING_ERROR_INVALID_INSTANCE} if instance is null or not an video processing instance. \n<br>{@link VIDEO_PROCESSING_ERROR_INVALID_PARAMETER} if the parameter is null. \n<br>{@link VIDEO_PROCESSING_ERROR_INVALID_VALUE} if some property of the parameter is invalid. For example, the parameter<br>contains unsupported parameter key or value. \n<br>{@link VIDEO_PROCESSING_ERROR_NO_MEMORY} if memory allocation failed. |

### OH_VideoProcessing_GetParameter()

```c
VideoProcessing_ErrorCode OH_VideoProcessing_GetParameter(OH_VideoProcessing* videoProcessor, OH_AVFormat* parameter)
```

**Description**

Get parameter of video processing.<br> Get parameter identified by the specified parameter key.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_VideoProcessing* videoProcessor | An video processing instance pointer. |
| OH_AVFormat* parameter | The parameter used by the video processing instance. |

**Returns**:

| Type | Description |
| -- | -- |
| VideoProcessing_ErrorCode | {@link VIDEO_PROCESSING_SUCCESS} if getting parameter is successful. \n<br>{@link VIDEO_PROCESSING_ERROR_INVALID_INSTANCE} if instance is null or not an video processing instance. \n<br>{@link VIDEO_PROCESSING_ERROR_INVALID_PARAMETER} if the parameter is null. \n |

### OH_VideoProcessing_Start()

```c
VideoProcessing_ErrorCode OH_VideoProcessing_Start(OH_VideoProcessing* videoProcessor)
```

**Description**

Start video processing instance.<br> After successfully calling this function, the state {@link VIDEO_PROCESSING_STATE_RUNNING} is reported by callback<br>function {@link OH_VideoProcessingCallback_OnState}.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_VideoProcessing* videoProcessor | A video processing instance pointer. |

**Returns**:

| Type | Description |
| -- | -- |
| VideoProcessing_ErrorCode | {@link VIDEO_PROCESSING_SUCCESS} if the operation is successful. \n<br>{@link VIDEO_PROCESSING_ERROR_INVALID_INSTANCE} if instance is null or not a video processing instance. \n<br>{@link VIDEO_PROCESSING_ERROR_OPERATION_NOT_PERMITTED} if output surface is not set, input surface is not created or  instance is already running. |

### OH_VideoProcessing_Stop()

```c
VideoProcessing_ErrorCode OH_VideoProcessing_Stop(OH_VideoProcessing* videoProcessor)
```

**Description**

To stop video processing instance.<br> After the video processing instance is stopped successfully, the state {@link VIDEO_PROCESSING_STATE_STOPPED} is<br>reported by callback function {@link OH_VideoProcessing_OnState}.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_VideoProcessing* videoProcessor | A video processing instance pointer. |

**Returns**:

| Type | Description |
| -- | -- |
| VideoProcessing_ErrorCode | {@link VIDEO_PROCESSING_SUCCESS} if the operation is successful. \n<br>{@link VIDEO_PROCESSING_ERROR_INVALID_INSTANCE} if instance is null or not a video processing instance. \n<br>{@link VIDEO_PROCESSING_ERROR_OPERATION_NOT_PERMITTED} if instance is already stopped. |

### OH_VideoProcessing_RenderOutputBuffer()

```c
VideoProcessing_ErrorCode OH_VideoProcessing_RenderOutputBuffer(OH_VideoProcessing* videoProcessor, uint32_t index)
```

**Description**

Send the output buffer out.<br> If the callback function {@link OH_VideoProcessingCallback_OnNewOutputBuffer} is set, the buffer's index is reported to user by the callback function when an output buffer is ready.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_VideoProcessing* videoProcessor | A video processing instance pointer. |
| uint32_t index | The output buffer's index. |

**Returns**:

| Type | Description |
| -- | -- |
| VideoProcessing_ErrorCode | {@link VIDEO_PROCESSING_SUCCESS} if the operation is successful. \n<br>{@link VIDEO_PROCESSING_ERROR_INVALID_INSTANCE} if instance is null or not a video processing instance. \n<br>{@link VIDEO_PROCESSING_ERROR_INVALID_PARAMETER} if index is invalid. \n<br>{@link VIDEO_PROCESSING_ERROR_OPERATION_NOT_PERMITTED} if callback {@link OH_VideoProcessing_OnNewOutputBuffer} is  not set or instance is stopped. |

### OH_VideoProcessingCallback_Create()

```c
VideoProcessing_ErrorCode OH_VideoProcessingCallback_Create(VideoProcessing_Callback** callback)
```

**Description**

Create a video processing callback object.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| VideoProcessing_Callback** callback | Output parameter. The *callback points to a new callback object. The *callback should be null before creating the callback object. |

**Returns**:

| Type | Description |
| -- | -- |
| VideoProcessing_ErrorCode | {@link VIDEO_PROCESSING_SUCCESS} if callback object is created successfully. \n<br>{@link VIDEO_PROCESSING_ERROR_INVALID_PARAMETER} if callback is null or <b></b>callback is <b>not</b> null. \n<br>{@link VIDEO_PROCESSING_ERROR_NO_MEMORY} if out of memory. |

### OH_VideoProcessingCallback_Destroy()

```c
VideoProcessing_ErrorCode OH_VideoProcessingCallback_Destroy(VideoProcessing_Callback* callback)
```

**Description**

Destroy the callback object.<br> The callback object can be destroyed after it is registered to video processing instance.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| VideoProcessing_Callback* callback | The callback object pointer. It is recommended setting the callback pointer to null after the callback object is destroyed. |

**Returns**:

| Type | Description |
| -- | -- |
| VideoProcessing_ErrorCode | {@link VIDEO_PROCESSING_SUCCESS} if callback is successfully destroyed. \n<br>{@link VIDEO_PROCESSING_ERROR_INVALID_PARAMETER} if callback is null. |

### OH_VideoProcessingCallback_BindOnError()

```c
VideoProcessing_ErrorCode OH_VideoProcessingCallback_BindOnError(VideoProcessing_Callback* callback, OH_VideoProcessingCallback_OnError onError)
```

**Description**

Bind the {@link OH_VideoProcessingCallback_OnError} callback function to callback object.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| VideoProcessing_Callback* callback | A callback object pointer. |
| OH_VideoProcessingCallback_OnError onError | The callback function. |

**Returns**:

| Type | Description |
| -- | -- |
| VideoProcessing_ErrorCode | {@link VIDEO_PROCESSING_SUCCESS} if the function is bound to callback object successfully. \n<br>{@link VIDEO_PROCESSING_ERROR_INVALID_PARAMETER} if the callback is null or onError is null. |

### OH_VideoProcessingCallback_BindOnState()

```c
VideoProcessing_ErrorCode OH_VideoProcessingCallback_BindOnState(VideoProcessing_Callback* callback, OH_VideoProcessingCallback_OnState onState)
```

**Description**

Bind the {@link OH_VideoProcessingCallback_OnState} callback function to callback object.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| VideoProcessing_Callback* callback | A callback object pointer. |
| OH_VideoProcessingCallback_OnState onState | The callback function. |

**Returns**:

| Type | Description |
| -- | -- |
| VideoProcessing_ErrorCode | {@link VIDEO_PROCESSING_SUCCESS} if the function is bound to callback object successfully. \n<br>{@link VIDEO_PROCESSING_ERROR_INVALID_PARAMETER} if the callback is null or onState is null. |

### OH_VideoProcessingCallback_BindOnNewOutputBuffer()

```c
VideoProcessing_ErrorCode OH_VideoProcessingCallback_BindOnNewOutputBuffer(VideoProcessing_Callback* callback, OH_VideoProcessingCallback_OnNewOutputBuffer onNewOutputBuffer)
```

**Description**

Bind the {@link OH_VideoProcessingCallback_OnNewOutputBuffer} callback function to callback object.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| VideoProcessing_Callback* callback | A callback object pointer. |
| OH_VideoProcessingCallback_OnNewOutputBuffer onNewOutputBuffer | The callback function. |

**Returns**:

| Type | Description |
| -- | -- |
| VideoProcessing_ErrorCode | {@link VIDEO_PROCESSING_SUCCESS} if the function is bound to callback object successfully. \n<br>{@link VIDEO_PROCESSING_ERROR_INVALID_PARAMETER} if the callback is null. |

### OH_VideoProcessing_IsAutoEffectSupported()

```c
bool OH_VideoProcessing_IsAutoEffectSupported(uint32_t type)
```

**Description**

Query if the autoeffect is supported.

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint32_t type | [in] The autoeffect type to query. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | <ul><li><b>true</b> if the autoeffect is supported.</li>      <li><b>false</b> if the autoeffect is not supported.</li></ul> |

### OH_VideoProcessing_UseAutoEffect()

```c
VideoProcessing_ErrorCode OH_VideoProcessing_UseAutoEffect(uint32_t type, bool enable, const char *name)
```

**Description**

Specifies whether the type effect is required in the XComponent named name that will be created.<br> Records the mapping between type, enable, and name in the internal map. This should be called before [OH_VideoProcessing_SetAutoEffectParam](capi-video-processing-h.md#oh_videoprocessing_setautoeffectparam).

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint32_t type | [in] Specify AutoEffect to use. |
| bool enable | [in] Enable or disable the type effect in the XComponent named name to be created later. |
| const char *name | [in] Specifies the name of an XComponent. If the current application has multiple XComponents with the same name, this parameter takes effect only on the first active XComponent. |

**Returns**:

| Type | Description |
| -- | -- |
| VideoProcessing_ErrorCode | <ul><li>{@link VIDEO_PROCESSING_SUCCESS} if the operation is successful.</li><br>    <li>{@link VIDEO_PROCESSING_ERROR_INVALID_VALUE} if type is not {@link VIDEO_PROCESSING_TYPE_AUTOEFFECT_AISR}<br>    or name is null.</li><br>    <li>{@link VIDEO_PROCESSING_ERROR_OPERATION_NOT_PERMITTED} if [OH_VideoProcessing_IsAutoEffectSupported](capi-video-processing-h.md#oh_videoprocessing_isautoeffectsupported)      returns false for the type, or the same name has already been registered by calling this function.</li></ul> |

### OH_VideoProcessing_SetAutoEffectParam()

```c
VideoProcessing_ErrorCode OH_VideoProcessing_SetAutoEffectParam(uint32_t type, const char *name, const OH_AVFormat *param)
```

**Description**

Sets parameters for the automatic effect associated with the XComponent. Currently, the AutoEffect only takes effect on the last invoked XComponent.

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint32_t type | [in] Specify AutoEffect to use. |
| const char *name | [in] Specifies the name of an XComponent. If the current application has multiple XComponents with the same name, this parameter takes effect only on the first active XComponent. |
| const OH_AVFormat *param | [in] The parameter according to the type see video_processing_type.h. |

**Returns**:

| Type | Description |
| -- | -- |
| VideoProcessing_ErrorCode | <ul><li>{@link VIDEO_PROCESSING_SUCCESS} if the operation is successful.</li><br>    <li>{@link VIDEO_PROCESSING_ERROR_INVALID_VALUE} if the name is nullptr or the param value is invalid.</li><br>    <li>{@link VIDEO_PROCESSING_ERROR_OPERATION_NOT_PERMITTED} if [OH_VideoProcessing_IsAutoEffectSupported](capi-video-processing-h.md#oh_videoprocessing_isautoeffectsupported)<br>    returns false for the type, or name does not match any registered name, or the VPE instance has not been<br>    created or [OH_VideoProcessing_UseAutoEffect](capi-video-processing-h.md#oh_videoprocessing_useautoeffect) has not been called for the name.</li><br>    <li>{@link VIDEO_PROCESSING_ERROR_UNKNOWN} if an internal algorithm error occurs.</li></ul> |


