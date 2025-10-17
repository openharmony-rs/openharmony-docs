# native_avcodec_audiodecoder.h

<!--Kit: AVCodec Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @mr-chencxy-->
<!--Designer: @dpy2650--->
<!--Tester: @baotianhao-->
<!--Adviser: @w_Machine_cc-->

## 概述

音频解码Native API的声明。

**引用文件：** <multimedia/player_framework/native_avcodec_audiodecoder.h>

**库：** libnative_media_adec.so

**系统能力：** SystemCapability.Multimedia.Media.AudioDecoder

**起始版本：** 9

**废弃版本：** 11

**替代建议：** 当前模块下的接口均已废弃，开发者可使用[native_avcodec_audiocodec.h](capi-native-avcodec-audiocodec-h.md)完成对应功能开发，单个接口的替代关系可查阅具体的接口说明。

**相关模块：** [AudioDecoder](capi-audiodecoder.md)

## 汇总

### 函数

| 名称 | 描述 |
| -- | -- |
| [OH_AVCodec *OH_AudioDecoder_CreateByMime(const char *mime)](#oh_audiodecoder_createbymime) | 根据MIME类型创建音频解码器实例，大多数场景下建议使用此方式。(API11废弃) |
| [OH_AVCodec *OH_AudioDecoder_CreateByName(const char *name)](#oh_audiodecoder_createbyname) | 通过音频解码器名称创建音频解码器实例，使用此接口的前提是知道解码器的确切名称。(API11废弃) |
| [OH_AVErrCode OH_AudioDecoder_Destroy(OH_AVCodec *codec)](#oh_audiodecoder_destroy) | 清理解码器内部资源，销毁解码器实例。(API11废弃) |
| [OH_AVErrCode OH_AudioDecoder_SetCallback(OH_AVCodec *codec, OH_AVCodecAsyncCallback callback, void *userData)](#oh_audiodecoder_setcallback) | 设置异步回调函数，使应用可以响应音频解码器生成的事件。在调用Prepare之前，必须调用此接口。(API11废弃) |
| [OH_AVErrCode OH_AudioDecoder_Configure(OH_AVCodec *codec, OH_AVFormat *format)](#oh_audiodecoder_configure) | 要配置音频解码器，通常需要配置从容器中提取的音频描述信息。在调用Prepare之前，必须调用此接口。(API11废弃) |
| [OH_AVErrCode OH_AudioDecoder_Prepare(OH_AVCodec *codec)](#oh_audiodecoder_prepare) | 准备解码器的内部资源，在调用此接口之前必须调用Configure接口。(API11废弃) |
| [OH_AVErrCode OH_AudioDecoder_Start(OH_AVCodec *codec)](#oh_audiodecoder_start) | 调用此接口启动解码器，在Prepare成功后执行。启动后，解码器将开始上报OH_AVCodecOnNeedInputData事件。(API11废弃) |
| [OH_AVErrCode OH_AudioDecoder_Stop(OH_AVCodec *codec)](#oh_audiodecoder_stop) | 停止解码器。<br>停止后，您可以通过Start重新进入已启动状态，但需要注意的是，如果解码器之前已输入数据，则需要重新输入解码器数据。(API11废弃) |
| [OH_AVErrCode OH_AudioDecoder_Flush(OH_AVCodec *codec)](#oh_audiodecoder_flush) | 清除解码器中缓存的输入和输出数据。<br>调用此接口后，以前通过异步回调上报的所有缓冲区索引都将失效，请确保不要访问这些索引对应的缓冲区。(API11废弃) |
| [OH_AVErrCode OH_AudioDecoder_Reset(OH_AVCodec *codec)](#oh_audiodecoder_reset) | 重置解码器。如果要继续解码，需要再次调用Configure接口配置解码器实例。(API11废弃) |
| [OH_AVFormat *OH_AudioDecoder_GetOutputDescription(OH_AVCodec *codec)](#oh_audiodecoder_getoutputdescription) | 获取解码器输出数据的描述信息。<br>需要注意的是，返回值所指向的OH_AVFormat实例的生命周期需要调用者手动释放。(API11废弃) |
| [OH_AVErrCode OH_AudioDecoder_SetParameter(OH_AVCodec *codec, OH_AVFormat *format)](#oh_audiodecoder_setparameter) | 配置解码器的动态参数。<br>注意：该接口必须在解码器启动后才能调用。另外，参数配置错误可能会导致解码失败。(API11废弃) |
| [OH_AVErrCode OH_AudioDecoder_PushInputData(OH_AVCodec *codec, uint32_t index, OH_AVCodecBufferAttr attr)](#oh_audiodecoder_pushinputdata) | 通知音频解码器已完成对index所对应缓冲区进行输入数据的填充。<br>[OH_AVCodecOnNeedInputData](capi-native-avcodec-base-h.md#oh_avcodeconneedinputdata)回调将报告可用的输入缓冲区和相应的索引值。一旦具有指定索引的缓冲区提交到音频解码器，则无法再次访问此缓冲区，直到再次收到[OH_AVCodecOnNeedInputData](capi-native-avcodec-base-h.md#oh_avcodeconneedinputdata)回调，收到相同索引时此缓冲区才可使用。<br>此外，对于某些解码器，需要在开始时向解码器输入特定配置参数，以初始化解码器的解码过程。(API11废弃) |
| [OH_AVErrCode OH_AudioDecoder_FreeOutputData(OH_AVCodec *codec, uint32_t index)](#oh_audiodecoder_freeoutputdata) | 将处理后的输出缓冲区返回给解码器。(API11废弃) |
| [OH_AVErrCode OH_AudioDecoder_IsValid(OH_AVCodec *codec, bool *isValid)](#oh_audiodecoder_isvalid) | 检查当前解码器实例是否有效，可用于后台故障恢复或应用程序从后台恢复时检测解码器有效状态。(API11废弃) |

## 函数说明

### OH_AudioDecoder_CreateByMime()

```
OH_AVCodec *OH_AudioDecoder_CreateByMime(const char *mime)
```

**描述**

根据MIME类型创建音频解码器实例，大多数场景下建议使用此方式。

**系统能力：** SystemCapability.Multimedia.Media.AudioDecoder

**起始版本：** 9

**废弃版本：** 11

**替代接口：** [OH_AudioCodec_CreateByMime](capi-native-avcodec-audiocodec-h.md#oh_audiocodec_createbymime)

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char *mime | MIME类型描述字符串，请参阅[AVCODEC_MIMETYPE](capi-native-avcodec-base-h.md#变量)。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AVCodec *](capi-codecbase-oh-avcodec.md) | 返回指向OH_AVCodec实例的指针。 |

### OH_AudioDecoder_CreateByName()

```
OH_AVCodec *OH_AudioDecoder_CreateByName(const char *name)
```

**描述**

通过音频解码器名称创建音频解码器实例，使用此接口的前提是知道解码器的确切名称。

**系统能力：** SystemCapability.Multimedia.Media.AudioDecoder

**起始版本：** 9

**废弃版本：** 11

**替代接口：** [OH_AudioCodec_CreateByName](capi-native-avcodec-audiocodec-h.md#oh_audiocodec_createbyname)

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char *name | 音频解码器名称。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AVCodec *](capi-codecbase-oh-avcodec.md) | 返回指向OH_AVCodec实例的指针。 |

### OH_AudioDecoder_Destroy()

```
OH_AVErrCode OH_AudioDecoder_Destroy(OH_AVCodec *codec)
```

**描述**

清理解码器内部资源，销毁解码器实例。

**系统能力：** SystemCapability.Multimedia.Media.AudioDecoder

**起始版本：** 9

**废弃版本：** 11

**替代接口：** [OH_AudioCodec_Destroy](capi-native-avcodec-audiocodec-h.md#oh_audiocodec_destroy)

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AVCodec](capi-codecbase-oh-avcodec.md) *codec | 指向OH_AVCodec实例的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AVErrCode](capi-native-averrors-h.md#oh_averrcode) | 如果执行成功，则返回AV_ERR_OK，否则返回特定错误代码。 |

### OH_AudioDecoder_SetCallback()

```
OH_AVErrCode OH_AudioDecoder_SetCallback(OH_AVCodec *codec, OH_AVCodecAsyncCallback callback, void *userData)
```

**描述**

设置异步回调函数，使应用可以响应音频解码器生成的事件。在调用Prepare之前，必须调用此接口。

**系统能力：** SystemCapability.Multimedia.Media.AudioDecoder

**起始版本：** 9

**废弃版本：** 11

**替代接口：** [OH_AudioCodec_RegisterCallback](capi-native-avcodec-audiocodec-h.md#oh_audiocodec_registercallback)

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AVCodec](capi-codecbase-oh-avcodec.md) *codec | 指向OH_AVCodec实例的指针。 |
| [OH_AVCodecAsyncCallback](capi-codecbase-oh-avcodecasynccallback.md) callback | 所有回调函数的集合。 |
| void *userData | 用户特定数据。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AVErrCode](capi-native-averrors-h.md#oh_averrcode) | 如果执行成功，则返回AV_ERR_OK，否则返回特定错误代码。 |

### OH_AudioDecoder_Configure()

```
OH_AVErrCode OH_AudioDecoder_Configure(OH_AVCodec *codec, OH_AVFormat *format)
```

**描述**

要配置音频解码器，通常需要配置从容器中提取的音频描述信息。在调用Prepare之前，必须调用此接口。

**系统能力：** SystemCapability.Multimedia.Media.AudioDecoder

**起始版本：** 9

**废弃版本：** 11

**替代接口：** [OH_AudioCodec_Configure](capi-native-avcodec-audiocodec-h.md#oh_audiocodec_configure)

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AVCodec](capi-codecbase-oh-avcodec.md) *codec | 指向OH_AVCodec实例的指针。 |
| [OH_AVFormat](capi-core-oh-avformat.md) *format | 指向OH_AVFormat的指针，给出要解码的音频轨道的描述。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AVErrCode](capi-native-averrors-h.md#oh_averrcode) | 如果执行成功，则返回AV_ERR_OK，否则返回特定错误代码。 |

### OH_AudioDecoder_Prepare()

```
OH_AVErrCode OH_AudioDecoder_Prepare(OH_AVCodec *codec)
```

**描述**

准备解码器的内部资源，在调用此接口之前必须调用Configure接口。

**系统能力：** SystemCapability.Multimedia.Media.AudioDecoder

**起始版本：** 9

**废弃版本：** 11

**替代接口：** [OH_AudioCodec_Prepare](capi-native-avcodec-audiocodec-h.md#oh_audiocodec_prepare)

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AVCodec](capi-codecbase-oh-avcodec.md) *codec | 指向OH_AVCodec实例的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AVErrCode](capi-native-averrors-h.md#oh_averrcode) | 如果执行成功，则返回AV_ERR_OK，否则返回特定错误代码。 |

### OH_AudioDecoder_Start()

```
OH_AVErrCode OH_AudioDecoder_Start(OH_AVCodec *codec)
```

**描述**

调用此接口启动解码器，在Prepare成功后执行。启动后，解码器将开始上报OH_AVCodecOnNeedInputData事件。

**系统能力：** SystemCapability.Multimedia.Media.AudioDecoder

**起始版本：** 9

**废弃版本：** 11

**替代接口：** [OH_AudioCodec_Start](capi-native-avcodec-audiocodec-h.md#oh_audiocodec_start)

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AVCodec](capi-codecbase-oh-avcodec.md) *codec | 指向OH_AVCodec实例的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AVErrCode](capi-native-averrors-h.md#oh_averrcode) | 如果执行成功，则返回AV_ERR_OK，否则返回特定错误代码。 |

### OH_AudioDecoder_Stop()

```
OH_AVErrCode OH_AudioDecoder_Stop(OH_AVCodec *codec)
```

**描述**

停止解码器。<br>停止后，您可以通过Start重新进入已启动状态，但需要注意的是，如果解码器之前已输入数据，则需要重新输入解码器数据。

**系统能力：** SystemCapability.Multimedia.Media.AudioDecoder

**起始版本：** 9

**废弃版本：** 11

**替代接口：** [OH_AudioCodec_Stop](capi-native-avcodec-audiocodec-h.md#oh_audiocodec_stop)

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AVCodec](capi-codecbase-oh-avcodec.md) *codec | 指向OH_AVCodec实例的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AVErrCode](capi-native-averrors-h.md#oh_averrcode) | 如果执行成功，则返回AV_ERR_OK，否则返回特定错误代码。 |

### OH_AudioDecoder_Flush()

```
OH_AVErrCode OH_AudioDecoder_Flush(OH_AVCodec *codec)
```

**描述**

清除解码器中缓存的输入和输出数据。<br>调用此接口后，以前通过异步回调上报的所有缓冲区索引都将失效，请确保不要访问这些索引对应的缓冲区。

**系统能力：** SystemCapability.Multimedia.Media.AudioDecoder

**起始版本：** 9

**废弃版本：** 11

**替代接口：** [OH_AudioCodec_Flush](capi-native-avcodec-audiocodec-h.md#oh_audiocodec_flush)

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AVCodec](capi-codecbase-oh-avcodec.md) *codec | 指向OH_AVCodec实例的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AVErrCode](capi-native-averrors-h.md#oh_averrcode) | 如果执行成功，则返回AV_ERR_OK，否则返回特定错误代码。 |

### OH_AudioDecoder_Reset()

```
OH_AVErrCode OH_AudioDecoder_Reset(OH_AVCodec *codec)
```

**描述**

重置解码器。如果要继续解码，需要再次调用Configure接口配置解码器实例。

**系统能力：** SystemCapability.Multimedia.Media.AudioDecoder

**起始版本：** 9

**废弃版本：** 11

**替代接口：** [OH_AudioCodec_Reset](capi-native-avcodec-audiocodec-h.md#oh_audiocodec_reset)

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AVCodec](capi-codecbase-oh-avcodec.md) *codec | 指向OH_AVCodec实例的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AVErrCode](capi-native-averrors-h.md#oh_averrcode) | 如果执行成功，则返回AV_ERR_OK，否则返回特定错误代码。 |

### OH_AudioDecoder_GetOutputDescription()

```
OH_AVFormat *OH_AudioDecoder_GetOutputDescription(OH_AVCodec *codec)
```

**描述**

获取解码器输出数据的描述信息。<br>需要注意的是，返回值所指向的OH_AVFormat实例的生命周期需要调用者手动释放。

**系统能力：** SystemCapability.Multimedia.Media.AudioDecoder

**起始版本：** 9

**废弃版本：** 11

**替代接口：** [OH_AudioCodec_GetOutputDescription](capi-native-avcodec-audiocodec-h.md#oh_audiocodec_getoutputdescription)

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AVCodec](capi-codecbase-oh-avcodec.md) *codec | 指向OH_AVCodec实例的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AVFormat](capi-core-oh-avformat.md) * | 返回OH_AVFormat句柄指针，生命周期将使用下一个GetOutputDescription刷新，或使用OH_AVCodec销毁。 |

### OH_AudioDecoder_SetParameter()

```
OH_AVErrCode OH_AudioDecoder_SetParameter(OH_AVCodec *codec, OH_AVFormat *format)
```

**描述**

配置解码器的动态参数。<br>注意：该接口必须在解码器启动后才能调用。另外，参数配置错误可能会导致解码失败。

**系统能力：** SystemCapability.Multimedia.Media.AudioDecoder

**起始版本：** 9

**废弃版本：** 11

**替代接口：** [OH_AudioCodec_SetParameter](capi-native-avcodec-audiocodec-h.md#oh_audiocodec_setparameter)

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AVCodec](capi-codecbase-oh-avcodec.md) *codec | 指向OH_AVCodec实例的指针。 |
| [OH_AVFormat](capi-core-oh-avformat.md) *format | OH_AVFormat句柄指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AVErrCode](capi-native-averrors-h.md#oh_averrcode) | 如果执行成功，则返回AV_ERR_OK，否则返回特定错误代码。 |

### OH_AudioDecoder_PushInputData()

```
OH_AVErrCode OH_AudioDecoder_PushInputData(OH_AVCodec *codec, uint32_t index, OH_AVCodecBufferAttr attr)
```

**描述**

通知音频解码器已完成对index所对应缓冲区进行输入数据的填充。<br>[OH_AVCodecOnNeedInputData](capi-native-avcodec-base-h.md#oh_avcodeconneedinputdata)回调将报告可用的输入缓冲区和相应的索引值。一旦具有指定索引的缓冲区提交到音频解码器，则无法再次访问此缓冲区，直到再次收到[OH_AVCodecOnNeedInputData](capi-native-avcodec-base-h.md#oh_avcodeconneedinputdata)回调，收到相同索引时此缓冲区才可使用。<br>此外，对于某些解码器，需要在开始时向解码器输入特定配置参数，以初始化解码器的解码过程。

**系统能力：** SystemCapability.Multimedia.Media.AudioDecoder

**起始版本：** 9

**废弃版本：** 11

**替代接口：** [OH_AudioCodec_PushInputBuffer](capi-native-avcodec-audiocodec-h.md#oh_audiocodec_pushinputbuffer)

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AVCodec](capi-codecbase-oh-avcodec.md) *codec | 指向OH_AVCodec实例的指针。 |
| uint32_t index | 输入缓冲区Buffer对应的索引值。 |
| [OH_AVCodecBufferAttr](capi-core-oh-avcodecbufferattr.md) attr | 描述缓冲区中包含的数据的信息。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AVErrCode](capi-native-averrors-h.md#oh_averrcode) | 如果执行成功，则返回AV_ERR_OK，否则返回特定错误代码。 |

### OH_AudioDecoder_FreeOutputData()

```
OH_AVErrCode OH_AudioDecoder_FreeOutputData(OH_AVCodec *codec, uint32_t index)
```

**描述**

将处理后的输出缓冲区返回给解码器。

**系统能力：** SystemCapability.Multimedia.Media.AudioDecoder

**起始版本：** 9

**废弃版本：** 11

**替代接口：** [OH_AudioCodec_FreeOutputBuffer](capi-native-avcodec-audiocodec-h.md#oh_audiocodec_freeoutputbuffer)

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AVCodec](capi-codecbase-oh-avcodec.md) *codec | 指向OH_AVCodec实例的指针。 |
| uint32_t index | 输出缓冲区Buffer对应的索引值。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AVErrCode](capi-native-averrors-h.md#oh_averrcode) | 如果执行成功，则返回AV_ERR_OK，否则返回特定错误代码。 |

### OH_AudioDecoder_IsValid()

```
OH_AVErrCode OH_AudioDecoder_IsValid(OH_AVCodec *codec, bool *isValid)
```

**描述**

检查当前解码器实例是否有效，可用于后台故障恢复或应用程序从后台恢复时检测解码器有效状态。

**系统能力：** SystemCapability.Multimedia.Media.AudioDecoder

**起始版本：** 10

**废弃版本：** 11

**替代接口：** [OH_AudioCodec_IsValid](capi-native-avcodec-audiocodec-h.md#oh_audiocodec_isvalid)

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AVCodec](capi-codecbase-oh-avcodec.md) *codec | 指向OH_AVCodec实例的指针。 |
| bool *isValid | 指向布尔类型的指针，true：解码器实例有效，false：解码器实例无效。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AVErrCode](capi-native-averrors-h.md#oh_averrcode) | 如果执行成功，则返回AV_ERR_OK，否则返回特定错误代码。 |
