# AVCodec Kit指南配套示例代码汇总

<!--Kit: AVCodec Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @rchdlee-->
<!--Designer: @dpy2650-->
<!--Tester: @cyakee; @baotianhao-->
<!--Adviser: @w_Machine_cc-->

AVCodec Kit开发指南配套的示例工程汇总如下，开发者可按开发场景获取对应示例代码参考。AVCodec Kit仅提供C接口，以下示例均为C/C++工程。

| 分类 | Sample名称 | 场景介绍 |
| -------- | -------- | -------- |
| 视频编解码 | [AVCodecSample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/BasicFeature/Media/AVCodec) | 使用AVCodec Kit（C/C++）完成视频编解码：播放器支持硬件/软件/自动选择解码（含软解回退）以及Surface、Buffer、OpenGL、Vulkan多种送显，录制时相机流经编码器Surface输入编码为H.264/H.265，同时覆盖异步与同步两种模式。 |
| 媒体数据封装与解封装 | [AVCodecSample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/BasicFeature/Media/AVCodec) | 播放时解封装mp4、mkv、mpeg-ts等媒体文件，获取轨道信息与音视频sample；录制时将音视频编码输出封装为mp4、flv文件。 |
| 智能流畅倍速解码 | [AVCodecSample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/BasicFeature/Media/AVCodec) | 倍速播放（X2/X3）时启用感知自适应（ADAPTIVE）保帧策略，恢复X1时切回全量直通（FULL），温控告警时切换平滑定比（UNIFORM），演示高倍速播放下的解码降载与功耗控制。 |
| 时域可分层编码 | [AVCodecSample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/BasicFeature/Media/AVCodec) | 演示时域可分层编码的输出回调处理，通过OH_MD_KEY_VIDEO_ENCODER_TEMPORAL_LAYER_ID获取时域层级信息，支撑逐层丢弃码流的帧率伸缩与抗弱网传输。 |
| ROI视频编码 | [ROISample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/AVCodec/ROISample) | 直播场景ROI编码：相机采集、OpenGL渲染、ROI区域提取与配置后编码并封装为mp4文件，覆盖NativeBuffer元数据配置、编码输入参数回调、Buffer帧数据三种ROI编码通路，并演示背景音乐添加、前后摄像头翻转等直播常用功能。 |
