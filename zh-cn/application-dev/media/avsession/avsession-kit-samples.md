---
kits: ["AVSession Kit / 音视频播控服务"]
description: "<!--RP2--><!--RP2End-->"
keywords: [<!--RP3--><!--RP3End-->]
doctype: guide
status: active
---

# AVSession Kit示例代码汇总
<!--Kit: AVSession Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @gcw_7KSyM10J; @devil_red-->
<!--Designer: @gcw_7KSyM10J-->
<!--Tester: @chenmingxi1_huawei-->
<!--Adviser: @w_Machine_cc-->

AVSession Kit提供音视频播控相关示例代码，覆盖本地媒体会话、媒体会话提供方、应用接入AVSession、媒体会话控制方、音频模板、通话设备切换等核心开发场景，帮助开发者快速定位示例代码。

| 场景分类 | Sample名称 | 语言 | 场景介绍 |
| -------- | -------- | -------- | -------- |
| 本地媒体会话 | [LocalAVSessionOverview](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/AVSession/LocalAVSession/LocalAVSessionOverview) | ArkTS | 演示通过AVSessionManager创建AVSession和AVSessionController对象，展示本地媒体会话提供方与控制方的交互过程。 |
| 媒体会话提供方 | [AVSessionProvider](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/AVSession/LocalAVSession/AVSessionProvider) | ArkTS | 演示音视频应用作为媒体会话提供方接入AVSession的完整流程，包括创建激活会话、设置元数据与播放状态、设置播放列表、设置启动Ability、发送自定义会话事件、注册固定播控命令与高级播控事件监听、获取自身控制器、歌词组件接入及资源释放。 |
| 媒体会话提供方 | [AVSessionProviderNative](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/AVSession/LocalAVSession/AVSessionProviderNative) | C/C++ | 使用OHAVSession C API实现媒体会话提供方，演示会话创建激活、OH_AVMetadataBuilder构造与销毁元数据、播放状态与播放位置更新、播控命令回调注册及会话资源释放。 |
| 应用接入AVSession | [AccessingAVSession](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/AVSession/LocalAVSession/AccessingAVSession) | ArkTS | 演示音视频应用接入AVSession的展示与控制场景，涵盖会话类型选择、元数据与歌词字段设置、进度条信息与媒体资源金标设置、播放状态设置、控制命令处理（快进快退、收藏、循环模式、进度条控制）、蓝牙按键适配及后台播放模式设置。 |
| 媒体会话控制方 | [AVSessionController](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/AVSession/LocalAVSession/AVSessionController) | ArkTS | 演示应用作为媒体会话控制方获取会话描述符、创建控制器、获取元数据与播放状态、监听媒体信息变化、查询有效命令、下发播控命令及资源释放。 |
| 音频模板 | [TemplateProvider](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/AVSession/TemplateProvider) | ArkTS | 演示媒体应用通过音频模板接入播控中心，包括创建音频模板实例、注册主标签查询等事件监听、同步用户信息及注销监听释放资源。 |
| 通话设备切换 | [SwitchCallDevices](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/AVSession/SwitchCallDevices) | ArkTS | 演示通过AVCastPicker和AVInputCastPicker组件实现通话输出设备与输入设备切换，涵盖创建voice_call类型会话、音频播放、默认样式与自定义样式实现、设备切换监听及会话销毁。 |
<!--RP1--><!--RP1End-->