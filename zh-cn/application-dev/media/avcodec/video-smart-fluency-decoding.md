# 智能流畅倍速解码

<!--Kit: AVCodec Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @yang-xiaoyu5-->
<!--Designer: @dpy2650--->
<!--Tester: @cyakee-->
<!--Adviser: @w_Machine_cc-->

## 特性简介

从API version 26开始，系统集成了智能流畅倍速解码特性。这是一种深度结合硬件解码能力和人因感知特性的系统级解码性能优化方案。

### 核心背景：倍速播放与感知冗余
在传统多媒体架构中，当用户开启2.0x或更高倍速播放时，视频流的理论帧率成倍膨胀（例如60fps视频在3.0x下技术上需要每秒处理180帧）。这种过载引发了两个超限问题：
1. **物理与生理超限**：出于对整机功耗的严格控制，移动端设备的视频播放送显帧率通常被硬性限制在最高60fps（这与部分设备支持的120Hz UI刷新率无关）。180fps远超此播放送显上限。同时，人眼在面对高倍速、高动态画面时，由于视觉暂留效应与动态视锐度下降，存在大量的时域感知冗余。强行渲染肉眼无法分辨的微小运动帧，属于无效功耗。
2. **应用层干预的局限**：传统架构中，倍速丢帧通常由应用层在渲染端被动触发。此时，解码算力已被白白浪费。若应用层试图在解码前进行内容感知，则必须对图像进行高耗能的像素级计算（如光流分析），在能耗上得不偿失。

**本方案的核心价值在于将丢帧/帧保留决策下移至系统层。** 系统感知引擎无需进行复杂的图像像素分析，而是直接读取硬件解码器上报的运动矢量（Motion Vectors，简称MV）与视频流固有的时域分层特征。通过建立这种低开销、高精度的筛选机制，实现在解码前对非关键帧的筛选与剔除，从而彻底免除了这部分帧的解码算力消耗。这一核心能力使得系统能够在大幅降低解码与送显负载（节省能耗与发热）的同时，保留视觉权重最高的关键帧，提供远超应用层无内容差别均匀抽帧的平滑连贯体验。

## 适用场景与帧保留模式

本特性主要聚焦于高负载倍速播放场景，旨在将复杂的时域内容感知与丢帧决策完全托管给系统。开发者只需进行极简的参数配置，即可在倍速场景下兼顾最优的系统能效与流畅的播放体验。

系统提供以下三种帧保留模式，开发者可依据业务状态灵活切换：

| 模式 | 实现原理 | 使用场景 |
| :--- | :--- | :--- |
| **感知自适应（ADAPTIVE）** | 全权托管给系统。感知引擎依据应用层传入的当前倍速，动态分析视频运动特征，优先剔除视觉感知权重较低的非关键帧。 | **本特性的核心推荐模式**。主要用于高倍速播放场景，提供比无内容差别均匀抽帧更符合人眼视觉连贯性的平滑体验。 |
| **全量直通（FULL）** | 即关闭智能丢帧功能。解码器处于基础的透明直通状态，不干预任何输入输出，对所有输入帧进行全量解码输出。 | 适用于正常倍速或慢速播放场景，确保画质绝对无损；同时作为初始化阶段的基线配置。 |
| **平滑定比（UNIFORM）** | 基于纯数学算法，按开发者指定的固定比例绝对均匀地进行抽帧剔除，不引入内容感知算法。 | 适用于特殊的降频与灾备痛点，如突破物理显示瓶颈限制、温控降级与极端省电，以及编辑预览时的快速拖拽响应。 |

## 参数规范说明

本特性需主动下发配置才可以生效。通过配置`OH_AVFormat`中的以下键值对来精确控制行为：

1. **OH_MD_KEY_VIDEO_DECODER_FRAME_RETENTION_MODE（模式配置）**
   - **类型**：`int32_t`
   - **取值**：参考枚举`OH_FrameRetentionMode`（0: FULL, 1: ADAPTIVE, 2: UNIFORM）。
   - **描述**：特性的总开关与模式选择，建议在初始化阶段配置。

2. **OH_MD_KEY_VIDEO_DECODER_SPEED（参考倍速）**
   - **类型**：`double`
   - **范围**：严格大于0.0。
   - **描述**：**在`ADAPTIVE`模式下必须同步配置此参数**，作为底层动态计算的依据。

