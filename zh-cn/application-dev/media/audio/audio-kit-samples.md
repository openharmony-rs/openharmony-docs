---
kits: ["Audio Kit / 音频服务"]
description: "按场景分类列出Audio Kit各示例工程的名称、开发语言与实现能力，涵盖ArkTS和C/C++两种语言，供开发者按需检索并跳转到对应示例代码工程。"
keywords: [Audio Kit, 示例工程, 音频示例, 设备路由示例, 音量管理示例, 示例代码, AudioSample, MIDI, 空间音频]
doctype: guide
status: active
---
# Audio Kit指南配套示例代码
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @boxwall-->
<!--Designer: @magekkkk-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

| 场景分类 | Sample名称 | 语言 | 场景介绍 |
| -------- | -------- | -------- | -------- |
| 低功耗音频播放 | [AudioRendererSampleJS](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/Audio/AudioRendererSampleJS) | ArkTS | 使用AudioRenderer以STREAM_USAGE_MUSIC流类型播放音乐，系统默认启用低功耗渲染器，可基于此示例实践低功耗音频播放。 |
| 空间音频能力查询和状态订阅 | [AudioRendererSampleJS](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/Audio/AudioRendererSampleJS) | ArkTS | 演示获取AudioSpatializationManager实例、查询设备空间音频渲染能力与开关状态，以及订阅/取消订阅开关状态变化事件的完整场景。 |
| 音频设备路由与音量管理 | [AudioRoutingAndVolumeSample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/Audio/AudioRoutingAndVolumeSample) | ArkTS | 音频输入/输出设备管理、路由切换与音量管理的综合示例。 |
| PC/2in1设备输入输出设备切换 | [AudioEnhanceDeviceSampleJS](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/Audio/AudioEnhanceDeviceSampleJS) | ArkTS | PC/2in1设备输入/输出设备切换示例。 |
| MIDI设备通信 | [Midi](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/Audio/Midi) | C/C++ | 演示创建MIDI客户端、枚举并打开USB或蓝牙MIDI设备、管理输入输出端口、以UMP格式收发MIDI消息，并通过虚拟钢琴键盘体验音符收发。 |
| 音频设备路由 | [AudioEnhanceDeviceSampleC](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/Audio/AudioEnhanceDeviceSampleC) | C/C++ | PC/2in1设备输入/输出设备切换示例。 |

## 相关主题推荐

- [Audio Kit简介](audio-kit-intro.md)
- [音频播放开发概述](audio-playback-overview.md)
- [音频录制开发概述](audio-recording-overview.md)
- [Audio Kit术语](audio-glossary.md)
