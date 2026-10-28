---
kits: ["AVCodec Kit / 音视频编解码服务"]
description: "汇总AVCodec Kit开发指南配套的示例工程，涵盖视频编解码、音频编解码、媒体数据封装与解封装、智能流畅倍速解码、时域可分层编码及ROI视频编码等场景，便于开发者按场景查找参考示例代码。"
keywords: [AVCodec Kit, 示例代码, Sample, 视频编解码, 音频编解码, 封装, 解封装, 智能流畅倍速解码, 时域可分层编码, ROI编码]
doctype: guide
status: active
---

# AVCodec Kit指南配套示例代码

<!--Kit: AVCodec Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @rchdlee-->
<!--Designer: @dpy2650-->
<!--Tester: @cyakee; @baotianhao-->
<!--Adviser: @w_Machine_cc-->

| 分类 | Sample名称 | 语言 | 场景介绍 |
| -------- | -------- | -------- | -------- |
| 视频编解码 | [AVCodecSample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/BasicFeature/Media/AVCodec) | C/C++ | 使用AVCodec Kit（C/C++）完成视频编解码：支持硬件/软件/自动选择解码（含软解回退）、Surface/Buffer模式、OpenGL/Vulkan送显方式，支持相机流通过编码器Surface输入，编码输出H.264/H.265码流，同步、异步两种工作模式均覆盖。 |
| 音频编解码 | [AVCodecSample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/BasicFeature/Media/AVCodec) | C/C++ | 使用AVCodec Kit（C/C++）完成音频编解码：播放时将AAC、MP3、FLAC等音频码流解码为PCM，经AudioRenderer回调播放；录制时通过AudioCapturer采集PCM，并根据配置的采样率、声道数与码率等参数编码为AAC码流；同步、异步两种工作模式均覆盖。 |
| 媒体数据封装与解封装 | [AVCodecSample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/BasicFeature/Media/AVCodec) | C/C++ | 播放时解封装mp4、mkv、mpeg-ts等媒体文件，获取轨道信息与音视频sample；录制时将音视频编码输出封装为mp4、flv文件。 |
| 智能流畅倍速解码 | [AVCodecSample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/BasicFeature/Media/AVCodec) | C/C++ | 倍速播放（X2/X3）时启用感知自适应（ADAPTIVE）保帧策略，恢复X1时切回全量直通（FULL），温控告警时切换平滑定比（UNIFORM），演示高倍速播放时的解码降负载与功耗优化。 |
| 时域可分层编码 | [AVCodecSample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/BasicFeature/Media/AVCodec) | C/C++ | 演示时域可分层编码的输出回调处理，通过OH_MD_KEY_VIDEO_ENCODER_TEMPORAL_LAYER_ID获取时域层级信息，支持通过逐层丢弃码流实现帧率伸缩，从而达成可抗弱网传输的动态码率调节。 |
| ROI视频编码 | [ROISample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/AVCodec/ROISample) | C/C++ | 直播场景ROI编码：相机采集、OpenGL渲染、ROI区域提取与配置后编码并封装为mp4文件，覆盖NativeBuffer元数据配置、编码输入参数回调、Buffer帧数据三种ROI编码通路，并演示背景音乐添加、前后摄像头翻转等直播常用功能。 |
