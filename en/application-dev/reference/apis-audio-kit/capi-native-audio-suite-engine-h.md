# native_audio_suite_engine.h
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @xxngwang-->
<!--Designer: @jay-liusong-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=54629084527d63783d2476fd78af0dbed183e764 translatedAt=2026-11-09T10:25:30.520Z pushedAt=2026-11-09T11:27:47.505Z nl=1 -->

## Overview

This file declares the API related to audio creation (including the engine, pipeline, and nodes).

**File to include**: <ohaudiosuite/native_audio_suite_engine.h>

**Library**: libohaudiosuite.so

**System capability**: SystemCapability.Multimedia.Audio.SuiteEngine

**Since**: 22

**Related module**: [OHAudioSuite](capi-ohaudiosuite.md)

## Summary

### Functions

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_AudioSuite_Result OH_AudioSuiteEngine_Create(OH_AudioSuiteEngine** audioSuiteEngine)](#oh_audiosuiteengine_create) | - | Creates an audio creation engine.|
| [OH_AudioSuite_Result OH_AudioSuiteEngine_Destroy(OH_AudioSuiteEngine* audioSuiteEngine)](#oh_audiosuiteengine_destroy) | - | Destroys the handle to an audio creation engine.|
| [OH_AudioSuite_Result OH_AudioSuiteEngine_CreatePipeline(OH_AudioSuiteEngine* audioSuiteEngine, OH_AudioSuitePipeline** audioSuitePipeline, OH_AudioSuite_PipelineWorkMode workMode)](#oh_audiosuiteengine_createpipeline) | - | Creates a pipeline within the current audio creation engine. A pipeline is the execution unit within the engine responsible for audio creation, and multiple pipelines can be created within a single engine.<br> A maximum of 10 pipelines can be created. Before API version 26.0.0, only one real-time preview pipeline can be created. Since API version 26.0.0, there is no longer a separate limit on the number of real-time preview pipelines. However, the total number of pipelines must not exceed 10.<br> Each pipeline must have at least one input node and exactly one output node.<br> When the pipeline operations in [OH_AudioSuite_PipelineWorkMode](capi-native-audio-suite-base-h.md#oh_audiosuite_pipelineworkmode).AUDIOSUITE_PIPELINE_EDIT_MODE mode, all effect nodes are supported.<br> Before API version 23, when a pipeline works in [OH_AudioSuite_PipelineWorkMode](capi-native-audio-suite-base-h.md#oh_audiosuite_pipelineworkmode).AUDIOSUITE_PIPELINE_REALTIME_MODE mode, only the effect node [OH_AudioNode_Type](capi-native-audio-suite-base-h.md#oh_audionode_type).EFFECT_NODE_TYPE_EQUALIZER is supported.<br> Since API version 23, when a pipeline works in [OH_AudioSuite_PipelineWorkMode](capi-native-audio-suite-base-h.md#oh_audiosuite_pipelineworkmode).AUDIOSUITE_PIPELINE_REALTIME_MODE mode, all effect nodes are supported.|
| [OH_AudioSuite_Result OH_AudioSuiteEngine_DestroyPipeline(OH_AudioSuitePipeline* audioSuitePipeline)](#oh_audiosuiteengine_destroypipeline) | - | Destroys the handle to an audio creation pipeline.|
| [OH_AudioSuite_Result OH_AudioSuiteEngine_StartPipeline(OH_AudioSuitePipeline* audioSuitePipeline)](#oh_audiosuiteengine_startpipeline) | - | Starts the pipeline. The pipeline will enter the [OH_AudioSuite_PipelineState](capi-native-audio-suite-base-h.md#oh_audiosuite_pipelinestate).AUDIOSUITE_PIPELINE_RUNNING state.|
| [OH_AudioSuite_Result OH_AudioSuiteEngine_StopPipeline(OH_AudioSuitePipeline* audioSuitePipeline)](#oh_audiosuiteengine_stoppipeline) | - | Stops the pipeline. The pipeline will enter the [OH_AudioSuite_PipelineState](capi-native-audio-suite-base-h.md#oh_audiosuite_pipelinestate).AUDIOSUITE_PIPELINE_STOPPED state. This function does not change the connections between nodes within the pipeline. Once the pipeline is stopped, [OH_AudioSuiteEngine_RenderFrame](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_renderframe) can no longer perform audio processing.|
| [OH_AudioSuite_Result OH_AudioSuiteEngine_GetPipelineState(OH_AudioSuitePipeline* audioSuitePipeline, OH_AudioSuite_PipelineState* pipelineState)](#oh_audiosuiteengine_getpipelinestate) | - | Retrieves the state of the pipeline.|
| [OH_AudioSuite_Result OH_AudioSuiteEngine_RenderFrame(OH_AudioSuitePipeline* audioSuitePipeline, void* audioData, int32_t requestFrameSize, int32_t* responseSize, bool* finishedFlag)](#oh_audiosuiteengine_renderframe) | - | Obtains the processed audio data from the pipeline (for single-output effect nodes).|
| [OH_AudioSuite_Result OH_AudioSuiteEngine_MultiRenderFrame(OH_AudioSuitePipeline* audioSuitePipeline, OH_AudioDataArray* audioDataArray, int32_t* responseSize, bool* finishedFlag)](#oh_audiosuiteengine_multirenderframe) | - | Renders the pipeline and obtains the processed audio data. For pipelines with multiple output effect nodes (for example, those containing audio separation nodes), the size of **audioDataArray** must correspond one-to-one with the number of outputs from the effect nodes. (For example, audio separation nodes require two outputs: the first for vocals and the second for background sound.)|
|<!--DelRow--> [int32_t OH_AudioSuiteEngine_MetaRenderFrame(OH_AudioSuitePipeline* audioSuitePipeline, OH_AudioSuite_MetaFrame* metaFrame, int32_t* responseAudioSize, int32_t* responseMetaSize, bool* finishedFlag)](#oh_audiosuiteengine_metarenderframe) | - | Processes audio data and metadata. The application must specify the audioData and metaData pointers and their corresponding sizes (AudioDataSize and metaDataSize) in the metaFrame struct.<br> After processing, the actual output data sizes are returned through responseAudioSize and responseMetaSize. |
| [OH_AudioSuite_Result OH_AudioSuiteNodeBuilder_Create(OH_AudioNodeBuilder** builder)](#oh_audiosuitenodebuilder_create) | - | Obtains an audio creation node builder, which is used to configure and create audio nodes. The builder can be reused. However, if the attributes of the new node are different from those of the previous node, you must use [OH_AudioSuiteNodeBuilder_Reset](capi-native-audio-suite-engine-h.md#oh_audiosuitenodebuilder_reset) to reset the builder.|
| [OH_AudioSuite_Result OH_AudioSuiteNodeBuilder_Destroy(OH_AudioNodeBuilder* builder)](#oh_audiosuitenodebuilder_destroy) | - | Destroys an audio creation node builder. This function must be called after the builder is no longer required.|
| [OH_AudioSuite_Result OH_AudioSuiteNodeBuilder_Reset(OH_AudioNodeBuilder* builder)](#oh_audiosuitenodebuilder_reset) | - | Resets an audio creation node builder, clearing all previously set parameters. If you want to reuse the builder to create a node with different properties, this function must be called to clear all properties (for example, node type).|
| [OH_AudioSuite_Result OH_AudioSuiteNodeBuilder_SetNodeType(OH_AudioNodeBuilder* builder, OH_AudioNode_Type type)](#oh_audiosuitenodebuilder_setnodetype) | - | Sets the type of node to be constructed by the current node builder. During node creation, other parameters are verified based on the node type. This property must be set for all node types.|
|<!--DelRow--> [int32_t OH_AudioSuiteNodeBuilderSystem_SetNodeType(OH_AudioNodeBuilder* builder, OH_AudioSuite_SystemNodeType type)](#oh_audiosuitenodebuildersystem_setnodetype) | - | Sets the audio node type to be created by the builder. |
| [OH_AudioSuite_Result OH_AudioSuiteNodeBuilder_SetFormat(OH_AudioNodeBuilder* builder, OH_AudioFormat audioFormat)](#oh_audiosuitenodebuilder_setformat) | - | Configures the audio format for input or output nodes. This function can only be used before node creation. For input nodes, it allows the application to specify the audio format for writing data.<br> For output nodes, it allows the application to specify the desired audio format for obtaining data.<br> This function is not supported for other node types.|
|<!--DelRow--> [int32_t OH_AudioSuiteNodeBuilderSystem_SetFormat(OH_AudioNodeBuilder* builder, OH_AudioSuite_SystemNodeFormat audioFormat)](#oh_audiosuitenodebuildersystem_setformat) | - | Sets the audio format supported by the node. |
| [typedef int32_t (\*OH_InputNode_RequestDataCallback)(OH_AudioNode* audioNode, void* userData, void* audioData, int32_t audioDataSize, bool* finished)](#oh_inputnode_requestdatacallback) | OH_InputNode_RequestDataCallback | Defines the callback function for the input node to request data.|
| [OH_AudioSuite_Result OH_AudioSuiteNodeBuilder_SetRequestDataCallback(OH_AudioNodeBuilder* builder, OH_InputNode_RequestDataCallback callback, void* userData)](#oh_audiosuitenodebuilder_setrequestdatacallback) | - | Sets a callback function for writing audio data for the current input node builder.|
|<!--DelRow--> [typedef int32_t (\*OH_InputNode_RequestMetaDataCallback)(OH_AudioNode* audioNode, void* userData, OH_AudioSuite_MetaFrame* metaFrame, int32_t* responseMetaDataSize, bool* finished)](#oh_inputnode_requestmetadatacallback) | OH_InputNode_RequestMetaDataCallback | Callback used to request metadata. Only [INPUT_NODE_TYPE_DEFAULT](capi-native-audio-suite-base-h.md#oh_audionode_type) supports this setting. The callback is triggered each time the application or user calls [OH_AudioSuiteEngine_MetaRenderFrame](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_metarenderframe). |
|<!--DelRow--> [int32_t OH_AudioSuiteNodeBuilder_SetRequestMetaDataCallback(OH_AudioNodeBuilder* builder, OH_InputNode_RequestMetaDataCallback callback, void* userData)](#oh_audiosuitenodebuilder_setrequestmetadatacallback) | - | Configures the callback for writing audio data and metadata of the current input node builder. Only [INPUT_NODE_TYPE_DEFAULT](capi-native-audio-suite-base-h.md#oh_audionode_type) supports this setting. |
| [OH_AudioSuite_Result OH_AudioSuiteEngine_CreateNode(OH_AudioSuitePipeline* audioSuitePipeline, OH_AudioNodeBuilder* builder, OH_AudioNode** audioNode)](#oh_audiosuiteengine_createnode) | - | Creates an audio node within the audio pipeline based on the audio creation builder. When this function is executed, the system checks the validity of the parameters based on the node type set in the builder.<br> Applications can determine the cause of errors based on the return value.|
| [OH_AudioSuite_Result OH_AudioSuiteEngine_DestroyNode(OH_AudioNode* audioNode)](#oh_audiosuiteengine_destroynode) | - | Destroys an audio creation node. Whether a node can be destroyed depends on the state of its associated pipeline. If the pipeline is not in the [OH_AudioSuite_PipelineState](capi-native-audio-suite-base-h.md#oh_audiosuite_pipelinestate).AUDIOSUITE_PIPELINE_STOPPED state and the node is in the pipeline processing path, the destruction fails.|
| [OH_AudioSuite_Result OH_AudioSuiteEngine_GetNodeBypassStatus(OH_AudioNode* audioNode, bool* bypassStatus)](#oh_audiosuiteengine_getnodebypassstatus) | - | Obtains the effect bypass status of the current node. This function can be used only on effect nodes.<br> If it is called on an input or output node, the AUDIOSUITE_ERROR_INVALID_PARAM error code is returned.|
| [OH_AudioSuite_Result OH_AudioSuiteEngine_BypassEffectNode(OH_AudioNode* audioNode, bool bypass)](#oh_audiosuiteengine_bypasseffectnode) | - | Sets the effect bypass status of the current node (supported only on effect nodes). When **bypass** is set to **true**, the effect node passes data through without any processing.<br> When **bypass** is set to **false**, the effect node performs the corresponding effect processing.|
| [OH_AudioSuite_Result OH_AudioSuiteEngine_SetAudioFormat(OH_AudioNode* audioNode, OH_AudioFormat *audioFormat)](#oh_audiosuiteengine_setaudioformat) | - | Sets the audio format for input or output nodes after creation. This function is supported only for input and output nodes. The input node specifies the audio source format, and the output node specifies the target format.|
|<!--DelRow--> [int32_t OH_AudioSuiteEngineSystem_SetAudioFormat(OH_AudioNode* audioNode, OH_AudioSuite_SystemNodeFormat* audioFormat)](#oh_audiosuiteenginesystem_setaudioformat) | - | Sets the audio format of the input/output node, specifying the audio format of the audio source for the input node, or the target audio format for the output node. |
| [OH_AudioSuite_Result OH_AudioSuiteEngine_ConnectNodes(OH_AudioNode* sourceAudioNode, OH_AudioNode* destAudioNode)](#oh_audiosuiteengine_connectnodes) | - | Connects two nodes, with the data flow going from sourceAudioNode to destAudioNode. Connecting nodes changes the pipeline topology and may cause partial data loss. It is recommended to perform this operation when the engine is in the stopped state.<br> Node connection order: input node -> effect node -> output node. |
| [OH_AudioSuite_Result OH_AudioSuiteEngine_DisconnectNodes(OH_AudioNode* sourceAudioNode, OH_AudioNode* destAudioNode)](#oh_audiosuiteengine_disconnectnodes) | - | Disconnects two nodes. This operation changes the pipeline topology and may cause data loss. It is recommended to perform this operation when the engine is in the stopped state. |
| [OH_AudioSuite_Result OH_AudioSuiteEngine_SetEqualizerFrequencyBandGains(OH_AudioNode* audioNode, OH_EqualizerFrequencyBandGains frequencyBandGains)](#oh_audiosuiteengine_setequalizerfrequencybandgains) | - | Sets the band gain effect for the current equalizer node.|
| [OH_AudioSuite_Result OH_AudioSuiteEngine_GetEqualizerFrequencyBandGains(OH_AudioNode* audioNode, OH_EqualizerFrequencyBandGains* frequencyBandGains)](#oh_audiosuiteengine_getequalizerfrequencybandgains) | - | Obtains the band gain effect of the current equalizer node.|
| [OH_AudioSuite_Result OH_AudioSuiteEngine_SetSoundFieldType(OH_AudioNode* audioNode, OH_SoundFieldType soundFieldType)](#oh_audiosuiteengine_setsoundfieldtype) | - | Sets the configuration parameters for the sound field effect node.|
| [OH_AudioSuite_Result OH_AudioSuiteEngine_GetSoundFieldType(OH_AudioNode* audioNode, OH_SoundFieldType* soundFieldType)](#oh_audiosuiteengine_getsoundfieldtype) | - | Obtains the configuration parameters of the sound field effect node.|
| [OH_AudioSuite_Result OH_AudioSuiteEngine_SetEnvironmentType(OH_AudioNode* audioNode, OH_EnvironmentType environmentType)](#oh_audiosuiteengine_setenvironmenttype) | - | Sets the configuration parameters for the environment effect node.|
| [OH_AudioSuite_Result OH_AudioSuiteEngine_GetEnvironmentType(OH_AudioNode* audioNode, OH_EnvironmentType* environmentType)](#oh_audiosuiteengine_getenvironmenttype) | - | Obtains the configuration parameters of the environment effect node.|
| [OH_AudioSuite_Result OH_AudioSuiteEngine_SetVoiceBeautifierType(OH_AudioNode* audioNode, OH_VoiceBeautifierType voiceBeautifierType)](#oh_audiosuiteengine_setvoicebeautifiertype) | - | Sets the configuration parameters for the voice beautifier effect node.|
| [OH_AudioSuite_Result OH_AudioSuiteEngine_GetVoiceBeautifierType(OH_AudioNode* audioNode, OH_VoiceBeautifierType* voiceBeautifierType)](#oh_audiosuiteengine_getvoicebeautifiertype) | - | Obtains the configuration parameters of the voice beautifier effect node.|
| [OH_AudioSuite_Result OH_AudioSuiteEngine_IsNodeTypeSupported(OH_AudioNode_Type nodeType, bool* isSupported)](#oh_audiosuiteengine_isnodetypesupported) | - | Checks whether the system supports the creation of a specified node type to avoid node creation failure. This function is called independently of engine and pipeline states and is only related to the system, without the need to create an engine or pipeline.|
| [OH_AudioSuite_Result OH_AudioSuiteEngine_SetSpaceRenderPositionParams(OH_AudioNode* audioNode, OH_AudioSuite_SpaceRenderPositionParams position)](#oh_audiosuiteengine_setspacerenderpositionparams) | - | Sets the configuration parameters for the fixed-position mode of the spatial rendering effect node.|
| [OH_AudioSuite_Result OH_AudioSuiteEngine_GetSpaceRenderPositionParams(OH_AudioNode* audioNode, OH_AudioSuite_SpaceRenderPositionParams* position)](#oh_audiosuiteengine_getspacerenderpositionparams) | - | Obtains the configuration parameters for the fixed-position mode of the spatial rendering effect node.|
| [OH_AudioSuite_Result OH_AudioSuiteEngine_SetSpaceRenderRotationParams(OH_AudioNode* audioNode, OH_AudioSuite_SpaceRenderRotationParams rotation)](#oh_audiosuiteengine_setspacerenderrotationparams) | - | Sets the configuration parameters for the rotation mode of the spatial rendering effect node.|
| [OH_AudioSuite_Result OH_AudioSuiteEngine_GetSpaceRenderRotationParams(OH_AudioNode* audioNode, OH_AudioSuite_SpaceRenderRotationParams* rotation)](#oh_audiosuiteengine_getspacerenderrotationparams) | - | Obtains the configuration parameters for the rotation mode of the spatial rendering effect node.|
| [OH_AudioSuite_Result OH_AudioSuiteEngine_SetSpaceRenderExtensionParams(OH_AudioNode* audioNode, OH_AudioSuite_SpaceRenderExtensionParams extension)](#oh_audiosuiteengine_setspacerenderextensionparams) | - | Sets the configuration parameters for the extension mode of the spatial rendering effect node.|
| [OH_AudioSuite_Result OH_AudioSuiteEngine_GetSpaceRenderExtensionParams(OH_AudioNode* audioNode, OH_AudioSuite_SpaceRenderExtensionParams* extension)](#oh_audiosuiteengine_getspacerenderextensionparams) | - | Obtains the configuration parameters for the extension mode of the spatial rendering effect node.|
| [OH_AudioSuite_Result OH_AudioSuiteEngine_SetTempoAndPitch(OH_AudioNode* audioNode, float speed, float pitch)](#oh_audiosuiteengine_settempoandpitch) | - | Sets the configuration parameters of the tempo and pitch shifting effect node.|
| [OH_AudioSuite_Result OH_AudioSuiteEngine_GetTempoAndPitch(OH_AudioNode* audioNode, float* speed, float* pitch)](#oh_audiosuiteengine_gettempoandpitch) | - | Obtains the configuration parameters of the tempo and pitch shifting effect node.|
| [OH_AudioSuite_Result OH_AudioSuiteEngine_SetPureVoiceChangeOption(OH_AudioNode* audioNode, OH_AudioSuite_PureVoiceChangeOption option)](#oh_audiosuiteengine_setpurevoicechangeoption) | - | Sets the configuration parameters of the pure voice change node.|
| [OH_AudioSuite_Result OH_AudioSuiteEngine_GetPureVoiceChangeOption(OH_AudioNode* audioNode, OH_AudioSuite_PureVoiceChangeOption* option)](#oh_audiosuiteengine_getpurevoicechangeoption) | - | Obtains the configuration parameters of the pure voice change node.|
| [OH_AudioSuite_Result OH_AudioSuiteEngine_SetGeneralVoiceChangeType(OH_AudioNode* audioNode, OH_AudioSuite_GeneralVoiceChangeType type)](#oh_audiosuiteengine_setgeneralvoicechangetype) | - | Sets the configuration parameters of the general voice change node.|
| [OH_AudioSuite_Result OH_AudioSuiteEngine_GetGeneralVoiceChangeType(OH_AudioNode* audioNode, OH_AudioSuite_GeneralVoiceChangeType* type)](#oh_audiosuiteengine_getgeneralvoicechangetype) | - | Obtains the configuration parameters of the general voice change node.|
| [OH_AudioSuite_Result OH_AudioSuite_PrintInfo(OH_AudioSuiteEngine* audioSuiteEngine, OH_AudioSuitePipeline* audioSuitePipeline, int fd)](#oh_audiosuite_printinfo) | - | Prints the AudioSuite runtime snapshot.|
|<!--DelRow--> [int32_t OH_AudioSuiteEngineSystem_SetNodeParam(OH_AudioNode* audioNode, uint8_t* param, uint32_t paramSize)](#oh_audiosuiteenginesystem_setnodeparam) | - | Sets the parameters of the system node. |
|<!--DelRow--> [int32_t OH_AudioSuiteEngineSystem_GetNodeParam(OH_AudioNode* audioNode, uint8_t* param, uint32_t paramSize)](#oh_audiosuiteenginesystem_getnodeparam) | - | Obtains the parameters of the system node. |
|<!--DelRow--> [int32_t OH_AudioSuiteEngineSystem_GetNodeInOutSize(OH_AudioNode* audioNode, uint32_t* inSize, uint32_t* outSize)](#oh_audiosuiteenginesystem_getnodeinoutsize) | - | Obtains the input and output frame sizes of the system node. |

## Function Description

### OH_AudioSuiteEngine_Create()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_Create(OH_AudioSuiteEngine** audioSuiteEngine)
```

**Description**

Creates an audio creation engine.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioSuiteEngine](capi-ohaudiosuite-oh-audiosuiteenginestruct.md)** audioSuiteEngine | Double pointer used to receive the handle to the newly created audio creation engine.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioSuite_Result](capi-native-audio-suite-base-h.md#oh_audiosuite_result) | **AUDIOSUITE_SUCCESS**: The function is executed successfully.<br>         **AUDIOSUITE_ERROR_INVALID_PARAM**: The **audioSuiteEngine** parameter is nullptr.<br>         **AUDIOSUITE_ERROR_INVALID_STATE**: The engine has been initialized.<br>         **AUDIOSUITE_ERROR_MEMORY_ALLOC_FAILED**: Memory allocation fails.<br>         **AUDIOSUITE_ERROR_SYSTEM**: Other system exceptions occur.|

### OH_AudioSuiteEngine_Destroy()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_Destroy(OH_AudioSuiteEngine* audioSuiteEngine)
```

**Description**

Destroys the handle to an audio creation engine.

>**NOTE** 
>When an engine is destroyed, all pipelines under the engine are destroyed.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioSuiteEngine](capi-ohaudiosuite-oh-audiosuiteenginestruct.md)* audioSuiteEngine | Audio creation engine handle, which is obtained by calling [OH_AudioSuiteEngine_Create](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_create).|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioSuite_Result](capi-native-audio-suite-base-h.md#oh_audiosuite_result) | AUDIOSUITE_SUCCESS: The function is executed successfully.<br>         AUDIOSUITE_ERROR_INVALID_PARAM: The audioSuiteEngine parameter is a null pointer.<br>         AUDIOSUITE_ERROR_INVALID_STATE: The engine has been deinitialized, not created, or not initialized.<br>         AUDIOSUITE_ERROR_SYSTEM: Another system exception occurs. |

### OH_AudioSuiteEngine_CreatePipeline()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_CreatePipeline(OH_AudioSuiteEngine* audioSuiteEngine, OH_AudioSuitePipeline** audioSuitePipeline, OH_AudioSuite_PipelineWorkMode workMode)
```

**Description**

Creates a pipeline within the current audio creation engine. A pipeline is the execution unit within the engine responsible for audio creation, and multiple pipelines can be created within a single engine.<br> A maximum of 10 pipelines can be created. Before API version 26.0.0, only one real-time preview pipeline can be created. Since API version 26.0.0, there is no longer a separate limit on the number of real-time preview pipelines. However, the total number of pipelines must not exceed 10.<br> Each pipeline must have at least one input node and exactly one output node.<br> When the pipeline works in [OH_AudioSuite_PipelineWorkMode](capi-native-audio-suite-base-h.md#oh_audiosuite_pipelineworkmode).AUDIOSUITE_PIPELINE_EDIT_MODE mode, all effect nodes are supported.<br> Before API version 23, when a pipeline works in [OH_AudioSuite_PipelineWorkMode](capi-native-audio-suite-base-h.md#oh_audiosuite_pipelineworkmode).AUDIOSUITE_PIPELINE_REALTIME_MODE mode, only the effect node [OH_AudioNode_Type](capi-native-audio-suite-base-h.md#oh_audionode_type).EFFECT_NODE_TYPE_EQUALIZER is supported.<br> Since API version 23, when a pipeline works in [OH_AudioSuite_PipelineWorkMode](capi-native-audio-suite-base-h.md#oh_audiosuite_pipelineworkmode).AUDIOSUITE_PIPELINE_REALTIME_MODE mode, all effect nodes are supported.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioSuiteEngine](capi-ohaudiosuite-oh-audiosuiteenginestruct.md)* audioSuiteEngine | Audio creation engine handle, which is obtained by calling [OH_AudioSuiteEngine_Create](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_create).|
| [OH_AudioSuitePipeline](capi-ohaudiosuite-oh-audiosuitepipelinestruct.md)** audioSuitePipeline | Double pointer used to receive the handle to the newly created audio creation pipeline.|
| [OH_AudioSuite_PipelineWorkMode](capi-native-audio-suite-base-h.md#oh_audiosuite_pipelineworkmode) workMode | Pipeline work mode. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioSuite_Result](capi-native-audio-suite-base-h.md#oh_audiosuite_result) | **AUDIOSUITE_SUCCESS**: The function is executed successfully.<br>         **AUDIOSUITE_ERROR_INVALID_PARAM**: The **audioSuiteEngine** or **audioSuitePipeline** parameter is nullptr.<br>         **AUDIOSUITE_ERROR_ENGINE_NOT_EXIST**: The engine is not initialized.<br>         **AUDIOSUITE_ERROR_CREATED_EXCEED_SYSTEM_LIMITS**: The number of pipelines created already reaches the upper limit. (An engine can create a maximum of 10 pipelines.)<br>         **AUDIOSUITE_ERROR_TIMEOUT**: The operation times out.<br>         **AUDIOSUITE_ERROR_MEMORY_ALLOC_FAILED**: Memory allocation fails.<br>         **AUDIOSUITE_ERROR_SYSTEM**: Other system exceptions occur.|

### OH_AudioSuiteEngine_DestroyPipeline()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_DestroyPipeline(OH_AudioSuitePipeline* audioSuitePipeline)
```

**Description**

Destroys the handle to an audio creation pipeline.

>**NOTE** 
>When a pipeline is destroyed, all nodes under the pipeline are destroyed.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioSuitePipeline](capi-ohaudiosuite-oh-audiosuitepipelinestruct.md)* audioSuitePipeline | Audio creation pipeline handle, which is obtained by calling [OH_AudioSuiteEngine_CreatePipeline](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_createpipeline).|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioSuite_Result](capi-native-audio-suite-base-h.md#oh_audiosuite_result) | **AUDIOSUITE_SUCCESS**: The function is executed successfully.<br>         **AUDIOSUITE_ERROR_INVALID_PARAM**: The **audioSuitePipeline** parameter is nullptr.<br>         **AUDIOSUITE_ERROR_PIPELINE_NOT_EXIST**: The pipeline does not exist or has been destroyed.<br>         **AUDIOSUITE_ERROR_TIMEOUT**: The operation times out.<br>         **AUDIOSUITE_ERROR_SYSTEM**: Other system exceptions occur.|

### OH_AudioSuiteEngine_StartPipeline()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_StartPipeline(OH_AudioSuitePipeline* audioSuitePipeline)
```

**Description**

Starts the pipeline. The pipeline will enter the [OH_AudioSuite_PipelineState](capi-native-audio-suite-base-h.md#oh_audiosuite_pipelinestate).AUDIOSUITE_PIPELINE_RUNNING state.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioSuitePipeline](capi-ohaudiosuite-oh-audiosuitepipelinestruct.md)* audioSuitePipeline | Audio creation pipeline handle, which is obtained by calling [OH_AudioSuiteEngine_CreatePipeline](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_createpipeline).|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioSuite_Result](capi-native-audio-suite-base-h.md#oh_audiosuite_result) | Returns AUDIOSUITE_SUCCESS if the function is executed successfully.<br>         Returns AUDIOSUITE_ERROR_INVALID_PARAM if the audioSuitePipeline parameter is a null pointer.<br>         Returns AUDIOSUITE_ERROR_PIPELINE_NOT_EXIST if the pipeline does not exist or has been destroyed.<br>         Returns AUDIOSUITE_ERROR_INVALID_STATE if the pipeline is already running or the node connection is abnormal.<br>         Possible causes are as follows:<br>         1. The pipeline is already in the running state;<br>         2. No output node exists in the current pipeline;<br>         3. The start node is not an input node.<br>         4. The input node in HOA (High-Order Ambisonics) audio format is not connected to an HOA spatial rendering node, or the preceding node of the HOA spatial rendering node is not an input node in HOA format.<br>         Returns AUDIOSUITE_ERROR_TIMEOUT if the operation processing times out.<br>         Returns AUDIOSUITE_ERROR_SYSTEM if another exception occurs in the system. |

### OH_AudioSuiteEngine_StopPipeline()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_StopPipeline(OH_AudioSuitePipeline* audioSuitePipeline)
```

**Description**

Stops the pipeline. The pipeline will enter the [OH_AudioSuite_PipelineState](capi-native-audio-suite-base-h.md#oh_audiosuite_pipelinestate).AUDIOSUITE_PIPELINE_STOPPED state. This function does not change the connections between nodes within the pipeline. Once the pipeline is stopped, [OH_AudioSuiteEngine_RenderFrame](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_renderframe) can no longer perform audio processing.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioSuitePipeline](capi-ohaudiosuite-oh-audiosuitepipelinestruct.md)* audioSuitePipeline | Audio creation pipeline handle, which is obtained by calling [OH_AudioSuiteEngine_CreatePipeline](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_createpipeline).|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioSuite_Result](capi-native-audio-suite-base-h.md#oh_audiosuite_result) | **AUDIOSUITE_SUCCESS**: The function is executed successfully.<br>         **AUDIOSUITE_ERROR_INVALID_PARAM**: The **audioSuitePipeline** parameter is nullptr.<br>         **AUDIOSUITE_ERROR_PIPELINE_NOT_EXIST**: The pipeline does not exist or has been destroyed.<br>         **AUDIOSUITE_ERROR_INVALID_STATE**: The pipeline is already stopped.<br>         **AUDIOSUITE_ERROR_TIMEOUT**: The operation times out.<br>         **AUDIOSUITE_ERROR_SYSTEM**: Other system exceptions occur.|

### OH_AudioSuiteEngine_GetPipelineState()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_GetPipelineState(OH_AudioSuitePipeline* audioSuitePipeline, OH_AudioSuite_PipelineState* pipelineState)
```

**Description**

Retrieves the state of the pipeline.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioSuitePipeline](capi-ohaudiosuite-oh-audiosuitepipelinestruct.md)* audioSuitePipeline | Audio creation pipeline handle, which is obtained by calling [OH_AudioSuiteEngine_CreatePipeline](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_createpipeline).|
| [OH_AudioSuite_PipelineState](capi-native-audio-suite-base-h.md#oh_audiosuite_pipelinestate)* pipelineState | Pointer to the pipeline state.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioSuite_Result](capi-native-audio-suite-base-h.md#oh_audiosuite_result) | **AUDIOSUITE_SUCCESS**: The function is executed successfully.<br>         **AUDIOSUITE_ERROR_INVALID_PARAM**: Invalid parameters. For example, **audioSuitePipeline** is nullptr.<br>         **AUDIOSUITE_ERROR_PIPELINE_NOT_EXIST**: The pipeline does not exist or has been destroyed.<br>         **AUDIOSUITE_ERROR_TIMEOUT**: The operation times out.<br>         **AUDIOSUITE_ERROR_SYSTEM**: Other system exceptions occur.|

### OH_AudioSuiteEngine_RenderFrame()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_RenderFrame(OH_AudioSuitePipeline* audioSuitePipeline, void* audioData, int32_t requestFrameSize, int32_t* responseSize, bool* finishedFlag)
```

**Description**

Obtains the processed audio data from the pipeline (for single-output effect nodes).

> **NOTE** 
>
> Applications need to call this function to obtain audio data that has been processed by effects.
> * When this function is called, the pipeline pulls data backward from the output node, applies effect processing, and fills the processed data into the **audioData** pointer provided by the application.
> * The system attempts to fill the data based on the size specified by **requestFrameSize**, and the actual size of the processed data is returned to the application via **responseSize**.
> * When the application has prepared data for all input nodes and submits the final data through the callback, it should set the completion flag in the callback.
> * After all inputs in the pipeline have passed the completion flag, the API will notify the application via **finishedFlag** once processing is complete.
> * If **finishedFlag** is **true**, the application should not call this function again.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioSuitePipeline](capi-ohaudiosuite-oh-audiosuitepipelinestruct.md)* audioSuitePipeline | Audio creation pipeline handle, which is obtained by calling [OH_AudioSuiteEngine_CreatePipeline](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_createpipeline).|
| void* audioData | Pointer to the address for writing the obtained audio data.|
| int32_t requestFrameSize | Byte size of the memory allocated for **audioData**. The value must be greater than 0.|
| int32_t* responseSize | Pointer to the size of the audio data written to **audioData** by the pipeline. The value cannot be greater than **requestFrameSize**. The unit is bytes.|
| bool* finishedFlag | Pointer to the flag indicating whether the current pipeline has completed rendering.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioSuite_Result](capi-native-audio-suite-base-h.md#oh_audiosuite_result) | **AUDIOSUITE_SUCCESS**: The function is executed successfully.<br>         **AUDIOSUITE_ERROR_INVALID_PARAM**: A parameter is nullptr or has an invalid value.<br>         Possible causes are as follows:<br>         1. The **audioSuitePipeline** parameter is nullptr.<br>         2. The **audioData** parameter is nullptr.<br>         3. The value of **requestFrameSize** is less than or equal to 0.<br>         4. The **responseSize** parameter is nullptr.<br>         5. The **finishedFlag** parameter is nullptr.<br>         **AUDIOSUITE_ERROR_PIPELINE_NOT_EXIST**: The pipeline does not exist or has been destroyed.<br>         **AUDIOSUITE_ERROR_INVALID_STATE**: The pipeline is not running.<br>         **AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION**: The pipeline rendering is complete. (**finishedFlag** is written as **true** when this function is called.)<br>         **AUDIOSUITE_ERROR_TIMEOUT**: The operation times out.<br>         **AUDIOSUITE_ERROR_SYSTEM**: Other system exceptions occur.|

### OH_AudioSuiteEngine_MultiRenderFrame()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_MultiRenderFrame(OH_AudioSuitePipeline* audioSuitePipeline, OH_AudioDataArray* audioDataArray, int32_t* responseSize, bool* finishedFlag)
```

**Description**

Renders the pipeline and obtains the processed audio data. For pipelines with multiple output effect nodes (for example, those containing audio separation nodes), the size of **audioDataArray** must correspond one-to-one with the number of outputs from the effect nodes. (For example, audio separation nodes require two outputs: the first for vocals and the second for background sound.)

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioSuitePipeline](capi-ohaudiosuite-oh-audiosuitepipelinestruct.md)* audioSuitePipeline | Audio creation pipeline handle, which is obtained by calling [OH_AudioSuiteEngine_CreatePipeline](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_createpipeline).|
| [OH_AudioDataArray](capi-ohaudiosuite-oh-audiodataarray.md)* audioDataArray | Pointer to the array used by the user to read audio data. Each element of the array must be of the same size.|
| int32_t* responseSize | Size of the audio data written by the pipeline to audioDataArray. The system ensures that each one-dimensional array is filled with data of the same size, in bytes. |
| bool* finishedFlag | Pointer to the flag indicating whether the current pipeline has completed rendering.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioSuite_Result](capi-native-audio-suite-base-h.md#oh_audiosuite_result) | **AUDIOSUITE_SUCCESS**: The function is executed successfully.<br>         **AUDIOSUITE_ERROR_INVALID_PARAM**: A parameter is nullptr or has an invalid value.<br>         Possible causes are as follows:<br>         1. The **audioSuitePipeline** parameter is nullptr.<br>         2. The **audioDataArray** parameter is nullptr.<br>         3. A member of the **audioDataArray** parameter is nullptr.<br>         4. The value of **requestFrameSize** in **audioDataArray** is less than or equal to 0.<br>         5. The **responseSize** parameter is nullptr.<br>         6. The **finishedFlag** parameter is nullptr.<br>         **AUDIOSUITE_ERROR_PIPELINE_NOT_EXIST**: The pipeline does not exist or has been destroyed.<br>         **AUDIOSUITE_ERROR_INVALID_STATE**: The pipeline is not running.<br>         **AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION**: The pipeline rendering is complete. (**finishedFlag** is written as **true** when this function is called.)<br>         **AUDIOSUITE_ERROR_TIMEOUT**: The operation times out.<br>         **AUDIOSUITE_ERROR_SYSTEM**: Other system exceptions occur.|
<!--Del-->
### OH_AudioSuiteEngine_MetaRenderFrame()

```c
int32_t OH_AudioSuiteEngine_MetaRenderFrame(OH_AudioSuitePipeline* audioSuitePipeline, OH_AudioSuite_MetaFrame* metaFrame, int32_t* responseAudioSize, int32_t* responseMetaSize, bool* finishedFlag)
```

**Description**

Processes audio data and metadata. The application must specify the audioData and metaData pointers and their corresponding sizes (AudioDataSize and metaDataSize) in the metaFrame struct.<br> After processing, the actual output data sizes are returned through responseAudioSize and responseMetaSize.

**Since:** 26.0.0

**System API:** This is a system API.

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioSuitePipeline](capi-ohaudiosuite-oh-audiosuitepipelinestruct.md)* audioSuitePipeline | Audio creation pipeline handle. Obtained through [OH_AudioSuiteEngine_CreatePipeline](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_createpipeline). |
| [OH_AudioSuite_MetaFrame](capi-ohaudiosuite-oh-audiosuite-metaframe-sys.md)* metaFrame | Pointer to the audio metadata frame struct. |
| int32_t* responseAudioSize | Size of the audio data actually written by the API, in bytes. |
| int32_t* responseMetaSize | Size of the metadata actually written by the API, in bytes. |
| bool* finishedFlag | Flag used to indicate to the user whether all data processing has been completed. |

**Returns**

| Type | Description |
| -- | -- |
| int32_t | Result code.<br> [AUDIOSUITE_SUCCESS](capi-native-audio-suite-base-h.md#oh_audiosuite_result): the function is executed successfully.<br>         202: a non-system application called this system API.<br>         [AUDIOSUITE_ERROR_INVALID_PARAM](capi-native-audio-suite-base-h.md#oh_audiosuite_result): the parameter is a null pointer or has another invalid value.<br>         [AUDIOSUITE_ERROR_PIPELINE_NOT_EXIST](capi-native-audio-suite-base-h.md#oh_audiosuite_result): the pipeline does not exist or has been destroyed.<br>         [AUDIOSUITE_ERROR_INVALID_STATE](capi-native-audio-suite-base-h.md#oh_audiosuite_result): the pipeline is not in the running state.<br>         [AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION](capi-native-audio-suite-base-h.md#oh_audiosuite_result): pipeline rendering is complete (finishedFlag was written as true in a previous call to this API).<br>         [AUDIOSUITE_ERROR_TIMEOUT](capi-native-audio-suite-base-h.md#oh_audiosuite_result): the operation processing timed out.<br>         [AUDIOSUITE_ERROR_SYSTEM](capi-native-audio-suite-base-h.md#oh_audiosuite_result): another system exception occurred. |
<!--DelEnd-->

### OH_AudioSuiteNodeBuilder_Create()

```c
OH_AudioSuite_Result OH_AudioSuiteNodeBuilder_Create(OH_AudioNodeBuilder** builder)
```

**Description**

Obtains an audio creation node builder, which is used to configure and create audio nodes. The builder can be reused. However, if the attributes of the new node are different from those of the previous node, you must use [OH_AudioSuiteNodeBuilder_Reset](capi-native-audio-suite-engine-h.md#oh_audiosuitenodebuilder_reset) to reset the builder.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioNodeBuilder](capi-ohaudiosuite-oh-audionodebuilderstruct.md)** builder | Double pointer used to receive the handle to the audio creation node.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioSuite_Result](capi-native-audio-suite-base-h.md#oh_audiosuite_result) | **AUDIOSUITE_SUCCESS**: The function is executed successfully.<br>         **AUDIOSUITE_ERROR_INVALID_PARAM**: Invalid parameters. For example, **builder** is nullptr.<br>         **AUDIOSUITE_ERROR_MEMORY_ALLOC_FAILED**: Memory allocation fails.<br>         **AUDIOSUITE_ERROR_SYSTEM**: Other system exceptions occur.|

### OH_AudioSuiteNodeBuilder_Destroy()

```c
OH_AudioSuite_Result OH_AudioSuiteNodeBuilder_Destroy(OH_AudioNodeBuilder* builder)
```

**Description**

Destroys an audio creation node builder. This function must be called after the builder is no longer required.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioNodeBuilder](capi-ohaudiosuite-oh-audionodebuilderstruct.md)* builder | Audio creation node handle, which is obtained by calling [OH_AudioSuiteNodeBuilder_Create](capi-native-audio-suite-engine-h.md#oh_audiosuitenodebuilder_create).|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioSuite_Result](capi-native-audio-suite-base-h.md#oh_audiosuite_result) | **AUDIOSUITE_SUCCESS**: The function is executed successfully.<br>         **AUDIOSUITE_ERROR_INVALID_PARAM**: Invalid parameters. For example, **builder** is nullptr.<br>         **AUDIOSUITE_ERROR_SYSTEM**: Other system exceptions occur.|

### OH_AudioSuiteNodeBuilder_Reset()

```c
OH_AudioSuite_Result OH_AudioSuiteNodeBuilder_Reset(OH_AudioNodeBuilder* builder)
```

**Description**

Resets an audio creation node builder, clearing all previously set parameters. If you want to reuse the builder to create a node with different properties, this function must be called to clear all properties (for example, node type).

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioNodeBuilder](capi-ohaudiosuite-oh-audionodebuilderstruct.md)* builder | Audio creation node handle, which is obtained by calling [OH_AudioSuiteNodeBuilder_Create](capi-native-audio-suite-engine-h.md#oh_audiosuitenodebuilder_create).|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioSuite_Result](capi-native-audio-suite-base-h.md#oh_audiosuite_result) | **AUDIOSUITE_SUCCESS**: The function is executed successfully.<br>         **AUDIOSUITE_ERROR_INVALID_PARAM**: Invalid parameters. For example, **builder** is nullptr.<br>         **AUDIOSUITE_ERROR_SYSTEM**: Other system exceptions occur.|

### OH_AudioSuiteNodeBuilder_SetNodeType()

```c
OH_AudioSuite_Result OH_AudioSuiteNodeBuilder_SetNodeType(OH_AudioNodeBuilder* builder, OH_AudioNode_Type type)
```

**Description**

Sets the type of node to be constructed by the current node builder. During node creation, other parameters are verified based on the node type. This property must be set for all node types.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioNodeBuilder](capi-ohaudiosuite-oh-audionodebuilderstruct.md)* builder | Audio creation node handle, which is obtained by calling [OH_AudioSuiteNodeBuilder_Create](capi-native-audio-suite-engine-h.md#oh_audiosuitenodebuilder_create).|
| [OH_AudioNode_Type](capi-native-audio-suite-base-h.md#oh_audionode_type) type | Node type.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioSuite_Result](capi-native-audio-suite-base-h.md#oh_audiosuite_result) | **AUDIOSUITE_SUCCESS**: The node type is set successfully.<br>         **AUDIOSUITE_ERROR_INVALID_PARAM**: A parameter is invalid. For example, **builder** is a null pointer.<br>         **AUDIOSUITE_ERROR_SYSTEM**: Other system exceptions occur.|
<!--Del-->
### OH_AudioSuiteNodeBuilderSystem_SetNodeType()

```c
int32_t OH_AudioSuiteNodeBuilderSystem_SetNodeType(OH_AudioNodeBuilder* builder, OH_AudioSuite_SystemNodeType type)
```

**Description**

Sets the audio node type to be created by the builder.

**Since:** 26.0.0

**System API:** This is a system API.

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioNodeBuilder](capi-ohaudiosuite-oh-audionodebuilderstruct.md)* builder | Handle to the audio creation node builder. Obtain it through [OH_AudioSuiteNodeBuilder_Create](capi-native-audio-suite-engine-h.md#oh_audiosuitenodebuilder_create). |
| [OH_AudioSuite_SystemNodeType](capi-native-audio-suite-base-h.md#oh_audiosuite_systemnodetype) type | Audio system node type of [OH_AudioSuite_SystemNodeType](capi-native-audio-suite-base-h.md#oh_audiosuite_systemnodetype). |

**Returns**

| Type | Description |
| -- | -- |
| int32_t | [AUDIOSUITE_SUCCESS](capi-native-audio-suite-base-h.md#oh_audiosuite_result): the node type is configured successfully.<br>         202: a non-system application calls this system API.<br>         [AUDIOSUITE_ERROR_INVALID_PARAM](capi-native-audio-suite-base-h.md#oh_audiosuite_result): invalid parameter, for example, builder is a null pointer. |
<!--DelEnd-->

### OH_AudioSuiteNodeBuilder_SetFormat()

```c
OH_AudioSuite_Result OH_AudioSuiteNodeBuilder_SetFormat(OH_AudioNodeBuilder* builder, OH_AudioFormat audioFormat)
```

**Description**

Configures the audio format of the input/output node. This function can be used only before the node is created. For an input node, this function allows the application to specify the audio format of the data to be written;<br> for an output node, this function allows the application to specify the audio format of the data it expects to obtain;<br> for nodes of other types, calling this function to set the audio format is not supported.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioNodeBuilder](capi-ohaudiosuite-oh-audionodebuilderstruct.md)* builder | Audio creation node handle, which is obtained by calling [OH_AudioSuiteNodeBuilder_Create](capi-native-audio-suite-engine-h.md#oh_audiosuitenodebuilder_create).|
| [OH_AudioFormat](capi-ohaudiosuite-oh-audioformat.md) audioFormat | Audio stream format.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioSuite_Result](capi-native-audio-suite-base-h.md#oh_audiosuite_result) | **AUDIOSUITE_SUCCESS**: The function is executed successfully.<br>         **AUDIOSUITE_ERROR_INVALID_PARAM**: A parameter is invalid. For example, **builder** is a null pointer.<br>         **AUDIOSUITE_ERROR_UNSUPPORTED_FORMAT**: The value of **channelCount** in **audioFormat** is not supported.<br>         **AUDIOSUITE_ERROR_SYSTEM**: Other system exceptions occur.|
<!--Del-->
### OH_AudioSuiteNodeBuilderSystem_SetFormat()

```c
int32_t OH_AudioSuiteNodeBuilderSystem_SetFormat(OH_AudioNodeBuilder* builder, OH_AudioSuite_SystemNodeFormat audioFormat)
```

**Description**

Sets the audio format supported by the node.

**Since:** 26.0.0

**System API:** This is a system API.

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioNodeBuilder](capi-ohaudiosuite-oh-audionodebuilderstruct.md)* builder | Handle to the audio creation node builder. Obtain it through [OH_AudioSuiteNodeBuilder_Create](capi-native-audio-suite-engine-h.md#oh_audiosuitenodebuilder_create). |
| [OH_AudioSuite_SystemNodeFormat](capi-ohaudiosuite-oh-audiosuite-systemnodeformat-sys.md) audioFormat | Audio node format. |

**Returns**

| Type | Description |
| -- | -- |
| int32_t | Result code.<br> [AUDIOSUITE_SUCCESS](capi-native-audio-suite-base-h.md#oh_audiosuite_result): the function is executed successfully.<br>         202: a non-system application calls this system API.<br>         [AUDIOSUITE_ERROR_INVALID_PARAM](capi-native-audio-suite-base-h.md#oh_audiosuite_result): invalid parameter, for example, builder is a null pointer.<br>         [AUDIOSUITE_ERROR_UNSUPPORTED_FORMAT](capi-native-audio-suite-base-h.md#oh_audiosuite_result): an audio format in audioFormat is not supported. |
<!--DelEnd-->

### OH_InputNode_RequestDataCallback()

```c
typedef int32_t (*OH_InputNode_RequestDataCallback)(OH_AudioNode* audioNode, void* userData, void* audioData, int32_t audioDataSize, bool* finished)
```

**Description**

Defines the callback function for the input node to request data.

> **NOTE**
>  
> Applications should write the PCM audio data to be processed to **audioData**, from which OHAudioSuite obtains the data for audio creation.
> * Applications should write data to **audioData** that does not exceed the size specified by **audioDataSize**.
> * Once all data has been passed to the pipeline through this callback, the application should set **finished** to **true** in the last callback. After this, the pipeline will no longer call this function.
> * Only input nodes require this configuration; other nodes do not.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| OH_AudioNode* audioNode | Audio creation node handle, which is obtained by calling [OH_AudioSuiteEngine_CreateNode](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_createnode).|
| void* userData | Pointer to user-specific data. When the system calls this callback function, **userData** passed by calling [OH_AudioSuiteNodeBuilder_SetRequestDataCallback](capi-native-audio-suite-engine-h.md#oh_audiosuitenodebuilder_setrequestdatacallback) is used.|
| void* audioData | Pointer to the memory address provided by the system, where the application should write the audio data stream to be processed (to be filled by the user).|
| int32_t audioDataSize | Size of the audio data pointed to by the memory address of audioData, in bytes. |
| bool* finished | Pointer to the flag indicating whether the audio data stream for the node specified by **audioNode** has been fully written. **true** if fully written, **false** otherwise.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Effective length of the data written into the **audioData** buffer (in bytes).<br> The return value must be in the range of [0, audioDataSize]. If the return value is less than 0, the system changes the return value to **0**.<br> If the return value is greater than **audioDataSize**, the system changes the return value to **audioDataSize**.|

### OH_AudioSuiteNodeBuilder_SetRequestDataCallback()

```c
OH_AudioSuite_Result OH_AudioSuiteNodeBuilder_SetRequestDataCallback(OH_AudioNodeBuilder* builder, OH_InputNode_RequestDataCallback callback, void* userData)
```

**Description**

Sets a callback function for writing audio data for the current input node builder.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioNodeBuilder](capi-ohaudiosuite-oh-audionodebuilderstruct.md)* builder | Audio creation node builder handle, which is obtained by calling [OH_AudioSuiteNodeBuilder_Create](capi-native-audio-suite-engine-h.md#oh_audiosuitenodebuilder_create).|
| [OH_InputNode_RequestDataCallback](capi-native-audio-suite-engine-h.md#oh_inputnode_requestdatacallback) callback | Callback for writing audio data.|
| void* userData | Pointer to the user-defined data, which is passed to the user in the callback. You can pass a null pointer if it is not used. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioSuite_Result](capi-native-audio-suite-base-h.md#oh_audiosuite_result) | **AUDIOSUITE_SUCCESS**: The function is executed successfully.<br>         **AUDIOSUITE_ERROR_INVALID_PARAM**:<br>         Possible causes are as follows:<br>         1. The **builder** parameter is nullptr.<br>         2. The **callback** parameter is nullptr.<br>         **AUDIOSUITE_ERROR_TIMEOUT**: The operation times out.<br>         **AUDIOSUITE_ERROR_SYSTEM**: Other system exceptions occur.|
<!--Del-->
### OH_InputNode_RequestMetaDataCallback()

```c
typedef int32_t (*OH_InputNode_RequestMetaDataCallback)(OH_AudioNode* audioNode, void* userData, OH_AudioSuite_MetaFrame* metaFrame, int32_t* responseMetaDataSize, bool* finished)
```

**Description**

Callback used to request metadata. Only [INPUT_NODE_TYPE_DEFAULT](capi-native-audio-suite-base-h.md#oh_audionode_type) supports this setting. The callback is triggered each time the application or user calls [OH_AudioSuiteEngine_MetaRenderFrame](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_metarenderframe).

**Since:** 26.0.0

**System API:** This is a system API.

**Parameters**

| Name | Description |
| -- | -- |
| OH_AudioNode\* audioNode | Handle to the audio creation node. Obtain it through [OH_AudioSuiteEngine_CreateNode](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_createnode). |
| void\* userData | Pointer to the user data passed by the user. |
| [OH_AudioSuite_MetaFrame](capi-ohaudiosuite-oh-audiosuite-metaframe-sys.md)\* metaFrame | Pointer to the audio metadata frame struct. |
| int32_t\* responseMetaDataSize | Size of the metadata actually written by the application, in bytes. |
| bool\* finished | Whether all audio data has been written successfully. |

**Returns**

| Type | Description |
| -- | -- |
| int32_t | Length of the valid audio data written to the audio data buffer, in bytes.<br> The return value ranges from [0, metaFrame->AudioDataSize]. |

### OH_AudioSuiteNodeBuilder_SetRequestMetaDataCallback()

```c
int32_t OH_AudioSuiteNodeBuilder_SetRequestMetaDataCallback(OH_AudioNodeBuilder* builder, OH_InputNode_RequestMetaDataCallback callback, void* userData)
```

**Description**

Configures the callback for writing audio data and metadata of the current input node builder. Only [INPUT_NODE_TYPE_DEFAULT](capi-native-audio-suite-base-h.md#oh_audionode_type) supports this setting.

**Since:** 26.0.0

**System API:** This is a system API.

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioNodeBuilder](capi-ohaudiosuite-oh-audionodebuilderstruct.md)* builder | Handle to the audio creation node builder. Obtain it through [OH_AudioSuiteNodeBuilder_Create](capi-native-audio-suite-engine-h.md#oh_audiosuitenodebuilder_create). |
| [OH_InputNode_RequestMetaDataCallback](capi-native-audio-suite-engine-h.md#oh_inputnode_requestmetadatacallback) callback | User-defined data. The address is passed to the user in the callback function. If it is not used, a null pointer can be passed. |
| void* userData | Pointer to the application data structure to be passed to the callback function. |

**Returns**

| Type | Description |
| -- | -- |
| int32_t | [AUDIOSUITE_SUCCESS](capi-native-audio-suite-base-h.md#oh_audiosuite_result): the function is executed successfully.<br>         202: a non-system application calls this system API.<br>         [AUDIOSUITE_ERROR_INVALID_PARAM](capi-native-audio-suite-base-h.md#oh_audiosuite_result): invalid parameter, for example, the builder parameter is a null pointer.<br>         [AUDIOSUITE_ERROR_TIMEOUT](capi-native-audio-suite-base-h.md#oh_audiosuite_result): the operation times out.<br>         [AUDIOSUITE_ERROR_SYSTEM](capi-native-audio-suite-base-h.md#oh_audiosuite_result): another system exception occurs. |
<!--DelEnd-->

### OH_AudioSuiteEngine_CreateNode()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_CreateNode(OH_AudioSuitePipeline* audioSuitePipeline, OH_AudioNodeBuilder* builder, OH_AudioNode** audioNode)
```

**Description**

Creates an audio node within the audio pipeline based on the audio creation builder. When this function is executed, the system checks the validity of the parameters based on the node type set in the builder.<br> Applications can determine the cause of errors based on the return value.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioSuitePipeline](capi-ohaudiosuite-oh-audiosuitepipelinestruct.md)* audioSuitePipeline | Audio creation pipeline handle, which is obtained by calling [OH_AudioSuiteEngine_CreatePipeline](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_createpipeline).|
| [OH_AudioNodeBuilder](capi-ohaudiosuite-oh-audionodebuilderstruct.md)* builder | Audio creation node builder handle, which is obtained by calling [OH_AudioSuiteNodeBuilder_Create](capi-native-audio-suite-engine-h.md#oh_audiosuitenodebuilder_create).|
| [OH_AudioNode](capi-ohaudiosuite-oh-audionodestruct.md)** audioNode | Output parameter, which is a pointer to the handle of the created audio creation node. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioSuite_Result](capi-native-audio-suite-base-h.md#oh_audiosuite_result) | **AUDIOSUITE_SUCCESS**: The function is executed successfully.<br>         **AUDIOSUITE_ERROR_INVALID_PARAM**: A parameter is nullptr or has an invalid value.<br>         Possible causes are as follows:<br>         1. The **audioSuitePipeline** parameter is nullptr.<br>         2. The **builder** parameter is nullptr.<br>         3. The **audioNode** parameter is nullptr.<br>         **AUDIOSUITE_ERROR_CREATED_EXCEED_SYSTEM_LIMITS**: The number of nodes of the current type already reaches the upper limit.<br>         For example, before API version 24, the number of effect nodes created exceeds five. Since API version 24, it exceeds 15.<br>         **AUDIOSUITE_ERROR_REQUIRED_PARAMETERS_MISSING**: Mandatory parameters are missing when creating a node of the specified type.<br>         For example, the node type is not set in the builder.<br>         **AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION**: Unsupported operations. For example, setting a callback function for an output node,<br>         or setting an audio format or callback function for an effect node.<br>         **AUDIOSUITE_ERROR_TIMEOUT**: The operation times out.<br>         **AUDIOSUITE_ERROR_MEMORY_ALLOC_FAILED**: Memory allocation fails.<br>         **AUDIOSUITE_ERROR_SYSTEM**: Other system exceptions occur.|

### OH_AudioSuiteEngine_DestroyNode()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_DestroyNode(OH_AudioNode* audioNode)
```

**Description**

Destroys an audio creation node. Whether a node can be destroyed depends on the state of its associated pipeline. If the pipeline is not in the [OH_AudioSuite_PipelineState](capi-native-audio-suite-base-h.md#oh_audiosuite_pipelinestate).AUDIOSUITE_PIPELINE_STOPPED state and the node is in the pipeline processing path, the destruction fails.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioNode](capi-ohaudiosuite-oh-audionodestruct.md)* audioNode | Audio creation node handle, which is obtained by calling [OH_AudioSuiteEngine_CreateNode](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_createnode).|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioSuite_Result](capi-native-audio-suite-base-h.md#oh_audiosuite_result) | **AUDIOSUITE_SUCCESS**: The function is executed successfully.<br>         **AUDIOSUITE_ERROR_INVALID_PARAM**: The **audioNode** parameter is nullptr.<br>         **AUDIOSUITE_ERROR_NODE_NOT_EXIST**: The node does not exist or has been destroyed.<br>         **AUDIOSUITE_ERROR_INVALID_STATE**: The pipeline is not in the stopped state.<br>         **AUDIOSUITE_ERROR_TIMEOUT**: The operation times out.<br>         **AUDIOSUITE_ERROR_SYSTEM**: Other system exceptions occur.|

### OH_AudioSuiteEngine_GetNodeBypassStatus()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_GetNodeBypassStatus(OH_AudioNode* audioNode, bool* bypassStatus)
```

**Description**

Obtains the effect bypass status of the current node. This function can be used only on effect nodes.<br> If it is called on an input or output node, the AUDIOSUITE_ERROR_INVALID_PARAM error code is returned.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioNode](capi-ohaudiosuite-oh-audionodestruct.md)* audioNode | Audio creation node handle, which is obtained by calling [OH_AudioSuiteEngine_CreateNode](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_createnode).|
| bool* bypassStatus | Pointer to the effect bypass status of the current node. **true** means that node processing is bypassed, and **false** means the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioSuite_Result](capi-native-audio-suite-base-h.md#oh_audiosuite_result) | **AUDIOSUITE_SUCCESS**: The function is executed successfully.<br>         **AUDIOSUITE_ERROR_INVALID_PARAM**:<br>         The **audioNode** or **bypassStatus** parameter is nullptr.<br>         **AUDIOSUITE_ERROR_NODE_NOT_EXIST**: The node does not exist or has been destroyed.<br>         **AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION**: The **audioNode** parameter does not point to an effect node.<br>         **AUDIOSUITE_ERROR_TIMEOUT**: The operation times out.<br>         **AUDIOSUITE_ERROR_SYSTEM**: Other system exceptions occur.|

### OH_AudioSuiteEngine_BypassEffectNode()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_BypassEffectNode(OH_AudioNode* audioNode, bool bypass)
```

**Description**

Sets the effect bypass status of the current node (supported only on effect nodes). When **bypass** is set to **true**, the effect node passes data through without any processing.<br> When **bypass** is set to **false**, the effect node performs the corresponding effect processing.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioNode](capi-ohaudiosuite-oh-audionodestruct.md)* audioNode | Audio creation node handle, which is obtained by calling [OH_AudioSuiteEngine_CreateNode](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_createnode).|
| bool bypass | Effect bypass status of the current node.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioSuite_Result](capi-native-audio-suite-base-h.md#oh_audiosuite_result) | **AUDIOSUITE_SUCCESS**: The function is executed successfully.<br>         **AUDIOSUITE_ERROR_INVALID_PARAM**: The **audioNode** parameter is nullptr.<br>         **AUDIOSUITE_ERROR_NODE_NOT_EXIST**: The node does not exist or has been destroyed.<br>         **AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION**: The **audioNode** parameter does not point to an effect node.<br>         **AUDIOSUITE_ERROR_TIMEOUT**: The operation times out.<br>         **AUDIOSUITE_ERROR_SYSTEM**: Other system exceptions occur.|

### OH_AudioSuiteEngine_SetAudioFormat()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_SetAudioFormat(OH_AudioNode* audioNode, OH_AudioFormat* audioFormat)
```

**Description**

Sets the audio format for input or output nodes after creation. This function is supported only for input and output nodes. The input node specifies the audio source format, and the output node specifies the target format.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioNode](capi-ohaudiosuite-oh-audionodestruct.md)* audioNode | Audio creation node handle, which is obtained by calling [OH_AudioSuiteEngine_CreateNode](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_createnode).|
| [OH_AudioFormat](capi-ohaudiosuite-oh-audioformat.md)* audioFormat | Pointer to the audio stream format, used to set the audio format information. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioSuite_Result](capi-native-audio-suite-base-h.md#oh_audiosuite_result) | **AUDIOSUITE_SUCCESS**: The function is executed successfully.<br>         **AUDIOSUITE_ERROR_INVALID_PARAM**: The **audioNode** parameter or **audioFormat** is nullptr.<br>         **AUDIOSUITE_ERROR_NODE_NOT_EXIST**: The node does not exist or has been destroyed.<br>         **AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION**: The **audioNode** parameter points to an effect node.<br>         **AUDIOSUITE_ERROR_UNSUPPORTED_FORMAT** (added in API version 26.0.0): The **audioFormat** parameter is set to an unsupported format.<br>         **AUDIOSUITE_ERROR_INVALID_STATE**: The pipeline is not in the stopped state.<br>         **AUDIOSUITE_ERROR_TIMEOUT**: The operation times out.<br>         **AUDIOSUITE_ERROR_SYSTEM**: Other system exceptions occur.|
<!--Del-->
### OH_AudioSuiteEngineSystem_SetAudioFormat()

```c
int32_t OH_AudioSuiteEngineSystem_SetAudioFormat(OH_AudioNode* audioNode, OH_AudioSuite_SystemNodeFormat* audioFormat)
```

**Description**

Sets the audio format of the input/output node, specifying the audio format of the audio source for the input node, or the target audio format for the output node.

**Since:** 26.0.0

**System API:** This is a system API.

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioNode](capi-ohaudiosuite-oh-audionodestruct.md)* audioNode | Handle to the audio creation node. Obtain it through [OH_AudioSuiteEngine_CreateNode](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_createnode). |
| [OH_AudioSuite_SystemNodeFormat](capi-ohaudiosuite-oh-audiosuite-systemnodeformat-sys.md)* audioFormat | Audio format. |

**Returns**

| Type | Description |
| -- | -- |
| int32_t | [AUDIOSUITE_SUCCESS](capi-native-audio-suite-base-h.md#oh_audiosuite_result): the function is executed successfully.<br>         202: a non-system application calls this system API.<br>         [AUDIOSUITE_ERROR_INVALID_PARAM](capi-native-audio-suite-base-h.md#oh_audiosuite_result): a parameter is a null pointer or has another invalid value.<br>         [AUDIOSUITE_ERROR_NODE_NOT_EXIST](capi-native-audio-suite-base-h.md#oh_audiosuite_result): the node does not exist or has been destroyed.<br>         [AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION](capi-native-audio-suite-base-h.md#oh_audiosuite_result): the node is an effect node.<br>         [AUDIOSUITE_ERROR_INVALID_STATE](capi-native-audio-suite-base-h.md#oh_audiosuite_result): the pipeline is not in the stopped state.<br>         [AUDIOSUITE_ERROR_TIMEOUT](capi-native-audio-suite-base-h.md#oh_audiosuite_result): the operation times out.<br>         [AUDIOSUITE_ERROR_SYSTEM](capi-native-audio-suite-base-h.md#oh_audiosuite_result): another system exception occurs. |
<!--DelEnd-->

### OH_AudioSuiteEngine_ConnectNodes()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_ConnectNodes(OH_AudioNode* sourceAudioNode, OH_AudioNode* destAudioNode)
```

**Description**

Connects two nodes, with the data flow going from sourceAudioNode to destAudioNode. Connecting nodes changes the pipeline topology and may cause partial data loss. It is recommended to perform this operation when the engine is in the stopped state.<br> Node connection order: input node -> effect node -> output node.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioNode](capi-ohaudiosuite-oh-audionodestruct.md)* sourceAudioNode | Audio creation node handle, which is obtained by calling [OH_AudioSuiteEngine_CreateNode](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_createnode).|
| [OH_AudioNode](capi-ohaudiosuite-oh-audionodestruct.md)* destAudioNode | Audio creation node handle, which is obtained by calling [OH_AudioSuiteEngine_CreateNode](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_createnode).|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioSuite_Result](capi-native-audio-suite-base-h.md#oh_audiosuite_result) | **AUDIOSUITE_SUCCESS**: The function is executed successfully.<br>         **AUDIOSUITE_ERROR_INVALID_PARAM**: The **sourceAudioNode** parameter or **destAudioNode** is nullptr.<br>         **AUDIOSUITE_ERROR_NODE_NOT_EXIST**: The node does not exist or has been destroyed.<br>         **AUDIOSUITE_ERROR_UNSUPPORTED_CONNECT**: Nodes do not support connection.<br>         Possible causes are as follows:<br>         1. The **sourceAudioNode** parameter points to an output node.<br>         2. The **destAudioNode** parameter is an input node.<br>         3. The **sourceAudioNode** and **destAudioNode** parameters point to the same node.<br>         4. The **sourceAudioNode** is of the audio source separation type, but **destAudioNode** is not an output node.<br>         5. The **sourceAudioNode** and **destAudioNode** parameters point to nodes within different pipelines.<br>         6. The pipeline is in the running state, but the **destAudioNode** parameter does not point to an audio mixer effect node.<br>         7. The pipeline is in the running state, the **destAudioNode** parameter points to an audio mixer effect node, but the **sourceAudioNode** parameter does not point to an input node.<br>         **AUDIOSUITE_ERROR_INVALID_STATE**: The pipeline is in an invalid state. For example, the output node cannot be found.<br>         **AUDIOSUITE_ERROR_TIMEOUT**: The operation times out.<br>         **AUDIOSUITE_ERROR_SYSTEM**: Other system exceptions occur.|

### OH_AudioSuiteEngine_DisconnectNodes()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_DisconnectNodes(OH_AudioNode* sourceAudioNode, OH_AudioNode* destAudioNode)
```

**Description**

Disconnects two nodes. This operation changes the pipeline topology and may cause data loss. It is recommended to perform this operation when the engine is in the stopped state.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioNode](capi-ohaudiosuite-oh-audionodestruct.md)* sourceAudioNode | Audio creation node handle, which is obtained by calling [OH_AudioSuiteEngine_CreateNode](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_createnode).|
| [OH_AudioNode](capi-ohaudiosuite-oh-audionodestruct.md)* destAudioNode | Audio creation node handle, which is obtained by calling [OH_AudioSuiteEngine_CreateNode](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_createnode).|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioSuite_Result](capi-native-audio-suite-base-h.md#oh_audiosuite_result) | Returns AUDIOSUITE_SUCCESS if the function is executed successfully.<br>         Returns AUDIOSUITE_ERROR_INVALID_PARAM if sourceAudioNode or destAudioNode is a null pointer.<br>         Returns AUDIOSUITE_ERROR_NODE_NOT_EXIST if the node does not exist or has been destroyed.<br>         Returns AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION if the operation is not supported.<br>         Possible causes are as follows:<br>         1. sourceAudioNode is an output node.<br>         2. destAudioNode is an input node.<br>         3. sourceAudioNode and destAudioNode are the same node.<br>         4. sourceAudioNode and destAudioNode are not in the same pipeline.<br>         5. The pipeline is in the running state, but destAudioNode is not a mix node.<br>         6. The pipeline is in the running state and destAudioNode is a mix node, but the mix node currently has only sourceAudioNode connected as its input.<br>         Returns AUDIOSUITE_ERROR_INVALID_STATE if the pipeline is in an invalid state, for example, the output node cannot be found.<br>         Returns AUDIOSUITE_ERROR_TIMEOUT if the operation times out.<br>         Returns AUDIOSUITE_ERROR_SYSTEM if another exception occurs in the system. |

### OH_AudioSuiteEngine_SetEqualizerFrequencyBandGains()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_SetEqualizerFrequencyBandGains(OH_AudioNode* audioNode, OH_EqualizerFrequencyBandGains frequencyBandGains)
```

**Description**

Sets the band gain effect for the current equalizer node.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioNode](capi-ohaudiosuite-oh-audionodestruct.md)* audioNode | Audio creation node handle, which is obtained by calling [OH_AudioSuiteEngine_CreateNode](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_createnode).|
| [OH_EqualizerFrequencyBandGains](capi-ohaudiosuite-oh-equalizerfrequencybandgains.md) frequencyBandGains | Band gains of the equalizer node.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioSuite_Result](capi-native-audio-suite-base-h.md#oh_audiosuite_result) | Result code.<br>         AUDIOSUITE_SUCCESS: The function is executed successfully.<br>         AUDIOSUITE_ERROR_NODE_NOT_EXIST: The node does not exist or has been destroyed.<br>         AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION: The audioNode node type is not an equalizer node.<br>         AUDIOSUITE_ERROR_INVALID_PARAM: The parameter is invalid.<br>         Possible causes:<br>         1. The audioNode parameter is a null pointer.<br>         2. The value of each member of the frequencyBandGains parameter is not within [-10, 10].<br>         AUDIOSUITE_ERROR_TIMEOUT: The operation timed out.<br>         AUDIOSUITE_ERROR_SYSTEM: Another system exception occurs. |

### OH_AudioSuiteEngine_GetEqualizerFrequencyBandGains()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_GetEqualizerFrequencyBandGains(OH_AudioNode* audioNode, OH_EqualizerFrequencyBandGains* frequencyBandGains)
```

**Description**

Obtains the band gain effect of the current equalizer node.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioNode](capi-ohaudiosuite-oh-audionodestruct.md)* audioNode | Audio creation node handle, which is obtained by calling [OH_AudioSuiteEngine_CreateNode](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_createnode).|
| [OH_EqualizerFrequencyBandGains](capi-ohaudiosuite-oh-equalizerfrequencybandgains.md)* frequencyBandGains | Band gains of the equalizer node.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioSuite_Result](capi-native-audio-suite-base-h.md#oh_audiosuite_result) | **AUDIOSUITE_SUCCESS**: The function is executed successfully.<br>         **AUDIOSUITE_ERROR_NODE_NOT_EXIST**: The node does not exist or has been destroyed.<br>         **AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION**: The **audioNode** parameter does not point to an equalizer node.<br>         **AUDIOSUITE_ERROR_INVALID_PARAM**: Invalid parameters. For example, **audioNode** or **frequencyBandGains** is nullptr.<br>         **AUDIOSUITE_ERROR_TIMEOUT**: The operation times out.<br>         **AUDIOSUITE_ERROR_SYSTEM**: Other system exceptions occur.|

### OH_AudioSuiteEngine_SetSoundFieldType()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_SetSoundFieldType(OH_AudioNode* audioNode, OH_SoundFieldType soundFieldType)
```

**Description**

Sets the configuration parameters for the sound field effect node.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioNode](capi-ohaudiosuite-oh-audionodestruct.md)* audioNode | Audio creation node handle, which is obtained by calling [OH_AudioSuiteEngine_CreateNode](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_createnode).|
| [OH_SoundFieldType](capi-native-audio-suite-base-h.md#oh_soundfieldtype) soundFieldType | Configuration parameters of the sound field effect node.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioSuite_Result](capi-native-audio-suite-base-h.md#oh_audiosuite_result) | **AUDIOSUITE_SUCCESS**: The function is executed successfully.<br>         **AUDIOSUITE_ERROR_NODE_NOT_EXIST**: The node does not exist or has been destroyed.<br>         **AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION**: The **audioNode** parameter does not point to a sound field effect node.<br>         **AUDIOSUITE_ERROR_INVALID_PARAM**: Invalid parameters. For example, **audioNode** is nullptr.<br>         **AUDIOSUITE_ERROR_TIMEOUT**: The operation times out.<br>         **AUDIOSUITE_ERROR_SYSTEM**: Other system exceptions occur.|

### OH_AudioSuiteEngine_GetSoundFieldType()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_GetSoundFieldType(OH_AudioNode* audioNode, OH_SoundFieldType* soundFieldType)
```

**Description**

Obtains the configuration parameters of the sound field effect node.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioNode](capi-ohaudiosuite-oh-audionodestruct.md)* audioNode | Audio creation node handle, which is obtained by calling [OH_AudioSuiteEngine_CreateNode](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_createnode).|
| [OH_SoundFieldType](capi-native-audio-suite-base-h.md#oh_soundfieldtype)* soundFieldType | Configuration parameters of the sound field effect node.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioSuite_Result](capi-native-audio-suite-base-h.md#oh_audiosuite_result) | **AUDIOSUITE_SUCCESS**: The function is executed successfully.<br>         **AUDIOSUITE_ERROR_NODE_NOT_EXIST**: The node does not exist or has been destroyed.<br>         **AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION**: The **audioNode** parameter does not point to a sound field effect node.<br>         **AUDIOSUITE_ERROR_INVALID_PARAM**: Invalid parameters. For example, **audioNode** or **soundFieldType** is nullptr.<br>         **AUDIOSUITE_ERROR_TIMEOUT**: The operation times out.<br>         **AUDIOSUITE_ERROR_SYSTEM**: Other system exceptions occur.|

### OH_AudioSuiteEngine_SetEnvironmentType()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_SetEnvironmentType(OH_AudioNode* audioNode, OH_EnvironmentType environmentType)
```

**Description**

Sets the configuration parameters for the environment effect node.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioNode](capi-ohaudiosuite-oh-audionodestruct.md)* audioNode | Audio creation node handle, which is obtained by calling [OH_AudioSuiteEngine_CreateNode](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_createnode).|
| [OH_EnvironmentType](capi-native-audio-suite-base-h.md#oh_environmenttype) environmentType | Configuration parameters of the environment effect node.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioSuite_Result](capi-native-audio-suite-base-h.md#oh_audiosuite_result) | **AUDIOSUITE_SUCCESS**: The function is executed successfully.<br>         **AUDIOSUITE_ERROR_NODE_NOT_EXIST**: The node does not exist or has been destroyed.<br>         **AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION**: The **audioNode** parameter does not point to an environment effect node.<br>         **AUDIOSUITE_ERROR_INVALID_PARAM**: Invalid parameters. For example, **audioNode** is nullptr.<br>         **AUDIOSUITE_ERROR_TIMEOUT**: The operation times out.<br>         **AUDIOSUITE_ERROR_SYSTEM**: Other system exceptions occur.|

### OH_AudioSuiteEngine_GetEnvironmentType()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_GetEnvironmentType(OH_AudioNode* audioNode, OH_EnvironmentType* environmentType)
```

**Description**

Obtains the configuration parameters of the environment effect node.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioNode](capi-ohaudiosuite-oh-audionodestruct.md)* audioNode | Audio creation node handle, which is obtained by calling [OH_AudioSuiteEngine_CreateNode](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_createnode).|
| [OH_EnvironmentType](capi-native-audio-suite-base-h.md#oh_environmenttype)* environmentType | Configuration parameters of the environment effect node.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioSuite_Result](capi-native-audio-suite-base-h.md#oh_audiosuite_result) | **AUDIOSUITE_SUCCESS**: The function is executed successfully.<br>         **AUDIOSUITE_ERROR_NODE_NOT_EXIST**: The node does not exist or has been destroyed.<br>         **AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION**: The **audioNode** parameter does not point to an environment effect node.<br>         **AUDIOSUITE_ERROR_INVALID_PARAM**: Invalid parameters. For example, **audioNode** or **environmentType** is nullptr.<br>         **AUDIOSUITE_ERROR_TIMEOUT**: The operation times out.<br>         **AUDIOSUITE_ERROR_SYSTEM**: Other system exceptions occur.|

### OH_AudioSuiteEngine_SetVoiceBeautifierType()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_SetVoiceBeautifierType(OH_AudioNode* audioNode, OH_VoiceBeautifierType voiceBeautifierType)
```

**Description**

Sets the configuration parameters for the voice beautifier effect node.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioNode](capi-ohaudiosuite-oh-audionodestruct.md)* audioNode | Audio creation node handle, which is obtained by calling [OH_AudioSuiteEngine_CreateNode](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_createnode).|
| [OH_VoiceBeautifierType](capi-native-audio-suite-base-h.md#oh_voicebeautifiertype) voiceBeautifierType | Configuration parameters of the voice beautifier effect node.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioSuite_Result](capi-native-audio-suite-base-h.md#oh_audiosuite_result) | **AUDIOSUITE_SUCCESS**: The function is executed successfully.<br>         **AUDIOSUITE_ERROR_NODE_NOT_EXIST**: The node does not exist or has been destroyed.<br>         **AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION**: The **audioNode** parameter does not point to a voice beautifier effect node.<br>         **AUDIOSUITE_ERROR_INVALID_PARAM**: Invalid parameters. For example, **audioNode** is nullptr.<br>         **AUDIOSUITE_ERROR_TIMEOUT**: The operation times out.<br>         **AUDIOSUITE_ERROR_SYSTEM**: Other system exceptions occur.|

### OH_AudioSuiteEngine_GetVoiceBeautifierType()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_GetVoiceBeautifierType(OH_AudioNode* audioNode, OH_VoiceBeautifierType* voiceBeautifierType)
```

**Description**

Obtains the configuration parameters of the voice beautifier effect node.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioNode](capi-ohaudiosuite-oh-audionodestruct.md)* audioNode | Audio creation node handle, which is obtained by calling [OH_AudioSuiteEngine_CreateNode](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_createnode).|
| [OH_VoiceBeautifierType](capi-native-audio-suite-base-h.md#oh_voicebeautifiertype)* voiceBeautifierType | Configuration parameters of the voice beautifier effect node.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioSuite_Result](capi-native-audio-suite-base-h.md#oh_audiosuite_result) | **AUDIOSUITE_SUCCESS**: The function is executed successfully.<br>         **AUDIOSUITE_ERROR_NODE_NOT_EXIST**: The node does not exist or has been destroyed.<br>         **AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION**: The **audioNode** parameter does not point to a voice beautifier effect node.<br>         **AUDIOSUITE_ERROR_INVALID_PARAM**: Invalid parameters.<br>         For example, **audioNode** or **voiceBeautifierType** is nullptr.<br>         **AUDIOSUITE_ERROR_TIMEOUT**: The operation times out.<br>         **AUDIOSUITE_ERROR_SYSTEM**: Other system exceptions occur.|

### OH_AudioSuiteEngine_IsNodeTypeSupported()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_IsNodeTypeSupported(OH_AudioNode_Type nodeType, bool* isSupported)
```

**Description**

Checks whether the system supports the creation of a specified node type to avoid node creation failure. This function is called independently of engine and pipeline states and is only related to the system, without the need to create an engine or pipeline.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioNode_Type](capi-native-audio-suite-base-h.md#oh_audionode_type) nodeType | Type of the node.|
| bool* isSupported | Pointer to the variable that specifies the support for node creation. **true** if supported, **false** otherwise.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioSuite_Result](capi-native-audio-suite-base-h.md#oh_audiosuite_result) | **AUDIOSUITE_SUCCESS**: The function is executed successfully.<br>         **AUDIOSUITE_ERROR_INVALID_PARAM**: Invalid input parameter.<br>         For example, the input parameter **nodeType** is not within the range of **OH_AudioNode_Type**, or **isSupported** is nullptr.<br>         **AUDIOSUITE_ERROR_SYSTEM**: Other system exceptions occur.|

### OH_AudioSuiteEngine_SetSpaceRenderPositionParams()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_SetSpaceRenderPositionParams(OH_AudioNode* audioNode, OH_AudioSuite_SpaceRenderPositionParams position)
```

**Description**

Sets the configuration parameters for the fixed-position mode of the spatial rendering effect node.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioNode](capi-ohaudiosuite-oh-audionodestruct.md)* audioNode | Audio creation node handle, which is obtained by calling [OH_AudioSuiteEngine_CreateNode](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_createnode).|
| [OH_AudioSuite_SpaceRenderPositionParams](capi-ohaudiosuite-oh-audiosuite-spacerenderpositionparams.md) position | Configuration parameters for the fixed-position mode of the spatial rendering effect node. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioSuite_Result](capi-native-audio-suite-base-h.md#oh_audiosuite_result) | **AUDIOSUITE_SUCCESS**: The function is executed successfully.<br>         **AUDIOSUITE_ERROR_NODE_NOT_EXIST**: The node does not exist or has been destroyed.<br>         **AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION**: The **audioNode** node type is not a spatial rendering effect node.<br>         **AUDIOSUITE_ERROR_INVALID_PARAM**: Invalid parameters. For example, **audioNode** is nullptr.<br>         **AUDIOSUITE_ERROR_TIMEOUT**: The operation times out.<br>         **AUDIOSUITE_ERROR_SYSTEM**: Other system exceptions occur.|

### OH_AudioSuiteEngine_GetSpaceRenderPositionParams()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_GetSpaceRenderPositionParams(OH_AudioNode* audioNode, OH_AudioSuite_SpaceRenderPositionParams* position)
```

**Description**

Obtains the configuration parameters for the fixed-position mode of the spatial rendering effect node.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioNode](capi-ohaudiosuite-oh-audionodestruct.md)* audioNode | Audio creation node handle, which is obtained by calling [OH_AudioSuiteEngine_CreateNode](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_createnode).|
| [OH_AudioSuite_SpaceRenderPositionParams](capi-ohaudiosuite-oh-audiosuite-spacerenderpositionparams.md)* position | Configuration parameters for the fixed-position mode of the spatial rendering effect node.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioSuite_Result](capi-native-audio-suite-base-h.md#oh_audiosuite_result) | **AUDIOSUITE_SUCCESS**: The function is executed successfully.<br>         **AUDIOSUITE_ERROR_NODE_NOT_EXIST**: The node does not exist or has been destroyed.<br>         **AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION**: The **audioNode** node type is not a spatial rendering effect node.<br>         **AUDIOSUITE_ERROR_INVALID_PARAM**: Invalid parameters. For example, **audioNode** is nullptr.<br>         **AUDIOSUITE_ERROR_TIMEOUT**: The operation times out.<br>         **AUDIOSUITE_ERROR_SYSTEM**: Other system exceptions occur.|

### OH_AudioSuiteEngine_SetSpaceRenderRotationParams()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_SetSpaceRenderRotationParams(OH_AudioNode* audioNode, OH_AudioSuite_SpaceRenderRotationParams rotation)
```

**Description**

Sets the configuration parameters for the rotation mode of the spatial rendering effect node.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioNode](capi-ohaudiosuite-oh-audionodestruct.md)* audioNode | Audio creation node handle, which is obtained by calling [OH_AudioSuiteEngine_CreateNode](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_createnode).|
| [OH_AudioSuite_SpaceRenderRotationParams](capi-ohaudiosuite-oh-audiosuite-spacerenderrotationparams.md) rotation | Configuration parameters for the rotation mode of the spatial rendering effect node.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioSuite_Result](capi-native-audio-suite-base-h.md#oh_audiosuite_result) | **AUDIOSUITE_SUCCESS**: The function is executed successfully.<br>         **AUDIOSUITE_ERROR_NODE_NOT_EXIST**: The node does not exist or has been destroyed.<br>         **AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION**: The **audioNode** node type is not a spatial rendering effect node.<br>         **AUDIOSUITE_ERROR_INVALID_PARAM**: Invalid parameters. For example, **audioNode** is nullptr.<br>         **AUDIOSUITE_ERROR_TIMEOUT**: The operation times out.<br>         **AUDIOSUITE_ERROR_SYSTEM**: Other system exceptions occur.|

### OH_AudioSuiteEngine_GetSpaceRenderRotationParams()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_GetSpaceRenderRotationParams(OH_AudioNode* audioNode, OH_AudioSuite_SpaceRenderRotationParams* rotation)
```

**Description**

Obtains the configuration parameters for the rotation mode of the spatial rendering effect node.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioNode](capi-ohaudiosuite-oh-audionodestruct.md)* audioNode | Audio creation node handle, which is obtained by calling [OH_AudioSuiteEngine_CreateNode](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_createnode).|
| [OH_AudioSuite_SpaceRenderRotationParams](capi-ohaudiosuite-oh-audiosuite-spacerenderrotationparams.md)* rotation | Configuration parameters for the rotation mode of the spatial rendering effect node.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioSuite_Result](capi-native-audio-suite-base-h.md#oh_audiosuite_result) | **AUDIOSUITE_SUCCESS**: The function is executed successfully.<br>         **AUDIOSUITE_ERROR_NODE_NOT_EXIST**: The node does not exist or has been destroyed.<br>         **AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION**: The **audioNode** node type is not a spatial rendering effect node.<br>         **AUDIOSUITE_ERROR_INVALID_PARAM**: Invalid parameters. For example, **audioNode** is nullptr.<br>         **AUDIOSUITE_ERROR_TIMEOUT**: The operation times out.<br>         **AUDIOSUITE_ERROR_SYSTEM**: Other system exceptions occur.|

### OH_AudioSuiteEngine_SetSpaceRenderExtensionParams()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_SetSpaceRenderExtensionParams(OH_AudioNode* audioNode, OH_AudioSuite_SpaceRenderExtensionParams extension)
```

**Description**

Sets the configuration parameters for the extension mode of the spatial rendering effect node.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioNode](capi-ohaudiosuite-oh-audionodestruct.md)* audioNode | Audio creation node handle, which is obtained by calling [OH_AudioSuiteEngine_CreateNode](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_createnode).|
| [OH_AudioSuite_SpaceRenderExtensionParams](capi-ohaudiosuite-oh-audiosuite-spacerenderextensionparams.md) extension | Configuration parameters for the extension mode of the spatial rendering effect node.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioSuite_Result](capi-native-audio-suite-base-h.md#oh_audiosuite_result) | **AUDIOSUITE_SUCCESS**: The function is executed successfully.<br>         **AUDIOSUITE_ERROR_NODE_NOT_EXIST**: The node does not exist or has been destroyed.<br>         **AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION**: The **audioNode** node type is not a spatial rendering effect node.<br>         **AUDIOSUITE_ERROR_INVALID_PARAM**: Invalid parameters. For example, **audioNode** is nullptr.<br>         **AUDIOSUITE_ERROR_TIMEOUT**: The operation times out.<br>         **AUDIOSUITE_ERROR_SYSTEM**: Other system exceptions occur.|

### OH_AudioSuiteEngine_GetSpaceRenderExtensionParams()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_GetSpaceRenderExtensionParams(OH_AudioNode* audioNode, OH_AudioSuite_SpaceRenderExtensionParams* extension)
```

**Description**

Obtains the configuration parameters for the extension mode of the spatial rendering effect node.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioNode](capi-ohaudiosuite-oh-audionodestruct.md)* audioNode | Audio creation node handle, which is obtained by calling [OH_AudioSuiteEngine_CreateNode](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_createnode).|
| [OH_AudioSuite_SpaceRenderExtensionParams](capi-ohaudiosuite-oh-audiosuite-spacerenderextensionparams.md)* extension | Configuration parameters for the extension mode of the spatial rendering effect node.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioSuite_Result](capi-native-audio-suite-base-h.md#oh_audiosuite_result) | **AUDIOSUITE_SUCCESS**: The function is executed successfully.<br>         **AUDIOSUITE_ERROR_NODE_NOT_EXIST**: The node does not exist or has been destroyed.<br>         **AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION**: The **audioNode** node type is not a spatial rendering effect node.<br>         **AUDIOSUITE_ERROR_INVALID_PARAM**: Invalid parameters. For example, **audioNode** is nullptr.<br>         **AUDIOSUITE_ERROR_TIMEOUT**: The operation times out.<br>         **AUDIOSUITE_ERROR_SYSTEM**: Other system exceptions occur.|

### OH_AudioSuiteEngine_SetTempoAndPitch()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_SetTempoAndPitch(OH_AudioNode* audioNode, float speed, float pitch)
```

**Description**

Sets the configuration parameters of the tempo and pitch shifting effect node.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioNode](capi-ohaudiosuite-oh-audionodestruct.md)* audioNode | Audio creation node handle, which is obtained by calling [OH_AudioSuiteEngine_CreateNode](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_createnode).|
| float speed | Speed change parameter. The value range is [0.5, 10.0].|
| float pitch | Pitch change parameter. The value range is [0.1, 5.0].|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioSuite_Result](capi-native-audio-suite-base-h.md#oh_audiosuite_result) | **AUDIOSUITE_SUCCESS**: The function is executed successfully.<br>         **AUDIOSUITE_ERROR_NODE_NOT_EXIST**: The node does not exist or has been destroyed.<br>         **AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION**: The **audioNode** node type is not a tempo and pitch shifting effect node.<br>         **AUDIOSUITE_ERROR_INVALID_PARAM**: Invalid parameters. For example, **audioNode** is nullptr.<br>         **AUDIOSUITE_ERROR_TIMEOUT**: The operation times out.<br>         **AUDIOSUITE_ERROR_SYSTEM**: Other system exceptions occur.|

### OH_AudioSuiteEngine_GetTempoAndPitch()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_GetTempoAndPitch(OH_AudioNode* audioNode, float* speed, float* pitch)
```

**Description**

Obtains the configuration parameters of the tempo and pitch shifting effect node.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioNode](capi-ohaudiosuite-oh-audionodestruct.md)* audioNode | Audio creation node handle, which is obtained by calling [OH_AudioSuiteEngine_CreateNode](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_createnode).|
| float* speed | Speed change parameter. The value range is [0.5, 10.0].|
| float* pitch | Pitch change parameter. The value range is [0.1, 5.0].|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioSuite_Result](capi-native-audio-suite-base-h.md#oh_audiosuite_result) | **AUDIOSUITE_SUCCESS**: The function is executed successfully.<br>         **AUDIOSUITE_ERROR_NODE_NOT_EXIST**: The node does not exist or has been destroyed.<br>         **AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION**: The **audioNode** node type is not a tempo and pitch shifting effect node.<br>         **AUDIOSUITE_ERROR_INVALID_PARAM**: Invalid parameters. For example, **audioNode** is nullptr.<br>         **AUDIOSUITE_ERROR_TIMEOUT**: The operation times out.<br>         **AUDIOSUITE_ERROR_SYSTEM**: Other system exceptions occur.|

### OH_AudioSuiteEngine_SetPureVoiceChangeOption()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_SetPureVoiceChangeOption(OH_AudioNode* audioNode, OH_AudioSuite_PureVoiceChangeOption option)
```

**Description**

Sets the configuration parameters of the pure voice change node.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioNode](capi-ohaudiosuite-oh-audionodestruct.md)* audioNode | Audio creation node handle, which is obtained by calling [OH_AudioSuiteEngine_CreateNode](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_createnode).|
| [OH_AudioSuite_PureVoiceChangeOption](capi-ohaudiosuite-oh-audiosuite-purevoicechangeoption.md) option | Configuration parameters of the pure voice change effect node.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioSuite_Result](capi-native-audio-suite-base-h.md#oh_audiosuite_result) | **AUDIOSUITE_SUCCESS**: The function is executed successfully.<br>         **AUDIOSUITE_ERROR_NODE_NOT_EXIST**: The node does not exist or has been destroyed.<br>         **AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION**: The **audioNode** node type is not a pure voice change effect node.<br>         **AUDIOSUITE_ERROR_INVALID_PARAM**: Invalid parameters. For example, **audioNode** is nullptr.<br>         **AUDIOSUITE_ERROR_TIMEOUT**: The operation times out.<br>         **AUDIOSUITE_ERROR_SYSTEM**: Other system exceptions occur.|

### OH_AudioSuiteEngine_GetPureVoiceChangeOption()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_GetPureVoiceChangeOption(OH_AudioNode* audioNode, OH_AudioSuite_PureVoiceChangeOption* option)
```

**Description**

Obtains the configuration parameters of the pure voice change node.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioNode](capi-ohaudiosuite-oh-audionodestruct.md)* audioNode | Audio creation node handle, which is obtained by calling [OH_AudioSuiteEngine_CreateNode](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_createnode).|
| [OH_AudioSuite_PureVoiceChangeOption](capi-ohaudiosuite-oh-audiosuite-purevoicechangeoption.md)* option | Configuration parameters of the pure voice change effect node.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioSuite_Result](capi-native-audio-suite-base-h.md#oh_audiosuite_result) | **AUDIOSUITE_SUCCESS**: The function is executed successfully.<br>         **AUDIOSUITE_ERROR_NODE_NOT_EXIST**: The node does not exist or has been destroyed.<br>         **AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION**: The **audioNode** node type is not a pure voice change effect node.<br>         **AUDIOSUITE_ERROR_INVALID_PARAM**: Invalid parameters. For example, **audioNode** is nullptr.<br>         **AUDIOSUITE_ERROR_TIMEOUT**: The operation times out.<br>         **AUDIOSUITE_ERROR_SYSTEM**: Other system exceptions occur.|

### OH_AudioSuiteEngine_SetGeneralVoiceChangeType()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_SetGeneralVoiceChangeType(OH_AudioNode* audioNode, OH_AudioSuite_GeneralVoiceChangeType type)
```

**Description**

Sets the configuration parameters of the general voice change node.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioNode](capi-ohaudiosuite-oh-audionodestruct.md)* audioNode | Audio creation node handle, which is obtained by calling [OH_AudioSuiteEngine_CreateNode](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_createnode).|
| [OH_AudioSuite_GeneralVoiceChangeType](capi-native-audio-suite-base-h.md#oh_audiosuite_generalvoicechangetype) type | Configuration parameters of the general voice change node.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioSuite_Result](capi-native-audio-suite-base-h.md#oh_audiosuite_result) | **AUDIOSUITE_SUCCESS**: The function is executed successfully.<br>         **AUDIOSUITE_ERROR_NODE_NOT_EXIST**: The node does not exist or has been destroyed.<br>         **AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION**: The **audioNode** node type is not a general voice change effect node.<br>         **AUDIOSUITE_ERROR_INVALID_PARAM**: Invalid parameters. For example, **audioNode** is nullptr.<br>         **AUDIOSUITE_ERROR_TIMEOUT**: The operation times out.<br>         **AUDIOSUITE_ERROR_SYSTEM**: Other system exceptions occur.|

### OH_AudioSuiteEngine_GetGeneralVoiceChangeType()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_GetGeneralVoiceChangeType(OH_AudioNode* audioNode, OH_AudioSuite_GeneralVoiceChangeType* type)
```

**Description**

Obtains the configuration parameters of the general voice change node.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioNode](capi-ohaudiosuite-oh-audionodestruct.md)* audioNode | Audio creation node handle, which is obtained by calling [OH_AudioSuiteEngine_CreateNode](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_createnode).|
| [OH_AudioSuite_GeneralVoiceChangeType](capi-native-audio-suite-base-h.md#oh_audiosuite_generalvoicechangetype)* type | Configuration parameters of the general voice change node.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioSuite_Result](capi-native-audio-suite-base-h.md#oh_audiosuite_result) | **AUDIOSUITE_SUCCESS**: The function is executed successfully.<br>         **AUDIOSUITE_ERROR_NODE_NOT_EXIST**: The node does not exist or has been destroyed.<br>         **AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION**: The **audioNode** node type is not a general voice change effect node.<br>         **AUDIOSUITE_ERROR_INVALID_PARAM**: Invalid parameters. For example, **audioNode** is nullptr.<br>         **AUDIOSUITE_ERROR_TIMEOUT**: The operation times out.<br>         **AUDIOSUITE_ERROR_SYSTEM**: Other system exceptions occur.|

### OH_AudioSuite_PrintInfo()

```c
OH_AudioSuite_Result OH_AudioSuite_PrintInfo(OH_AudioSuiteEngine* audioSuiteEngine, OH_AudioSuitePipeline* audioSuitePipeline, int fd)
```

**Description**

Prints the AudioSuite runtime snapshot.

**Since:** 26.0.0

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioSuiteEngine](capi-ohaudiosuite-oh-audiosuiteenginestruct.md)* audioSuiteEngine | Pointer to the **AudioSuiteEngine** for which the runtime snapshot is to be displayed.|
| [OH_AudioSuitePipeline](capi-ohaudiosuite-oh-audiosuitepipelinestruct.md)* audioSuitePipeline | Pointer to the AudioSuitePipeline whose runtime snapshot is to be displayed.<br>                           If audioSuitePipeline is null, outputs all pipelines (all pipelines/nodes under the engine). Otherwise, outputs only the snapshot of this pipeline and its nodes. |
| int fd | File descriptor, which indicates the location where the snapshot information is stored.<br>           If **fd** is less than 0, the snapshot information is stored in the log. Otherwise, the snapshot is stored in append mode in the file pointed to by the **fd** handle.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioSuite_Result](capi-native-audio-suite-base-h.md#oh_audiosuite_result) | **AUDIOSUITE_SUCCESS**: The function is executed successfully.<br>         **AUDIOSUITE_ERROR_INVALID_PARAM**: A parameter is nullptr or has an invalid value.<br>         **AUDIOSUITE_ERROR_SYSTEM**: Other system exceptions occur.|

<!--Del-->
### OH_AudioSuiteEngineSystem_SetNodeParam()

```c
int32_t OH_AudioSuiteEngineSystem_SetNodeParam(OH_AudioNode* audioNode, uint8_t* param, uint32_t paramSize)
```

**Description**

Sets the parameters of the system node.

**Since:** 26.0.0

**System API:** This is a system API.

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioNode](capi-ohaudiosuite-oh-audionodestruct.md)* audioNode | Handle to the audio creation node. Obtain it through [OH_AudioSuiteEngine_CreateNode](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_createnode). |
| uint8_t* param | Parameter buffer. |
| uint32_t paramSize | Size of the parameter buffer. |

**Returns**

| Type | Description |
| -- | -- |
| int32_t | Result code.<br>         [AUDIOSUITE_SUCCESS](capi-native-audio-suite-base-h.md#oh_audiosuite_result): success.<br>         202: a non-system application calls this system API.<br>         [AUDIOSUITE_ERROR_NODE_NOT_EXIST](capi-native-audio-suite-base-h.md#oh_audiosuite_result): the node does not exist or has been destroyed.<br>         [AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION](capi-native-audio-suite-base-h.md#oh_audiosuite_result): the node is not a system-type node.<br>         [AUDIOSUITE_ERROR_INVALID_PARAM](capi-native-audio-suite-base-h.md#oh_audiosuite_result): the parameter is a null pointer or has another invalid value.<br>         [AUDIOSUITE_ERROR_TIMEOUT](capi-native-audio-suite-base-h.md#oh_audiosuite_result): the operation times out.<br>         [AUDIOSUITE_ERROR_SYSTEM](capi-native-audio-suite-base-h.md#oh_audiosuite_result): another system exception occurs. |

### OH_AudioSuiteEngineSystem_GetNodeParam()

```c
int32_t OH_AudioSuiteEngineSystem_GetNodeParam(OH_AudioNode* audioNode, uint8_t* param, uint32_t paramSize)
```

**Description**

Obtains the parameters of the system node.

**Since:** 26.0.0

**System API:** This is a system API.

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioNode](capi-ohaudiosuite-oh-audionodestruct.md)* audioNode | Handle to the audio creation node. Obtain it through [OH_AudioSuiteEngine_CreateNode](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_createnode). |
| uint8_t* param | Parameter buffer. |
| uint32_t paramSize | Size of the parameter buffer. |

**Returns**

| Type | Description |
| -- | -- |
| int32_t | Result code.<br>         [AUDIOSUITE_SUCCESS](capi-native-audio-suite-base-h.md#oh_audiosuite_result): the function is executed successfully.<br>         202: a non-system application calls this system API.<br>         [AUDIOSUITE_ERROR_NODE_NOT_EXIST](capi-native-audio-suite-base-h.md#oh_audiosuite_result): the audio node does not exist or has been destroyed.<br>         [AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION](capi-native-audio-suite-base-h.md#oh_audiosuite_result): the node is not a system-type node.<br>         [AUDIOSUITE_ERROR_INVALID_PARAM](capi-native-audio-suite-base-h.md#oh_audiosuite_result): the parameter is a null pointer or has another invalid value.<br>         [AUDIOSUITE_ERROR_TIMEOUT](capi-native-audio-suite-base-h.md#oh_audiosuite_result): the operation times out.<br>         [AUDIOSUITE_ERROR_SYSTEM](capi-native-audio-suite-base-h.md#oh_audiosuite_result): another system exception occurs. |

### OH_AudioSuiteEngineSystem_GetNodeInOutSize()

```c
int32_t OH_AudioSuiteEngineSystem_GetNodeInOutSize(OH_AudioNode* audioNode, uint32_t* inSize, uint32_t* outSize)
```

**Description**

Obtains the input and output frame sizes of the system node.

**Since:** 26.0.0

**System API:** This is a system API.

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioNode](capi-ohaudiosuite-oh-audionodestruct.md)* audioNode | Handle to the audio creation node. Obtain it through [OH_AudioSuiteEngine_CreateNode](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_createnode). |
| uint32_t* inSize | Input frame size, in bytes. |
| uint32_t* outSize | Output frame size, in bytes. |

**Returns**

| Type | Description |
| -- | -- |
| int32_t | Result code.<br>         [AUDIOSUITE_SUCCESS](capi-native-audio-suite-base-h.md#oh_audiosuite_result): the function is executed successfully.<br>         202: a non-system application calls this system API.<br>         [AUDIOSUITE_ERROR_NODE_NOT_EXIST](capi-native-audio-suite-base-h.md#oh_audiosuite_result): the audio node does not exist or has been destroyed.<br>         [AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION](capi-native-audio-suite-base-h.md#oh_audiosuite_result): the node is not a system-type node.<br>         [AUDIOSUITE_ERROR_INVALID_PARAM](capi-native-audio-suite-base-h.md#oh_audiosuite_result): the parameter is a null pointer or has another invalid value.<br>         [AUDIOSUITE_ERROR_TIMEOUT](capi-native-audio-suite-base-h.md#oh_audiosuite_result): the operation times out.<br>         [AUDIOSUITE_ERROR_SYSTEM](capi-native-audio-suite-base-h.md#oh_audiosuite_result): another system exception occurs. |
<!--DelEnd-->

