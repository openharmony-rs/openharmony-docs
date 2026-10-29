# native_audio_suite_engine.h（系统接口）

## 概述

声明与音频编创相关接口。（包括引擎、管线、节点）。

**库：** libohaudiosuite.so

**系统能力：** SystemCapability.Multimedia.Audio.SuiteEngine

**起始版本：** 22

**系统接口：** 此接口为系统接口。

**相关模块：** [OHAudioSuite](capi-ohaudiosuite.md)

## 汇总

### 函数

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [int32_t OH_AudioSuiteEngine_MetaRenderFrame(OH_AudioSuitePipeline* audioSuitePipeline, OH_AudioSuite_MetaFrame* metaFrame, int32_t* responseAudioSize, int32_t* responseMetaSize, bool* finishedFlag)（系统接口）](#oh_audiosuiteengine_metarenderframe) | - | 应用程序使用此接口进行音频数据和元数据处理。 应用需在metaFrame结构体中指定audioData和metaData指针及其对应的大小（AudioDataSize和metaDataSize）。 <br>处理完成后，实际输出的数据大小将通过responseAudioSize和responseMetaSize返回。<br>**系统接口：** 此接口为系统接口。 |
| [int32_t OH_AudioSuiteNodeBuilderSystem_SetNodeType(OH_AudioNodeBuilder* builder, OH_AudioSuite_SystemNodeType type)（系统接口）](#oh_audiosuitenodebuildersystem_setnodetype) | - | 设置要由构建器创建的音频节点类型。<br>**系统接口：** 此接口为系统接口。 |
| [int32_t OH_AudioSuiteNodeBuilderSystem_SetFormat(OH_AudioNodeBuilder* builder, OH_AudioSuite_SystemNodeFormat audioFormat)（系统接口）](#oh_audiosuitenodebuildersystem_setformat) | - | 设置节点支持的音频格式。<br>**系统接口：** 此接口为系统接口。 |
| [typedef int32_t (\*OH_InputNode_RequestMetaDataCallback)(OH_AudioNode* audioNode, void* userData, OH_AudioSuite_MetaFrame* metaFrame, int32_t* responseMetaDataSize, bool* finished)（系统接口）](#oh_inputnode_requestmetadatacallback) | OH_InputNode_RequestMetaDataCallback | 请求元数据的回调函数，仅[INPUT_NODE_TYPE_DEFAULT](capi-native-audio-suite-base-h.md#oh_audionode_type)支持此设置。 每当应用程序或用户调用[OH_AudioSuiteEngine_MetaRenderFrame](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_metarenderframe)时， 则会触发一次回调。<br>**系统接口：** 此接口为系统接口。 |
| [int32_t OH_AudioSuiteNodeBuilder_SetRequestMetaDataCallback(OH_AudioNodeBuilder* builder, OH_InputNode_RequestMetaDataCallback callback, void* userData)（系统接口）](#oh_audiosuitenodebuilder_setrequestmetadatacallback) | - | 配置当前输入节点构造器的写入音频数据和元数据回调函数。只有[INPUT_NODE_TYPE_DEFAULT](capi-native-audio-suite-base-h.md#oh_audionode_type)支持该设置。<br>**系统接口：** 此接口为系统接口。 |
| [int32_t OH_AudioSuiteEngineSystem_SetAudioFormat(OH_AudioNode* audioNode, OH_AudioSuite_SystemNodeFormat* audioFormat)（系统接口）](#oh_audiosuiteenginesystem_setaudioformat) | - | 设置输入输出节点的音频格式，指定音频源的音频格式输入节点，或为输出节点指定目标音频格式。<br>**系统接口：** 此接口为系统接口。 |
| [int32_t OH_AudioSuiteEngineSystem_SetNodeParam(OH_AudioNode* audioNode, uint8_t* param, uint32_t paramSize)（系统接口）](#oh_audiosuiteenginesystem_setnodeparam) | - | 设置系统节点的参数。<br>**系统接口：** 此接口为系统接口。 |
| [int32_t OH_AudioSuiteEngineSystem_GetNodeParam(OH_AudioNode* audioNode, uint8_t* param, uint32_t paramSize)（系统接口）](#oh_audiosuiteenginesystem_getnodeparam) | - | 获取系统节点的参数。<br>**系统接口：** 此接口为系统接口。 |
| [int32_t OH_AudioSuiteEngineSystem_GetNodeInOutSize(OH_AudioNode* audioNode, uint32_t* inSize, uint32_t* outSize)（系统接口）](#oh_audiosuiteenginesystem_getnodeinoutsize) | - | 获取系统节点的输入和输出帧大小。<br>**系统接口：** 此接口为系统接口。 |

### 变量

| 名称 | 描述 |
| -- | -- |
| int32_t (*OH_InputNode_RequestMetaDataCallback)(OH_AudioNode* audioNode, void* userData, OH_AudioSuite_MetaFrame* metaFrame, int32_t* responseMetaDataSize, bool* finished)（系统接口） | 请求元数据的回调函数，仅[INPUT_NODE_TYPE_DEFAULT](capi-native-audio-suite-base-h.md#oh_audionode_type)支持此设置。 每当应用程序或用户调用[OH_AudioSuiteEngine_MetaRenderFrame](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_metarenderframe)时， 则会触发一次回调。<br>**起始版本：** 26.0.0<br>**系统能力：** SystemCapability.Multimedia.Audio.SuiteEngine<br>**系统接口：** 此接口为系统接口。 |

## 函数说明

### OH_AudioSuiteEngine_MetaRenderFrame()

```c
int32_t OH_AudioSuiteEngine_MetaRenderFrame(OH_AudioSuitePipeline* audioSuitePipeline, OH_AudioSuite_MetaFrame* metaFrame, int32_t* responseAudioSize, int32_t* responseMetaSize, bool* finishedFlag)
```

**描述：**

应用程序使用此接口进行音频数据和元数据处理。 应用需在metaFrame结构体中指定audioData和metaData指针及其对应的大小（AudioDataSize和metaDataSize）。 <br>处理完成后，实际输出的数据大小将通过responseAudioSize和responseMetaSize返回。

**系统能力：** SystemCapability.Multimedia.Audio.SuiteEngine

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSuitePipeline](capi-ohaudiosuite-oh-audiosuitepipeline.md)* audioSuitePipeline | 音频编创管线句柄。通过[OH_AudioSuiteEngine_CreatePipeline](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_createpipeline)获取。 |
| [OH_AudioSuite_MetaFrame](capi-ohaudiosuite-oh-audiosuite-metaframe-sys.md)* metaFrame | 音频元数据帧结构体指针。 |
| int32_t* responseAudioSize | 接口实际写入的音频数据的大小，单位是字节(Byte)。 |
| int32_t* responseMetaSize | 接口实际写入的元数据的大小，单位是字节(Byte)。 |
| bool* finishedFlag | 该标志用于向用户指示是否已完成所有数据处理。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | <ul> <li>[AUDIOSUITE_SUCCESS](capi-native-audio-suite-base-h.md#oh_audiosuite_result) 函数执行成功。</li> <li>202 非系统应用调用了此系统API。</li> <li>[AUDIOSUITE_ERROR_INVALID_PARAM](capi-native-audio-suite-base-h.md#oh_audiosuite_result) 参数为空指针或其他非法值。</li> <li>[AUDIOSUITE_ERROR_PIPELINE_NOT_EXIST](capi-native-audio-suite-base-h.md#oh_audiosuite_result) 管线不存在或已被销毁。</li> <li>[AUDIOSUITE_ERROR_INVALID_STATE](capi-native-audio-suite-base-h.md#oh_audiosuite_result) 管线不在运行状态。</li> <li>[AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION](capi-native-audio-suite-base-h.md#oh_audiosuite_result)管线渲染已完成（之前调用该接口时finishedFlag已写入为true）。</li> <li>[AUDIOSUITE_ERROR_TIMEOUT](capi-native-audio-suite-base-h.md#oh_audiosuite_result) 操作处理超时。</li> <li>[AUDIOSUITE_ERROR_SYSTEM](capi-native-audio-suite-base-h.md#oh_audiosuite_result) 系统发生其他异常。</li> </ul> |

### OH_AudioSuiteNodeBuilderSystem_SetNodeType()

```c
int32_t OH_AudioSuiteNodeBuilderSystem_SetNodeType(OH_AudioNodeBuilder* builder, OH_AudioSuite_SystemNodeType type)
```

**描述：**

设置要由构建器创建的音频节点类型。

**系统能力：** SystemCapability.Multimedia.Audio.SuiteEngine

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioNodeBuilder](capi-ohaudiosuite-oh-audionodebuilder.md)* builder | 音频编创节点构造器句柄。通过[OH_AudioSuiteNodeBuilder_Create](capi-native-audio-suite-engine-h.md#oh_audiosuitenodebuilder_create)获取。 |
| OH_AudioSuite_SystemNodeType type | [OH_AudioSuite_SystemNodeType](capi-native-audio-suite-base-h.md#oh_audiosuite_systemnodetype)音频系统节点类型。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | <ul> <li>[AUDIOSUITE_SUCCESS](capi-native-audio-suite-base-h.md#oh_audiosuite_result) 配置节点类型成功。</li> <li>202 非系统应用调用了此系统API。</li> <li>[AUDIOSUITE_ERROR_INVALID_PARAM](capi-native-audio-suite-base-h.md#oh_audiosuite_result) 参数无效，例如，builder为空指针。</li> </ul> |

### OH_AudioSuiteNodeBuilderSystem_SetFormat()

```c
int32_t OH_AudioSuiteNodeBuilderSystem_SetFormat(OH_AudioNodeBuilder* builder, OH_AudioSuite_SystemNodeFormat audioFormat)
```

**描述：**

设置节点支持的音频格式。

**系统能力：** SystemCapability.Multimedia.Audio.SuiteEngine

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioNodeBuilder](capi-ohaudiosuite-oh-audionodebuilder.md)* builder | 音频编创节点构造器句柄。通过[OH_AudioSuiteNodeBuilder_Create](capi-native-audio-suite-engine-h.md#oh_audiosuitenodebuilder_create)获取。 |
| [OH_AudioSuite_SystemNodeFormat](capi-ohaudiosuite-oh-audiosuite-systemnodeformat-sys.md) audioFormat | 音频节点格式。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | <ul> <li>[AUDIOSUITE_SUCCESS](capi-native-audio-suite-base-h.md#oh_audiosuite_result) 函数执行成功。</li> <li>202 非系统应用调用了此系统API。</li> <li>[AUDIOSUITE_ERROR_INVALID_PARAM](capi-native-audio-suite-base-h.md#oh_audiosuite_result) 参数无效，例如，builder为空指针。</li> <li>[AUDIOSUITE_ERROR_UNSUPPORTED_FORMAT](capi-native-audio-suite-base-h.md#oh_audiosuite_result) audioFormat中的某种音频格式不支持。</li> </ul> |

### OH_InputNode_RequestMetaDataCallback()

```c
typedef int32_t (*OH_InputNode_RequestMetaDataCallback)(OH_AudioNode* audioNode, void* userData, OH_AudioSuite_MetaFrame* metaFrame, int32_t* responseMetaDataSize, bool* finished)
```

**描述：**

请求元数据的回调函数，仅[INPUT_NODE_TYPE_DEFAULT](capi-native-audio-suite-base-h.md#oh_audionode_type)支持此设置。 每当应用程序或用户调用[OH_AudioSuiteEngine_MetaRenderFrame](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_metarenderframe)时， 则会触发一次回调。

**系统能力：** SystemCapability.Multimedia.Audio.SuiteEngine

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioNode](capi-ohaudiosuite-oh-audionode.md)* audioNode | 音频编创节点句柄。通过[OH_AudioSuiteEngine_CreateNode](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_createnode)获取。 |
| void* userData | 由用户传递的用户数据指针。 |
| [OH_AudioSuite_MetaFrame](capi-ohaudiosuite-oh-audiosuite-metaframe-sys.md)* metaFrame | 音频元数据帧结构体指针。 |
| int32_t* responseMetaDataSize | 应用程序实际写入的元数据的大小，单位是字节(Byte)。 |
| bool* finished | 此布尔值表示是否已成功写入所有音频数据。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 写入audio data缓冲区的有效音频数据长度，单位为字节(Byte)。<br>返回值范围为[0, metaFrame->AudioDataSize]。 |

### OH_AudioSuiteNodeBuilder_SetRequestMetaDataCallback()

```c
int32_t OH_AudioSuiteNodeBuilder_SetRequestMetaDataCallback(OH_AudioNodeBuilder* builder, OH_InputNode_RequestMetaDataCallback callback, void* userData)
```

**描述：**

配置当前输入节点构造器的写入音频数据和元数据回调函数。只有[INPUT_NODE_TYPE_DEFAULT](capi-native-audio-suite-base-h.md#oh_audionode_type)支持该设置。

**系统能力：** SystemCapability.Multimedia.Audio.SuiteEngine

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioNodeBuilder](capi-ohaudiosuite-oh-audionodebuilder.md)* builder | 音频编创节点构造器句柄。通过[OH_AudioSuiteNodeBuilder_Create](capi-native-audio-suite-engine-h.md#oh_audiosuitenodebuilder_create)获取。 |
| [OH_InputNode_RequestMetaDataCallback](capi-native-audio-suite-engine-h.md#oh_inputnode_requestmetadatacallback) callback | 用户自定义数据，会在callback函数中将地址传入给用户，如果不使用，可以传入空指针。 |
| void* userData | 指向将传递给回调函数的应用程序数据结构的指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | <ul> <li>[AUDIOSUITE_SUCCESS](capi-native-audio-suite-base-h.md#oh_audiosuite_result) 函数执行成功。</li> <li>202 非系统应用调用了此系统API。</li> <li>[AUDIOSUITE_ERROR_INVALID_PARAM](capi-native-audio-suite-base-h.md#oh_audiosuite_result) 参数非法，例如，参数builder为空指针。</li> <li>[AUDIOSUITE_ERROR_TIMEOUT](capi-native-audio-suite-base-h.md#oh_audiosuite_result) 操作处理超时。</li> <li>[AUDIOSUITE_ERROR_SYSTEM](capi-native-audio-suite-base-h.md#oh_audiosuite_result) 系统发生其他异常。</li> </ul> |

### OH_AudioSuiteEngineSystem_SetAudioFormat()

```c
int32_t OH_AudioSuiteEngineSystem_SetAudioFormat(OH_AudioNode* audioNode, OH_AudioSuite_SystemNodeFormat* audioFormat)
```

**描述：**

设置输入输出节点的音频格式，指定音频源的音频格式输入节点，或为输出节点指定目标音频格式。

**系统能力：** SystemCapability.Multimedia.Audio.SuiteEngine

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioNode](capi-ohaudiosuite-oh-audionode.md)* audioNode | 音频编创节点句柄。通过[OH_AudioSuiteEngine_CreateNode](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_createnode)获取。 |
| [OH_AudioSuite_SystemNodeFormat](capi-ohaudiosuite-oh-audiosuite-systemnodeformat-sys.md)* audioFormat | 音频格式。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | <ul> <li>[AUDIOSUITE_SUCCESS](capi-native-audio-suite-base-h.md#oh_audiosuite_result) 函数执行成功。</li> <li>202 非系统应用调用了此系统API。</li> <li>[AUDIOSUITE_ERROR_INVALID_PARAM](capi-native-audio-suite-base-h.md#oh_audiosuite_result) 参数为空指针或其他非法值。</li> <li>[AUDIOSUITE_ERROR_NODE_NOT_EXIST](capi-native-audio-suite-base-h.md#oh_audiosuite_result) 节点不存在或已被销毁。</li> <li>[AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION](capi-native-audio-suite-base-h.md#oh_audiosuite_result) 节点是效果节点。</li> <li>[AUDIOSUITE_ERROR_INVALID_STATE](capi-native-audio-suite-base-h.md#oh_audiosuite_result) 管线不在停止状态。</li> <li>[AUDIOSUITE_ERROR_TIMEOUT](capi-native-audio-suite-base-h.md#oh_audiosuite_result) 操作处理超时。</li> <li>[AUDIOSUITE_ERROR_SYSTEM](capi-native-audio-suite-base-h.md#oh_audiosuite_result) 系统发生其他异常。</li> </ul> |

### OH_AudioSuiteEngineSystem_SetNodeParam()

```c
int32_t OH_AudioSuiteEngineSystem_SetNodeParam(OH_AudioNode* audioNode, uint8_t* param, uint32_t paramSize)
```

**描述：**

设置系统节点的参数。

**系统能力：** SystemCapability.Multimedia.Audio.SuiteEngine

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioNode](capi-ohaudiosuite-oh-audionode.md)* audioNode | 音频编创节点句柄。通过[OH_AudioSuiteEngine_CreateNode](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_createnode)获取。 |
| uint8_t* param | 参数缓冲区。 |
| uint32_t paramSize | 参数缓冲区大小。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | <ul> <li>[AUDIOSUITE_SUCCESS](capi-native-audio-suite-base-h.md#oh_audiosuite_result) 函数执行成功。</li> <li>202 非系统应用调用了此系统API。</li> <li>[AUDIOSUITE_ERROR_NODE_NOT_EXIST](capi-native-audio-suite-base-h.md#oh_audiosuite_result) 节点不存在或已被销毁。</li> <li>[AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION](capi-native-audio-suite-base-h.md#oh_audiosuite_result) 节点为非系统类型节点。</li> <li>[AUDIOSUITE_ERROR_INVALID_PARAM](capi-native-audio-suite-base-h.md#oh_audiosuite_result) 参数为空指针或其他非法值。</li> <li>[AUDIOSUITE_ERROR_TIMEOUT](capi-native-audio-suite-base-h.md#oh_audiosuite_result) 操作处理超时。</li> <li>[AUDIOSUITE_ERROR_SYSTEM](capi-native-audio-suite-base-h.md#oh_audiosuite_result) 系统发生其他异常。</li> </ul> |

### OH_AudioSuiteEngineSystem_GetNodeParam()

```c
int32_t OH_AudioSuiteEngineSystem_GetNodeParam(OH_AudioNode* audioNode, uint8_t* param, uint32_t paramSize)
```

**描述：**

获取系统节点的参数。

**系统能力：** SystemCapability.Multimedia.Audio.SuiteEngine

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioNode](capi-ohaudiosuite-oh-audionode.md)* audioNode | 音频编创节点句柄。通过[OH_AudioSuiteEngine_CreateNode](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_createnode)获取。 |
| uint8_t* param | 参数缓冲区。 |
| uint32_t paramSize | 参数缓冲区大小。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | <ul> <li>[AUDIOSUITE_SUCCESS](capi-native-audio-suite-base-h.md#oh_audiosuite_result) 函数执行成功。</li> <li>202 非系统应用调用了此系统API。</li> <li>[AUDIOSUITE_ERROR_NODE_NOT_EXIST](capi-native-audio-suite-base-h.md#oh_audiosuite_result) 音频节点不存在或已被销毁。</li> <li>[AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION](capi-native-audio-suite-base-h.md#oh_audiosuite_result) 节点为非系统类型节点。</li> <li>[AUDIOSUITE_ERROR_INVALID_PARAM](capi-native-audio-suite-base-h.md#oh_audiosuite_result) 参数为空指针或其他非法值。</li> <li>[AUDIOSUITE_ERROR_TIMEOUT](capi-native-audio-suite-base-h.md#oh_audiosuite_result) 操作处理超时。</li> <li>[AUDIOSUITE_ERROR_SYSTEM](capi-native-audio-suite-base-h.md#oh_audiosuite_result) 系统发生其他异常。</li> </ul> |

### OH_AudioSuiteEngineSystem_GetNodeInOutSize()

```c
int32_t OH_AudioSuiteEngineSystem_GetNodeInOutSize(OH_AudioNode* audioNode, uint32_t* inSize, uint32_t* outSize)
```

**描述：**

获取系统节点的输入和输出帧大小。

**系统能力：** SystemCapability.Multimedia.Audio.SuiteEngine

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioNode](capi-ohaudiosuite-oh-audionode.md)* audioNode | 音频编创节点句柄。通过[OH_AudioSuiteEngine_CreateNode](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_createnode)获取。 |
| uint32_t* inSize | 输入帧大小，单位为字节(Byte)。 |
| uint32_t* outSize | 输出帧大小，单位为字节(Byte)。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | <ul> <li>[AUDIOSUITE_SUCCESS](capi-native-audio-suite-base-h.md#oh_audiosuite_result) 函数执行成功。</li> <li>202 非系统应用调用了此系统API。</li> <li>[AUDIOSUITE_ERROR_NODE_NOT_EXIST](capi-native-audio-suite-base-h.md#oh_audiosuite_result) 音频节点不存在或已被销毁。</li> <li>[AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION](capi-native-audio-suite-base-h.md#oh_audiosuite_result) 节点为非系统类型节点。</li> <li>[AUDIOSUITE_ERROR_INVALID_PARAM](capi-native-audio-suite-base-h.md#oh_audiosuite_result) 参数为空指针或其他非法值。</li> <li>[AUDIOSUITE_ERROR_TIMEOUT](capi-native-audio-suite-base-h.md#oh_audiosuite_result) 操作处理超时。</li> <li>[AUDIOSUITE_ERROR_SYSTEM](capi-native-audio-suite-base-h.md#oh_audiosuite_result) 系统发生其他异常。</li> </ul> |


