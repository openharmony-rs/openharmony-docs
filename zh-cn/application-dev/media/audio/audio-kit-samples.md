---
kits: ["Audio Kit / 音频服务"]
description: "按场景分类列出Audio Kit各示例工程的名称、开发语言与实现能力，涵盖ArkTS和C/C++两种语言，供开发者按需检索并跳转到对应示例代码工程。"
keywords: [Audio Kit, 示例工程, 音频示例, 音频播放示例, 音频录制示例, 设备路由示例, 音量管理示例, 示例代码, AudioSample]
doctype: guide
status: active
---
# Audio Kit示例代码汇总
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @boxwall-->
<!--Designer: @magekkkk-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

Audio Kit提供丰富的音频示例代码，覆盖音频播放、录制、通话、会话与焦点、设备路由与音量、音效、编创、空间音频、MIDI等核心开发场景，帮助开发者快速定位示例代码。

| 场景分类 | Sample名称 | 语言 | 场景介绍 |
| -------- | -------- | -------- | -------- |
| 音频播放 | [AudioRendererSampleJS](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/Audio/AudioRendererSampleJS) | ArkTS | 使用AudioRenderer开发音频播放的完整示例，包含播放流状态管理、采样率配置等。 |
| 音频录制 | [AudioCaptureSampleJS](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/Audio/AudioCaptureSampleJS) | ArkTS | 使用AudioCapturer开发音频录制、内录及耳返的示例。 |
| 音效管理 | [AudioEffectManagement](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/Audio/AudioEffectManagement) | ArkTS | 使用AudioRenderer进行预置音效查询与实时音效设置。 |
| 音频通话 | [VoipCallSampleJS](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/Audio/VoipCallSampleJS) | ArkTS | 使用AudioRenderer与AudioCapturer实现VoIP音频通话的完整示例，含3A算法配置。 |
| 音频会话 | [AudioSessionSampleJS](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/Audio/AudioSessionSampleJS) | ArkTS | 使用AudioSessionManager进行音频会话管理、焦点持有的示例。 |
| 应用内音频焦点管理 | [AudioIntraAppFocusSample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/Audio/AudioIntraAppFocusSample) | ArkTS | 同应用内多条音频流之间的音频焦点管理示例。 |
| 音频设备路由与音量管理 | [AudioRoutingAndVolumeSample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/Audio/AudioRoutingAndVolumeSample) | ArkTS | 音频输入/输出设备管理、路由切换与音量管理的综合示例。 |
| PC/2in1设备输入输出设备切换 | [AudioEnhanceDeviceSampleJS](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/Audio/AudioEnhanceDeviceSampleJS) | ArkTS | PC/2in1设备输入/输出设备切换示例。 |
| 系统音效 | [SystemSoundPlayer](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/Audio/SystemSoundPlayer) | ArkTS | 使用SoundPlayer播放系统音效的示例。 |
| 音频播放 | [AudioRendererSampleC](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/Audio/AudioRendererSampleC) | C/C++ | 使用OHAudio开发音频普通播放与低时延播放的示例，包含音量设置、声道布局、工作组等能力。 |
| 音频录制 | [AudioCapturerSampleC](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/Audio/AudioCapturerSampleC) | C/C++ | 使用OHAudio开发音频录制、低时延录制及回环采集的示例。 |
| 后台录音 | [AudioVoIPCallSampleC](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/Audio/AudioVoIPCallSampleC) | C/C++ | VoIP通话与后台录音示例。 |
| 音频会话 | [AudioSessionSampleC](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/Audio/AudioSessionSampleC) | C/C++ | 使用OHAudio进行音频会话管理、焦点持有的示例。 |
| 音频设备路由 | [AudioEnhanceDeviceSampleC](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/Audio/AudioEnhanceDeviceSampleC) | C/C++ | PC/2in1设备输入/输出设备切换示例。 |
| 音频编创 | [AudioSuiteSample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/Audio/AudioSuiteSample) | C/C++ | 使用OHAudioSuite进行音频离线编辑、实时预览、格式转换、效果处理与空间渲染的示例。 |
| MIDI | [Midi](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/Audio/Midi) | C/C++ | 使用OH_MIDI进行MIDI设备通信的示例。 |
| 音频快照与调试 | [AudioSnapshot](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/Audio/AudioSnapshot) | C/C++ | 使用音频快照获取问题定位信息的示例。 |

## 相关主题推荐

- [Audio Kit简介](audio-kit-intro.md)
- [音频播放开发概述](audio-playback-overview.md)
- [音频录制开发概述](audio-recording-overview.md)
- [Audio Kit术语](audio-glossary.md)