3. **OH_MD_KEY_VIDEO_DECODER_FRAME_RETENTION_RATIO（保留比例）**
   - **类型**：`double`
   - **范围**：`[0.01, 1.0]`（例如0.5表示保留50%的解码帧）。
   - **描述**：仅在`UNIFORM`模式下生效。配置越界或异常时，系统默认以30fps为目标帧率进行兜底。

## 典型倍速播放开发实践（主线场景）

在主流的媒体播放器业务中，推荐采用**基线准备 + 按需切换**的策略：
- **基线准备**：在视频起播前的初始化阶段，配置为全量直通（FULL）模式。
- **按需切换**：在播放过程中，仅当目标倍速**严格大于1.0x**（即高倍速场景）时，动态切换至感知自适应（ADAPTIVE）模式，使能系统丢帧管控；当处于1.0x及以下倍速时，切回全量直通模式，确保画质绝对无损。

### 步骤一：初始化状态基线准备（Configure）

在视频起播前，配置初始模式。

<!-- @[configure_full_baseline](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/BasicFeature/Media/AVCodec/entry/src/main/cpp/capbilities/video_decoder.cpp) -->

``` C++
int32_t VideoDecoder::Configure(const SampleInfo &sampleInfo)
{
    OH_AVFormat *format = OH_AVFormat_Create();
    CHECK_AND_RETURN_RET_LOG(format != nullptr, AVCODEC_SAMPLE_ERR_ERROR, "AVFormat create failed");

    OH_AVFormat_SetIntValue(format, OH_MD_KEY_WIDTH, sampleInfo.videoWidth);
    OH_AVFormat_SetIntValue(format, OH_MD_KEY_HEIGHT, sampleInfo.videoHeight);
    OH_AVFormat_SetDoubleValue(format, OH_MD_KEY_FRAME_RATE, sampleInfo.frameRate);
    OH_AVFormat_SetIntValue(format, OH_MD_KEY_PIXEL_FORMAT, sampleInfo.pixelFormat);
    OH_AVFormat_SetIntValue(format, OH_MD_KEY_ROTATION, sampleInfo.rotation);
    if (sampleInfo.codecSyncMode) {
        OH_AVFormat_SetIntValue(format, OH_MD_KEY_ENABLE_SYNC_MODE, sampleInfo.codecSyncMode);
    }
    if (sampleInfo.isSmartFluencySupported) {
        // 配置 FULL 模式，为后续 ADAPTIVE 模式性能体验最大化准备好运行环境。
        OH_AVFormat_SetIntValue(format, OH_MD_KEY_VIDEO_DECODER_FRAME_RETENTION_MODE,
                                OH_FRAME_RETENTION_MODE_FULL);
    }

    int ret = OH_VideoDecoder_Configure(decoder_, format);
    OH_AVFormat_Destroy(format);
    format = nullptr;
    CHECK_AND_RETURN_RET_LOG(ret == AV_ERR_OK, AVCODEC_SAMPLE_ERR_ERROR, "Config failed, ret: %{public}d", ret);
    return AVCODEC_SAMPLE_ERR_OK;
}
```

### 步骤二：运行态按需切换（Running）

系统支持在运行态下动态切换帧保留模式。开发者可通过调用`OH_VideoDecoder_SetParameter`实时下发配置，参数的生效时机与该接口的标准行为一致。

<!-- @[onUserSpeedChanged](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/BasicFeature/Media/AVCodec/entry/src/main/cpp/capbilities/video_decoder.cpp) -->

``` C++
int32_t VideoDecoder::OnUserSpeedChanged(double targetSpeed)
{
    OH_AVFormat *param = OH_AVFormat_Create();
    CHECK_AND_RETURN_RET_LOG(param != nullptr, AVCODEC_SAMPLE_ERR_ERROR, "AVFormat create failed");

    // 引入 epsilon 处理 double 类型的精度比较。
    const double EPSILON = 1e-6;

    if (targetSpeed > 1.0 + EPSILON) {
        // 场景：高倍速播放 (如 1.5x, 2.0x, 3.0x 等)。
        // 策略：使能感知自适应模式。
        OH_AVFormat_SetIntValue(param, OH_MD_KEY_VIDEO_DECODER_FRAME_RETENTION_MODE,
                                OH_FRAME_RETENTION_MODE_ADAPTIVE);
        OH_AVFormat_SetDoubleValue(param, OH_MD_KEY_VIDEO_DECODER_SPEED, targetSpeed);
    } else {
        // 场景：正常播放 (1.0x) 或慢速播放 (< 1.0x)。
        // 策略：切换到全量直通模式，保障帧帧送显。
        OH_AVFormat_SetIntValue(param, OH_MD_KEY_VIDEO_DECODER_FRAME_RETENTION_MODE,
                                OH_FRAME_RETENTION_MODE_FULL);
    }

    // 实时下发参数，动态调整系统帧保留策略。
    int32_t ret = OH_VideoDecoder_SetParameter(decoder_, param);
    OH_AVFormat_Destroy(param);
    CHECK_AND_RETURN_RET_LOG(ret == AV_ERR_OK, AVCODEC_SAMPLE_ERR_ERROR,
                             "SetParameter failed, ret: %{public}d", ret);
    return AVCODEC_SAMPLE_ERR_OK;
}
```

