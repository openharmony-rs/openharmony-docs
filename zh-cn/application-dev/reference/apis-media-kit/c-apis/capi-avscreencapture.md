# AVScreenCapture

## 概述

调用本模块下的接口，应用可以实现屏幕录制功能。支持录屏取码流和录屏写文件两种模式，适用于需要捕获屏幕音视频内容的各类场景，帮助开发者灵活获取屏幕数据并进行后续处理或保存为文件。典型使用场景包括：在线会议录制、游戏直播分享、教学演示视频制作、远程协作屏幕共享等。开发者可根据实际的开发需求，参考对应的开发指南及样例：- [使用AVScreenCapture录屏取码流](../../media/media/avscreencapture-c-basic-process.md)- [使用AVScreenCapture录屏写文件](../../media/media/using-avscreencapture-for-file.md)

**起始版本：** 10
## 文件汇总

| 名称 | 描述 |
| -- | -- |
| [native_avscreen_capture.h](capi-native-avscreen-capture-h.md) | 声明用于构造屏幕录制对象的API。支持录屏取码流和录屏存文件两种模式，可采集麦克风音频和内录音频数据，获取视频缓冲区数据，提供状态变更、数据处理、错误处理等回调机制，支持Surface模式录屏、内容过滤、隐私保护、捕获策略配置、捕获区域设置与高亮、多屏幕录制等功能，适用于需要在应用内实现屏幕录制、屏幕共享或直播推流等场景。 |
| [native_avscreen_capture_base.h](capi-native-avscreen-capture-base-h.md) | 声明用于运行屏幕录制相关的结构体、字符常量、枚举、变量和函数。屏幕录制通过配置参数设置录制模式与音视频信息，通过回调函数获取录制数据、状态变更和隐私保护事件通知。支持多种录制模式（主屏幕、指定屏幕、指定窗口）、音频源类型（麦克风、内录、指定应用音频）配置及隐私保护、内容过滤等功能，适用于需要捕获屏幕画面和音频数据的应用场景。详细设计逻辑请参见AVScreenCapture。 |
| [native_avscreen_capture_errors.h](capi-native-avscreen-capture-errors-h.md) | 声明屏幕录制接口调用的错误码，帮助开发者识别和处理屏幕录制中的各类异常情况，适用于屏幕录制故障排查和错误处理的开发场景。 |
