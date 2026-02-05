# native_audio_suite_engine.h
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @caixuejiang; @hao-liangfei; @zhanganxiang-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

## Overview

The file declares the functions related to audio creation, including the engine, pipeline, and node.

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
| [OH_AudioSuite_Result OH_AudioSuiteEngine_CreatePipeline(OH_AudioSuiteEngine* audioSuiteEngine, OH_AudioSuitePipeline** audioSuitePipeline, OH_AudioSuite_PipelineWorkMode workMode)](#oh_audiosuiteengine_createpipeline) | - | Creates a pipeline within the current audio creation engine. A pipeline is the execution unit within the engine responsible for audio creation, and multiple pipelines can be created within a single engine.<br> Up to 10 pipelines can be created, with a maximum of one real-time rendering pipeline.<br> Each pipeline must have at least one input node and exactly one output node.<br> When the pipeline operations in [OH_AudioSuite_PipelineWorkMode](capi-native-audio-suite-base-h.md#oh_audiosuite_pipelineworkmode).AUDIOSUITE_PIPELINE_EDIT_MODE mode, all effect nodes are supported.<br> When the pipeline operations in [OH_AudioSuite_PipelineWorkMode](capi-native-audio-suite-base-h.md#oh_audiosuite_pipelineworkmode).AUDIOSUITE_PIPELINE_REALTIME_MODE mode, only the [OH_AudioNode_Type](capi-native-audio-suite-base-h.md#oh_audionode_type).EFFECT_NODE_TYPE_EQUALIZER effect node is supported.|
| [OH_AudioSuite_Result OH_AudioSuiteEngine_DestroyPipeline(OH_AudioSuitePipeline* audioSuitePipeline)](#oh_audiosuiteengine_destroypipeline) | - | Destroys the handle to an audio creation pipeline.|
| [OH_AudioSuite_Result OH_AudioSuiteEngine_StartPipeline(OH_AudioSuitePipeline* audioSuitePipeline)](#oh_audiosuiteengine_startpipeline) | - | Starts the pipeline. The pipeline will enter the [OH_AudioSuite_PipelineState](capi-native-audio-suite-base-h.md#oh_audiosuite_pipelinestate).AUDIOSUITE_PIPELINE_RUNNING state.|
| [OH_AudioSuite_Result OH_AudioSuiteEngine_StopPipeline(OH_AudioSuitePipeline* audioSuitePipeline)](#oh_audiosuiteengine_stoppipeline) | - | Stops the pipeline. The pipeline will enter the [OH_AudioSuite_PipelineState](capi-native-audio-suite-base-h.md#oh_audiosuite_pipelinestate).AUDIOSUITE_PIPELINE_STOPPED state. This function does not change the connections between nodes within the pipeline. Once the pipeline is stopped, [OH_AudioSuiteEngine_RenderFrame](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_renderframe) can no longer perform audio processing.|
| [OH_AudioSuite_Result OH_AudioSuiteEngine_GetPipelineState(OH_AudioSuitePipeline* audioSuitePipeline, OH_AudioSuite_PipelineState* pipelineState)](#oh_audiosuiteengine_getpipelinestate) | - | Retrieves the state of the pipeline.|
| [OH_AudioSuite_Result OH_AudioSuiteEngine_RenderFrame(OH_AudioSuitePipeline* audioSuitePipeline, void* audioData, int32_t requestFrameSize, int32_t* responseSize, bool* finishedFlag)](#oh_audiosuiteengine_renderframe) | - | Obtains the processed audio data from the pipeline (for single-output effect nodes).|
| [OH_AudioSuite_Result OH_AudioSuiteEngine_MultiRenderFrame(OH_AudioSuitePipeline* audioSuitePipeline, OH_AudioDataArray* audioDataArray, int32_t* responseSize, bool* finishedFlag)](#oh_audiosuiteengine_multirenderframe) | - | Renders the pipeline and obtains the processed audio data. For pipelines with multiple output effect nodes (for example, those containing audio separation nodes), the size of **audioDataArray** must correspond one-to-one with the number of outputs from the effect nodes. (For example, audio separation nodes require two outputs: the first for vocals and the second for background sound.)|
| [OH_AudioSuite_Result OH_AudioSuiteNodeBuilder_Create(OH_AudioNodeBuilder** builder)](#oh_audiosuitenodebuilder_create) | - | Obtains an audio creation node builder, which is used to configure and create audio nodes. The builder can be reused. However, if the properties of the new node differ from those of the previous node, you must use [OH_AudioSuiteNodeBuilder_Reset](#oh_audiosuitenodebuilder_reset) to reset the builder.|
| [OH_AudioSuite_Result OH_AudioSuiteNodeBuilder_Destroy(OH_AudioNodeBuilder* builder)](#oh_audiosuitenodebuilder_destroy) | - | Destroys an audio creation node builder. This function must be called after the builder is no longer required.|
| [OH_AudioSuite_Result OH_AudioSuiteNodeBuilder_Reset(OH_AudioNodeBuilder* builder)](#oh_audiosuitenodebuilder_reset) | - | Resets an audio creation node builder, clearing all previously set parameters. If you want to reuse the builder to create a node with different properties, this function must be called to clear all properties (for example, node type).|
| [OH_AudioSuite_Result OH_AudioSuiteNodeBuilder_SetNodeType(OH_AudioNodeBuilder* builder, OH_AudioNode_Type type)](#oh_audiosuitenodebuilder_setnodetype) | - | Sets the type of node to be constructed by the current node builder. During node creation, other parameters are verified based on the node type. This property must be set for all node types.|
| [OH_AudioSuite_Result OH_AudioSuiteNodeBuilder_SetFormat(OH_AudioNodeBuilder* builder, OH_AudioFormat audioFormat)](#oh_audiosuitenodebuilder_setformat) | - | Configures the audio format for input or output nodes. This function can only be used before node creation. For input nodes, it allows the application to specify the audio format for writing data.<br> For output nodes, it allows the application to specify the desired audio format for obtaining data.<br> This function is not supported for other node types.|
| [typedef int32_t (\*OH_InputNode_RequestDataCallback)(OH_AudioNode* audioNode, void* userData, void* audioData, int32_t audioDataSize, bool* finished)](#oh_inputnode_requestdatacallback) | OH_InputNode_RequestDataCallback | Sets a callback function for the input node to request data.|
| [OH_AudioSuite_Result OH_AudioSuiteNodeBuilder_SetRequestDataCallback(OH_AudioNodeBuilder* builder, OH_InputNode_RequestDataCallback callback, void* userData)](#oh_audiosuitenodebuilder_setrequestdatacallback) | - | Sets a callback function for writing audio data for the current input node builder.|
| [OH_AudioSuite_Result OH_AudioSuiteEngine_CreateNode(OH_AudioSuitePipeline* audioSuitePipeline, OH_AudioNodeBuilder* builder, OH_AudioNode** audioNode)](#oh_audiosuiteengine_createnode) | - | Creates an audio node within the audio pipeline based on the audio creation builder. When this function is executed, the system checks the validity of the parameters based on the node type set in the builder.<br> Applications can determine the cause of errors based on the return value.|
| [OH_AudioSuite_Result OH_AudioSuiteEngine_DestroyNode(OH_AudioNode* audioNode)](#oh_audiosuiteengine_destroynode) | - | Destroys an audio creation node. To destroy a node, the pipeline must be in the [OH_AudioSuite_PipelineState](capi-native-audio-suite-base-h.md#oh_audiosuite_pipelinestate).AUDIOSUITE_PIPELINE_STOPPED state.|
| [OH_AudioSuite_Result OH_AudioSuiteEngine_GetNodeBypassStatus(OH_AudioNode* audioNode, bool* bypassStatus)](#oh_audiosuiteengine_getnodebypassstatus) | - | Obtains the effect bypass status of the current node. This function can be used only on effect nodes.<br> If it is called on an input or output node, the AUDIOSUITE_ERROR_INVALID_PARAM error code is returned.|
| [OH_AudioSuite_Result OH_AudioSuiteEngine_BypassEffectNode(OH_AudioNode* audioNode, bool bypass)](#oh_audiosuiteengine_bypasseffectnode) | - | Sets the effect bypass status of the current node (supported only on effect nodes). When **bypass** is set to **true**, the effect node passes data through without any processing. When **bypass** is set to **false**, the effect node performs the corresponding effect processing.|
| [OH_AudioSuite_Result OH_AudioSuiteEngine_SetAudioFormat(OH_AudioNode* audioNode, OH_AudioFormat *audioFormat)](#oh_audiosuiteengine_setaudioformat) | - | Sets the audio format for input or output nodes after creation. This function is supported only for input and output nodes. The input node specifies the audio source format, and the output node specifies the target format.|
| [OH_AudioSuite_Result OH_AudioSuiteEngine_ConnectNodes(OH_AudioNode* sourceAudioNode, OH_AudioNode* destAudioNode)](#oh_audiosuiteengine_connectnodes) | - | Connects two nodes, with data flowing from **sourceAudioNode** to **destAudioNode**. Connecting nodes will change the pipeline topology and may cause data loss. You are advised to perform this operation when the engine is stopped.<br> The connection order of nodes in a pipeline is as follows: input node -> effect node -> output node.|
| [OH_AudioSuite_Result OH_AudioSuiteEngine_DisconnectNodes(OH_AudioNode* sourceAudioNode, OH_AudioNode* destAudioNode)](#oh_audiosuiteengine_disconnectnodes) | - | Disconnect two nodes. This operation will change the pipeline topology and may cause data loss. You are advised to perform this operation when the engine is stopped.|
| [OH_AudioSuite_Result OH_AudioSuiteEngine_SetEqualizerFrequencyBandGains(OH_AudioNode* audioNode, OH_EqualizerFrequencyBandGains frequencyBandGains)](#oh_audiosuiteengine_setequalizerfrequencybandgains) | - | Sets the band gain effect for the current equalizer node.|
| [OH_AudioSuite_Result OH_AudioSuiteEngine_GetEqualizerFrequencyBandGains(OH_AudioNode* audioNode, OH_EqualizerFrequencyBandGains* frequencyBandGains)](#oh_audiosuiteengine_getequalizerfrequencybandgains) | - | Obtains the band gain effect of the current equalizer node.|
| [OH_AudioSuite_Result OH_AudioSuiteEngine_SetSoundFieldType(OH_AudioNode* audioNode, OH_SoundFieldType soundFieldType)](#oh_audiosuiteengine_setsoundfieldtype) | - | Sets the configuration parameters for the sound field effect node.|
| [OH_AudioSuite_Result OH_AudioSuiteEngine_GetSoundFieldType(OH_AudioNode* audioNode, OH_SoundFieldType* soundFieldType)](#oh_audiosuiteengine_getsoundfieldtype) | - | Obtains the configuration parameters of the sound field effect node.|
| [OH_AudioSuite_Result OH_AudioSuiteEngine_SetEnvironmentType(OH_AudioNode* audioNode, OH_EnvironmentType environmentType)](#oh_audiosuiteengine_setenvironmenttype) | - | Sets the configuration parameters for the environment effect node.|
| [OH_AudioSuite_Result OH_AudioSuiteEngine_GetEnvironmentType(OH_AudioNode* audioNode, OH_EnvironmentType* environmentType)](#oh_audiosuiteengine_getenvironmenttype) | - | Obtains the configuration parameters of the environment effect node.|
| [OH_AudioSuite_Result OH_AudioSuiteEngine_SetVoiceBeautifierType(OH_AudioNode* audioNode, OH_VoiceBeautifierType voiceBeautifierType)](#oh_audiosuiteengine_setvoicebeautifiertype) | - | Sets the configuration parameters for the voice beautifier effect node.|
| [OH_AudioSuite_Result OH_AudioSuiteEngine_GetVoiceBeautifierType(OH_AudioNode* audioNode, OH_VoiceBeautifierType* voiceBeautifierType)](#oh_audiosuiteengine_getvoicebeautifiertype) | - | Obtains the configuration parameters of the voice beautifier effect node.|
| [OH_AudioSuite_Result OH_AudioSuiteEngine_IsNodeTypeSupported(OH_AudioNode_Type nodeType, bool* isSupported)](#oh_audiosuiteengine_isnodetypesupported) | - | Checks whether the system supports the creation of a specified node type to avoid node creation failure. This function is called independently of engine and pipeline states and is only related to the system, without the need to create an engine or pipeline.|

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
| [OH_AudioSuite_Result](capi-native-audio-suite-base-h.md#oh_audiosuite_result) | **AUDIOSUITE_SUCCESS**: The function is executed successfully.<br>         **AUDIOSUITE_ERROR_INVALID_PARAM**: The **audioSuiteEngine** parameter is nullptr.<br>         **AUDIOSUITE_ERROR_INVALID_STATE**: The engine has been deinitialized, is not created, or is not initialized.<br>         **AUDIOSUITE_ERROR_SYSTEM**: Other system exceptions occur.|

### OH_AudioSuiteEngine_CreatePipeline()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_CreatePipeline(OH_AudioSuiteEngine* audioSuiteEngine, OH_AudioSuitePipeline** audioSuitePipeline, OH_AudioSuite_PipelineWorkMode workMode)
```

**Description**

Creates a pipeline within the current audio creation engine. A pipeline is the execution unit within the engine responsible for audio creation, and multiple pipelines can be created within a single engine.<br> Up to 10 pipelines can be created, with a maximum of one real-time rendering pipeline.<br> Each pipeline must have at least one input node and exactly one output node.<br> When the pipeline operations in [OH_AudioSuite_PipelineWorkMode](capi-native-audio-suite-base-h.md#oh_audiosuite_pipelineworkmode).AUDIOSUITE_PIPELINE_EDIT_MODE mode, all effect nodes are supported.<br> When the pipeline operations in [OH_AudioSuite_PipelineWorkMode](capi-native-audio-suite-base-h.md#oh_audiosuite_pipelineworkmode).AUDIOSUITE_PIPELINE_REALTIME_MODE mode, only the [OH_AudioNode_Type](capi-native-audio-suite-base-h.md#oh_audionode_type).EFFECT_NODE_TYPE_EQUALIZER effect node is supported.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioSuiteEngine](capi-ohaudiosuite-oh-audiosuiteenginestruct.md)* audioSuiteEngine | Audio creation engine handle, which is obtained by calling [OH_AudioSuiteEngine_Create](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_create).|
| [OH_AudioSuitePipeline](capi-ohaudiosuite-oh-audiosuitepipelinestruct.md)** audioSuitePipeline | Double pointer used to receive the handle to the newly created audio creation pipeline.|
| [OH_AudioSuite_PipelineWorkMode](capi-native-audio-suite-base-h.md#oh_audiosuite_pipelineworkmode) workMode | Working mode of the pipeline.<br> 1. **AUDIOSUITE_PIPELINE_EDIT_MODE**: All effect nodes are supported.<br> 2. **AUDIOSUITE_PIPELINE_REALTIME_MODE**: Equalizer effect nodes are supported.|

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
| [OH_AudioSuite_Result](capi-native-audio-suite-base-h.md#oh_audiosuite_result) | **AUDIOSUITE_SUCCESS**: The function is executed successfully.<br>         **AUDIOSUITE_ERROR_INVALID_PARAM**: The **audioSuitePipeline** parameter is nullptr.<br>         **AUDIOSUITE_ERROR_PIPELINE_NOT_EXIST**: The pipeline does not exist or has been destroyed.<br>         **AUDIOSUITE_ERROR_INVALID_STATE**: The pipeline is running or the node connection is abnormal.<br>         Possible causes are as follows:<br>         1. The pipeline is already running.<br>         2. The pipeline does not contain any output node.<br>         3. The first node is not an input node.<br>         **AUDIOSUITE_ERROR_TIMEOUT**: The operation times out.<br>         **AUDIOSUITE_ERROR_SYSTEM**: Other system exceptions occur.|

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

>**NOTE**
>Applications need to call this function to obtain audio data that has been processed by effects.
 * When this function is called, the pipeline pulls data backward from the output node, apply effect processing,
 * and fill the processed data into the **audioData** pointer provided by the application.
 * The system attempts to fill the data based on the size specified by **requestFrameSize**, and the actual size of the processed data is returned to the application via **responseSize**.
 * When the application has prepared data for all input nodes and submits the last data through a callback, it should set the finish flag in the callback.
 * Once all inputs in the pipeline have passed the finish flag, the pipeline notifies the application through **finishedFlag** after processing is complete.
 * If **finishedFlag** is **true**, the application should not call this function again.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioSuitePipeline](capi-ohaudiosuite-oh-audiosuitepipelinestruct.md)* audioSuitePipeline | Audio creation pipeline handle, which is obtained by calling [OH_AudioSuiteEngine_CreatePipeline](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_createpipeline).|
| void* audioData | Pointer to the address for writing the obtained audio data.|
| int32_t requestFrameSize | Byte size of the memory allocated for **audioData**. The value must be greater than 0.|
| int32_t* responseSize | Pointer to the size of the audio data written to **audioData** by the pipeline. The value cannot be greater than **requestFrameSize**.|
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
| int32_t* responseSize | Pointer to the size of the audio data written into each element of **audioDataArray** by the pipeline. The system ensures consistent data size across all elements.|
| bool* finishedFlag | Pointer to the flag indicating whether the current pipeline has completed rendering.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioSuite_Result](capi-native-audio-suite-base-h.md#oh_audiosuite_result) | **AUDIOSUITE_SUCCESS**: The function is executed successfully.<br>         **AUDIOSUITE_ERROR_INVALID_PARAM**: A parameter is nullptr or has an invalid value.<br>         Possible causes are as follows:<br>         1. The **audioSuitePipeline** parameter is nullptr.<br>         2. The **audioDataArray** parameter is nullptr.<br>         3. A member of the **audioDataArray** parameter is nullptr.<br>         4. The value of **requestFrameSize** in **audioDataArray** is less than or equal to 0.<br>         5. The **responseSize** parameter is nullptr.<br>         6. The **finishedFlag** parameter is nullptr.<br>         **AUDIOSUITE_ERROR_PIPELINE_NOT_EXIST**: The pipeline does not exist or has been destroyed.<br>         **AUDIOSUITE_ERROR_INVALID_STATE**: The pipeline is not running.<br>         **AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION**: The pipeline rendering is complete. (**finishedFlag** is written as **true** when this function is called.)<br>         **AUDIOSUITE_ERROR_TIMEOUT**: The operation times out.<br>         **AUDIOSUITE_ERROR_SYSTEM**: Other system exceptions occur.|

### OH_AudioSuiteNodeBuilder_Create()

```c
OH_AudioSuite_Result OH_AudioSuiteNodeBuilder_Create(OH_AudioNodeBuilder** builder)
```

**Description**

Obtains an audio creation node builder, which is used to configure and create audio nodes. The builder can be reused. However, if the properties of the new node differ from those of the previous node, you must use [OH_AudioSuiteNodeBuilder_Reset](#oh_audiosuitenodebuilder_reset) to reset the builder.

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

### OH_AudioSuiteNodeBuilder_SetFormat()

```c
OH_AudioSuite_Result OH_AudioSuiteNodeBuilder_SetFormat(OH_AudioNodeBuilder* builder, OH_AudioFormat audioFormat)
```

**Description**

Configures the audio format for input or output nodes. This function can only be used before node creation. For input nodes, it allows the application to specify the audio format for writing data.<br> For output nodes, it allows the application to specify the desired audio format for obtaining data.<br> This function is not supported for other node types.

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

### OH_InputNode_RequestDataCallback()

```c
typedef int32_t (*OH_InputNode_RequestDataCallback)(OH_AudioNode* audioNode, void* userData, void* audioData, int32_t audioDataSize, bool* finished)
```

**Description**

Sets a callback function for the input node to request data.

>**NOTE**
>Applications should write the PCM audio data to be processed to **audioData**, from which OHAudioSuite obtains the data for audio creation.
 * Applications should write data to **audioData** that does not exceed the size specified by **audioDataSize**.
 * Once all data has been passed to the pipeline through this callback, the application should set **finished** to **true** in the last callback. After this, the pipeline will no longer call this function.
 * Only input nodes require this configuration; other nodes do not.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| OH_AudioNode* audioNode | Audio creation node handle, which is obtained by calling [OH_AudioSuiteEngine_CreateNode](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_createnode).|
| void* userData | Pointer to user-specific data. When the system calls this callback function, **userData** passed by calling [OH_AudioSuiteNodeBuilder_SetRequestDataCallback](capi-native-audio-suite-engine-h.md#oh_audiosuitenodebuilder_setrequestdatacallback) is used.|
| void* audioData | Pointer to the memory address provided by the system, where the application should write the audio data stream to be processed (to be filled by the user).|
| int32_t audioDataSize | Byte size of the memory address allocated for **audioData**.|
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
| [OH_AudioNodeBuilder](capi-ohaudiosuite-oh-audionodebuilderstruct.md)* builder | Audio creation node handle, which is obtained by calling [OH_AudioSuiteNodeBuilder_Create](capi-native-audio-suite-engine-h.md#oh_audiosuitenodebuilder_create).|
| [OH_InputNode_RequestDataCallback](capi-native-audio-suite-engine-h.md#oh_inputnode_requestdatacallback) callback | Callback for writing audio data.|
| void* userData | Pointer to user-specific data. The address is passed to the user within the callback function. If it is not used, nullptr can be provided.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioSuite_Result](capi-native-audio-suite-base-h.md#oh_audiosuite_result) | **AUDIOSUITE_SUCCESS**: The function is executed successfully.<br>         **AUDIOSUITE_ERROR_INVALID_PARAM**:<br>         Possible causes are as follows:<br>         1. The **builder** parameter is nullptr.<br>         2. The **callback** parameter is nullptr.<br>         **AUDIOSUITE_ERROR_TIMEOUT**: The operation times out.<br>         **AUDIOSUITE_ERROR_SYSTEM**: Other system exceptions occur.|

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
| [OH_AudioNodeBuilder](capi-ohaudiosuite-oh-audionodebuilderstruct.md)* builder | Audio creation node handle, which is obtained by calling [OH_AudioSuiteNodeBuilder_Create](capi-native-audio-suite-engine-h.md#oh_audiosuitenodebuilder_create).|
| [OH_AudioNode](capi-ohaudiosuite-oh-audionodestruct.md)** audioNode | Audio creation node handle,|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioSuite_Result](capi-native-audio-suite-base-h.md#oh_audiosuite_result) | **AUDIOSUITE_SUCCESS**: The function is executed successfully.<br>         **AUDIOSUITE_ERROR_INVALID_PARAM**: A parameter is nullptr or has an invalid value.<br>         Possible causes are as follows:<br>         1. The **audioSuitePipeline** parameter is nullptr.<br>         2. The **builder** parameter is nullptr.<br>         3. The **audioNode** parameter is nullptr.<br>         **AUDIOSUITE_ERROR_CREATED_EXCEED_SYSTEM_LIMITS**: The number of nodes of the current type already reaches the upper limit.<br>         For example, attempting to create more than 5 effect nodes.<br>         **AUDIOSUITE_ERROR_REQUIRED_PARAMETERS_MISSING**: Mandatory parameters are missing when creating a node of the specified type.<br>         For example, the node type is not set in the builder.<br>         **AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION**: Unsupported operations. For example, setting a callback function for an output node,<br>         or setting an audio format or callback function for an effect node.<br>         **AUDIOSUITE_ERROR_TIMEOUT**: The operation times out.<br>         **AUDIOSUITE_ERROR_MEMORY_ALLOC_FAILED**: Memory allocation fails.<br>         **AUDIOSUITE_ERROR_SYSTEM**: Other system exceptions occur.|

### OH_AudioSuiteEngine_DestroyNode()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_DestroyNode(OH_AudioNode* audioNode)
```

**Description**

Destroys an audio creation node. Whether a node can be destroyed depends on the state of its associated pipeline. If the pipeline is not in the [OH_AudioSuite_PipelineState.AUDIOSUITE_PIPELINE_STOPPED](../apis-audio-kit/capi-native-audio-suite-base-h.md#oh_audiosuite_pipelinestate) state and the node is in the pipeline processing path, the destruction fails.

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

Sets the effect bypass status of the current node (supported only on effect nodes). When **bypass** is set to **true**, the effect node passes data through without any processing. When **bypass** is set to **false**, the effect node performs the corresponding effect processing.

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
OH_AudioSuite_Result OH_AudioSuiteEngine_SetAudioFormat(OH_AudioNode* audioNode, OH_AudioFormat *audioFormat)
```

**Description**

Sets the audio format for input or output nodes after creation. This function is supported only for input and output nodes. The input node specifies the audio source format, and the output node specifies the target format.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioNode](capi-ohaudiosuite-oh-audionodestruct.md)* audioNode | Audio creation node handle, which is obtained by calling [OH_AudioSuiteEngine_CreateNode](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_createnode).|
| [OH_AudioFormat](capi-ohaudiosuite-oh-audioformat.md) *audioFormat | Audio stream format.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioSuite_Result](capi-native-audio-suite-base-h.md#oh_audiosuite_result) | **AUDIOSUITE_SUCCESS**: The function is executed successfully.<br>         **AUDIOSUITE_ERROR_INVALID_PARAM**: The **audioNode** parameter or **audioFormat** is nullptr.<br>         **AUDIOSUITE_ERROR_NODE_NOT_EXIST**: The node does not exist or has been destroyed.<br>         **AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION**: The **audioNode** parameter does not point to an effect node.<br>         **AUDIOSUITE_ERROR_INVALID_STATE**: The pipeline is not in the stopped state.<br>         **AUDIOSUITE_ERROR_TIMEOUT**: The operation times out.<br>         **AUDIOSUITE_ERROR_SYSTEM**: Other system exceptions occur.|

### OH_AudioSuiteEngine_ConnectNodes()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_ConnectNodes(OH_AudioNode* sourceAudioNode, OH_AudioNode* destAudioNode)
```

**Description**

 Connects two nodes, with data flowing from sourceAudioNode to destAudioNode. Connecting nodes will change the pipeline topology and may cause data loss. You are advised to perform this operation when the engine is stopped.<br> The connection order of nodes in a pipeline is as follows: input node -> effect node -> output node.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioNode](capi-ohaudiosuite-oh-audionodestruct.md)* sourceAudioNode | Audio creation node handle, which is obtained by calling [OH_AudioSuiteEngine_CreateNode](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_createnode).|
| [OH_AudioNode](capi-ohaudiosuite-oh-audionodestruct.md)* destAudioNode | Audio creation node handle, which is obtained by calling [OH_AudioSuiteEngine_CreateNode](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_createnode).|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioSuite_Result](capi-native-audio-suite-base-h.md#oh_audiosuite_result) | **AUDIOSUITE_SUCCESS**: The function is executed successfully.<br>         **AUDIOSUITE_ERROR_INVALID_PARAM**: The **sourceAudioNode** parameter or **destAudioNode** is nullptr.<br>         **AUDIOSUITE_ERROR_NODE_NOT_EXIST**: The node does not exist or has been destroyed.<br>         **AUDIOSUITE_ERROR_UNSUPPORTED_CONNECT**: Nodes do not support connection.<br>         Possible causes are as follows:<br>         1. The **sourceAudioNode** parameter points to an output node.<br>         2. The **destAudioNode** parameter points to an input node.<br>         3. The **sourceAudioNode** and **destAudioNode** parameters point to the same node.<br>         4. The **sourceAudioNode** parameter points to a source separation effect node, but the **destAudioNode** parameter does not point to an output node.<br>         5. The **sourceAudioNode** and **destAudioNode** parameters point to nodes within different pipelines.<br>         6. The pipeline is in the running state, but the **destAudioNode** parameter does not point to an audio mixer effect node.<br>         7. The pipeline is in the running state, the **destAudioNode** parameter points to an audio mixer effect node, but the **sourceAudioNode** parameter does not point to an input node.<br>         **AUDIOSUITE_ERROR_INVALID_STATE**: The pipeline is in an invalid state. For example, the output node cannot be found.<br>         **AUDIOSUITE_ERROR_TIMEOUT**: The operation times out.<br>         **AUDIOSUITE_ERROR_SYSTEM**: Other system exceptions occur.|

### OH_AudioSuiteEngine_DisconnectNodes()

```c
OH_AudioSuite_Result OH_AudioSuiteEngine_DisconnectNodes(OH_AudioNode* sourceAudioNode, OH_AudioNode* destAudioNode)
```

**Description**

Disconnect two nodes. This operation will change the pipeline topology and may cause data loss. You are advised to perform this operation when the engine is stopped.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioNode](capi-ohaudiosuite-oh-audionodestruct.md)* sourceAudioNode | Audio creation node handle, which is obtained by calling [OH_AudioSuiteEngine_CreateNode](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_createnode).|
| [OH_AudioNode](capi-ohaudiosuite-oh-audionodestruct.md)* destAudioNode | Audio creation node handle, which is obtained by calling [OH_AudioSuiteEngine_CreateNode](capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_createnode).|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioSuite_Result](capi-native-audio-suite-base-h.md#oh_audiosuite_result) | **AUDIOSUITE_SUCCESS**: The function is executed successfully.<br>         **AUDIOSUITE_ERROR_INVALID_PARAM**: The **sourceAudioNode** parameter or **destAudioNode** is nullptr.<br>         **AUDIOSUITE_ERROR_NODE_NOT_EXIST**: The node does not exist or has been destroyed.<br>         **AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION**: Unsupported operation.<br>         Possible causes are as follows:<br>         1. The **sourceAudioNode** parameter points to an output node.<br>         2. The **destAudioNode** parameter points to an input node.<br>         3. The **sourceAudioNode** and **destAudioNode** parameters point to the same node.<br>         4. The **sourceAudioNode** and **destAudioNode** parameters point to nodes within different pipelines.<br>         5. The pipeline is in the running state, but the **destAudioNode** parameter does not point to an audio mixer effect node.<br>         6. The pipeline is in the running state, the **destAudioNode** parameter points to an audio mixer effect node, but this mixer node is currently connected to only **sourceAudioNode**.<br>         **AUDIOSUITE_ERROR_INVALID_STATE**: The pipeline is in an invalid state. For example, the output node cannot be found.<br>         **AUDIOSUITE_ERROR_TIMEOUT**: The operation times out.<br>         **AUDIOSUITE_ERROR_SYSTEM**: Other system exceptions occur.|

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
| [OH_AudioSuite_Result](capi-native-audio-suite-base-h.md#oh_audiosuite_result) | **AUDIOSUITE_SUCCESS**: The function is executed successfully.<br>         **AUDIOSUITE_ERROR_NODE_NOT_EXIST**: The node does not exist or has been destroyed.<br>         **AUDIOSUITE_ERROR_UNSUPPORTED_OPERATION**: The **audioNode** parameter does not point to an equalizer node.<br>         **AUDIOSUITE_ERROR_INVALID_PARAM**:<br>         Possible causes are as follows:<br>         1. The **audioNode** parameter is nullptr.<br>         2. The value of each member in **frequencyBandGains** is not within the range [–10, 10].<br>         **AUDIOSUITE_ERROR_TIMEOUT**: The operation times out.<br>         **AUDIOSUITE_ERROR_SYSTEM**: Other system exceptions occur.|

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
| [OH_SoundFieldType](capi-native-audio-suite-base-h.md#oh_soundfieldtype)* soundFieldType | Pointer to the configuration parameters of the sound field effect node.|

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
| [OH_EnvironmentType](capi-native-audio-suite-base-h.md#oh_environmenttype)* environmentType | Pointer to the configuration parameters of the environment effect node.|

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
| [OH_VoiceBeautifierType](capi-native-audio-suite-base-h.md#oh_voicebeautifiertype)* voiceBeautifierType | Pointer to the configuration parameters of the voice beautifier effect node.|

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
