---
kits: ["Audio Kit / 音频服务"]
description: "汇总Audio Kit指南配套示例代码，覆盖低功耗音频播放、空间音频能力查询与状态订阅场景，供开发者对照指南获取示例工程快速实践。"
keywords: [Audio Kit, 示例代码, 低功耗播放, 空间音频, AudioRenderer, OHAudio, AudioSpatializationManager]
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
| 低功耗音频播放 | [OHAudio](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/Audio/OHAudio) | C/C++ | 使用OHAudio以AUDIOSTREAM_USAGE_MUSIC流类型播放音频，系统默认启用低功耗渲染器，可基于此示例实践C/C++侧低功耗音频播放。 |
| 空间音频能力查询和状态订阅 | [AudioRendererSampleJS](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/Audio/AudioRendererSampleJS) | ArkTS | 演示获取AudioSpatializationManager实例、查询设备空间音频渲染能力与开关状态，以及订阅/取消订阅开关状态变化事件的完整场景。 |
