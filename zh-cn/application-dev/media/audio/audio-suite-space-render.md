# 空间渲染效果节点(C/C++)
 <!--Kit: Audio Kit-->
 <!--Subsystem: Multimedia-->
 <!--Owner: @xxngwang-->
 <!--Designer: @jay-liusong-->
 <!--Tester: @Filger-->
 <!--Adviser: @w_Machine_cc-->

从API version 23开始，OHAudioSuite给开发者提供空间渲染效果节点[EFFECT_NODE_TYPE_SPACE_RENDER](../../reference/apis-audio-kit/capi-native-audio-suite-base-h.md#oh_audionode_typ)），用于实现三维空间音频渲染能力。空间渲染效果节点可以将音频源在三维空间中进行定位、旋转和扩展处理，为用户营造沉浸式的三维听觉体验。

## 功能概述

### 工作模式

- **[固定摆位模式](audio-suite-space-render.md#固定摆位模式)**：将音频源固定在三维空间的指定位置
-  **[旋转模式](audio-suite-space-render.md#旋转模式)**：让音频源在三维空间中按照设定的轨迹旋转环绕
- **[扩展模式](audio-suite-space-render.md#扩展模式)**：将音频源扩展为一定范围内的空间区域

### 坐标系说明

空间渲染采用左手坐标系：

伸出左手，用拇指和食指形成一个"L"形：
- 拇指指向右侧 → X轴正方向
- 食指向上 → Y轴正方向
- 其余手指指向前 → Z轴正方向

坐标系参数说明：
- **X坐标**：左右方向，负值表示左侧，正值表示右侧，取值范围[-5.0, 5.0]米
- **Y坐标**：上下方向，负值表示下方，正值表示上方，取值范围[-5.0, 5.0]米
- **Z坐标**：前后方向，负值表示后方，正值表示前方，取值范围[-5.0, 5.0]米

## 工作模式详解

固定摆位模式：固定摆位模式用于将音频源放置在三维空间的固定位置，适用于需要固定音源位置的场景，用户可通过调用[oh_audiosuiteengine_setspacerenderpositionparams](../../reference/apis-audio-kit/capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_setspacerenderpositionparams)对空间渲染节点进行设置。

固定摆位示意图

![固定.png](https://raw.gitcode.com/user-images/assets/9860003/07e503e8-3355-460c-9c7b-e942fc5ff7ab/固定.png '固定.png')

旋转模式：旋转模式让音频源在三维空间中按照设定的轨迹进行旋转环绕，用户可通过调用[oh_audiosuiteengine_setspacerenderrotationparams](../../reference/apis-audio-kit/capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_setspacerenderrotationparams)对空间渲染节点进行设置。

旋转模式示意图

![旋转.png](https://raw.gitcode.com/user-images/assets/9860003/10cff5ce-191c-4610-84b0-96a984e83e7e/旋转.png '旋转.png')

扩展模式：扩展模式将音频源从点源扩展为一定范围内的空间区域，用户可通过调用[oh_audiosuiteengine_setspacerenderpositionparams](../../reference/apis-audio-kit/capi-native-audio-suite-engine-h.md#oh_audiosuiteengine_setspacerenderpositionparams)对空间渲染节点进行设置。

扩展模式示意图

![扩展.png](https://raw.gitcode.com/user-images/assets/9860003/9c56ad46-efb7-402b-b5d5-b1a2b9f246a5/扩展.png '扩展.png')

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
   <!-- @[audioSuite_StartSpaceRenderRotationPipeline](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioSuiteSample/entry/src/main/cpp/space_render_rotation.cpp) -->

4. 资源销毁。

   <!-- @[audioSuite_DestroySpaceRenderRotation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioSuiteSample/entry/src/main/cpp/real_time_rendering.cpp) -->

## 完整示例代码

- [音频编创示例代码](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/Audio/AudioSuiteSample)