## 其他有益延伸场景（UNIFORM模式）

本特性除了在倍速播放场景下推荐使用，在以下场景也可使用，获得性能和体验收益。比如：

- **物理显示瓶颈限制**：当视频解码帧率远超设备播放刷新上限时。开发者可直接计算比例下发`UNIFORM`模式。在不依赖智能算法的前提下，精准且均匀地削减解码与渲染功耗。
- **温控降级与极端省电**：当设备触发高温严重告警时，此时流畅度让位于设备生存。开发者可无视当前播放状态，强切`UNIFORM`模式并下发极低比例（如0.3），强行削减算力消耗，为系统提供最可靠的灾备降温。
- **编辑预览与快速拖拽**：在视频编辑场景中快速拖拽时间线时，途经帧的全量解码会造成严重的交互延迟与卡顿。开发者可在此类高频拖拽状态下临时切入`UNIFORM`模式并下发较低比例。通过牺牲拖拽过程中的绝对连贯性来换取极速的画面响应，极大提升操作的跟手性与流畅感。

**业务逻辑代码示例（以应对温控告警为例）：**

<!-- @[onThermalWarningReceived](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/BasicFeature/Media/AVCodec/entry/src/main/cpp/capbilities/video_decoder.cpp) -->

``` C++
int32_t VideoDecoder::OnThermalWarningReceived(double ratio)
{
    OH_AVFormat *param = OH_AVFormat_Create();
    CHECK_AND_RETURN_RET_LOG(param != nullptr, AVCODEC_SAMPLE_ERR_ERROR, "AVFormat create failed");

    // 采用 UNIFORM 平滑定比模式。
    OH_AVFormat_SetIntValue(param, OH_MD_KEY_VIDEO_DECODER_FRAME_RETENTION_MODE,
                            OH_FRAME_RETENTION_MODE_UNIFORM);

    // 设定保留比例（如 0.3 表示仅保留 30% 的解码帧输出）。
    OH_AVFormat_SetDoubleValue(param, OH_MD_KEY_VIDEO_DECODER_FRAME_RETENTION_RATIO, ratio);

    // 实时下发生效，系统将执行均匀的抽帧剔除，降低整机负载。
    int32_t ret = OH_VideoDecoder_SetParameter(decoder_, param);
    OH_AVFormat_Destroy(param);
    CHECK_AND_RETURN_RET_LOG(ret == AV_ERR_OK, AVCODEC_SAMPLE_ERR_ERROR,
                             "SetParameter failed, ret: %{public}d", ret);
    return AVCODEC_SAMPLE_ERR_OK;
}
```

## 约束和限制与行为细节

- **格式支持**：本特性属于视频解码专属能力，仅支持H.264、H.265及H.266视频码流格式。
- **参数越界与兜底机制**：在`UNIFORM`模式下，若传入的保留比例非法或因业务异常导致实际比例不明确，系统决策引擎不会产生不可控行为，而是作为安全兜底策略，直接按照30fps进行解码与送显。
- **降级行为保障**：`ADAPTIVE`模式依赖硬件解码输出运动矢量（MV）等解码信息的能力。受限于硬件支持情况，该能力的技术性能收益存在平台差异，但系统底层兜底策略会确保**体验流畅度不受影响**。为了获得系统最大收益，强烈建议开发者在`Configure`阶段配置`FULL`模式，为后续使能智能倍速丢帧准备好运行环境。
- **音视频同步（AV Sync）安全**：智能倍速丢帧机制仅决定帧的存留，不会修改保留帧原始的PTS（显示时间戳）与DTS（解码时间戳）信息，不影响音画同步。