# native_audio_suite_engine.h(System API)

## Overview

Declare audio suite engine related interfaces.<br> This file provides interfaces for creating audioSuiteEngine, audioSuitePipeline, and audioSuiteNode.

**Library**: libohaudiosuite.so

**System capability**: SystemCapability.Multimedia.Audio.SuiteEngine

**Since**: 22

**System API:** This is a system API.

**Related module**: [OHAudioSuite](capi-ohaudiosuite.md)

## Summary

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [int32_t OH_AudioSuiteEngine_MetaRenderFrame(OH_AudioSuitePipeline* audioSuitePipeline, OH_AudioSuite_MetaFrame* metaFrame, int32_t* responseAudioSize, int32_t* responseMetaSize, bool* finishedFlag)(System API)](#oh_audiosuiteengine_metarenderframe) | - | The application uses this interface for audio data and meta data processing.<br> The application needs to set the audioData and metaData pointers in the metaFrame structure, as well as the data sizes (audioDataSize and metaDataSize). The actual sizes of the processed data will be returned through responseAudioSize and responseMetaSize.**System API:** This is a system API. |
| [int32_t OH_AudioSuiteNodeBuilderSystem_SetNodeType(OH_AudioNodeBuilder* builder, OH_AudioSuite_SystemNodeType type)(System API)](#oh_audiosuitenodebuildersystem_setnodetype) | - | Set the audio node type to be created by the builder.**System API:** This is a system API. |
| [int32_t OH_AudioSuiteNodeBuilderSystem_SetFormat(OH_AudioNodeBuilder* builder, OH_AudioSuite_SystemNodeFormat audioFormat)(System API)](#oh_audiosuitenodebuildersystem_setformat) | - | Set the audio format supported by the node.**System API:** This is a system API. |
| [typedef int32_t (\*OH_InputNode_RequestMetaDataCallback)(OH_AudioNode* audioNode, void* userData, OH_AudioSuite_MetaFrame* metaFrame, int32_t* responseMetaDataSize, bool* finished)(System API)](#oh_inputnode_requestmetadatacallback) | OH_InputNode_RequestMetaDataCallback | Callback function of request meta data, Only {@link INPUT_NODE_TYPE_DEFAULT} support this setting.<br> Each time the application or user invokes [OH_AudioSuiteEngine_MetaRenderFrame](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_metarenderframe), the callback is triggered once.**System API:** This is a system API. |
| [int32_t OH_AudioSuiteNodeBuilder_SetRequestMetaDataCallback(OH_AudioNodeBuilder* builder, OH_InputNode_RequestMetaDataCallback callback, void* userData)(System API)](#oh_audiosuitenodebuilder_setrequestmetadatacallback) | - | Set input node request meta data callback with frame structure, Only {@link INPUT_NODE_TYPE_DEFAULT} support this setting.**System API:** This is a system API. |
| [int32_t OH_AudioSuiteEngineSystem_SetAudioFormat(OH_AudioNode* audioNode, OH_AudioSuite_SystemNodeFormat* audioFormat)(System API)](#oh_audiosuiteenginesystem_setaudioformat) | - | Set the audio format for input and output nodes, specify the audio format of the audio source for the input node, or specify the target audio format for the output node.**System API:** This is a system API. |
| [int32_t OH_AudioSuiteEngineSystem_SetNodeParam(OH_AudioNode* audioNode, uint8_t* param, uint32_t paramSize)(System API)](#oh_audiosuiteenginesystem_setnodeparam) | - | Set param of system node.**System API:** This is a system API. |
| [int32_t OH_AudioSuiteEngineSystem_GetNodeParam(OH_AudioNode* audioNode, uint8_t* param, uint32_t paramSize)(System API)](#oh_audiosuiteenginesystem_getnodeparam) | - | Get param of system node.**System API:** This is a system API. |
| [int32_t OH_AudioSuiteEngineSystem_GetNodeInOutSize(OH_AudioNode* audioNode, uint32_t* inSize, uint32_t* outSize)(System API)](#oh_audiosuiteenginesystem_getnodeinoutsize) | - | Get input and output frame size of system node.**System API:** This is a system API. |

### Variable

| Name | Description |
| -- | -- |
| int32_t (*OH_InputNode_RequestMetaDataCallback)(OH_AudioNode* audioNode, void* userData, OH_AudioSuite_MetaFrame* metaFrame, int32_t* responseMetaDataSize, bool* finished)(System API) | Callback function of request meta data, Only {@link INPUT_NODE_TYPE_DEFAULT} support this setting.<br> Each time the application or user invokes [OH_AudioSuiteEngine_MetaRenderFrame](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_metarenderframe), the callback is triggered once.<br>**Since**: 26.0.0<br>**System API:** This is a system API.**System API:** This is a system API. |

## Function description

### OH_AudioSuiteEngine_MetaRenderFrame()

```c
int32_t OH_AudioSuiteEngine_MetaRenderFrame(OH_AudioSuitePipeline* audioSuitePipeline, OH_AudioSuite_MetaFrame* metaFrame, int32_t* responseAudioSize, int32_t* responseMetaSize, bool* finishedFlag)
```

**Description**

The application uses this interface for audio data and meta data processing.<br> The application needs to set the audioData and metaData pointers in the metaFrame structure, as well as the data sizes (audioDataSize and metaDataSize). The actual sizes of the processed data will be returned through responseAudioSize and responseMetaSize.

**Since**: 26.0.0

**System API:** This is a system API.

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioSuitePipeline* audioSuitePipeline | Reference created by [OH_AudioSuiteEngine_CreatePipeline](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_createpipeline). |
| OH_AudioSuite_MetaFrame* metaFrame | Pointer to audio meta data frame structure. |
| int32_t* responseAudioSize | Size of audio data the interface really write, unit is byte. |
| int32_t* responseMetaSize | Size of meta data the interface really write, unit is byte. |
| bool* finishedFlag | This flag is used to indicate to the user whether all data processing has been completed. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>          <li>{@link #AUDIOSUITE_SUCCESS} if execution succeeds.</li><br>        <li>202 if a non-system application calls this system API.</li><br>        <li>{@link #AUDIOSUITE_ERROR_INVALID_PARAM} if parameter is nullptr or not valid value.</li><br>        <li>{@link #AUDIOSUITE_ERROR_PIPELINE_NOT_EXIST}<br>            if pipeline does not exist or has already been destroyed.</li><br>        <li>{@link #AUDIOSUITE_ERROR_INVALID_STATE} if the pipeline is in the Stop state.</li><br>        <li>{@link #AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION} if in the last call, finishedFlag was set to true.</li><br>        <li>{@link #AUDIOSUITE_ERROR_TIMEOUT} if an operation times out before completion.</li><br>        <li>{@link #AUDIOSUITE_ERROR_SYSTEM} if the system has other abnormalities.</li>          </ul> |

### OH_AudioSuiteNodeBuilderSystem_SetNodeType()

```c
int32_t OH_AudioSuiteNodeBuilderSystem_SetNodeType(OH_AudioNodeBuilder* builder, OH_AudioSuite_SystemNodeType type)
```

**Description**

Set the audio node type to be created by the builder.

**Since**: 26.0.0

**System API:** This is a system API.

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioNodeBuilder* builder | Reference created by [OH_AudioSuiteNodeBuilder_Create](capi-native-audio-suite-engine-h.md#oh_audiosuitenodebuilder_create). |
| OH_AudioSuite_SystemNodeType type | Audio system node type. {@link OH_AudioSuite_SystemNodeType} |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>          <li>{@link #AUDIOSUITE_SUCCESS} if execution succeeds.</li><br>        <li>202 if a non-system application calls this system API.</li><br>        <li>{@link #AUDIOSUITE_ERROR_INVALID_PARAM} if parameter is invalid, e.g. builder is nullptr, e.t.c.</li>          </ul> |

### OH_AudioSuiteNodeBuilderSystem_SetFormat()

```c
int32_t OH_AudioSuiteNodeBuilderSystem_SetFormat(OH_AudioNodeBuilder* builder, OH_AudioSuite_SystemNodeFormat audioFormat)
```

**Description**

Set the audio format supported by the node.

**Since**: 26.0.0

**System API:** This is a system API.

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioNodeBuilder* builder | Reference created by [OH_AudioSuiteNodeBuilder_Create](capi-native-audio-suite-engine-h.md#oh_audiosuitenodebuilder_create). |
| OH_AudioSuite_SystemNodeFormat audioFormat | audio node format. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>          <li>{@link #AUDIOSUITE_SUCCESS} if execution succeeds.</li><br>        <li>202 if a non-system application calls this system API.</li><br>        <li>{@link #AUDIOSUITE_ERROR_INVALID_PARAM} if parameter is invalid, e.g. builder is nullptr, e.t.c.</li><br>        <li>{@link #AUDIOSUITE_ERROR_UNSUPPORTED_FORMAT} if an unsupported format is set in audioFormat.</li>          </ul> |

### OH_InputNode_RequestMetaDataCallback()

```c
typedef int32_t (*OH_InputNode_RequestMetaDataCallback)(OH_AudioNode* audioNode, void* userData, OH_AudioSuite_MetaFrame* metaFrame, int32_t* responseMetaDataSize, bool* finished)
```

**Description**

Callback function of request meta data, Only {@link INPUT_NODE_TYPE_DEFAULT} support this setting.<br> Each time the application or user invokes [OH_AudioSuiteEngine_MetaRenderFrame](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_metarenderframe), the callback is triggered once.

**Since**: 26.0.0

**System API:** This is a system API.

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioNode\* audioNode | AudioNode where this callback occurs. |
| void\* userData | User data which is passed by user. |
| OH_AudioSuite_MetaFrame\* metaFrame | Pointer to audio meta data frame structure. |
| int32_t\* responseMetaDataSize | Size of meta data the application really write, unit is byte. |
| bool\* finished | This Boolean value indicates whether all audio data was successfully written. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>          <li>Length of the valid audio data that has written into audioData buffer.              The return value must be in range of [0, metaFrame->audioDataSize].</li>          </ul> |

### OH_AudioSuiteNodeBuilder_SetRequestMetaDataCallback()

```c
int32_t OH_AudioSuiteNodeBuilder_SetRequestMetaDataCallback(OH_AudioNodeBuilder* builder, OH_InputNode_RequestMetaDataCallback callback, void* userData)
```

**Description**

Set input node request meta data callback with frame structure, Only {@link INPUT_NODE_TYPE_DEFAULT} support this setting.

**Since**: 26.0.0

**System API:** This is a system API.

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioNodeBuilder* builder | Reference created by [OH_AudioSuiteNodeBuilder_Create](capi-native-audio-suite-engine-h.md#oh_audiosuitenodebuilder_create). |
| [OH_InputNode_RequestMetaDataCallback](capi-native-audio-suite-engine-h.md#oh_inputnode_requestmetadatacallback) callback | Callback to functions that will write audio data and meta data. |
| void* userData | Pointer to an application data structure that will be passed to the callback functions. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>          <li>{@link #AUDIOSUITE_SUCCESS} if execution succeeds.</li><br>        <li>202 if a non-system application calls this system API.</li><br>        <li>{@link #AUDIOSUITE_ERROR_INVALID_PARAM} if parameter is invalid, e.g. builder is nullptr, e.t.c.</li><br>        <li>{@link #AUDIOSUITE_ERROR_TIMEOUT} if an operation times out before completion.</li><br>        <li>{@link #AUDIOSUITE_ERROR_SYSTEM} if the system has other abnormalities.</li>          </ul> |

### OH_AudioSuiteEngineSystem_SetAudioFormat()

```c
int32_t OH_AudioSuiteEngineSystem_SetAudioFormat(OH_AudioNode* audioNode, OH_AudioSuite_SystemNodeFormat* audioFormat)
```

**Description**

Set the audio format for input and output nodes, specify the audio format of the audio source for the input node, or specify the target audio format for the output node.

**Since**: 26.0.0

**System API:** This is a system API.

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioNode* audioNode | Reference created by [OH_AudioSuiteEngine_CreateNode](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_createnode). |
| OH_AudioSuite_SystemNodeFormat* audioFormat | Audio Format. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>          <li>{@link #AUDIOSUITE_SUCCESS} if execution succeeds.</li><br>        <li>202 if a non-system application calls this system API.</li><br>        <li>{@link #AUDIOSUITE_ERROR_INVALID_PARAM} if parameter is nullptr.</li><br>        <li>{@link #AUDIOSUITE_ERROR_NODE_NOT_EXIST} if audioNode does not exist or has been destroyed.</li><br>        <li>{@link #AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION} if the audioNode is an effect node.</li><br>        <li>{@link #AUDIOSUITE_ERROR_INVALID_STATE}<br>            if the pipeline where the node resides is not in the stop state.</li><br>        <li>{@link #AUDIOSUITE_ERROR_TIMEOUT} if an operation times out before completion.</li><br>        <li>{@link #AUDIOSUITE_ERROR_SYSTEM} if the system has other abnormalities.</li>          </ul> |

### OH_AudioSuiteEngineSystem_SetNodeParam()

```c
int32_t OH_AudioSuiteEngineSystem_SetNodeParam(OH_AudioNode* audioNode, uint8_t* param, uint32_t paramSize)
```

**Description**

Set param of system node.

**Since**: 26.0.0

**System API:** This is a system API.

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioNode* audioNode | Reference created by [OH_AudioSuiteEngine_CreateNode](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_createnode). |
| uint8_t* param | Parameter buffer. |
| uint32_t paramSize | Parameter buffer size. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>          <li>{@link #AUDIOSUITE_SUCCESS} if execution succeeds.</li><br>        <li>202 if a non-system application calls this system API.</li><br>        <li>{@link #AUDIOSUITE_ERROR_NODE_NOT_EXIST} if audioNode does not exist or has been destroyed.</li><br>        <li>{@link #AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION} if audioNode is not a system node.</li><br>        <li>{@link #AUDIOSUITE_ERROR_INVALID_PARAM} if parameter is invalid, e.g. audioNode is nullptr, e.t.c.</li><br>        <li>{@link #AUDIOSUITE_ERROR_TIMEOUT} if an operation times out before completion.</li><br>        <li>{@link #AUDIOSUITE_ERROR_SYSTEM} if the system has other abnormalities.</li>          </ul> |

### OH_AudioSuiteEngineSystem_GetNodeParam()

```c
int32_t OH_AudioSuiteEngineSystem_GetNodeParam(OH_AudioNode* audioNode, uint8_t* param, uint32_t paramSize)
```

**Description**

Get param of system node.

**Since**: 26.0.0

**System API:** This is a system API.

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioNode* audioNode | Reference created by [OH_AudioSuiteEngine_CreateNode](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_createnode). |
| uint8_t* param | Parameter buffer. |
| uint32_t paramSize | Parameter buffer size. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>          <li>{@link #AUDIOSUITE_SUCCESS} if execution succeeds.</li><br>        <li>202 if a non-system application calls this system API.</li><br>        <li>{@link #AUDIOSUITE_ERROR_NODE_NOT_EXIST} if audioNode does not exist or has been destroyed.</li><br>        <li>{@link #AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION} if audioNode is not a system node.</li><br>        <li>{@link #AUDIOSUITE_ERROR_INVALID_PARAM} if parameter is invalid, e.g. audioNode is nullptr, e.t.c.</li><br>        <li>{@link #AUDIOSUITE_ERROR_TIMEOUT} if an operation times out before completion.</li><br>        <li>{@link #AUDIOSUITE_ERROR_SYSTEM} if the system has other abnormalities.</li>          </ul> |

### OH_AudioSuiteEngineSystem_GetNodeInOutSize()

```c
int32_t OH_AudioSuiteEngineSystem_GetNodeInOutSize(OH_AudioNode* audioNode, uint32_t* inSize, uint32_t* outSize)
```

**Description**

Get input and output frame size of system node.

**Since**: 26.0.0

**System API:** This is a system API.

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioNode* audioNode | Reference created by [OH_AudioSuiteEngine_CreateNode](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_createnode). |
| uint32_t* inSize | Input frame size, unit is byte. |
| uint32_t* outSize | Output frame size, unit is byte. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>          <li>{@link #AUDIOSUITE_SUCCESS} if execution succeeds.</li><br>        <li>202 if a non-system application calls this system API.</li><br>        <li>{@link #AUDIOSUITE_ERROR_NODE_NOT_EXIST} if audioNode does not exist or has been destroyed.</li><br>        <li>{@link #AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION} if audioNode is not a system node.</li><br>        <li>{@link #AUDIOSUITE_ERROR_INVALID_PARAM} if parameter is invalid, e.g. audioNode is nullptr, e.t.c.</li><br>        <li>{@link #AUDIOSUITE_ERROR_TIMEOUT} if an operation times out before completion.</li><br>        <li>{@link #AUDIOSUITE_ERROR_SYSTEM} if the system has other abnormalities.</li>          </ul> |


