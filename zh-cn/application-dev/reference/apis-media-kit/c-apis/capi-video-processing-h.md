# video_processing.h

## 概述

声明视频处理函数。

**库：** libvideo_processing.so

**系统能力：** SystemCapability.Multimedia.VideoProcessingEngine

**起始版本：** 12

**相关模块：** [VideoProcessing](capi-videoprocessing.md)

## 汇总

### 函数

| 名称 | 描述 |
| -- | -- |
| [VideoProcessing_ErrorCode OH_VideoProcessing_InitializeEnvironment(void)](#oh_videoprocessing_initializeenvironment) | 初始化视频处理全局环境。<br>该函数是可选的。<br>该函数只在主进程启动时被调用一次，用于初始化视频处理全局环境，这样可以减少[OH_VideoProcessing_Create](capi-video-processing-h.md#oh_videoprocessing_create)的时间。<br>调用[OH_VideoProcessing_DeinitializeEnvironment](capi-video-processing-h.md#oh_videoprocessing_deinitializeenvironment)释放视频处理全局环境。<br>初始化后，必须释放视频处理全局环境，释放方式及时机详见[OH_VideoProcessing_DeinitializeEnvironment](capi-video-processing-h.md#oh_videoprocessing_deinitializeenvironment)。 |
| [VideoProcessing_ErrorCode OH_VideoProcessing_DeinitializeEnvironment(void)](#oh_videoprocessing_deinitializeenvironment) | 释放视频处理全局环境。<br>调用前，必须调用[OH_VideoProcessing_InitializeEnvironment](capi-video-processing-h.md#oh_videoprocessing_initializeenvironment)初始化。<br>通常在主进程即将退出时调用该函数，以释放通过调用[OH_VideoProcessing_InitializeEnvironment](capi-video-processing-h.md#oh_videoprocessing_initializeenvironment)函数初始化的全局环境。<br>如果仍有视频处理的实例运行中，就不能调用该函数。 |
| [bool OH_VideoProcessing_IsColorSpaceConversionSupported(const VideoProcessing_ColorSpaceInfo* sourceVideoInfo, const VideoProcessing_ColorSpaceInfo* destinationVideoInfo)](#oh_videoprocessing_iscolorspaceconversionsupported) | 查询是否支持视频颜色空间转换。 |
| [bool OH_VideoProcessing_IsMetadataGenerationSupported(const VideoProcessing_ColorSpaceInfo* sourceVideoInfo)](#oh_videoprocessing_ismetadatagenerationsupported) | 查询是否支持视频元数据生成。 |
| [VideoProcessing_ErrorCode OH_VideoProcessing_Create(OH_VideoProcessing** videoProcessor, int type)](#oh_videoprocessing_create) | 创建视频处理实例。 |
| [VideoProcessing_ErrorCode OH_VideoProcessing_Destroy(OH_VideoProcessing* videoProcessor)](#oh_videoprocessing_destroy) | 销毁视频处理实例。<br>销毁之前先停止实例，参阅[OH_VideoProcessing_Stop](capi-video-processing-h.md#oh_videoprocessing_stop)。 |
| [VideoProcessing_ErrorCode OH_VideoProcessing_RegisterCallback(OH_VideoProcessing* videoProcessor, const VideoProcessing_Callback* callback, void* userData)](#oh_videoprocessing_registercallback) | 注册回调函数。<br>在开始视频处理之前注册回调函数，视频处理过程中无法注册回调函数。 |
| [VideoProcessing_ErrorCode OH_VideoProcessing_SetSurface(OH_VideoProcessing* videoProcessor, const OHNativeWindow* window)](#oh_videoprocessing_setsurface) | 设置视频处理输出surface。<br>在视频处理启动之前设置输出surface。 |
| [VideoProcessing_ErrorCode OH_VideoProcessing_GetSurface(OH_VideoProcessing* videoProcessor, OHNativeWindow** window)](#oh_videoprocessing_getsurface) | 创建surface。<br>在视频处理启动之前创建输入surface。调用{@link OH_NativeWindow_DestroyNativeWindow}销毁输入surface。 |
| [VideoProcessing_ErrorCode OH_VideoProcessing_SetParameter(OH_VideoProcessing* videoProcessor, const OH_AVFormat* parameter)](#oh_videoprocessing_setparameter) | 设置视频处理输出参数。 |
| [VideoProcessing_ErrorCode OH_VideoProcessing_GetParameter(OH_VideoProcessing* videoProcessor, OH_AVFormat* parameter)](#oh_videoprocessing_getparameter) | 获取视频处理参数。 |
| [VideoProcessing_ErrorCode OH_VideoProcessing_Start(OH_VideoProcessing* videoProcessor)](#oh_videoprocessing_start) | 启动视频处理。<br>成功启动后，回调函数[OH_VideoProcessingCallback_OnState](capi-video-processing-types-h.md#oh_videoprocessingcallback_onstate)会报告[VideoProcessing_State](capi-video-processing-types-h.md#videoprocessing_state).VIDEO_PROCESSING_STATE_RUNNING状态。 |
| [VideoProcessing_ErrorCode OH_VideoProcessing_Stop(OH_VideoProcessing* videoProcessor)](#oh_videoprocessing_stop) | 停止视频处理。<br>成功停止后，回调函数[OH_VideoProcessingCallback_OnState](capi-video-processing-types-h.md#oh_videoprocessingcallback_onstate)会报告[VideoProcessing_State](capi-video-processing-types-h.md#videoprocessing_state).VIDEO_PROCESSING_STATE_STOPPED状态。 |
| [VideoProcessing_ErrorCode OH_VideoProcessing_RenderOutputBuffer(OH_VideoProcessing* videoProcessor, uint32_t index)](#oh_videoprocessing_renderoutputbuffer) | 渲染处理并输出buffer。<br>如果设置了回调函数[OH_VideoProcessingCallback_OnNewOutputBuffer](capi-video-processing-types-h.md#oh_videoprocessingcallback_onnewoutputbuffer)，当输出buffer准备好之后会通过回调函数把buffer的索引返回给用户。 |
| [VideoProcessing_ErrorCode OH_VideoProcessingCallback_Create(VideoProcessing_Callback** callback)](#oh_videoprocessingcallback_create) | 创建视频处理回调函数对象。 |
| [VideoProcessing_ErrorCode OH_VideoProcessingCallback_Destroy(VideoProcessing_Callback* callback)](#oh_videoprocessingcallback_destroy) | 销毁回调对象。回调对象在注册之后就可以销毁。 |
| [VideoProcessing_ErrorCode OH_VideoProcessingCallback_BindOnError(VideoProcessing_Callback* callback, OH_VideoProcessingCallback_OnError onError)](#oh_videoprocessingcallback_bindonerror) | 绑定回调函数[OH_VideoProcessingCallback_OnError](capi-video-processing-types-h.md#oh_videoprocessingcallback_onerror)到回调对象。绑定完成之后，需要调用 [OH_VideoProcessing_RegisterCallback](capi-video-processing-h.md#oh_videoprocessing_registercallback)，将回调对象注册到视频处理实例，才能使其生效。 |
| [VideoProcessing_ErrorCode OH_VideoProcessingCallback_BindOnState(VideoProcessing_Callback* callback, OH_VideoProcessingCallback_OnState onState)](#oh_videoprocessingcallback_bindonstate) | 绑定回调函数[OH_VideoProcessingCallback_OnState](capi-video-processing-types-h.md#oh_videoprocessingcallback_onstate)到回调对象。绑定完成之后，需要调用 [OH_VideoProcessing_RegisterCallback](capi-video-processing-h.md#oh_videoprocessing_registercallback)，将回调对象注册到视频处理实例，才能使其生效。 |
| [VideoProcessing_ErrorCode OH_VideoProcessingCallback_BindOnNewOutputBuffer(VideoProcessing_Callback* callback, OH_VideoProcessingCallback_OnNewOutputBuffer onNewOutputBuffer)](#oh_videoprocessingcallback_bindonnewoutputbuffer) | 绑定回调函数[OH_VideoProcessingCallback_OnNewOutputBuffer](capi-video-processing-types-h.md#oh_videoprocessingcallback_onnewoutputbuffer)到回调对象。绑定完成之后，需要调用[OH_VideoProcessing_RegisterCallback](capi-video-processing-h.md#oh_videoprocessing_registercallback)，将回调对象注册到视频处理实例，才能使其生效。 |
| [bool OH_VideoProcessing_IsAutoEffectSupported(uint32_t type)](#oh_videoprocessing_isautoeffectsupported) | Query if the autoeffect is supported. |
| [VideoProcessing_ErrorCode OH_VideoProcessing_UseAutoEffect(uint32_t type, bool enable, const char *name)](#oh_videoprocessing_useautoeffect) | Specifies whether the type effect is required in the XComponent named name that will be created.Records the mapping between type, enable, and name in the internal map.This should be called before [OH_VideoProcessing_SetAutoEffectParam](capi-video-processing-h.md#oh_videoprocessing_setautoeffectparam). |
| [VideoProcessing_ErrorCode OH_VideoProcessing_SetAutoEffectParam(uint32_t type, const char *name, const OH_AVFormat *param)](#oh_videoprocessing_setautoeffectparam) | Sets parameters for the automatic effect associated with the XComponent. Currently, the AutoEffect only takes effect on the last invoked XComponent. |

## 函数说明

### OH_VideoProcessing_InitializeEnvironment()

```c
VideoProcessing_ErrorCode OH_VideoProcessing_InitializeEnvironment(void)
```

**描述**

初始化视频处理全局环境。<br>该函数是可选的。<br>该函数只在主进程启动时被调用一次，用于初始化视频处理全局环境，这样可以减少[OH_VideoProcessing_Create](capi-video-processing-h.md#oh_videoprocessing_create)的时间。<br>调用[OH_VideoProcessing_DeinitializeEnvironment](capi-video-processing-h.md#oh_videoprocessing_deinitializeenvironment)释放视频处理全局环境。<br>初始化后，必须释放视频处理全局环境，释放方式及时机详见[OH_VideoProcessing_DeinitializeEnvironment](capi-video-processing-h.md#oh_videoprocessing_deinitializeenvironment)。

**起始版本：** 12

**返回：**

| 类型 | 说明 |
| -- | -- |
| [VideoProcessing_ErrorCode](capi-video-processing-types-h.md#videoprocessing_errorcode) | 如果初始化成功，返回VIDEO_PROCESSING_SUCCESS，否则返回VIDEO_PROCESSING_ERROR_INITIALIZE_FAILED。      <br>如果失败，应用需要检查GPU是否正常工作。 |

### OH_VideoProcessing_DeinitializeEnvironment()

```c
VideoProcessing_ErrorCode OH_VideoProcessing_DeinitializeEnvironment(void)
```

**描述**

释放视频处理全局环境。<br>调用前，必须调用[OH_VideoProcessing_InitializeEnvironment](capi-video-processing-h.md#oh_videoprocessing_initializeenvironment)初始化。<br>通常在主进程即将退出时调用该函数，以释放通过调用[OH_VideoProcessing_InitializeEnvironment](capi-video-processing-h.md#oh_videoprocessing_initializeenvironment)函数初始化的全局环境。<br>如果仍有视频处理的实例运行中，就不能调用该函数。

**起始版本：** 12

**返回：**

| 类型 | 说明 |
| -- | -- |
| [VideoProcessing_ErrorCode](capi-video-processing-types-h.md#videoprocessing_errorcode) | 如果执行成功，返回VIDEO_PROCESSING_SUCCESS。      <br>如果还有视频处理的实例没有销毁或者没有调用[OH_VideoProcessing_InitializeEnvironment](capi-video-processing-h.md#oh_videoprocessing_initializeenvironment)，      返回VIDEO_PROCESSING_ERROR_OPERATION_NOT_PERMITTED。 |

### OH_VideoProcessing_IsColorSpaceConversionSupported()

```c
bool OH_VideoProcessing_IsColorSpaceConversionSupported(const VideoProcessing_ColorSpaceInfo* sourceVideoInfo, const VideoProcessing_ColorSpaceInfo* destinationVideoInfo)
```

**描述**

查询是否支持视频颜色空间转换。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const VideoProcessing_ColorSpaceInfo](capi-videoprocessing-videoprocessing-colorspaceinfo.md)* sourceVideoInfo | 输入视频颜色空间信息。 |
| [const VideoProcessing_ColorSpaceInfo](capi-videoprocessing-videoprocessing-colorspaceinfo.md)* destinationVideoInfo | 输出视频颜色空间信息。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| bool | 如果支持视频颜色空间转换返回true，否则返回false。 |

### OH_VideoProcessing_IsMetadataGenerationSupported()

```c
bool OH_VideoProcessing_IsMetadataGenerationSupported(const VideoProcessing_ColorSpaceInfo* sourceVideoInfo)
```

**描述**

查询是否支持视频元数据生成。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const VideoProcessing_ColorSpaceInfo](capi-videoprocessing-videoprocessing-colorspaceinfo.md)* sourceVideoInfo | 输入视频颜色空间信息。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| bool | 如果支持视频元数据生成返回true，否则返回false。 |

### OH_VideoProcessing_Create()

```c
VideoProcessing_ErrorCode OH_VideoProcessing_Create(OH_VideoProcessing** videoProcessor, int type)
```

**描述**

创建视频处理实例。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_VideoProcessing](capi-videoprocessing-oh-videoprocessing.md)** videoProcessor | 输出参数。指向视频处理对象的指针的指针。输入前\*videoProcessor必须是空指针。 |
| int type | 使用视频处理实例常量来指定处理类型。实例的处理类型不能改变。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [VideoProcessing_ErrorCode](capi-video-processing-types-h.md#videoprocessing_errorcode) | 如果视频处理实例创建成功，返回VIDEO_PROCESSING_SUCCESS。      <br>如果处理类型不支持，返回VIDEO_PROCESSING_ERROR_UNSUPPORTED_PROCESSING，例如，不支持元数据生成。      <br>如果创建视频处理实例失败，返回VIDEO_PROCESSING_ERROR_CREATE_FAILED。      <br>如果实例为空或实例的指针非空，返回VIDEO_PROCESSING_ERROR_INVALID_INSTANCE。      <br>如果处理类型无效，返回VIDEO_PROCESSING_ERROR_INVALID_PARAMETER。 |

### OH_VideoProcessing_Destroy()

```c
VideoProcessing_ErrorCode OH_VideoProcessing_Destroy(OH_VideoProcessing* videoProcessor)
```

**描述**

销毁视频处理实例。<br>销毁之前先停止实例，参阅[OH_VideoProcessing_Stop](capi-video-processing-h.md#oh_videoprocessing_stop)。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_VideoProcessing](capi-videoprocessing-oh-videoprocessing.md)* videoProcessor | 指向视频处理实例的指针，建议在实例销毁之后将其设置为空指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [VideoProcessing_ErrorCode](capi-video-processing-types-h.md#videoprocessing_errorcode) | 如果实例销毁成功，返回VIDEO_PROCESSING_SUCCESS。      <br>如果实例为空或者不是一个视频处理实例，返回VIDEO_PROCESSING_ERROR_INVALID_INSTANCE。      <br>如果实例仍在运行，返回VIDEO_PROCESSING_ERROR_OPERATION_NOT_PERMITTED。 |

### OH_VideoProcessing_RegisterCallback()

```c
VideoProcessing_ErrorCode OH_VideoProcessing_RegisterCallback(OH_VideoProcessing* videoProcessor, const VideoProcessing_Callback* callback, void* userData)
```

**描述**

注册回调函数。<br>在开始视频处理之前注册回调函数，视频处理过程中无法注册回调函数。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_VideoProcessing](capi-videoprocessing-oh-videoprocessing.md)* videoProcessor | 指向视频处理实例的指针。 |
| [const VideoProcessing_Callback](capi-videoprocessing-videoprocessing-callback.md)* callback | 回调函数指针。 |
| void* userData | 指向用户特定数据的指针，如this指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [VideoProcessing_ErrorCode](capi-video-processing-types-h.md#videoprocessing_errorcode) | 如果回调函数注册成功，返回VIDEO_PROCESSING_SUCCESS。      <br>如果实例为空或者不是一个视频处理实例，返回VIDEO_PROCESSING_ERROR_INVALID_INSTANCE。      <br>如果回调函数指针为空，返回VIDEO_PROCESSING_ERROR_INVALID_PARAMETER。      <br>如果实例仍在运行，返回VIDEO_PROCESSING_ERROR_OPERATION_NOT_PERMITTED。 |

### OH_VideoProcessing_SetSurface()

```c
VideoProcessing_ErrorCode OH_VideoProcessing_SetSurface(OH_VideoProcessing* videoProcessor, const OHNativeWindow* window)
```

**描述**

设置视频处理输出surface。<br>在视频处理启动之前设置输出surface。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_VideoProcessing](capi-videoprocessing-oh-videoprocessing.md)* videoProcessor | 指向视频处理实例的指针。 |
| [const OHNativeWindow](capi-videoprocessing-nativewindow.md)* window | 指向输出surface的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [VideoProcessing_ErrorCode](capi-video-processing-types-h.md#videoprocessing_errorcode) | 如果输出surface设置成功，返回VIDEO_PROCESSING_SUCCESS。      <br>如果实例为空或者不是一个视频处理实例，返回VIDEO_PROCESSING_ERROR_INVALID_INSTANCE。      <br>如果window为空指针，返回VIDEO_PROCESSING_ERROR_INVALID_PARAMETER。 |

### OH_VideoProcessing_GetSurface()

```c
VideoProcessing_ErrorCode OH_VideoProcessing_GetSurface(OH_VideoProcessing* videoProcessor, OHNativeWindow** window)
```

**描述**

创建surface。<br>在视频处理启动之前创建输入surface。调用{@link OH_NativeWindow_DestroyNativeWindow}销毁输入surface。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_VideoProcessing](capi-videoprocessing-oh-videoprocessing.md)* videoProcessor | 指向视频处理实例的指针。 |
| [OHNativeWindow](capi-videoprocessing-nativewindow.md)** window | 指向输入surface的指针。例如，此输入surface指针可以指向视频解码器输出surface。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [VideoProcessing_ErrorCode](capi-video-processing-types-h.md#videoprocessing_errorcode) | 如果执行成功，返回VIDEO_PROCESSING_SUCCESS。      <br>如果实例为空或者不是一个视频处理实例，返回VIDEO_PROCESSING_ERROR_INVALID_INSTANCE。      <br>如果window为空指针或指向window的指针为空，返回VIDEO_PROCESSING_ERROR_INVALID_PARAMETER。      <br>如果创建surface失败，或者输入surface已经创建，或者视频处理实例还在运行，返回VIDEO_PROCESSING_ERROR_OPERATION_NOT_PERMITTED。 |

### OH_VideoProcessing_SetParameter()

```c
VideoProcessing_ErrorCode OH_VideoProcessing_SetParameter(OH_VideoProcessing* videoProcessor, const OH_AVFormat* parameter)
```

**描述**

设置视频处理输出参数。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_VideoProcessing](capi-videoprocessing-oh-videoprocessing.md)* videoProcessor | 指向视频处理实例的指针。 |
| [const OH_AVFormat](capi-videoprocessing-oh-avformat.md)* parameter | 指向视频处理参数实例的指针，用于传入需设置的视频处理参数，例如视频宽度、高度、像素格式及编解码格式等。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [VideoProcessing_ErrorCode](capi-video-processing-types-h.md#videoprocessing_errorcode) | 如果参数设置成功，返回VIDEO_PROCESSING_SUCCESS。      <br>如果实例为空或者不是一个视频处理实例，返回VIDEO_PROCESSING_ERROR_INVALID_INSTANCE。      <br>如果参数为空，返回VIDEO_PROCESSING_ERROR_INVALID_PARAMETER。      <br>如果参数的某些属性无效，返回VIDEO_PROCESSING_ERROR_INVALID_VALUE，例如，包含不支持的参数值。      <br>如果内存分配失败，返回VIDEO_PROCESSING_ERROR_NO_MEMORY。 |

### OH_VideoProcessing_GetParameter()

```c
VideoProcessing_ErrorCode OH_VideoProcessing_GetParameter(OH_VideoProcessing* videoProcessor, OH_AVFormat* parameter)
```

**描述**

获取视频处理参数。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_VideoProcessing](capi-videoprocessing-oh-videoprocessing.md)* videoProcessor | 指向视频处理实例的指针。 |
| [OH_AVFormat](capi-videoprocessing-oh-avformat.md)* parameter | 指向视频处理参数实例的指针，用于获取当前视频处理的参数，比如视频宽度、高度、像素格式、编解码格式等。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [VideoProcessing_ErrorCode](capi-video-processing-types-h.md#videoprocessing_errorcode) | 如果参数获取成功，返回VIDEO_PROCESSING_SUCCESS。      <br>如果实例为空或者不是一个视频处理实例，返回VIDEO_PROCESSING_ERROR_INVALID_INSTANCE。      <br>如果参数为空，返回VIDEO_PROCESSING_ERROR_INVALID_PARAMETER。 |

### OH_VideoProcessing_Start()

```c
VideoProcessing_ErrorCode OH_VideoProcessing_Start(OH_VideoProcessing* videoProcessor)
```

**描述**

启动视频处理。<br>成功启动后，回调函数[OH_VideoProcessingCallback_OnState](capi-video-processing-types-h.md#oh_videoprocessingcallback_onstate)会报告[VideoProcessing_State](capi-video-processing-types-h.md#videoprocessing_state).VIDEO_PROCESSING_STATE_RUNNING状态。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_VideoProcessing](capi-videoprocessing-oh-videoprocessing.md)* videoProcessor | 指向视频处理实例的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [VideoProcessing_ErrorCode](capi-video-processing-types-h.md#videoprocessing_errorcode) | 如果执行成功，返回VIDEO_PROCESSING_SUCCESS。      <br>如果实例为空或者不是一个视频处理实例，返回VIDEO_PROCESSING_ERROR_INVALID_INSTANCE。      <br>如果没有设置输出surface，或者没有创建输入surface，或者实例已经运行，返回VIDEO_PROCESSING_ERROR_OPERATION_NOT_PERMITTED。 |

### OH_VideoProcessing_Stop()

```c
VideoProcessing_ErrorCode OH_VideoProcessing_Stop(OH_VideoProcessing* videoProcessor)
```

**描述**

停止视频处理。<br>成功停止后，回调函数[OH_VideoProcessingCallback_OnState](capi-video-processing-types-h.md#oh_videoprocessingcallback_onstate)会报告[VideoProcessing_State](capi-video-processing-types-h.md#videoprocessing_state).VIDEO_PROCESSING_STATE_STOPPED状态。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_VideoProcessing](capi-videoprocessing-oh-videoprocessing.md)* videoProcessor | 指向视频处理实例的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [VideoProcessing_ErrorCode](capi-video-processing-types-h.md#videoprocessing_errorcode) | 如果执行成功，返回VIDEO_PROCESSING_SUCCESS。      <br>如果实例为空或者不是一个视频处理实例，返回VIDEO_PROCESSING_ERROR_INVALID_INSTANCE。      <br>如果实例已经停止，返回VIDEO_PROCESSING_ERROR_OPERATION_NOT_PERMITTED。 |

### OH_VideoProcessing_RenderOutputBuffer()

```c
VideoProcessing_ErrorCode OH_VideoProcessing_RenderOutputBuffer(OH_VideoProcessing* videoProcessor, uint32_t index)
```

**描述**

渲染处理并输出buffer。<br>如果设置了回调函数[OH_VideoProcessingCallback_OnNewOutputBuffer](capi-video-processing-types-h.md#oh_videoprocessingcallback_onnewoutputbuffer)，当输出buffer准备好之后会通过回调函数把buffer的索引返回给用户。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_VideoProcessing](capi-videoprocessing-oh-videoprocessing.md)* videoProcessor | 指向视频处理实例的指针。 |
| uint32_t index | 输出buffer的索引。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [VideoProcessing_ErrorCode](capi-video-processing-types-h.md#videoprocessing_errorcode) | 如果执行成功，返回VIDEO_PROCESSING_SUCCESS。      <br>如果实例为空或者不是一个视频处理实例，返回VIDEO_PROCESSING_ERROR_INVALID_INSTANCE。      <br>如果索引值无效，输出VIDEO_PROCESSING_ERROR_INVALID_PARAMETER。      <br>如果没有设置回调函数[OH_VideoProcessingCallback_OnNewOutputBuffer](capi-video-processing-types-h.md#oh_videoprocessingcallback_onnewoutputbuffer)或者实例已经停止运行，      返回VIDEO_PROCESSING_ERROR_OPERATION_NOT_PERMITTED。 |

### OH_VideoProcessingCallback_Create()

```c
VideoProcessing_ErrorCode OH_VideoProcessingCallback_Create(VideoProcessing_Callback** callback)
```

**描述**

创建视频处理回调函数对象。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [VideoProcessing_Callback](capi-videoprocessing-videoprocessing-callback.md)** callback | 输出参数。\*callback是指向回调函数对象的指针。在创建回调函数对象之前\*callback必须为空指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [VideoProcessing_ErrorCode](capi-video-processing-types-h.md#videoprocessing_errorcode) | 如果回调函数对象创建成功，返回VIDEO_PROCESSING_SUCCESS。      <br>如果callback为空，返回VIDEO_PROCESSING_ERROR_INVALID_PARAMETER。      <br>如果内存不足，返回VIDEO_PROCESSING_ERROR_NO_MEMORY。 |

### OH_VideoProcessingCallback_Destroy()

```c
VideoProcessing_ErrorCode OH_VideoProcessingCallback_Destroy(VideoProcessing_Callback* callback)
```

**描述**

销毁回调对象。回调对象在注册之后就可以销毁。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [VideoProcessing_Callback](capi-videoprocessing-videoprocessing-callback.md)* callback | 指向回调对象的指针，建议在回调对象销毁之后将其设置为空指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [VideoProcessing_ErrorCode](capi-video-processing-types-h.md#videoprocessing_errorcode) | 如果回调对象销毁成功，返回VIDEO_PROCESSING_SUCCESS。      <br>如果callback为空，返回VIDEO_PROCESSING_ERROR_INVALID_PARAMETER。 |

### OH_VideoProcessingCallback_BindOnError()

```c
VideoProcessing_ErrorCode OH_VideoProcessingCallback_BindOnError(VideoProcessing_Callback* callback, OH_VideoProcessingCallback_OnError onError)
```

**描述**

绑定回调函数[OH_VideoProcessingCallback_OnError](capi-video-processing-types-h.md#oh_videoprocessingcallback_onerror)到回调对象。绑定完成之后，需要调用 [OH_VideoProcessing_RegisterCallback](capi-video-processing-h.md#oh_videoprocessing_registercallback)，将回调对象注册到视频处理实例，才能使其生效。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [VideoProcessing_Callback](capi-videoprocessing-videoprocessing-callback.md)* callback | 指向回调对象的指针。 |
| [OH_VideoProcessingCallback_OnError](capi-video-processing-types-h.md#oh_videoprocessingcallback_onerror) onError | 回调函数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [VideoProcessing_ErrorCode](capi-video-processing-types-h.md#videoprocessing_errorcode) | 如果函数绑定成功，返回VIDEO_PROCESSING_SUCCESS。      <br>如果callback为空或者onError为空，返回VIDEO_PROCESSING_ERROR_INVALID_PARAMETER。 |

### OH_VideoProcessingCallback_BindOnState()

```c
VideoProcessing_ErrorCode OH_VideoProcessingCallback_BindOnState(VideoProcessing_Callback* callback, OH_VideoProcessingCallback_OnState onState)
```

**描述**

绑定回调函数[OH_VideoProcessingCallback_OnState](capi-video-processing-types-h.md#oh_videoprocessingcallback_onstate)到回调对象。绑定完成之后，需要调用 [OH_VideoProcessing_RegisterCallback](capi-video-processing-h.md#oh_videoprocessing_registercallback)，将回调对象注册到视频处理实例，才能使其生效。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [VideoProcessing_Callback](capi-videoprocessing-videoprocessing-callback.md)* callback | 指向回调对象的指针。 |
| [OH_VideoProcessingCallback_OnState](capi-video-processing-types-h.md#oh_videoprocessingcallback_onstate) onState | 回调函数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [VideoProcessing_ErrorCode](capi-video-processing-types-h.md#videoprocessing_errorcode) | 如果函数绑定成功，返回VIDEO_PROCESSING_SUCCESS。      <br>如果callback为空或者onState为空，返回VIDEO_PROCESSING_ERROR_INVALID_PARAMETER。 |

### OH_VideoProcessingCallback_BindOnNewOutputBuffer()

```c
VideoProcessing_ErrorCode OH_VideoProcessingCallback_BindOnNewOutputBuffer(VideoProcessing_Callback* callback, OH_VideoProcessingCallback_OnNewOutputBuffer onNewOutputBuffer)
```

**描述**

绑定回调函数[OH_VideoProcessingCallback_OnNewOutputBuffer](capi-video-processing-types-h.md#oh_videoprocessingcallback_onnewoutputbuffer)到回调对象。绑定完成之后，需要调用[OH_VideoProcessing_RegisterCallback](capi-video-processing-h.md#oh_videoprocessing_registercallback)，将回调对象注册到视频处理实例，才能使其生效。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [VideoProcessing_Callback](capi-videoprocessing-videoprocessing-callback.md)* callback | 指向回调对象的指针。 |
| [OH_VideoProcessingCallback_OnNewOutputBuffer](capi-video-processing-types-h.md#oh_videoprocessingcallback_onnewoutputbuffer) onNewOutputBuffer | 回调函数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [VideoProcessing_ErrorCode](capi-video-processing-types-h.md#videoprocessing_errorcode) | 如果函数绑定成功，返回VIDEO_PROCESSING_SUCCESS。      <br>如果callback为空，返回VIDEO_PROCESSING_ERROR_INVALID_PARAMETER。 |

### OH_VideoProcessing_IsAutoEffectSupported()

```c
bool OH_VideoProcessing_IsAutoEffectSupported(uint32_t type)
```

**描述**

Query if the autoeffect is supported.

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| uint32_t type | [in] The autoeffect type to query. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| bool | <ul><li><b>true</b> if the autoeffect is supported.</li>      <li><b>false</b> if the autoeffect is not supported.</li></ul> |

### OH_VideoProcessing_UseAutoEffect()

```c
VideoProcessing_ErrorCode OH_VideoProcessing_UseAutoEffect(uint32_t type, bool enable, const char *name)
```

**描述**

Specifies whether the type effect is required in the XComponent named name that will be created.Records the mapping between type, enable, and name in the internal map.This should be called before [OH_VideoProcessing_SetAutoEffectParam](capi-video-processing-h.md#oh_videoprocessing_setautoeffectparam).

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| uint32_t type | [in] Specify AutoEffect to use. |
| bool enable | [in] Enable or disable the type effect in the XComponent named name to be created later. |
| const char *name | [in] Specifies the name of an XComponent. If the current application has multiple XComponents withthe same name, this parameter takes effect only on the first active XComponent. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [VideoProcessing_ErrorCode](capi-video-processing-types-h.md#videoprocessing_errorcode) | <ul><li>[VIDEO_PROCESSING_SUCCESS](capi-video-processing-types-h.md#videoprocessing_errorcode) if the operation is successful.</li>      <li>[VIDEO_PROCESSING_ERROR_INVALID_VALUE](capi-video-processing-types-h.md#videoprocessing_errorcode) if type is not {@link VIDEO_PROCESSING_TYPE_AUTOEFFECT_AISR}      or name is null.</li>      <li>[VIDEO_PROCESSING_ERROR_OPERATION_NOT_PERMITTED](capi-video-processing-types-h.md#videoprocessing_errorcode) if [OH_VideoProcessing_IsAutoEffectSupported](capi-video-processing-h.md#oh_videoprocessing_isautoeffectsupported)      returns false for the type, or the same name has already been registered by calling this function.</li></ul> |

### OH_VideoProcessing_SetAutoEffectParam()

```c
VideoProcessing_ErrorCode OH_VideoProcessing_SetAutoEffectParam(uint32_t type, const char *name, const OH_AVFormat *param)
```

**描述**

Sets parameters for the automatic effect associated with the XComponent. Currently, the AutoEffect only takes effect on the last invoked XComponent.

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| uint32_t type | [in] Specify AutoEffect to use. |
| const char *name | [in] Specifies the name of an XComponent. If the current application has multiple XComponentswith the same name, this parameter takes effect only on the first active XComponent. |
| [const OH_AVFormat](capi-videoprocessing-oh-avformat.md) *param | [in] The parameter according to the type see video_processing_type.h. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [VideoProcessing_ErrorCode](capi-video-processing-types-h.md#videoprocessing_errorcode) | <ul><li>[VIDEO_PROCESSING_SUCCESS](capi-video-processing-types-h.md#videoprocessing_errorcode) if the operation is successful.</li>      <li>[VIDEO_PROCESSING_ERROR_INVALID_VALUE](capi-video-processing-types-h.md#videoprocessing_errorcode) if the name is nullptr or the param value is invalid.</li>      <li>[VIDEO_PROCESSING_ERROR_OPERATION_NOT_PERMITTED](capi-video-processing-types-h.md#videoprocessing_errorcode) if [OH_VideoProcessing_IsAutoEffectSupported](capi-video-processing-h.md#oh_videoprocessing_isautoeffectsupported)      returns false for the type, or name does not match any registered name, or the VPE instance has not been      created or [OH_VideoProcessing_UseAutoEffect](capi-video-processing-h.md#oh_videoprocessing_useautoeffect) has not been called for the name.</li>      <li>[VIDEO_PROCESSING_ERROR_UNKNOWN](capi-video-processing-types-h.md#videoprocessing_errorcode) if an internal algorithm error occurs.</li></ul> |


