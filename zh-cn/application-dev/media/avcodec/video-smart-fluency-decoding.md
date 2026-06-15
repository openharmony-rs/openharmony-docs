# 智能流畅倍速解码

<!--Kit: AVCodec Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @yang-xiaoyu5-->
<!--Designer: @dpy2650--->
<!--Tester: @cyakee-->
<!--Adviser: @w_Machine_cc-->

## 特性简介

从API version 26开始，系统集成了智能流畅倍速解码特性。该特性是一种结合硬件解码能力与人因感知模型的系统级解码性能优化方案。

在传统多媒体架构中，开启高倍速播放会导致视频理论帧率成倍增加（如60fps视频在3.0x下需每秒处理180帧），主要带来以下两方面问题：
1. **物理限制与感知冗余**：移动端设备的视频送显帧率通常受限于整机功耗管控（常为 60fps），远低于高倍速下的理论帧率。此外，在高速动态画面下，受限于人眼的视觉暂留效应与动态视锐度下降，强行解码并渲染超出分辨能力的微小运动帧，会产生无效的算力消耗。
2. **应用层干预代价高**：传统架构中的倍速丢帧通常在应用层的渲染端被动触发，此时多余帧的解码算力已经消耗。若应用层试图在解码前主动进行内容感知，则需引入高耗能的像素级计算（如光流分析），导致整体功耗反而增加。

本方案将丢帧决策下移至系统层。系统无需进行复杂的像素级图像分析，而是直接利用硬件解码器输出的运动矢量（Motion Vectors，简称 MV）以及视频码流的时域分层特征。依托此低开销筛选链路，系统能够在解码前精准剔除视觉感知权重较低的非关键帧，避免无效的解码计算。该特性在大幅降低解码与渲染负载、有效控制设备发热的同时，能提供比应用层单纯均匀抽帧更平滑连贯的播放体验。

## 帧保留模式详解

系统提供以下三种帧保留模式，供开发者按需切换：

| 模式 | 实现原理 | 使用场景 |
| :--- | :--- | :--- |
| **感知自适应（ADAPTIVE）** | 系统依据应用层传入的当前倍速，动态分析视频运动特征，优先剔除视觉感知权重较低的非关键帧。 | **本特性的核心推荐模式**。主要用于高倍速播放场景，提供比无内容差别均匀抽帧更符合人眼视觉连贯性的平滑体验。 |
| **全量直通（FULL）** | 解码器透明直通，不干预解码输入输出，对所有输入帧进行全量解码输出。 | 适用于正常倍速或慢速播放场景，确保画质绝对无损；同时作为初始化阶段的基线配置。 |
| **平滑定比（UNIFORM）** | 系统按开发者指定的固定比例均匀地进行抽帧。 | 适用于特殊的降载与提速场景，如高温场景下的降载降温，以及编辑预览场景下的拖拽流畅性提升。|

## 参数说明

本特性需主动下发配置才可以生效。通过配置`OH_AVFormat`中的以下键值对来精确控制行为：

1. **OH_MD_KEY_VIDEO_DECODER_FRAME_RETENTION_MODE（模式配置）**
   - **类型**：`int32_t`
   - **取值**：参考枚举`OH_FrameRetentionMode`（0: FULL, 1: ADAPTIVE, 2: UNIFORM）。
   - **描述**：特性的总开关与模式选择，建议在初始化阶段配置。

2. **OH_MD_KEY_VIDEO_DECODER_SPEED（解码倍速）**
   - **类型**：`double`
   - **范围**：严格大于0.0。
   - **描述**：**在`ADAPTIVE`模式下必须同步配置此参数**，作为系统动态计算的依据。

3. **OH_MD_KEY_VIDEO_DECODER_FRAME_RETENTION_RATIO（保留比例）**
   - **类型**：`double`
   - **范围**：`[0.01, 1.0]`（例如0.5表示保留50%的解码帧）。
   - **描述**：仅在`UNIFORM`模式下生效。配置越界或异常时，系统默认以30fps为目标帧率进行兜底。

## 倍速播放场景开发实践

对于常规视频播放业务，建议采用**初始化配置与动态切换结合**的策略：

- **初始化配置**：在视频起播前的初始化阶段，统一配置为全量直通（`FULL`）模式，完成底层特征链路的准备工作。
- **动态切换**：在播放过程中，当目标倍速大于 1.0x 时，动态切入感知自适应（`ADAPTIVE`）模式，交由系统接管丢帧决策；当恢复至 1.0x 及以下倍速时，切回全量直通（`FULL`）模式，恢复全量帧解码输出。

### 步骤一：初始化状态基线准备

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

### 步骤二：运行态按需切换

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
        // 场景：正常播放 (1.0x) 或 慢速播放 (< 1.0x)。
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

## 其他有益场景开发实践

本特性除了在倍速播放场景下推荐使用，在以下场景也可使用，获得性能和体验收益。比如：

- **高温场景下的降载降温**：当设备发热触发温控告警时，降低功耗优先于画面流畅度。开发者可切换至`UNIFORM`模式并下发较低比例（如0.3），通过减少解码和显示帧率来降低系统负载，从而有效辅助设备降温。
- **编辑预览场景下的拖拽流畅性提升**：在视频编辑等需要频繁拖拽进度条的场景中，全量解码途经帧会显著拖慢画面的刷新响应。开发者可在此状态下临时切入`UNIFORM`模式并下发较低比例，通过适当减少途经画面的解码帧数来换取更快的画面刷新速度，从而显著提升交互的跟手感与流畅性。

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

## 约束与限制

- **格式支持**：此特性仅在视频解码链路生效，当前仅支持 H.264、H.265 及 H.266 码流格式。
- **参数异常兜底**：在`UNIFORM`模式下，若传入的保留比例非法或未明确指定，系统将默认以30fps为目标输出帧率进行解码与送显。
- **硬件能力降级**：`ADAPTIVE`模式依赖硬件解码输出运动矢量（MV）等特征信息。在不支持该能力的硬件平台上，系统会自动降级处理以维持基础的平滑播放，但无法提供最佳的功耗收益。
- **音视频同步（AV Sync）安全**：智能倍速丢帧机制仅决定帧的存留，不会修改保留帧原始的PTS（显示时间戳）与DTS（解码时间戳）信息，不影响音画同步。