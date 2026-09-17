# native_audio_suite_engine.h

## Overview

Declare audio suite engine related interfaces.<br> This file provides interfaces for creating audioSuiteEngine, audioSuitePipeline, and audioSuiteNode.

**Library**: libohaudiosuite.so

**System capability**: SystemCapability.Multimedia.Audio.SuiteEngine

**Since**: 22

**Related module**: [OHAudioSuite](capi-ohaudiosuite.md)

## Summary

### Macro

| Name | Description |
| -- | -- |
| NATIVE_AUDIO_SUITE_ENGINE_H | Declare audio suite engine related interfaces.<br> This file provides interfaces for creating audioSuiteEngine, audioSuitePipeline, and audioSuiteNode.<br>**Since**: 22<br>**System capability**: SystemCapability.Multimedia.Audio.SuiteEngine |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AudioSuite_Result OH_AudioSuiteEngine_Create(OH_AudioSuiteEngine** audioSuiteEngine)](#oh_audiosuiteengine_create) | - | Request to create the audio engine. |
| [OH_AudioSuite_Result OH_AudioSuiteEngine_Destroy(OH_AudioSuiteEngine* audioSuiteEngine)](#oh_audiosuiteengine_destroy) | - | Request to destroy the engine. |
| [OH_AudioSuite_Result OH_AudioSuiteEngine_CreatePipeline(OH_AudioSuiteEngine* audioSuiteEngine, OH_AudioSuitePipeline** audioSuitePipeline, OH_AudioSuite_PipelineWorkMode workMode)](#oh_audiosuiteengine_createpipeline) | - | Request to create the pipeline.<br> The pipeline is the unit within the engine responsible for executing audio editing, the engine can create multiple pipelines, and one pipeline must include at least one input node and one output node. When the pipeline operates in {@link #AUDIOSUITE_PIPELINE_EDIT_MODE}, it supports all effect nodes.<br>When the pipeline operates in {@link #AUDIOSUITE_PIPELINE_REALTIME_MODE},<br>before API version 23, it only supports the {@link EFFECT_NODE_TYPE_EQUALIZER} effect node, in API version 23 and later, it supports all effect nodes. |
| [OH_AudioSuite_Result OH_AudioSuiteEngine_DestroyPipeline(OH_AudioSuitePipeline* audioSuitePipeline)](#oh_audiosuiteengine_destroypipeline) | - | Request to destroy the pipeline. |
| [OH_AudioSuite_Result OH_AudioSuiteEngine_StartPipeline(OH_AudioSuitePipeline* audioSuitePipeline)](#oh_audiosuiteengine_startpipeline) | - | Request to start the pipeline. |
| [OH_AudioSuite_Result OH_AudioSuiteEngine_StopPipeline(OH_AudioSuitePipeline* audioSuitePipeline)](#oh_audiosuiteengine_stoppipeline) | - | Stop the pipeline and clear the node cache.<br> This function will not alter the connection relationships between nodes in the pipeline. Once the pipeline is stopped, [OH_AudioSuiteEngine_RenderFrame](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_renderframe) should not be used for executing audio processing. |
| [OH_AudioSuite_Result OH_AudioSuiteEngine_GetPipelineState(OH_AudioSuitePipeline* audioSuitePipeline, OH_AudioSuite_PipelineState* pipelineState)](#oh_audiosuiteengine_getpipelinestate) | - | Request to get one pipeline state |
| [OH_AudioSuite_Result OH_AudioSuiteEngine_RenderFrame(OH_AudioSuitePipeline* audioSuitePipeline, void* audioData, int32_t requestFrameSize, int32_t* responseSize, bool* finishedFlag)](#oh_audiosuiteengine_renderframe) | - | The application uses this interface for audio data processing.<br> The application needs to call this interface to retrieve the data processed with effects frame by frame. After the application calls this interface, the pipeline will sequentially fetch data from the output node forward, process the effects, and ultimately fill the processed data into the audioData pointer passed by the application. The pipeline will attempt to fill the data according to the requestFrameSize as much as possible, and the actual size of the data processed by the pipeline will be returned to the application via responseSize. The pipeline supports multiple input nodes, each of which will obtain raw audio data from the application through the data acquisition interface registered by the application. When the application has handed over all the data prepared for each input node to the pipeline, the application should pass a finish flag during the last callback. Once all inputs in the pipeline have passed the finish flag, the pipeline will inform the application through the finishedFlag in the OH_AudioSuiteEngine_RenderFrame interface after processing is complete. When finishedFlag is true, the application should no longer call this interface. |
| [OH_AudioSuite_Result OH_AudioSuiteEngine_MultiRenderFrame(OH_AudioSuitePipeline* audioSuitePipeline, OH_AudioDataArray* audioDataArray, int32_t* responseSize, bool* finishedFlag)](#oh_audiosuiteengine_multirenderframe) | - | The application uses this interface for audio data processing.<br> For most nodes, a piece of data is obtained from the preceding node, processed, and then passed on to the subsequent node. For nodes with multiple outputs, such as the {@link EFFECT_MULTII_OUTPUT_NODE_TYPE_AUDIO_SEPARATION}, a piece of data is obtained from the preceding node, processed by an algorithm, and then multiple pieces of data are passed on to the subsequent nodes. If such nodes exist in the pipeline, this interface must be used to obtain the processed data. The size of the audioDataArray should correspond one-to-one with the number of data outputs from the node. For the audio source separation node, audioDataArray should have two elements: the first element carries the vocal sound, and the second element carries the background sound. |
| [OH_AudioSuite_Result OH_AudioSuiteNodeBuilder_Create(OH_AudioNodeBuilder** builder)](#oh_audiosuitenodebuilder_create) | - | Create an audio node builder which can be used to create an audio node<br> The builder is a tool used to create nodes, and it can be utilized to set the properties of the nodes to be created. After creating a node, the builder can be reused. However, it must be noted that if the attributes of the new node are inconsistent with the previous node, the application must use OH_AudioSuiteNodeBuilder_Reset to reset the builder. |
| [OH_AudioSuite_Result OH_AudioSuiteNodeBuilder_Destroy(OH_AudioNodeBuilder* builder)](#oh_audiosuitenodebuilder_destroy) | - | Destroy audio node builder.<br> This function must be called when you are done using the builder. |
| [OH_AudioSuite_Result OH_AudioSuiteNodeBuilder_Reset(OH_AudioNodeBuilder* builder)](#oh_audiosuitenodebuilder_reset) | - | Reset audio node builder.<br> If the application intends to reuse the builder to add new nodes and the properties of the new nodes differ from those of the previously created nodes, the application must call this interface to clear all properties, such as audio node type, e.t.c. |
| [OH_AudioSuite_Result OH_AudioSuiteNodeBuilder_SetNodeType(OH_AudioNodeBuilder* builder, OH_AudioNode_Type type)](#oh_audiosuitenodebuilder_setnodetype) | - | Set the audio node type to be created by the builder.<br> When creating a node, other parameters are validated based on the node type, so this method needs to be executed for all types of nodes. |
| [OH_AudioSuite_Result OH_AudioSuiteNodeBuilder_SetFormat(OH_AudioNodeBuilder* builder, OH_AudioFormat audioFormat)](#oh_audiosuitenodebuilder_setformat) | - | Set the audio format supported by the node.<br> For {@link INPUT_NODE_TYPE_DEFAULT},<br>the set audioFormat is used to specify the format in which the application writes data.<br>For {@link OUTPUT_NODE_TYPE_DEFAULT}, the set audioFormat is used to specify the format in which the application ultimately wants to retrieve the data. Other types of nodes do not support this setting. |
| [typedef int32_t (\*OH_InputNode_RequestDataCallback)(OH_AudioNode* audioNode, void* userData, void* audioData, int32_t audioDataSize, bool* finished)](#oh_inputnode_requestdatacallback) | OH_InputNode_RequestDataCallback | Callback function of request data, Only {@link INPUT_NODE_TYPE_DEFAULT} support this setting.<br> This function allows the application to write partial data which ranges from 0 to the audioDataSize. The application should fill the data according to the size of audioDataSize. When all the data from the application has been passed to the pipeline through the callback, the application should set finished to true in the last callback. When finished is set to true, the pipeline will no longer call this interface to obtain data from the application. This callback is triggered when the pipeline needs audio data from the input node during rendering process. The callback is triggered repeatedly during [OH_AudioSuiteEngine_RenderFrame](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_renderframe) execution until finished is set to true. |
| [OH_AudioSuite_Result OH_AudioSuiteNodeBuilder_SetRequestDataCallback(OH_AudioNodeBuilder* builder, OH_InputNode_RequestDataCallback callback, void* userData)](#oh_audiosuitenodebuilder_setrequestdatacallback) | - | Set input node request data callback, Only {@link INPUT_NODE_TYPE_DEFAULT} support this setting. |
| [OH_AudioSuite_Result OH_AudioSuiteEngine_CreateNode(OH_AudioSuitePipeline* audioSuitePipeline, OH_AudioNodeBuilder* builder, OH_AudioNode** audioNode)](#oh_audiosuiteengine_createnode) | - | Request to create audio node with audio node builder.<br> When executing this function, the system will validate the parameters based on the audio node type in the builder. The application can determine the cause of the error through the return value. |
| [OH_AudioSuite_Result OH_AudioSuiteEngine_DestroyNode(OH_AudioNode* audioNode)](#oh_audiosuiteengine_destroynode) | - | Destroy an audio node.<br> Whether the node can be deleted depends on the state of the pipeline it belongs to. If the pipeline is not in the stopped state and the node is in an active processing path, the operation will return that deletion is not supported. |
| [OH_AudioSuite_Result OH_AudioSuiteEngine_GetNodeBypassStatus(OH_AudioNode* audioNode, bool* bypassStatus)](#oh_audiosuiteengine_getnodebypassstatus) | - | Request to get audio node bypass status.<br> Only effect node support bypass, When application call this interface with an input node or output node, it will return {@link #AUDIOSUITE_ERROR_INVALID_PARAM} |
| [OH_AudioSuite_Result OH_AudioSuiteEngine_BypassEffectNode(OH_AudioNode* audioNode, bool bypass)](#oh_audiosuiteengine_bypasseffectnode) | - | Request to set the effect node bypass.<br> This command can only be set on an effect node. when bypass is set true, the effect node only passes data to the next node without performing any effect processing. |
| [OH_AudioSuite_Result OH_AudioSuiteEngine_SetAudioFormat(OH_AudioNode* audioNode, OH_AudioFormat* audioFormat)](#oh_audiosuiteengine_setaudioformat) | - | Set the audio format for input and output nodes, specify the audio format of the audio source for the input node, or specify the target audio format for the output node. |
| [OH_AudioSuite_Result OH_AudioSuiteEngine_ConnectNodes(OH_AudioNode* sourceAudioNode, OH_AudioNode* destAudioNode)](#oh_audiosuiteengine_connectnodes) | - | Executing the connect command will link two nodes in sequence.<br> Connect two nodes will alter the topology of the pipeline. This may result in partial data loss, so it is recommended to perform this command when the engine is in stopped state. Node connections follow a specific order: the input node is the starting point of the pipeline, multiple effect nodes can be connected in between, and the output node is the endpoint of the pipeline. |
| [OH_AudioSuite_Result OH_AudioSuiteEngine_DisconnectNodes(OH_AudioNode* sourceAudioNode, OH_AudioNode* destAudioNode)](#oh_audiosuiteengine_disconnectnodes) | - | Executing the disconnect command will sever the connection between two nodes. This command alters the pipeline's topology and may result in partial data loss. It is recommended to perform this operation when the engine is in a stopped state. |
| [OH_AudioSuite_Result OH_AudioSuiteEngine_IsNodeTypeSupported(OH_AudioNode_Type nodeType, bool* isSupported)](#oh_audiosuiteengine_isnodetypesupported) | - | Request to check whether the current system supports a specific node type. |
| [OH_AudioSuite_Result OH_AudioSuiteEngine_SetEqualizerFrequencyBandGains(OH_AudioNode* audioNode, OH_EqualizerFrequencyBandGains frequencyBandGains)](#oh_audiosuiteengine_setequalizerfrequencybandgains) | - | Set equalizer frequency band gains of audio node. |
| [OH_AudioSuite_Result OH_AudioSuiteEngine_GetEqualizerFrequencyBandGains(OH_AudioNode* audioNode, OH_EqualizerFrequencyBandGains* frequencyBandGains)](#oh_audiosuiteengine_getequalizerfrequencybandgains) | - | Get equalizer frequency band gains of audio node. |
| [OH_AudioSuite_Result OH_AudioSuiteEngine_SetSoundFieldType(OH_AudioNode* audioNode, OH_SoundFieldType soundFieldType)](#oh_audiosuiteengine_setsoundfieldtype) | - | Set sound field type of audio node. |
| [OH_AudioSuite_Result OH_AudioSuiteEngine_GetSoundFieldType(OH_AudioNode* audioNode, OH_SoundFieldType* soundFieldType)](#oh_audiosuiteengine_getsoundfieldtype) | - | Get sound field type of audio node. |
| [OH_AudioSuite_Result OH_AudioSuiteEngine_SetEnvironmentType(OH_AudioNode* audioNode, OH_EnvironmentType environmentType)](#oh_audiosuiteengine_setenvironmenttype) | - | Set environment type of audio node. |
| [OH_AudioSuite_Result OH_AudioSuiteEngine_GetEnvironmentType(OH_AudioNode* audioNode, OH_EnvironmentType* environmentType)](#oh_audiosuiteengine_getenvironmenttype) | - | Get environment type of audio node. |
| [OH_AudioSuite_Result OH_AudioSuiteEngine_SetVoiceBeautifierType(OH_AudioNode* audioNode, OH_VoiceBeautifierType voiceBeautifierType)](#oh_audiosuiteengine_setvoicebeautifiertype) | - | Set voice beautifier type of audio node. |
| [OH_AudioSuite_Result OH_AudioSuiteEngine_GetVoiceBeautifierType(OH_AudioNode* audioNode, OH_VoiceBeautifierType* voiceBeautifierType)](#oh_audiosuiteengine_getvoicebeautifiertype) | - | Get voice beautifier type of audio node. |
| [OH_AudioSuite_Result OH_AudioSuiteEngine_SetSpaceRenderPositionParams(OH_AudioNode* audioNode, OH_AudioSuite_SpaceRenderPositionParams position)](#oh_audiosuiteengine_setspacerenderpositionparams) | - | Set position parameters for space rendering |
| [OH_AudioSuite_Result OH_AudioSuiteEngine_GetSpaceRenderPositionParams(OH_AudioNode* audioNode, OH_AudioSuite_SpaceRenderPositionParams* position)](#oh_audiosuiteengine_getspacerenderpositionparams) | - | Get position parameters for space rendering |
| [OH_AudioSuite_Result OH_AudioSuiteEngine_SetSpaceRenderRotationParams(OH_AudioNode* audioNode, OH_AudioSuite_SpaceRenderRotationParams rotation)](#oh_audiosuiteengine_setspacerenderrotationparams) | - | Set rotation parameters for space rendering |
| [OH_AudioSuite_Result OH_AudioSuiteEngine_GetSpaceRenderRotationParams(OH_AudioNode* audioNode, OH_AudioSuite_SpaceRenderRotationParams* rotation)](#oh_audiosuiteengine_getspacerenderrotationparams) | - | Get rotation parameters for space rendering |
| [OH_AudioSuite_Result OH_AudioSuiteEngine_SetSpaceRenderExtensionParams(OH_AudioNode* audioNode, OH_AudioSuite_SpaceRenderExtensionParams extension)](#oh_audiosuiteengine_setspacerenderextensionparams) | - | Set extension parameters for space rendering |
| [OH_AudioSuite_Result OH_AudioSuiteEngine_GetSpaceRenderExtensionParams(OH_AudioNode* audioNode, OH_AudioSuite_SpaceRenderExtensionParams* extension)](#oh_audiosuiteengine_getspacerenderextensionparams) | - | Get extension parameters for space rendering |
| [OH_AudioSuite_Result OH_AudioSuiteEngine_SetTempoAndPitch(OH_AudioNode* audioNode, float speed, float pitch)](#oh_audiosuiteengine_settempoandpitch) | - | Set the tempo and pitch adjustment parameters. |
| [OH_AudioSuite_Result OH_AudioSuiteEngine_GetTempoAndPitch(OH_AudioNode* audioNode, float* speed, float* pitch)](#oh_audiosuiteengine_gettempoandpitch) | - | Get the tempo and pitch adjustment parameters. |
| [OH_AudioSuite_Result OH_AudioSuiteEngine_SetPureVoiceChangeOption(OH_AudioNode* audioNode, OH_AudioSuite_PureVoiceChangeOption option)](#oh_audiosuiteengine_setpurevoicechangeoption) | - | Set pure change voice option of audio node. |
| [OH_AudioSuite_Result OH_AudioSuiteEngine_GetPureVoiceChangeOption(OH_AudioNode* audioNode, OH_AudioSuite_PureVoiceChangeOption* option)](#oh_audiosuiteengine_getpurevoicechangeoption) | - | Get pure voice change option of audio node. |
| [OH_AudioSuite_Result OH_AudioSuiteEngine_SetGeneralVoiceChangeType(OH_AudioNode* audioNode, OH_AudioSuite_GeneralVoiceChangeType type)](#oh_audiosuiteengine_setgeneralvoicechangetype) | - | Set general voice change type of audio node. |
| [OH_AudioSuite_Result OH_AudioSuiteEngine_GetGeneralVoiceChangeType(OH_AudioNode* audioNode, OH_AudioSuite_GeneralVoiceChangeType* type)](#oh_audiosuiteengine_getgeneralvoicechangetype) | - | Get general voice change type of audio node. |
| [OH_AudioSuite_Result OH_AudioSuite_PrintInfo(OH_AudioSuiteEngine* audioSuiteEngine, OH_AudioSuitePipeline* audioSuitePipeline, int fd)](#oh_audiosuite_printinfo) | - | Print AudioSuite runtime snapshot. |

### Variable

| Name | Description |
| -- | -- |
| int32_t (*OH_InputNode_RequestDataCallback)( OH_AudioNode* audioNode, void* userData, void* audioData, int32_t audioDataSize, bool* finished) | Callback function of request data, Only {@link INPUT_NODE_TYPE_DEFAULT} support this setting.<br> This function allows the application to write partial data which ranges from 0 to the audioDataSize. The application should fill the data according to the size of audioDataSize. When all the data from the application has been passed to the pipeline through the callback, the application should set finished to true in the last callback. When finished is set to true, the pipeline will no longer call this interface to obtain data from the application. This callback is triggered when the pipeline needs audio data from the input node during rendering process. The callback is triggered repeatedly during [OH_AudioSuiteEngine_RenderFrame](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_renderframe) execution until finished is set to true.<br>**Since**: 22 |

## Function description

### OH_AudioSuiteEngine_Create()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_Create(OH_AudioSuiteEngine** audioSuiteEngine)
```

**Description**

Request to create the audio engine.

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioSuiteEngine** audioSuiteEngine | Pointer to a variable to receive audioSuiteEngine. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioSuite_Result | {@link #AUDIOSUITE_SUCCESS} if execution succeeds,<br>or {@link #AUDIOSUITE_ERROR_INVALID_PARAM} if audioSuiteEngine is nullptr,<br>or {@link #AUDIOSUITE_ERROR_INVALID_STATE} if the engine is already created.<br>or {@link #AUDIOSUITE_ERROR_MEMORY_ALLOC_FAILED} if memory allocation failed.<br>or {@link #AUDIOSUITE_ERROR_SYSTEM} if the system has other abnormalities. |

### OH_AudioSuiteEngine_Destroy()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_Destroy(OH_AudioSuiteEngine* audioSuiteEngine)
```

**Description**

Request to destroy the engine.

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioSuiteEngine* audioSuiteEngine | Reference created by OH_AudioSuiteEngine_Create. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioSuite_Result | {@link #AUDIOSUITE_SUCCESS} if execution succeeds,<br>or {@link #AUDIOSUITE_ERROR_INVALID_PARAM} if audioSuiteEngine is nullptr,<br>or {@link #AUDIOSUITE_ERROR_INVALID_STATE} if audioSuiteEngine has not been created.<br>or {@link #AUDIOSUITE_ERROR_SYSTEM} if the system has other abnormalities. |

### OH_AudioSuiteEngine_CreatePipeline()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_CreatePipeline(OH_AudioSuiteEngine* audioSuiteEngine, OH_AudioSuitePipeline** audioSuitePipeline, OH_AudioSuite_PipelineWorkMode workMode)
```

**Description**

Request to create the pipeline.<br> The pipeline is the unit within the engine responsible for executing audio editing, the engine can create multiple pipelines, and one pipeline must include at least one input node and one output node. When the pipeline operates in {@link #AUDIOSUITE_PIPELINE_EDIT_MODE}, it supports all effect nodes.<br>When the pipeline operates in {@link #AUDIOSUITE_PIPELINE_REALTIME_MODE},<br>before API version 23, it only supports the {@link EFFECT_NODE_TYPE_EQUALIZER} effect node, in API version 23 and later, it supports all effect nodes.

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioSuiteEngine* audioSuiteEngine | Reference created by OH_AudioSuiteEngine_Create. |
| OH_AudioSuitePipeline** audioSuitePipeline | Pointer to a variable to receive the pipeline. |
| OH_AudioSuite_PipelineWorkMode workMode | It indicates whether the pipeline is operating in Edit mode or real-time rendering mode. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioSuite_Result | {@link #AUDIOSUITE_SUCCESS} if execution succeeds<br>or {@link #AUDIOSUITE_ERROR_INVALID_PARAM} if parameter is nullptr<br>or {@link #AUDIOSUITE_ERROR_ENGINE_NOT_EXIST} if the engine is not created.<br>or {@link #AUDIOSUITE_ERROR_CREATED_EXCEED_SYSTEM_LIMITS} if the number of created pipelines exceeds the upper limit.<br>or {@link #AUDIOSUITE_ERROR_TIMEOUT} if an operation times out before completion.<br>or {@link #AUDIOSUITE_ERROR_MEMORY_ALLOC_FAILED} if memory allocation failed.<br>or {@link #AUDIOSUITE_ERROR_SYSTEM} if the system has other abnormalities. |

### OH_AudioSuiteEngine_DestroyPipeline()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_DestroyPipeline(OH_AudioSuitePipeline* audioSuitePipeline)
```

**Description**

Request to destroy the pipeline.

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioSuitePipeline* audioSuitePipeline | Reference created by OH_AudioSuiteEngine_CreatePipeline. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioSuite_Result | <ul>          <li>{@link #AUDIOSUITE_SUCCESS} if execution succeeds.</li><br>        <li>{@link #AUDIOSUITE_ERROR_INVALID_PARAM} if parameter is invalid,<br>            e.g. audioSuitePipeline is nullptr, e.t.c.</li><br>        <li>{@link #AUDIOSUITE_ERROR_PIPELINE_NOT_EXIST}<br>            if pipeline does not exist or has already been destroyed.</li><br>        <li>{@link #AUDIOSUITE_ERROR_TIMEOUT} if an operation times out before completion.</li><br>        <li>{@link #AUDIOSUITE_ERROR_SYSTEM} if the system has other abnormalities.</li>          </ul> |

### OH_AudioSuiteEngine_StartPipeline()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_StartPipeline(OH_AudioSuitePipeline* audioSuitePipeline)
```

**Description**

Request to start the pipeline.

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioSuitePipeline* audioSuitePipeline | Reference created by OH_AudioSuiteEngine_CreatePipeline. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioSuite_Result | {@link #AUDIOSUITE_SUCCESS} if execution succeeds,<br>or {@link #AUDIOSUITE_ERROR_INVALID_PARAM} if parameter is invalid, e.g. audioSuitePipeline is nullptr, e.t.c.<br>or {@link #AUDIOSUITE_ERROR_PIPELINE_NOT_EXIST} if pipeline does not exist or has already been destroyed.<br>or {@link #AUDIOSUITE_ERROR_INVALID_STATE} if the pipeline is already in running state<br>or the node connection is abnormal.<br>or {@link #AUDIOSUITE_ERROR_TIMEOUT} if an operation times out before completion.<br>or {@link #AUDIOSUITE_ERROR_SYSTEM} if the system has other abnormalities. |

### OH_AudioSuiteEngine_StopPipeline()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_StopPipeline(OH_AudioSuitePipeline* audioSuitePipeline)
```

**Description**

Stop the pipeline and clear the node cache.<br> This function will not alter the connection relationships between nodes in the pipeline. Once the pipeline is stopped, [OH_AudioSuiteEngine_RenderFrame](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_renderframe) should not be used for executing audio processing.

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioSuitePipeline* audioSuitePipeline | Reference created by OH_AudioSuiteEngine_CreatePipeline. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioSuite_Result | {@link #AUDIOSUITE_SUCCESS} if execution succeeds<br>or {@link #AUDIOSUITE_ERROR_INVALID_PARAM} if parameter is invalid, e.g. audioSuitePipeline is nullptr, e.t.c.<br>or {@link #AUDIOSUITE_ERROR_PIPELINE_NOT_EXIST} if pipeline does not exist or has already been destroyed.<br>or {@link #AUDIOSUITE_ERROR_INVALID_STATE} if the pipeline is already in stopped state.<br>or {@link #AUDIOSUITE_ERROR_TIMEOUT} if an operation times out before completion.<br>or {@link #AUDIOSUITE_ERROR_SYSTEM} if the system has other abnormalities. |

### OH_AudioSuiteEngine_GetPipelineState()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_GetPipelineState(OH_AudioSuitePipeline* audioSuitePipeline, OH_AudioSuite_PipelineState* pipelineState)
```

**Description**

Request to get one pipeline state

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioSuitePipeline* audioSuitePipeline | Reference created by OH_AudioSuiteEngine_CreatePipeline. |
| OH_AudioSuite_PipelineState* pipelineState | Pipeline state, which will be returned as the output parameter. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioSuite_Result | {@link #AUDIOSUITE_SUCCESS} if execution succeeds<br>or {@link #AUDIOSUITE_ERROR_INVALID_PARAM} if parameter is invalid, e.g. audioSuitePipeline is nullptr, e.t.c.<br>or {@link #AUDIOSUITE_ERROR_PIPELINE_NOT_EXIST} if pipeline does not exist or has already been destroyed.<br>or {@link #AUDIOSUITE_ERROR_TIMEOUT} if an operation times out before completion.<br>or {@link #AUDIOSUITE_ERROR_SYSTEM} if the system has other abnormalities. |

### OH_AudioSuiteEngine_RenderFrame()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_RenderFrame(OH_AudioSuitePipeline* audioSuitePipeline, void* audioData, int32_t requestFrameSize, int32_t* responseSize, bool* finishedFlag)
```

**Description**

The application uses this interface for audio data processing.<br> The application needs to call this interface to retrieve the data processed with effects frame by frame. After the application calls this interface, the pipeline will sequentially fetch data from the output node forward, process the effects, and ultimately fill the processed data into the audioData pointer passed by the application. The pipeline will attempt to fill the data according to the requestFrameSize as much as possible, and the actual size of the data processed by the pipeline will be returned to the application via responseSize. The pipeline supports multiple input nodes, each of which will obtain raw audio data from the application through the data acquisition interface registered by the application. When the application has handed over all the data prepared for each input node to the pipeline, the application should pass a finish flag during the last callback. Once all inputs in the pipeline have passed the finish flag, the pipeline will inform the application through the finishedFlag in the OH_AudioSuiteEngine_RenderFrame interface after processing is complete. When finishedFlag is true, the application should no longer call this interface.

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioSuitePipeline* audioSuitePipeline | Reference created by OH_AudioSuiteEngine_CreatePipeline |
| void* audioData | Audio data pointer, where user should read, unit is byte. |
| int32_t requestFrameSize | Size of audio data user specified, unit is byte. |
| int32_t* responseSize | Size of audio data the system really writes. |
| bool* finishedFlag | This flag is used to indicate to the user whether all data processing has been completed. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioSuite_Result | {@link #AUDIOSUITE_SUCCESS} if execution succeeds<br>or {@link #AUDIOSUITE_ERROR_INVALID_PARAM} if parameter is nullptr or not valid value.<br>or {@link #AUDIOSUITE_ERROR_PIPELINE_NOT_EXIST} if pipeline does not exist or has already been destroyed.<br>or {@link #AUDIOSUITE_ERROR_INVALID_STATE} if the pipeline is in the Stop state.<br>or {@link #AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION} if in the last call, finishedFlag was set to true.<br>or {@link #AUDIOSUITE_ERROR_TIMEOUT} if an operation times out before completion.<br>or {@link #AUDIOSUITE_ERROR_SYSTEM} if the system has other abnormalities. |

### OH_AudioSuiteEngine_MultiRenderFrame()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_MultiRenderFrame(OH_AudioSuitePipeline* audioSuitePipeline, OH_AudioDataArray* audioDataArray, int32_t* responseSize, bool* finishedFlag)
```

**Description**

The application uses this interface for audio data processing.<br> For most nodes, a piece of data is obtained from the preceding node, processed, and then passed on to the subsequent node. For nodes with multiple outputs, such as the {@link EFFECT_MULTII_OUTPUT_NODE_TYPE_AUDIO_SEPARATION}, a piece of data is obtained from the preceding node, processed by an algorithm, and then multiple pieces of data are passed on to the subsequent nodes. If such nodes exist in the pipeline, this interface must be used to obtain the processed data. The size of the audioDataArray should correspond one-to-one with the number of data outputs from the node. For the audio source separation node, audioDataArray should have two elements: the first element carries the vocal sound, and the second element carries the background sound.

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioSuitePipeline* audioSuitePipeline | Reference created by OH_AudioSuiteEngine_CreatePipeline. |
| OH_AudioDataArray* audioDataArray | Audio data array pointer, where user should read, The size of each one-dimensional array should be consistent. |
| int32_t* responseSize | Size of audio data the system really writes, The system ensures that the data size filled for each one-dimensional array is consistent, unit is byte. |
| bool* finishedFlag | This flag is used to indicate to the user whether all data processing has been completed. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioSuite_Result | {@link #AUDIOSUITE_SUCCESS} if execution succeeds<br>or {@link #AUDIOSUITE_ERROR_INVALID_PARAM} if parameter is nullptr or not valid value.<br>or {@link #AUDIOSUITE_ERROR_PIPELINE_NOT_EXIST} if pipeline does not exist or has already been destroyed.<br>or {@link #AUDIOSUITE_ERROR_INVALID_STATE} if the pipeline is in the Stop state.<br>or {@link #AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION} if in the last call, finishedFlag was set to true.<br>or {@link #AUDIOSUITE_ERROR_TIMEOUT} if an operation times out before completion.<br>or {@link #AUDIOSUITE_ERROR_SYSTEM} if the system has other abnormalities. |

### OH_AudioSuiteNodeBuilder_Create()

```c
OH_AudioSuite_Result OH_AudioSuiteNodeBuilder_Create(OH_AudioNodeBuilder** builder)
```

**Description**

Create an audio node builder which can be used to create an audio node<br> The builder is a tool used to create nodes, and it can be utilized to set the properties of the nodes to be created. After creating a node, the builder can be reused. However, it must be noted that if the attributes of the new node are inconsistent with the previous node, the application must use OH_AudioSuiteNodeBuilder_Reset to reset the builder.

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioNodeBuilder** builder | The builder reference to the created result. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioSuite_Result | {@link #AUDIOSUITE_SUCCESS} if execution succeeds<br>or {@link #AUDIOSUITE_ERROR_INVALID_PARAM} if parameter is invalid, e.g. builder is nullptr, e.t.c.<br>or {@link #AUDIOSUITE_ERROR_MEMORY_ALLOC_FAILED} if memory allocation failed.<br>or {@link #AUDIOSUITE_ERROR_SYSTEM} if the system has other abnormalities. |

### OH_AudioSuiteNodeBuilder_Destroy()

```c
OH_AudioSuite_Result OH_AudioSuiteNodeBuilder_Destroy(OH_AudioNodeBuilder* builder)
```

**Description**

Destroy audio node builder.<br> This function must be called when you are done using the builder.

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioNodeBuilder* builder | Reference created by OH_AudioSuiteNodeBuilder_Create. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioSuite_Result | {@link #AUDIOSUITE_SUCCESS} if execution succeeds<br>or {@link #AUDIOSUITE_ERROR_INVALID_PARAM} if parameter is invalid, e.g. builder is nullptr, e.t.c.<br>or {@link #AUDIOSUITE_ERROR_SYSTEM} if the system has other abnormalities. |

### OH_AudioSuiteNodeBuilder_Reset()

```c
OH_AudioSuite_Result OH_AudioSuiteNodeBuilder_Reset(OH_AudioNodeBuilder* builder)
```

**Description**

Reset audio node builder.<br> If the application intends to reuse the builder to add new nodes and the properties of the new nodes differ from those of the previously created nodes, the application must call this interface to clear all properties, such as audio node type, e.t.c.

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioNodeBuilder* builder | Reference created by OH_AudioSuiteNodeBuilder_Create. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioSuite_Result | {@link #AUDIOSUITE_SUCCESS} if execution succeeds<br>or {@link #AUDIOSUITE_ERROR_INVALID_PARAM} if parameter is invalid, e.g. builder is nullptr, e.t.c.<br>or {@link #AUDIOSUITE_ERROR_SYSTEM} if the system has other abnormalities. |

### OH_AudioSuiteNodeBuilder_SetNodeType()

```c
OH_AudioSuite_Result OH_AudioSuiteNodeBuilder_SetNodeType(OH_AudioNodeBuilder* builder, OH_AudioNode_Type type)
```

**Description**

Set the audio node type to be created by the builder.<br> When creating a node, other parameters are validated based on the node type, so this method needs to be executed for all types of nodes.

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioNodeBuilder* builder | Reference created by OH_AudioSuiteNodeBuilder_Create. |
| OH_AudioNode_Type type | Audio node type. {@link OH_AudioNode_Type} |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioSuite_Result | {@link #AUDIOSUITE_SUCCESS} if execution succeeds<br>or {@link #AUDIOSUITE_ERROR_INVALID_PARAM} if parameter is invalid, e.g. builder is nullptr, e.t.c.<br>or {@link #AUDIOSUITE_ERROR_SYSTEM} if the system has other abnormalities. |

### OH_AudioSuiteNodeBuilder_SetFormat()

```c
OH_AudioSuite_Result OH_AudioSuiteNodeBuilder_SetFormat(OH_AudioNodeBuilder* builder, OH_AudioFormat audioFormat)
```

**Description**

Set the audio format supported by the node.<br> For {@link INPUT_NODE_TYPE_DEFAULT},<br>the set audioFormat is used to specify the format in which the application writes data.<br>For {@link OUTPUT_NODE_TYPE_DEFAULT}, the set audioFormat is used to specify the format in which the application ultimately wants to retrieve the data. Other types of nodes do not support this setting.

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioNodeBuilder* builder | Reference created by OH_AudioSuiteNodeBuilder_Create. |
| OH_AudioFormat audioFormat | audio node format. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioSuite_Result | {@link #AUDIOSUITE_SUCCESS} if execution succeeds<br>or {@link #AUDIOSUITE_ERROR_INVALID_PARAM} if parameter is invalid, e.g. builder is nullptr, e.t.c.<br>or {@link #AUDIOSUITE_ERROR_UNSUPPORTED_FORMAT} if an unsupported format is set in audioFormat.<br>or {@link #AUDIOSUITE_ERROR_SYSTEM} if the system has other abnormalities. |

### OH_InputNode_RequestDataCallback()

```c
typedef int32_t (*OH_InputNode_RequestDataCallback)(OH_AudioNode* audioNode, void* userData, void* audioData, int32_t audioDataSize, bool* finished)
```

**Description**

Callback function of request data, Only {@link INPUT_NODE_TYPE_DEFAULT} support this setting.<br> This function allows the application to write partial data which ranges from 0 to the audioDataSize. The application should fill the data according to the size of audioDataSize. When all the data from the application has been passed to the pipeline through the callback, the application should set finished to true in the last callback. When finished is set to true, the pipeline will no longer call this interface to obtain data from the application. This callback is triggered when the pipeline needs audio data from the input node during rendering process. The callback is triggered repeatedly during [OH_AudioSuiteEngine_RenderFrame](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_renderframe) execution until finished is set to true.

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioNode\* audioNode | AudioNode where this callback occurs. |
| void\* userData | User data which is passed by user. |
| void\* audioData | Audio data pointer, where user should fill in audio data. |
| int32_t audioDataSize | Size of audio data that user should fill in, unit is byte. |
| bool\* finished | This boolean value indicates that all data of the application has been consumed since last execute [OH_AudioSuiteEngine_StartPipeline](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_startpipeline). |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Length of the valid data that has written into audioData buffer.  The return value must be in range of  [0, audioDataSize]. If the return value is less than 0,  the system changes it to 0. And, if the return value is  greater than audioDataSize, the system changes it to audioDataSize. |

### OH_AudioSuiteNodeBuilder_SetRequestDataCallback()

```c
OH_AudioSuite_Result OH_AudioSuiteNodeBuilder_SetRequestDataCallback(OH_AudioNodeBuilder* builder, OH_InputNode_RequestDataCallback callback, void* userData)
```

**Description**

Set input node request data callback, Only {@link INPUT_NODE_TYPE_DEFAULT} support this setting.

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioNodeBuilder* builder | Reference created by OH_AudioSuiteNodeBuilder_Create. |
| [OH_InputNode_RequestDataCallback](capi-native-audio-suite-engine-h.md#oh_inputnode_requestdatacallback) callback | Callback to functions that will write audio data. |
| void* userData | Pointer to an application data structure that will be passed to the callback functions. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioSuite_Result | {@link #AUDIOSUITE_SUCCESS} if execution succeeds<br>or {@link #AUDIOSUITE_ERROR_INVALID_PARAM} if parameter is invalid, e.g. builder is nullptr, e.t.c.<br>or {@link #AUDIOSUITE_ERROR_TIMEOUT} if an operation times out before completion.<br>or {@link #AUDIOSUITE_ERROR_SYSTEM} if the system has other abnormalities. |

### OH_AudioSuiteEngine_CreateNode()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_CreateNode(OH_AudioSuitePipeline* audioSuitePipeline, OH_AudioNodeBuilder* builder, OH_AudioNode** audioNode)
```

**Description**

Request to create audio node with audio node builder.<br> When executing this function, the system will validate the parameters based on the audio node type in the builder. The application can determine the cause of the error through the return value.

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioSuitePipeline* audioSuitePipeline | Reference created by OH_AudioSuiteEngine_CreatePipeline. |
| OH_AudioNodeBuilder* builder | Audio node builder created by OH_AudioSuiteNodeBuilder_Create. |
| OH_AudioNode** audioNode | Pointer to a variable to receive the audio node. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioSuite_Result | <ul>          <li>{@link #AUDIOSUITE_SUCCESS} if execution succeeds.</li><br>        <li>{@link #AUDIOSUITE_ERROR_INVALID_PARAM} if parameter is nullptr or not valid value.</li><br>        <li>{@link #AUDIOSUITE_ERROR_CREATED_EXCEED_SYSTEM_LIMITS} the number of nodes<br>            of the current type exceeds the pipeline limit.</li><br>        <li>{@link #AUDIOSUITE_ERROR_REQUIRED_PARAMETERS_MISSING} if the input type is inputNode,<br>            but no callback function is set, e.t.c.</li><br>        <li>{@link #AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION}<br>            if the current constructor node type is output node but the Callback function was set,<br>            or the constructor node type is an effect node but the audio format or callback function was set.</li><br>        <li>{@link #AUDIOSUITE_ERROR_TIMEOUT} if an operation times out before completion.</li><br>        <li>{@link #AUDIOSUITE_ERROR_MEMORY_ALLOC_FAILED} if memory allocation failed.</li><br>        <li>{@link #AUDIOSUITE_ERROR_SYSTEM} if the system has other abnormalities.</li>          </ul> |

### OH_AudioSuiteEngine_DestroyNode()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_DestroyNode(OH_AudioNode* audioNode)
```

**Description**

Destroy an audio node.<br> Whether the node can be deleted depends on the state of the pipeline it belongs to. If the pipeline is not in the stopped state and the node is in an active processing path, the operation will return that deletion is not supported.

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioNode* audioNode | Reference created by OH_AudioSuiteEngine_CreateNode. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioSuite_Result | {@link #AUDIOSUITE_SUCCESS} if execution succeeds,<br>or {@link #AUDIOSUITE_ERROR_INVALID_PARAM} if parameter is nullptr,<br>or {@link #AUDIOSUITE_ERROR_NODE_NOT_EXIST} if audioNode does not exist or has been destroyed.<br>or {@link #AUDIOSUITE_ERROR_INVALID_STATE} if the pipeline is not stopped.<br>or {@link #AUDIOSUITE_ERROR_TIMEOUT} if an operation times out before completion.<br>or {@link #AUDIOSUITE_ERROR_SYSTEM} if the system has other abnormalities. |

### OH_AudioSuiteEngine_GetNodeBypassStatus()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_GetNodeBypassStatus(OH_AudioNode* audioNode, bool* bypassStatus)
```

**Description**

Request to get audio node bypass status.<br> Only effect node support bypass, When application call this interface with an input node or output node, it will return {@link #AUDIOSUITE_ERROR_INVALID_PARAM}

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioNode* audioNode | Reference created by OH_AudioSuiteEngine_CreateNode. |
| bool* bypassStatus | node bypass status, which will be returned as the output parameter, When the value of bypassStatus is false, it indicates that the node has not been set to bypass; when it is true, it means the node has been set to bypass. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioSuite_Result | {@link #AUDIOSUITE_SUCCESS} if execution succeeds<br>or {@link #AUDIOSUITE_ERROR_INVALID_PARAM} if parameter is invalid, e.g. audioNode is nullptr, e.t.c.<br>or {@link #AUDIOSUITE_ERROR_NODE_NOT_EXIST} if audioNode does not exist or has been destroyed.<br>or {@link #AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION} if audioNode is not an effect node type.<br>or {@link #AUDIOSUITE_ERROR_TIMEOUT} if an operation times out before completion.<br>or {@link #AUDIOSUITE_ERROR_SYSTEM} if the system has other abnormalities. |

### OH_AudioSuiteEngine_BypassEffectNode()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_BypassEffectNode(OH_AudioNode* audioNode, bool bypass)
```

**Description**

Request to set the effect node bypass.<br> This command can only be set on an effect node. when bypass is set true, the effect node only passes data to the next node without performing any effect processing.

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioNode* audioNode | Reference created by OH_AudioSuiteEngine_CreateNode. |
| bool bypass | This parameter determines whether the node merely forwards data transparently. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioSuite_Result | {@link #AUDIOSUITE_SUCCESS} if execution succeeds<br>or {@link #AUDIOSUITE_ERROR_INVALID_PARAM} if parameter is invalid, e.g. audioNode is nullptr, e.t.c.<br>or {@link #AUDIOSUITE_ERROR_NODE_NOT_EXIST} if audioNode does not exist or has been destroyed.<br>or {@link #AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION} if the audioNode is not an effect node.<br>or {@link #AUDIOSUITE_ERROR_TIMEOUT} if an operation times out before completion.<br>or {@link #AUDIOSUITE_ERROR_SYSTEM} if the system has other abnormalities. |

### OH_AudioSuiteEngine_SetAudioFormat()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_SetAudioFormat(OH_AudioNode* audioNode, OH_AudioFormat* audioFormat)
```

**Description**

Set the audio format for input and output nodes, specify the audio format of the audio source for the input node, or specify the target audio format for the output node.

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioNode* audioNode | Reference created by OH_AudioSuiteEngine_CreateNode. |
| OH_AudioFormat* audioFormat | Audio Format. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioSuite_Result | <ul>          <li>{@link #AUDIOSUITE_SUCCESS} if execution succeeds</li><br>        <li>{@link #AUDIOSUITE_ERROR_INVALID_PARAM} if parameter is nullptr.</li><br>        <li>{@link #AUDIOSUITE_ERROR_NODE_NOT_EXIST} if audioNode does not exist or has been destroyed.</li><br>        <li>{@link #AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION} if the audioNode is an effect node.</li><br>        <li>{@link #AUDIOSUITE_ERROR_UNSUPPORTED_FORMAT}<br>            if an unsupported format is set in audioFormat. [since 26.0.0]</li><br>        <li>{@link #AUDIOSUITE_ERROR_INVALID_STATE}<br>            if the pipeline where the node resides is not in the stop state.</li><br>        <li>{@link #AUDIOSUITE_ERROR_TIMEOUT} if an operation times out before completion.</li><br>        <li>{@link #AUDIOSUITE_ERROR_SYSTEM} if the system has other abnormalities.</li>          </ul> |

### OH_AudioSuiteEngine_ConnectNodes()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_ConnectNodes(OH_AudioNode* sourceAudioNode, OH_AudioNode* destAudioNode)
```

**Description**

Executing the connect command will link two nodes in sequence.<br> Connect two nodes will alter the topology of the pipeline. This may result in partial data loss, so it is recommended to perform this command when the engine is in stopped state. Node connections follow a specific order: the input node is the starting point of the pipeline, multiple effect nodes can be connected in between, and the output node is the endpoint of the pipeline.

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioNode* sourceAudioNode | source node Reference created by OH_AudioSuiteEngine_CreateNode. |
| OH_AudioNode* destAudioNode | dest node Reference created by OH_AudioSuiteEngine_CreateNode. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioSuite_Result | <ul>          <li>{@link #AUDIOSUITE_SUCCESS} if execution succeeds.</li><br>        <li>{@link #AUDIOSUITE_ERROR_INVALID_PARAM} if parameter is invalid,<br>            e.g. sourceAudioNode is nullptr, e.t.c.</li><br>        <li>{@link #AUDIOSUITE_ERROR_INVALID_STATE} if pipeline state is invalid,<br>            e.g. can not find output node, e.t.c.</li><br>        <li>{@link #AUDIOSUITE_ERROR_NODE_NOT_EXIST} if audioNode does not exist or has been destroyed.</li><br>        <li>{@link #AUDIOSUITE_ERROR_UNSUPPORTED_CONNECT}<br>            if connections between two node types are not supported.</li><br>        <li>{@link #AUDIOSUITE_ERROR_TIMEOUT} if an operation times out before completion.</li><br>        <li>{@link #AUDIOSUITE_ERROR_SYSTEM} if the system has other abnormalities.</li>          </ul> |

### OH_AudioSuiteEngine_DisconnectNodes()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_DisconnectNodes(OH_AudioNode* sourceAudioNode, OH_AudioNode* destAudioNode)
```

**Description**

Executing the disconnect command will sever the connection between two nodes. This command alters the pipeline's topology and may result in partial data loss. It is recommended to perform this operation when the engine is in a stopped state.

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioNode* sourceAudioNode | Preceding audio node Reference created by OH_AudioSuiteEngine_CreateNode. |
| OH_AudioNode* destAudioNode | Subsequent audio node Reference created by OH_AudioSuiteEngine_CreateNode. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioSuite_Result | <ul>          <li>{@link #AUDIOSUITE_SUCCESS} if execution succeeds.</li><br>        <li>{@link #AUDIOSUITE_ERROR_INVALID_PARAM} if parameter is invalid,<br>            e.g. sourceAudioNode is nullptr, e.t.c.</li><br>        <li>{@link #AUDIOSUITE_ERROR_INVALID_STATE} if pipeline state is invalid,<br>            e.g. can not find output node, e.t.c.</li><br>        <li>{@link #AUDIOSUITE_ERROR_NODE_NOT_EXIST} if audioNode does not exist or has been destroyed.</li><br>        <li>{@link #AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION} if sourceAudioNode and destAudioNode are the same node,<br>            e.t.c.</li><br>        <li>{@link #AUDIOSUITE_ERROR_TIMEOUT} if an operation times out before completion.</li><br>        <li>{@link #AUDIOSUITE_ERROR_SYSTEM} if the system has other abnormalities.</li>          </ul> |

### OH_AudioSuiteEngine_IsNodeTypeSupported()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_IsNodeTypeSupported(OH_AudioNode_Type nodeType, bool* isSupported)
```

**Description**

Request to check whether the current system supports a specific node type.

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioNode_Type nodeType | Audio node type. {@link OH_AudioNode_Type} |
| bool* isSupported | True means this node type is supported, False means this node type is not supported. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioSuite_Result | {@link #AUDIOSUITE_SUCCESS} if execution succeeds,<br>or {@link #AUDIOSUITE_ERROR_INVALID_PARAM} if param nullptr or not valid value.<br>or {@link #AUDIOSUITE_ERROR_SYSTEM} if the system has other abnormalities. |

### OH_AudioSuiteEngine_SetEqualizerFrequencyBandGains()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_SetEqualizerFrequencyBandGains(OH_AudioNode* audioNode, OH_EqualizerFrequencyBandGains frequencyBandGains)
```

**Description**

Set equalizer frequency band gains of audio node.

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioNode* audioNode | Reference created by OH_AudioSuiteEngine_CreateNode. |
| OH_EqualizerFrequencyBandGains frequencyBandGains | The equalizer frequency band gains. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioSuite_Result | {@link #AUDIOSUITE_SUCCESS} if execution succeeds<br>or {@link #AUDIOSUITE_ERROR_NODE_NOT_EXIST} if audioNode does not exist or has been destroyed.<br>or {@link #AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION} if audioNode is not an equalizer node.<br>or {@link #AUDIOSUITE_ERROR_INVALID_PARAM} if parameter is invalid, e.g. audioNode is nullptr, e.t.c.<br>or {@link #AUDIOSUITE_ERROR_TIMEOUT} if an operation times out before completion.<br>or {@link #AUDIOSUITE_ERROR_SYSTEM} if the system has other abnormalities. |

### OH_AudioSuiteEngine_GetEqualizerFrequencyBandGains()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_GetEqualizerFrequencyBandGains(OH_AudioNode* audioNode, OH_EqualizerFrequencyBandGains* frequencyBandGains)
```

**Description**

Get equalizer frequency band gains of audio node.

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioNode* audioNode | Reference created by OH_AudioSuiteEngine_CreateNode. |
| OH_EqualizerFrequencyBandGains* frequencyBandGains | Current equalizer frequency band gains of audioNode. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioSuite_Result | {@link #AUDIOSUITE_SUCCESS} if execution succeeds<br>or {@link #AUDIOSUITE_ERROR_NODE_NOT_EXIST} if audioNode does not exist or has been destroyed.<br>or {@link #AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION} if audioNode is not an equalizer node.<br>or {@link #AUDIOSUITE_ERROR_INVALID_PARAM} if parameter is invalid, e.g. audioNode or<br>frequencyBandGains is nullptr, e.t.c.<br>or {@link #AUDIOSUITE_ERROR_TIMEOUT} if an operation times out before completion.<br>or {@link #AUDIOSUITE_ERROR_SYSTEM} if the system has other abnormalities. |

### OH_AudioSuiteEngine_SetSoundFieldType()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_SetSoundFieldType(OH_AudioNode* audioNode, OH_SoundFieldType soundFieldType)
```

**Description**

Set sound field type of audio node.

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioNode* audioNode | Reference created by OH_AudioSuiteEngine_CreateNode. |
| OH_SoundFieldType soundFieldType | The sound field type. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioSuite_Result | <ul>           <li>{@link #AUDIOSUITE_SUCCESS} if execution succeeds.</li><br>        <li>{@link #AUDIOSUITE_ERROR_NODE_NOT_EXIST} if audioNode does not exist or has been destroyed.</li><br>        <li>{@link #AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION} if audioNode is not a soundfield node.</li><br>        <li>{@link #AUDIOSUITE_ERROR_INVALID_PARAM} if parameter is invalid, e.g. audioNode is nullptr, e.t.c.</li><br>        <li>{@link #AUDIOSUITE_ERROR_TIMEOUT} if an operation times out before completion.</li><br>        <li>{@link #AUDIOSUITE_ERROR_SYSTEM} if the system has other abnormalities.</li>          </ul> |

### OH_AudioSuiteEngine_GetSoundFieldType()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_GetSoundFieldType(OH_AudioNode* audioNode, OH_SoundFieldType* soundFieldType)
```

**Description**

Get sound field type of audio node.

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioNode* audioNode | Reference created by OH_AudioSuiteEngine_CreateNode. |
| OH_SoundFieldType* soundFieldType | Current sound field type of audioNode. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioSuite_Result | <ul>          <li>{@link #AUDIOSUITE_SUCCESS} if execution succeeds.</li><br>        <li>{@link #AUDIOSUITE_ERROR_NODE_NOT_EXIST} if audioNode does not exist or has been destroyed.</li><br>        <li>{@link #AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION} if audioNode is not a soundfield node.</li><br>        <li>{@link #AUDIOSUITE_ERROR_INVALID_PARAM} if parameter is invalid, e.g. audioNode or<br>            soundFieldType is nullptr, e.t.c.</li><br>        <li>{@link #AUDIOSUITE_ERROR_TIMEOUT} if an operation times out before completion.</li><br>        <li>{@link #AUDIOSUITE_ERROR_SYSTEM} if the system has other abnormalities.</li>          </ul> |

### OH_AudioSuiteEngine_SetEnvironmentType()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_SetEnvironmentType(OH_AudioNode* audioNode, OH_EnvironmentType environmentType)
```

**Description**

Set environment type of audio node.

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioNode* audioNode | Reference created by OH_AudioSuiteEngine_CreateNode. |
| OH_EnvironmentType environmentType | The environment type. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioSuite_Result | {@link #AUDIOSUITE_SUCCESS} if execution succeeds<br>or {@link #AUDIOSUITE_ERROR_NODE_NOT_EXIST} if audioNode does not exist or has been destroyed.<br>or {@link #AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION} if audioNode is not an environment node.<br>or {@link #AUDIOSUITE_ERROR_INVALID_PARAM} if parameter is invalid, e.g. audioNode is nullptr, e.t.c.<br>or {@link #AUDIOSUITE_ERROR_TIMEOUT} if an operation times out before completion.<br>or {@link #AUDIOSUITE_ERROR_SYSTEM} if the system has other abnormalities. |

### OH_AudioSuiteEngine_GetEnvironmentType()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_GetEnvironmentType(OH_AudioNode* audioNode, OH_EnvironmentType* environmentType)
```

**Description**

Get environment type of audio node.

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioNode* audioNode | Reference created by OH_AudioSuiteEngine_CreateNode. |
| OH_EnvironmentType* environmentType | Current environment type of audioNode. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioSuite_Result | {@link #AUDIOSUITE_SUCCESS} if execution succeeds<br>or {@link #AUDIOSUITE_ERROR_NODE_NOT_EXIST} if audioNode does not exist or has been destroyed.<br>or {@link #AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION} if audioNode is not an environment node.<br>or {@link #AUDIOSUITE_ERROR_INVALID_PARAM} if parameter is invalid, e.g. audioNode or<br>environmentType is nullptr, e.t.c.<br>or {@link #AUDIOSUITE_ERROR_TIMEOUT} if an operation times out before completion.<br>or {@link #AUDIOSUITE_ERROR_SYSTEM} if the system has other abnormalities. |

### OH_AudioSuiteEngine_SetVoiceBeautifierType()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_SetVoiceBeautifierType(OH_AudioNode* audioNode, OH_VoiceBeautifierType voiceBeautifierType)
```

**Description**

Set voice beautifier type of audio node.

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioNode* audioNode | Reference created by OH_AudioSuiteEngine_CreateNode. |
| OH_VoiceBeautifierType voiceBeautifierType | the voice beautifier type. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioSuite_Result | <ul>          <li>{@link #AUDIOSUITE_SUCCESS} if execution succeeds.</li><br>        <li>{@link #AUDIOSUITE_ERROR_NODE_NOT_EXIST} if audioNode does not exist or has been destroyed.</li><br>        <li>{@link #AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION} if audioNode is not a voiceBeautifier node.</li><br>        <li>{@link #AUDIOSUITE_ERROR_INVALID_PARAM} if parameter is invalid, e.g. audioNode is nullptr, e.t.c.</li><br>        <li>{@link #AUDIOSUITE_ERROR_TIMEOUT} if an operation times out before completion.</li><br>        <li>{@link #AUDIOSUITE_ERROR_SYSTEM} if the system has other abnormalities.</li>          </ul> |

### OH_AudioSuiteEngine_GetVoiceBeautifierType()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_GetVoiceBeautifierType(OH_AudioNode* audioNode, OH_VoiceBeautifierType* voiceBeautifierType)
```

**Description**

Get voice beautifier type of audio node.

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioNode* audioNode | Reference created by OH_AudioSuiteEngine_CreateNode. |
| OH_VoiceBeautifierType* voiceBeautifierType | Current voice beautifier type of audioNode. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioSuite_Result | <ul>          <li>{@link #AUDIOSUITE_SUCCESS} if execution succeeds.</li><br>        <li>{@link #AUDIOSUITE_ERROR_NODE_NOT_EXIST} if audioNode does not exist or has been destroyed.</li><br>        <li>{@link #AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION} if audioNode is not a voiceBeautifier node.</li><br>        <li>{@link #AUDIOSUITE_ERROR_INVALID_PARAM} if parameter is invalid, e.g. audioNode or<br>            voiceBeautifierType is nullptr, e.t.c.</li><br>        <li>{@link #AUDIOSUITE_ERROR_TIMEOUT} if an operation times out before completion.</li><br>        <li>{@link #AUDIOSUITE_ERROR_SYSTEM} if the system has other abnormalities.</li></ul> |

### OH_AudioSuiteEngine_SetSpaceRenderPositionParams()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_SetSpaceRenderPositionParams(OH_AudioNode* audioNode, OH_AudioSuite_SpaceRenderPositionParams position)
```

**Description**

Set position parameters for space rendering

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioNode* audioNode | Reference created by OH_AudioSuiteEngine_CreateNode. |
| OH_AudioSuite_SpaceRenderPositionParams position | Position parameters. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioSuite_Result | {@link #AUDIOSUITE_SUCCESS} if execution succeeds<br>or {@link #AUDIOSUITE_ERROR_NODE_NOT_EXIST} if audioNode does not exist or has been destroyed.<br>or {@link #AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION} if audioNode is not a space render node.<br>or {@link #AUDIOSUITE_ERROR_INVALID_PARAM} if parameter is invalid, e.g. audioNode is nullptr, e.t.c.<br>or {@link #AUDIOSUITE_ERROR_TIMEOUT} if an operation times out before completion.<br>or {@link #AUDIOSUITE_ERROR_SYSTEM} if the system has other abnormalities. |

### OH_AudioSuiteEngine_GetSpaceRenderPositionParams()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_GetSpaceRenderPositionParams(OH_AudioNode* audioNode, OH_AudioSuite_SpaceRenderPositionParams* position)
```

**Description**

Get position parameters for space rendering

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioNode* audioNode | Reference created by OH_AudioSuiteEngine_CreateNode. |
| OH_AudioSuite_SpaceRenderPositionParams* position | Position parameters. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioSuite_Result | {@link #AUDIOSUITE_SUCCESS} if execution succeeds<br>or {@link #AUDIOSUITE_ERROR_NODE_NOT_EXIST} if audioNode does not exist or has been destroyed.<br>or {@link #AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION} if audioNode is not a space render node.<br>or {@link #AUDIOSUITE_ERROR_INVALID_PARAM} if parameter is invalid, e.g. audioNode is nullptr, e.t.c.<br>or {@link #AUDIOSUITE_ERROR_TIMEOUT} if an operation times out before completion.<br>or {@link #AUDIOSUITE_ERROR_SYSTEM} if the system has other abnormalities. |

### OH_AudioSuiteEngine_SetSpaceRenderRotationParams()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_SetSpaceRenderRotationParams(OH_AudioNode* audioNode, OH_AudioSuite_SpaceRenderRotationParams rotation)
```

**Description**

Set rotation parameters for space rendering

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioNode* audioNode | Reference created by OH_AudioSuiteEngine_CreateNode. |
| OH_AudioSuite_SpaceRenderRotationParams rotation | Rotation parameters. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioSuite_Result | {@link #AUDIOSUITE_SUCCESS} if execution succeeds<br>or {@link #AUDIOSUITE_ERROR_NODE_NOT_EXIST} if audioNode does not exist or has been destroyed.<br>or {@link #AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION} if audioNode is not a space render node.<br>or {@link #AUDIOSUITE_ERROR_INVALID_PARAM} if parameter is invalid, e.g. audioNode is nullptr, e.t.c.<br>or {@link #AUDIOSUITE_ERROR_TIMEOUT} if an operation times out before completion.<br>or {@link #AUDIOSUITE_ERROR_SYSTEM} if the system has other abnormalities. |

### OH_AudioSuiteEngine_GetSpaceRenderRotationParams()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_GetSpaceRenderRotationParams(OH_AudioNode* audioNode, OH_AudioSuite_SpaceRenderRotationParams* rotation)
```

**Description**

Get rotation parameters for space rendering

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioNode* audioNode | Reference created by OH_AudioSuiteEngine_CreateNode. |
| OH_AudioSuite_SpaceRenderRotationParams* rotation | Rotation parameters. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioSuite_Result | {@link #AUDIOSUITE_SUCCESS} if execution succeeds<br>or {@link #AUDIOSUITE_ERROR_NODE_NOT_EXIST} if audioNode does not exist or has been destroyed.<br>or {@link #AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION} if audioNode is not a space render node.<br>or {@link #AUDIOSUITE_ERROR_INVALID_PARAM} if parameter is invalid, e.g. audioNode is nullptr, e.t.c.<br>or {@link #AUDIOSUITE_ERROR_TIMEOUT} if an operation times out before completion.<br>or {@link #AUDIOSUITE_ERROR_SYSTEM} if the system has other abnormalities. |

### OH_AudioSuiteEngine_SetSpaceRenderExtensionParams()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_SetSpaceRenderExtensionParams(OH_AudioNode* audioNode, OH_AudioSuite_SpaceRenderExtensionParams extension)
```

**Description**

Set extension parameters for space rendering

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioNode* audioNode | Reference created by OH_AudioSuiteEngine_CreateNode. |
| OH_AudioSuite_SpaceRenderExtensionParams extension | Extension parameters. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioSuite_Result | {@link #AUDIOSUITE_SUCCESS} if execution succeeds<br>or {@link #AUDIOSUITE_ERROR_NODE_NOT_EXIST} if audioNode does not exist or has been destroyed.<br>or {@link #AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION} if audioNode is not a space render node.<br>or {@link #AUDIOSUITE_ERROR_INVALID_PARAM} if parameter is invalid, e.g. audioNode is nullptr, e.t.c.<br>or {@link #AUDIOSUITE_ERROR_TIMEOUT} if an operation times out before completion.<br>or {@link #AUDIOSUITE_ERROR_SYSTEM} if the system has other abnormalities. |

### OH_AudioSuiteEngine_GetSpaceRenderExtensionParams()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_GetSpaceRenderExtensionParams(OH_AudioNode* audioNode, OH_AudioSuite_SpaceRenderExtensionParams* extension)
```

**Description**

Get extension parameters for space rendering

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioNode* audioNode | Reference created by OH_AudioSuiteEngine_CreateNode. |
| OH_AudioSuite_SpaceRenderExtensionParams* extension | Extension parameters. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioSuite_Result | {@link #AUDIOSUITE_SUCCESS} if execution succeeds<br>or {@link #AUDIOSUITE_ERROR_NODE_NOT_EXIST} if audioNode does not exist or has been destroyed.<br>or {@link #AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION} if audioNode is not a space render node.<br>or {@link #AUDIOSUITE_ERROR_INVALID_PARAM} if parameter is invalid, e.g. audioNode is nullptr, e.t.c.<br>or {@link #AUDIOSUITE_ERROR_TIMEOUT} if an operation times out before completion.<br>or {@link #AUDIOSUITE_ERROR_SYSTEM} if the system has other abnormalities. |

### OH_AudioSuiteEngine_SetTempoAndPitch()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_SetTempoAndPitch(OH_AudioNode* audioNode, float speed, float pitch)
```

**Description**

Set the tempo and pitch adjustment parameters.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioNode* audioNode | Reference created by OH_AudioSuiteEngine_CreateNode. |
| float speed | value range: [0.5, 10.0] for Tempo, where 1.0 means normal tempo speed. If the value is outside the valid range, {@link #AUDIOSUITE_ERROR_INVALID_PARAM} will be returned. |
| float pitch | value range: [0.1, 5.0] for Pitch, where 1.0 means normal pitch. If the value is outside the valid range, {@link #AUDIOSUITE_ERROR_INVALID_PARAM} will be returned. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioSuite_Result | {@link #AUDIOSUITE_SUCCESS} if execution succeeds<br>or {@link #AUDIOSUITE_ERROR_NODE_NOT_EXIST} if audioNode does not exist or has been destroyed.<br>or {@link #AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION} if audioNode is not a tempo and pitch node.<br>or {@link #AUDIOSUITE_ERROR_INVALID_PARAM} if parameter is invalid, e.g. audioNode is nullptr, e.t.c.<br>or {@link #AUDIOSUITE_ERROR_TIMEOUT} if an operation times out before completion.<br>or {@link #AUDIOSUITE_ERROR_SYSTEM} if the system has other abnormalities. |

### OH_AudioSuiteEngine_GetTempoAndPitch()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_GetTempoAndPitch(OH_AudioNode* audioNode, float* speed, float* pitch)
```

**Description**

Get the tempo and pitch adjustment parameters.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioNode* audioNode | Reference created by OH_AudioSuiteEngine_CreateNode. |
| float* speed | value range: [0.5, 10.0] for Tempo. |
| float* pitch | value range: [0.1, 5.0] for Pitch. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioSuite_Result | {@link #AUDIOSUITE_SUCCESS} if execution succeeds<br>or {@link #AUDIOSUITE_ERROR_NODE_NOT_EXIST} if audioNode does not exist or has been destroyed.<br>or {@link #AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION} if audioNode is not a tempo and pitch node.<br>or {@link #AUDIOSUITE_ERROR_INVALID_PARAM} if parameter is invalid, e.g. audioNode is nullptr, e.t.c.<br>or {@link #AUDIOSUITE_ERROR_TIMEOUT} if an operation times out before completion.<br>or {@link #AUDIOSUITE_ERROR_SYSTEM} if the system has other abnormalities. |

### OH_AudioSuiteEngine_SetPureVoiceChangeOption()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_SetPureVoiceChangeOption(OH_AudioNode* audioNode, OH_AudioSuite_PureVoiceChangeOption option)
```

**Description**

Set pure change voice option of audio node.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioNode* audioNode | Reference created by OH_AudioSuiteEngine_CreateNode. |
| OH_AudioSuite_PureVoiceChangeOption option | Change voice option. {@link #OH_AudioSuite_PureVoiceChangeOption} |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioSuite_Result | {@link #AUDIOSUITE_SUCCESS} if execution succeeds<br>or {@link #AUDIOSUITE_ERROR_NODE_NOT_EXIST} if audioNode does not exist or has been destroyed.<br>or {@link #AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION} if audioNode is not a pure voice change node.<br>or {@link #AUDIOSUITE_ERROR_INVALID_PARAM} if parameter is invalid, e.g. audioNode is nullptr, e.t.c.<br>or {@link #AUDIOSUITE_ERROR_TIMEOUT} if an operation times out before completion.<br>or {@link #AUDIOSUITE_ERROR_SYSTEM} if the system has other abnormalities. |

### OH_AudioSuiteEngine_GetPureVoiceChangeOption()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_GetPureVoiceChangeOption(OH_AudioNode* audioNode, OH_AudioSuite_PureVoiceChangeOption* option)
```

**Description**

Get pure voice change option of audio node.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioNode* audioNode | Reference created by OH_AudioSuiteEngine_CreateNode. |
| OH_AudioSuite_PureVoiceChangeOption* option | Change voice option. {@link #OH_AudioSuite_PureVoiceChangeOption} |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioSuite_Result | {@link #AUDIOSUITE_SUCCESS} if execution succeeds<br>or {@link #AUDIOSUITE_ERROR_NODE_NOT_EXIST} if audioNode does not exist or has been destroyed.<br>or {@link #AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION} if audioNode is not a pure voice change node.<br>or {@link #AUDIOSUITE_ERROR_INVALID_PARAM} if parameter is invalid, e.g. audioNode is nullptr, e.t.c.<br>or {@link #AUDIOSUITE_ERROR_TIMEOUT} if an operation times out before completion.<br>or {@link #AUDIOSUITE_ERROR_SYSTEM} if the system has other abnormalities. |

### OH_AudioSuiteEngine_SetGeneralVoiceChangeType()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_SetGeneralVoiceChangeType(OH_AudioNode* audioNode, OH_AudioSuite_GeneralVoiceChangeType type)
```

**Description**

Set general voice change type of audio node.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioNode* audioNode | Reference created by OH_AudioSuiteEngine_CreateNode. |
| OH_AudioSuite_GeneralVoiceChangeType type | Change voice type. {@link #OH_AudioSuite_GeneralVoiceChangeType} |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioSuite_Result | {@link #AUDIOSUITE_SUCCESS} if execution succeeds<br>or {@link #AUDIOSUITE_ERROR_NODE_NOT_EXIST} if audioNode does not exist or has been destroyed.<br>or {@link #AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION} if audioNode is not a general voice change node.<br>or {@link #AUDIOSUITE_ERROR_INVALID_PARAM} if parameter is invalid, e.g. audioNode is nullptr, e.t.c.<br>or {@link #AUDIOSUITE_ERROR_TIMEOUT} if an operation times out before completion.<br>or {@link #AUDIOSUITE_ERROR_SYSTEM} if the system has other abnormalities. |

### OH_AudioSuiteEngine_GetGeneralVoiceChangeType()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_GetGeneralVoiceChangeType(OH_AudioNode* audioNode, OH_AudioSuite_GeneralVoiceChangeType* type)
```

**Description**

Get general voice change type of audio node.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioNode* audioNode | Reference created by OH_AudioSuiteEngine_CreateNode. |
| OH_AudioSuite_GeneralVoiceChangeType* type | Change voice type. {@link #OH_AudioSuite_GeneralVoiceChangeType} |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioSuite_Result | {@link #AUDIOSUITE_SUCCESS} if execution succeeds<br>or {@link #AUDIOSUITE_ERROR_NODE_NOT_EXIST} if audioNode does not exist or has been destroyed.<br>or {@link #AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION} if audioNode is not a general voice change node.<br>or {@link #AUDIOSUITE_ERROR_INVALID_PARAM} if parameter is invalid, e.g. audioNode is nullptr, e.t.c.<br>or {@link #AUDIOSUITE_ERROR_TIMEOUT} if an operation times out before completion.<br>or {@link #AUDIOSUITE_ERROR_SYSTEM} if the system has other abnormalities. |

### OH_AudioSuite_PrintInfo()

```c
OH_AudioSuite_Result OH_AudioSuite_PrintInfo(OH_AudioSuiteEngine* audioSuiteEngine, OH_AudioSuitePipeline* audioSuitePipeline, int fd)
```

**Description**

Print AudioSuite runtime snapshot.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioSuiteEngine* audioSuiteEngine | Pointer to the AudioSuiteEngine whose runtime snapshot needs to be displayed. |
| OH_AudioSuitePipeline* audioSuitePipeline | Pointer to the AudioSuitePipeline whose runtime snapshot needs to be displayed. If audioSuitePipeline is NULL: output all pipelines (all pipelines/nodes under the engine). Otherwise, output only the snapshot of this pipeline and nodes. |
| int fd | is a file handle, indicates the location where the snapshot information is stored. If the fd is less than 0, the snapshot information is stored in the log. Otherwise, the snapshot is stored in the file pointed to by the fd handle in append mode. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioSuite_Result | {@link #AUDIOSUITE_SUCCESS} if execution succeeds,<br>or {@link #AUDIOSUITE_ERROR_INVALID_PARAM} if parameter is nullptr or not valid value.<br>or {@link #AUDIOSUITE_ERROR_SYSTEM} if the system has other abnormalities. |


