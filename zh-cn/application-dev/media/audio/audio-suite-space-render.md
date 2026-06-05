# 空间渲染效果节点(C/C++)
 <!--Kit: Audio Kit-->
 <!--Subsystem: Multimedia-->
 <!--Owner: @xxngwang-->
 <!--Designer: @jay-liusong-->
 <!--Tester: @Filger-->
 <!--Adviser: @w_Machine_cc-->

从API version 23开始，OHAudioSuite给开发者提供空间渲染效果节点（EFFECT_NODE_TYPE_SPACE_RENDER），用于实现三维空间音频渲染能力。空间渲染效果节点可以将音频源在三维空间中进行定位、旋转和扩展处理，为用户营造沉浸式的三维听觉体验。

## 功能概述

空间渲染效果节点支持三种工作模式：

1. **固定摆位模式**：将音频源固定在三维空间的指定位置
2. **旋转模式**：让音频源在三维空间中按照设定的轨迹旋转环绕
3. **扩展模式**：将音频源扩展为一定范围内的空间区域

**图1**：空间渲染效果示意图

![空间渲染效果](https://raw.gitcode.com/openharmony/docs/files/master/zh-cn/application-dev/media/audio/figures/audiosuite-pipeline.png)

## 坐标系说明

空间渲染采用左手坐标系：

**图2**：左手坐标系示意图

伸出左手，用拇指和食指形成一个"L"形：
- 拇指指向右侧 → X轴正方向
- 食指向上 → Y轴正方向
- 其余手指指向前 → Z轴正方向

坐标系参数说明：
- **X坐标**：左右方向，负值表示左侧，正值表示右侧，取值范围[-5.0, 5.0]米
- **Y坐标**：上下方向，负值表示下方，正值表示上方，取值范围[-5.0, 5.0]米
- **Z坐标**：前后方向，负值表示后方，正值表示前方，取值范围[-5.0, 5.0]米

## 音频格式说明

### 输出音频格式（API明确规定）

根据API文档定义，空间渲染效果节点的**输出音频格式**为：
- 采样率：48000Hz
- 采样格式：AUDIO_SAMPLE_S16LE（16位小端）
- 声道数：2（立体声）

### 输入音频格式

API文档未明确规定空间渲染节点的输入音频格式要求。输入音频格式由输入节点配置决定，开发者需要根据实际音频源格式进行配置。

> **说明**：本文档示例代码中使用48kHz、16位、立体声的输入格式作为演示，实际开发中应根据您的音频源格式进行相应配置。如果音频源格式与输出格式不一致，可能需要使用其他效果节点进行格式转换。

## 开发基础配置

开发者使用OHAudioSuite提供的空间渲染效果节点，需要添加对应的头文件并链接动态库。

### 在CMake脚本中链接动态库

```cmake
target_link_libraries(sample PUBLIC libohaudiosuite.so)
```

### 添加头文件

开发者通过引入头文件使用音频编创相关API：

```c++
#include <ohaudiosuite/native_audio_suite_base.h>
#include <ohaudiosuite/native_audio_suite_engine.h>
```

## 工作模式详解

### 1. 固定摆位模式

固定摆位模式用于将音频源放置在三维空间的固定位置，适用于需要固定音源位置的场景，如：
- 背景音乐固定在某个方位
- 对话声音固定在前方
- 环境音效固定在特定位置

#### 配置参数结构体

```c
typedef struct OH_AudioSuite_SpaceRenderPositionParams {
    float x;  // X坐标，取值范围[-5.0, 5.0]，单位：米
    float y;  // Y坐标，取值范围[-5.0, 5.0]，单位：米
    float z;  // Z坐标，取值范围[-5.0, 5.0]，单位：米
} OH_AudioSuite_SpaceRenderPositionParams;
```

**图3**：固定摆位示意图

![固定摆位](https://raw.gitcode.com/openharmony/docs/files/master/zh-cn/application-dev/media/audio/figures/audiosuite-eq-edit.png)

#### 参数说明

| 参数名 | 类型 | 取值范围 | 单位 | 说明 |
|--------|------|----------|------|------|
| x | float | [-5.0, 5.0] | 米 | 空间中X轴坐标，控制左右位置 |
| y | float | [-5.0, 5.0] | 米 | 空间中Y轴坐标，控制上下位置 |
| z | float | [-5.0, 5.0] | 米 | 空间中Z轴坐标，控制前后位置 |

#### 典型应用场景示例

- **前方音源**：x=0, y=0, z=2.0（听众前方2米处）
- **左侧音源**：x=-2.0, y=0, z=0（听众左侧2米处）
- **上方音源**：x=0, y=2.0, z=0（听众上方2米处）
- **环绕听众**：x=2.0, y=0, z=2.0（听众右前方）

### 2. 旋转模式

旋转模式让音频源在三维空间中按照设定的轨迹进行旋转环绕，适用于：
- 环绕音效（如直升机声音）
- 动态背景音乐
- 游戏中的移动音效

#### 配置参数结构体

```c
typedef struct OH_AudioSuite_SpaceRenderRotationParams {
    float x;                                    // X坐标，取值范围[-5.0, 5.0]，单位：米
    float y;                                    // Y坐标，取值范围[-5.0, 5.0]，单位：米
    float z;                                    // Z坐标，取值范围[-5.0, 5.0]，单位：米
    int32_t surroundTime;                       // 单周环绕时间，取值范围[2, 40]，单位：秒
    OH_AudioSuite_SurroundDirection surroundDirection;  // 环绕方向
} OH_AudioSuite_SpaceRenderRotationParams;
```

**图4**：旋转模式示意图

![旋转环绕](https://raw.gitcode.com/openharmony/docs/files/master/zh-cn/application-dev/media/audio/figures/audiosuite-audio-separation-edit.png)

#### 参数说明

| 参数名 | 类型 | 取值范围 | 单位 | 说明 |
|--------|------|----------|------|------|
| x | float | [-5.0, 5.0] | 米 | 旋转中心X坐标 |
| y | float | [-5.0, 5.0] | 米 | 旋转中心Y坐标 |
| z | float | [-5.0, 5.0] | 米 | 旋转中心Z坐标 |
| surroundTime | int32_t | [2, 40] | 秒 | 完成一周环绕所需时间 |
| surroundDirection | enum | [0, 1] | - | 环绕方向：0=逆时针(SPACE_RENDER_CCW)，1=顺时针(SPACE_RENDER_CW) |

#### 环绕方向枚举

```c
enum OH_AudioSuite_SurroundDirection {
    SPACE_RENDER_CCW = 0,  // 逆时针旋转
    SPACE_RENDER_CW = 1    // 顺时针旋转
};
```

#### 典型应用场景示例

- **慢速环绕**：surroundTime=20秒，营造舒缓的环绕效果
- **快速环绕**：surroundTime=5秒，营造紧张的动态效果
- **水平环绕**：x=2.0, y=0, z=0，在水平面旋转
- **垂直环绕**：x=0, y=2.0, z=2.0，在垂直面旋转

### 3. 扩展模式

扩展模式将音频源从点源扩展为一定范围内的空间区域，适用于：
- 大型乐器（如钢琴、管弦乐）
- 环境氛围音效（如雷声、海浪）
- 群体声源（如人群、合唱）

#### 配置参数结构体

```c
typedef struct OH_AudioSuite_SpaceRenderExtensionParams {
    float extRadius;    // 扩展半径，取值范围[1.0, 5.0]，单位：米
    int32_t extAngle;   // 扩展角度，取值范围(0, 360)，单位：度
} OH_AudioSuite_SpaceRenderExtensionParams;
```

**图5**：扩展模式示意图

![扩展模式](https://raw.gitcode.com/openharmony/docs/files/master/zh-cn/application-dev/media/audio/figures/audiosuite-mix-edit.png)

#### 参数说明

| 参数名 | 类型 | 取值范围 | 单位 | 说明 |
|--------|------|----------|------|------|
| extRadius | float | [1.0, 5.0] | 米 | 扩展半径，控制音源的空间范围大小 |
| extAngle | int32_t | (0, 360) | 度 | 扩展角度，控制音源覆盖的空间角度范围 |

#### 典型应用场景示例

- **小型音源**：extRadius=1.5, extAngle=30（如单个乐器）
- **中型音源**：extRadius=3.0, extAngle=90（如小型乐队）
- **大型音源**：extRadius=5.0, extAngle=180（如管弦乐团）
- **全景音源**：extRadius=4.0, extAngle=360（如环绕式环境音）

## 开发步骤

### 1. 创建引擎和管线

首先需要创建音频编创引擎和管线：

```c++
// 示例接口未包含返回值校验，实际使用时请务必添加校验逻辑。
// 创建引擎
OH_AudioSuiteEngine *audioSuiteEngine = nullptr;
OH_AudioSuiteEngine_Create(&audioSuiteEngine);

// 创建管线（可选择编辑模式或实时预览模式）
OH_AudioSuitePipeline *audioSuitePipeline = nullptr;
OH_AudioSuiteEngine_CreatePipeline(audioSuiteEngine, &audioSuitePipeline,
                                   OH_AudioSuite_PipelineWorkMode::AUDIOSUITE_PIPELINE_EDIT_MODE);
```

> **注意**：
> - 编辑模式（AUDIOSUITE_PIPELINE_EDIT_MODE）：支持所有效果节点，适用于离线音频处理
> - 实时预览模式（AUDIOSUITE_PIPELINE_REALTIME_MODE）：支持实时音频处理，API version 23及以后支持所有效果节点

### 2. 创建输入节点

创建输入节点需要设置音频格式和实现数据回调函数：

```c++
// 定义音频数据结构
struct AudioDataInfo {
    uint8_t *buffer = nullptr;   // 音频数据
    int32_t bufferSize = 0;      // 音频数据总大小
    int32_t totalWriteSize = 0;  // 处理过的音频数据总大小
    int32_t totalReadSize = 0;   // 已读取的音频数据总大小
};

// 输入节点请求数据的回调函数
static int32_t InputNodeWriteDataCallBack(OH_AudioNode *audioNode, void *userData, 
                                          void *audioData, int32_t audioDataSize, bool *finished)
{
    if ((audioNode == nullptr) || (userData == nullptr) || (audioData == nullptr) || 
        (audioDataSize <= 0) || (finished == nullptr)) {
        return -1;
    }

    struct AudioDataInfo *info = static_cast<struct AudioDataInfo *>(userData);
    // 要处理的音频大小
    int32_t actualDataSize = std::min(audioDataSize, info->bufferSize - info->totalWriteSize);
    
    // 将PCM音频数据写入audioData
    if (actualDataSize > 0) {
        std::copy(info->buffer + info->totalWriteSize, 
                  info->buffer + info->totalWriteSize + actualDataSize,
                  static_cast<uint8_t *>(audioData));
    }
    info->totalWriteSize += actualDataSize;

    // 音频数据全部处理完
    if (info->totalWriteSize >= info->bufferSize) {
        *finished = true;
    }
    return actualDataSize;
}

// 创建输入节点
OH_AudioNodeBuilder *nodeBuilder = nullptr;
OH_AudioSuiteNodeBuilder_Create(&nodeBuilder);
OH_AudioSuiteNodeBuilder_SetNodeType(nodeBuilder, OH_AudioNode_Type::INPUT_NODE_TYPE_DEFAULT);

// 配置音频数据格式（根据实际音频源格式设置）
OH_AudioFormat audioFormatInput;
audioFormatInput.samplingRate = OH_Audio_SampleRate::SAMPLE_RATE_48000;        // 48kHz
audioFormatInput.channelLayout = OH_AudioChannelLayout::CH_LAYOUT_STEREO;      // 立体声
audioFormatInput.channelCount = 2;                                             // 2声道
audioFormatInput.sampleFormat = OH_Audio_SampleFormat::AUDIO_SAMPLE_S16LE;    // 16位小端
audioFormatInput.encodingType = OH_Audio_EncodingType::AUDIO_ENCODING_TYPE_RAW; // PCM编码

OH_AudioSuiteNodeBuilder_SetFormat(nodeBuilder, audioFormatInput);

// 设置音频流回调
void *userData = static_cast<void *>(audioInfo);
OH_AudioSuiteNodeBuilder_SetRequestDataCallback(nodeBuilder, InputNodeWriteDataCallBack, userData);

// 创建输入节点
OH_AudioNode *inputNode = nullptr;
OH_AudioSuiteEngine_CreateNode(audioSuitePipeline, nodeBuilder, &inputNode);
```

### 3. 创建空间渲染效果节点

创建空间渲染效果节点并配置参数：

```c++
// 重置构造器配置
OH_AudioSuiteNodeBuilder_Reset(nodeBuilder);
OH_AudioSuiteNodeBuilder_SetNodeType(nodeBuilder, OH_AudioNode_Type::EFFECT_NODE_TYPE_SPACE_RENDER);

// 创建空间渲染节点
OH_AudioNode *spaceRenderNode = nullptr;
OH_AudioSuiteEngine_CreateNode(audioSuitePipeline, nodeBuilder, &spaceRenderNode);
```

### 4. 配置空间渲染参数

根据应用场景选择合适的模式并配置参数：

#### 固定摆位模式示例

```c++
// 配置固定摆位参数
OH_AudioSuite_SpaceRenderPositionParams positionParams;
positionParams.x = 0.0f;    // 正前方
positionParams.y = 0.0f;    // 与听众同高
positionParams.z = 2.0f;    // 前方2米

// 设置固定摆位参数
OH_AudioSuiteEngine_SetSpaceRenderPositionParams(spaceRenderNode, positionParams);

// 获取当前参数（可选）
OH_AudioSuite_SpaceRenderPositionParams currentPosition;
OH_AudioSuiteEngine_GetSpaceRenderPositionParams(spaceRenderNode, &currentPosition);
```

#### 旋转模式示例

```c++
// 配置旋转模式参数
OH_AudioSuite_SpaceRenderRotationParams rotationParams;
rotationParams.x = 2.0f;                              // 旋转中心X坐标
rotationParams.y = 0.0f;                              // 旋转中心Y坐标
rotationParams.z = 0.0f;                              // 旋转中心Z坐标
rotationParams.surroundTime = 10;                     // 10秒完成一周
rotationParams.surroundDirection = OH_AudioSuite_SurroundDirection::SPACE_RENDER_CW; // 顺时针

// 设置旋转模式参数
OH_AudioSuiteEngine_SetSpaceRenderRotationParams(spaceRenderNode, rotationParams);

// 获取当前参数（可选）
OH_AudioSuite_SpaceRenderRotationParams currentRotation;
OH_AudioSuiteEngine_GetSpaceRenderRotationParams(spaceRenderNode, &currentRotation);
```

#### 扩展模式示例

```c++
// 配置扩展模式参数
OH_AudioSuite_SpaceRenderExtensionParams extensionParams;
extensionParams.extRadius = 3.0f;    // 扩展半径3米
extensionParams.extAngle = 90;       // 扩展角度90度

// 设置扩展模式参数
OH_AudioSuiteEngine_SetSpaceRenderExtensionParams(spaceRenderNode, extensionParams);

// 获取当前参数（可选）
OH_AudioSuite_SpaceRenderExtensionParams currentExtension;
OH_AudioSuiteEngine_GetSpaceRenderExtensionParams(spaceRenderNode, &currentExtension);
```

### 5. 创建输出节点

创建输出节点用于输出处理后的音频：

```c++
// 重置构造器配置
OH_AudioSuiteNodeBuilder_Reset(nodeBuilder);
OH_AudioSuiteNodeBuilder_SetNodeType(nodeBuilder, OH_AudioNode_Type::OUTPUT_NODE_TYPE_DEFAULT);

// 配置输出音频格式
OH_AudioFormat audioFormatOutput;
audioFormatOutput.samplingRate = OH_Audio_SampleRate::SAMPLE_RATE_48000;
audioFormatOutput.channelLayout = OH_AudioChannelLayout::CH_LAYOUT_STEREO;
audioFormatOutput.channelCount = 2;
audioFormatOutput.sampleFormat = OH_Audio_SampleFormat::AUDIO_SAMPLE_S16LE;
audioFormatOutput.encodingType = OH_Audio_EncodingType::AUDIO_ENCODING_TYPE_RAW;

OH_AudioSuiteNodeBuilder_SetFormat(nodeBuilder, audioFormatOutput);

// 创建输出节点
OH_AudioNode *outputNode = nullptr;
OH_AudioSuiteEngine_CreateNode(audioSuitePipeline, nodeBuilder, &outputNode);

// 销毁节点构造器
OH_AudioSuiteNodeBuilder_Destroy(nodeBuilder);
```

### 6. 连接节点组网

将各个节点按顺序连接组成管线：

```c++
// 连接节点：输入节点 -> 空间渲染节点 -> 输出节点
OH_AudioSuiteEngine_ConnectNodes(inputNode, spaceRenderNode);
OH_AudioSuiteEngine_ConnectNodes(spaceRenderNode, outputNode);
```

**图6**：空间渲染管线组网示意图

![管线组网](https://raw.gitcode.com/openharmony/docs/files/master/zh-cn/application-dev/media/audio/figures/audiosuite-pipeline-state.png)

### 7. 渲染音频数据

启动管线并渲染音频数据：

```c++
// 计算单帧处理数据大小
int32_t frameSize = RENDER_FRAME_DURATION_MS * OH_Audio_SampleRate::SAMPLE_RATE_48000 * 
                    CHANNEL_COUNT * SAMPLE_FORMAT_S16LE_BYTE_SIZE / MS_PER_SECOND;

// 准备接收渲染后的输出音频数据
uint8_t *audioData = (uint8_t *)malloc(frameSize);
int32_t responseSize = 0;
bool finished = false;

// 启动管线
OH_AudioSuiteEngine_StartPipeline(audioSuitePipeline);

// 渲染循环
do {
    OH_AudioSuite_Result result = OH_AudioSuiteEngine_RenderFrame(
        audioSuitePipeline, static_cast<void *>(audioData), frameSize, 
        &responseSize, &finished);
    
    if ((result != OH_AudioSuite_Result::AUDIOSUITE_SUCCESS) || (responseSize <= 0)) {
        // 音频编创渲染失败
        break;
    } else {
        // audioData是经过空间渲染处理的音频数据
        // 音频数据长度为responseSize
        // 开发者根据业务场景自行使用或保存
        // ...
    }
} while (!finished);

// 停止管线
OH_AudioSuiteEngine_StopPipeline(audioSuitePipeline);

// 释放内存
free(audioData);
audioData = nullptr;
```

### 8. 资源销毁

使用完成后销毁所有资源：

```c++
// 销毁节点
OH_AudioSuiteEngine_DestroyNode(inputNode);
OH_AudioSuiteEngine_DestroyNode(spaceRenderNode);
OH_AudioSuiteEngine_DestroyNode(outputNode);

// 销毁管线
OH_AudioSuiteEngine_DestroyPipeline(audioSuitePipeline);

// 销毁引擎
OH_AudioSuiteEngine_Destroy(audioSuiteEngine);
```

## 动态参数调整

在音频渲染过程中，可以动态调整空间渲染参数：

```c++
// 管线运行过程中可以动态修改参数
// 例如：从固定位置移动到新位置
OH_AudioSuite_SpaceRenderPositionParams newPosition;
newPosition.x = -2.0f;   // 移动到左侧
newPosition.y = 1.0f;    // 稍微提高
newPosition.z = 3.0f;    // 距离更远

OH_AudioSuiteEngine_SetSpaceRenderPositionParams(spaceRenderNode, newPosition);

// 或切换到旋转模式
OH_AudioSuite_SpaceRenderRotationParams newRotation;
newRotation.x = 1.5f;
newRotation.y = 0.5f;
newRotation.z = 1.5f;
newRotation.surroundTime = 15;
newRotation.surroundDirection = OH_AudioSuite_SurroundDirection::SPACE_RENDER_CCW;

OH_AudioSuiteEngine_SetSpaceRenderRotationParams(spaceRenderNode, newRotation);
```

## 效果使能控制

可以控制空间渲染效果的开启和关闭：

```c++
// 查询当前效果使能状态
bool bypassStatus = false;
OH_AudioSuiteEngine_GetNodeBypassStatus(spaceRenderNode, &bypassStatus);

// 关闭效果（透传数据，不进行空间渲染处理）
OH_AudioSuiteEngine_BypassEffectNode(spaceRenderNode, true);

// 开启效果（进行空间渲染处理）
OH_AudioSuiteEngine_BypassEffectNode(spaceRenderNode, false);
```

## 注意事项

1. **音频格式配置**：
   - 空间渲染节点的输出格式固定为48kHz、16位、立体声
   - 输入格式由开发者根据实际音频源配置，需要确保输入节点的音频格式设置正确
   - 如果音频源格式与节点处理需求不匹配，可能导致处理失败或效果异常

2. **坐标系理解**：正确理解左手坐标系的方向定义，确保参数设置符合实际需求。

3. **参数范围限制**：
   - 坐标参数必须在[-5.0, 5.0]米范围内
   - 环绕时间必须在[2, 40]秒范围内
   - 扩展半径必须在[1.0, 5.0]米范围内
   - 扩展角度必须在(0, 360)度范围内

4. **管线状态管理**：
   - 连接节点建议在管线停止状态下进行
   - 动态调整参数可以在管线运行状态下进行
   - 销毁节点前需确保管线处于停止状态

5. **实时预览限制**：
   - API version 23之前实时预览模式仅支持均衡器节点
   - API version 23及以后实时预览模式支持空间渲染节点

6. **错误码处理**：详细错误码请参考OH_AudioSuite_Result：
   - AUDIOSUITE_SUCCESS：成功
   - AUDIOSUITE_ERROR_INVALID_PARAM：参数无效
   - AUDIOSUITE_ERROR_INVALID_STATE：非法状态
   - AUDIOSUITE_ERROR_UNSUPPORTED_FORMAT：不支持的音频格式
   - AUDIOSUITE_ERROR_SYSTEM：系统错误

## 应用场景示例

### 场景1：沉浸式音乐播放

```c++
// 将乐器分布在不同空间位置
// 主唱：前方中心
OH_AudioSuite_SpaceRenderPositionParams vocalPosition = {0.0f, 0.5f, 2.0f};

// 鼓：后方扩展
OH_AudioSuite_SpaceRenderExtensionParams drumExtension = {2.0f, 180};

// 吉他：左侧旋转环绕
OH_AudioSuite_SpaceRenderRotationParams guitarRotation = {2.0f, 0.0f, 0.0f, 20, SPACE_RENDER_CW};
```

### 场景2：游戏音效定位

```c++
// 根据游戏对象位置动态调整音效位置
void updateSoundPosition(float objectX, float objectY, float objectZ) {
    OH_AudioSuite_SpaceRenderPositionParams gamePosition;
    gamePosition.x = objectX;
    gamePosition.y = objectY;
    gamePosition.z = objectZ;
    
    OH_AudioSuiteEngine_SetSpaceRenderPositionParams(spaceRenderNode, gamePosition);
}
```

### 场景3：VR/AR环境音

```c++
// 创建360度环绕环境音
OH_AudioSuite_SpaceRenderExtensionParams environmentExtension;
environmentExtension.extRadius = 4.0f;    // 4米范围
environmentExtension.extAngle = 360;      // 全方位覆盖

OH_AudioSuiteEngine_SetSpaceRenderExtensionParams(spaceRenderNode, environmentExtension);
```

## API接口汇总

### 空间渲染参数设置接口

| 接口名称 | 功能描述 | 参数类型 |
|---------|---------|---------|
| OH_AudioSuiteEngine_SetSpaceRenderPositionParams | 设置固定摆位模式参数 | OH_AudioSuite_SpaceRenderPositionParams |
| OH_AudioSuiteEngine_GetSpaceRenderPositionParams | 获取固定摆位模式参数 | OH_AudioSuite_SpaceRenderPositionParams* |
| OH_AudioSuiteEngine_SetSpaceRenderRotationParams | 设置旋转模式参数 | OH_AudioSuite_SpaceRenderRotationParams |
| OH_AudioSuiteEngine_GetSpaceRenderRotationParams | 获取旋转模式参数 | OH_AudioSuite_SpaceRenderRotationParams* |
| OH_AudioSuiteEngine_SetSpaceRenderExtensionParams | 设置扩展模式参数 | OH_AudioSuite_SpaceRenderExtensionParams |
| OH_AudioSuiteEngine_GetSpaceRenderExtensionParams | 获取扩展模式参数 | OH_AudioSuite_SpaceRenderExtensionParams* |

### 管线控制接口

| 接口名称 | 功能描述 |
|---------|---------|
| OH_AudioSuiteEngine_Create | 创建音频编创引擎 |
| OH_AudioSuiteEngine_Destroy | 销毁音频编创引擎 |
| OH_AudioSuiteEngine_CreatePipeline | 创建音频编创管线 |
| OH_AudioSuiteEngine_DestroyPipeline | 销毁音频编创管线 |
| OH_AudioSuiteEngine_StartPipeline | 启动管线 |
| OH_AudioSuiteEngine_StopPipeline | 停止管线 |
| OH_AudioSuiteEngine_GetPipelineState | 获取管线状态 |

### 节点管理接口

| 接口名称 | 功能描述 |
|---------|---------|
| OH_AudioSuiteNodeBuilder_Create | 创建节点构造器 |
| OH_AudioSuiteNodeBuilder_Destroy | 销毁节点构造器 |
| OH_AudioSuiteNodeBuilder_SetNodeType | 设置节点类型 |
| OH_AudioSuiteNodeBuilder_SetFormat | 设置音频格式 |
| OH_AudioSuiteNodeBuilder_SetRequestDataCallback | 设置数据回调 |
| OH_AudioSuiteEngine_CreateNode | 创建节点 |
| OH_AudioSuiteEngine_DestroyNode | 销毁节点 |
| OH_AudioSuiteEngine_ConnectNodes | 连接节点 |
| OH_AudioSuiteEngine_BypassEffectNode | 设置效果使能状态 |
| OH_AudioSuiteEngine_GetNodeBypassStatus | 获取效果使能状态 |

### 渲染接口

| 接口名称 | 功能描述 |
|---------|---------|
| OH_AudioSuiteEngine_RenderFrame | 渲染单帧音频数据 |
| OH_AudioSuiteEngine_MultiRenderFrame | 渲染多路输出音频数据 |

## 完整示例代码

完整的示例代码请参考：
- [音频编创示例代码](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/Audio/AudioSuiteSample)

## 相关文档

- [音频编创开发概述](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/media/audio/audio-suite.md)
- [离线编辑](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/media/audio/audio-suite-manual-rendering.md)
- [实时预览](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/media/audio/audio-suite-real-time-rendering.md)
- [OHAudioSuite API参考](https://gitcode.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis-audio-kit/capi-ohaudiosuite.md)