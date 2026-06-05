# 空间渲染效果节点(C/C++)
 <!--Kit: Audio Kit-->
 <!--Subsystem: Multimedia-->
 <!--Owner: @xxngwang-->
 <!--Designer: @jay-liusong-->
 <!--Tester: @Filger-->
 <!--Adviser: @w_Machine_cc-->

从API version 23开始，OHAudioSuite给开发者提供空间渲染效果节点[EFFECT_NODE_TYPE_SPACE_RENDER](../../reference/apis-audio-kit/capi-native-audio-suite-base-h.md#oh_audionode_typ)，用于实现三维空间音频渲染能力。空间渲染效果节点可以将音频源在三维空间中进行定位、旋转和扩展处理，为用户营造沉浸式的三维听觉体验。

## 功能概述

### 工作模式

- **固定摆位模式**：将音频源固定在特定空间的指定位置。
- **旋转模式**：让音频源在指定位置设定单周环绕时间与时针方向进行动态渲染。
- **扩展模式**：将音频源按照半径和角度进行扩展。

### 坐标系说明

空间渲染采用左手坐标系，即伸出左手，用拇指和食指形成一个"L"形。

- 拇指指向右侧表示：X轴正方向。
- 食指向上表示：Y轴正方向。
- 其余手指指向前表示：Z轴正方向。

坐标系参数说明：
- X坐标：左右方向。负值表示左侧，正值表示右侧。取值范围为[-5.0, 5.0]，单位为米（m）。
- Y坐标：上下方向，负值表示下方，正值表示上方。取值范围为[-5.0, 5.0]，单位为米（m）。
- Z坐标：前后方向，负值表示后方，正值表示前方。取值范围为[-5.0, 5.0]，单位为米（m）。

## 工作模式详解

固定摆位模式：固定摆位模式用于将音频源放置在特定空间的固定位置，适用于需要固定音源位置的场景，用户可通过调用[oh_audiosuiteengine_setspacerenderpositionparams](../../reference/apis-audio-kit/capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_setspacerenderpositionparams)对空间渲染节点进行设置。固定摆位示意图如下：

![audiosuite-space-render-position](figures/audiosuite-space-render-position.png)

旋转模式：旋转模式让音频源在指定位置设定单周环绕时间与时针方向进行动态渲染，用户可通过调用[oh_audiosuiteengine_setspacerenderrotationparams](../../reference/apis-audio-kit/capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_setspacerenderrotationparams)对空间渲染节点进行设置。旋转模式示意图如下：

![audiosuite-space-render-rotation](figures/audiosuite-space-render-rotation.png)

扩展模式：扩展模式将音频源按照半径和角度进行扩展，用户可通过调用[oh_audiosuiteengine_setspacerenderextensionparams](../../reference/apis-audio-kit/capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_setspacerenderextensionparams)对空间渲染节点进行设置。扩展模式示意图如下：

![audiosuite-space-render-extension](figures/audiosuite-space-render-extension.png)

## 开发基础配置

开发者使用OHAudioSuite提供的空间渲染效果节点，需要添加对应的头文件并链接动态库。

### 在CMake脚本中链接动态库

``` cmake
target_link_libraries(sample PUBLIC libohaudio.so libohaudiosuite.so)
```

### 添加头文件

开发者通过引入头文件使用音频编创相关API：

<!-- @[audioSuite_SpaceRenderEffectInclude](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioSuiteSample/entry/src/main/cpp/space_render_rotation.cpp) -->

## 开发步骤

### 接口调用

详细的API说明请参考[OHAudioSuite](../../reference/apis-audio-kit/capi-ohaudiosuite.md)。

### 空间渲染固定摆位效果


1.  创建引擎和管线。

   <!-- @[audioSuite_CreateSpaceRenderRotationEngineAndPipeline](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioSuiteSample/entry/src/main/cpp/space_render_rotation.cpp) -->

2. 创建输入、输出、空间渲染等节点并连接组网。

  创建输入节点需要实现自定义回调函数`InputNodeWriteDataCallBack`，函数类型为[OH_InputNode_RequestDataCallback()](../../reference/apis-audio-kit/capi-native-audio-suite-engine-h.md#oh_inputnode_requestdatacallback)，调用[OH_AudioSuiteNodeBuilder_SetRequestDataCallback()](../../reference/apis-audio-kit/capi-native-audio-suite-engine-h.md#oh_audiosuitenodebuilder_setrequestdatacallback)接口设置回调函数。

   <!-- @[audioSuite_AudioDataInfo](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioSuiteSample/entry/src/main/cpp/pcm_file_utils.h) -->
   <!-- @[audioSuite_SpaceRenderRotationInputNodeWriteDataCallBack](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioSuiteSample/entry/src/main/cpp/space_render_rotation.cpp) -->
   <!-- @[audioSuite_CreateSpaceRenderRotation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioSuiteSample/entry/src/main/cpp/space_render_rotation.cpp) -->

3. 在播放器的回调函数中，将处理后的数据复制到OH_AudioRenderer实例的缓冲区中，实现音频播放过程中实时预览。

   <!-- @[audioSuite_SpaceRenderRotationAudioRendererOnWriteData](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioSuiteSample/entry/src/main/cpp/space_render_rotation.cpp) -->
   
   ``` C++
   // 示例接口未包含返回值校验，实际使用时请务必添加校验逻辑。
   static OH_AudioData_Callback_Result AudioRendererOnWriteData(OH_AudioRenderer *renderer, void *userData,
                                                                void *audioData, int32_t audioDataSize)
   {
       bool finishedFlag = false;
       int32_t writeSize = 0;
       OH_AudioSuite_Result result = OH_AudioSuiteEngine_RenderFrame(static_cast<OH_AudioSuitePipeline *>(userData),
                                                                     audioData, audioDataSize, &writeSize, &finishedFlag);
       if (result != OH_AudioSuite_Result::AUDIOSUITE_SUCCESS) {
           // 音频编创渲染失败。
           return AUDIO_DATA_CALLBACK_RESULT_INVALID;
       }
       // 音频编创渲染完成。
       if (finishedFlag) {
           // 开发者自定义的行为。
       }
   
       return AUDIO_DATA_CALLBACK_RESULT_VALID;
   }
   ```
   <!-- @[audioSuite_StartSpaceRenderRotationPipeline](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioSuiteSample/entry/src/main/cpp/space_render_rotation.cpp) -->
   
   ``` C++
   // 示例接口未包含返回值校验，实际使用时请务必添加校验逻辑。
   // 创建构建器。
   OH_AudioStreamBuilder_Create(&g_rendererBuilder, OH_AudioStream_Type::AUDIOSTREAM_TYPE_RENDERER);
   OH_AudioStreamBuilder_SetSamplingRate(g_rendererBuilder, OH_Audio_SampleRate::SAMPLE_RATE_48000);
   OH_AudioStreamBuilder_SetChannelCount(g_rendererBuilder, CHANNEL_COUNT);
   OH_AudioStreamBuilder_SetSampleFormat(g_rendererBuilder, AUDIOSTREAM_SAMPLE_S16LE);
   OH_AudioStreamBuilder_SetEncodingType(g_rendererBuilder, AUDIOSTREAM_ENCODING_TYPE_RAW);
   OH_AudioStreamBuilder_SetRendererInfo(g_rendererBuilder, AUDIOSTREAM_USAGE_MUSIC);
   
   // 如果samplingRate为11025请使用40ms来计算。
   OH_AudioFormat audioFormatOutput;
   ConfigureAudioFormat(audioFormatOutput);
   int32_t frameSize = RENDER_FRAME_DURATION_MS * audioFormatOutput.samplingRate * audioFormatOutput.channelCount *
                       SAMPLE_FORMAT_S16LE_BYTE_SIZE / MS_PER_SECOND;
   // 设置audioDataSize长度（待播放的数据大小）。
   OH_AudioStreamBuilder_SetFrameSizeInCallback(g_rendererBuilder, frameSize);
   // 配置写入音频数据回调函数。
   OH_AudioStreamBuilder_SetRendererWriteDataCallback(g_rendererBuilder, AudioRendererOnWriteData,
                                                      static_cast<void *>(g_audioSuitePipeline));
   
   // 启动管线。
   OH_AudioSuiteEngine_StartPipeline(g_audioSuitePipeline);
   // ...
   // 停止管线。
   OH_AudioSuiteEngine_StopPipeline(g_audioSuitePipeline);
   ```

4. 资源销毁。

   <!-- @[audioSuite_DestroySpaceRenderRotation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioSuiteSample/entry/src/main/cpp/real_time_rendering.cpp) -->

## 完整示例代码

- [音频编创示例代码](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/Audio/AudioSuiteSample)