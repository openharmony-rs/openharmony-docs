# VideoDecoder
<!--Kit: AVCodec Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @zhanghongran-->
<!--Designer: @dpy2650-->
<!--Tester: @cyakee-->
<!--Adviser: @w_Machine_cc-->

## 模块简介

VideoDecoder 模块提供用于视频解码的 C API。开发者通过本模块可以创建视频解码器实例，配置解码参数，异步或同步处理解码输入输出，实现视频码流到原始视频帧的解码。

本模块提供的主要能力包括：

- **解码器创建与销毁**：根据 MIME 类型或解码器名称创建视频解码器实例，销毁解码器实例释放资源。
- **解码参数配置**：配置解码视频的描述信息（分辨率、帧率、像素格式等），设置输出 Surface，设置 DRM 解密配置。
- **异步回调机制**：注册回调函数，响应解码器生成的错误、流变化、输入缓冲区请求、输出缓冲区就绪等事件。
- **解码控制**：启动、停止、刷新、重置解码器，控制解码流程状态。
- **输入输出处理**：提交填充数据的输入缓冲区，释放或渲染输出缓冲区，支持 Buffer 模式和 Surface 模式。
- **同步模式支持**：查询并获取可用的输入输出缓冲区，实现同步解码流程。
- **动态参数设置**：在解码运行时设置解码器动态参数。
- **DRM 解密支持**：配置 DRM 会话，支持安全视频通路和非安全视频通路。

适用场景包括：播放本地视频文件、网络视频流解码、视频通话、视频会议、视频录制回放、受 DRM 保护的视频内容解码等需要将压缩视频码流解码为原始帧数据的场景。

本模块包含头文件 `native_avcodec_videodecoder.h`，提供结构体 `MediaKeySession`，以及创建、配置、控制、输入输出处理等函数。

## 关键术语

### 动态分辨率切换
仅硬件解码器支持的能力。当输入码流分辨率发生变化时触发OnStreamChanged回调，解码器自动适应新的分辨率。

### 动态切换surface
Surface模式下动态切换输出NativeWindow的能力。通过调用OH_VideoDecoder_SetSurface接口实现。

### 低时延解码
通过配置OH_MD_KEY_VIDEO_ENABLE_LOW_LATENCY使能的解码模式。若平台支持，视频解码器按照解码序输出帧，适用于低时延场景。

### SPS/PPS重传
解码器执行Flush/Reset/Stop后重新开始解码时，必须重新向解码器发送SPS/PPS码流参数集。确保解码器能正确解码后续帧。

### 解码器多路约束
多路解码器绑定同一NativeWindow时的约束。若1号解码器Destroy时2号解码器处于Running状态，会导致2号解码器画面卡住。需按正确顺序操作。

### 安全解码器创建
创建安全解码器的方式。使用OH_VideoDecoder_CreateByName函数，参数为解码器名称后拼接.secure（如"[CodecName].secure"），用于安全视频通路。

## 概述

VideoDecoder模块提供用于视频解码的函数，支持将视频码流解码为视频帧，帮助应用获取可播放或可处理的图像数据，适用于视频播放、视频编辑等需要将编码视频数据解码为图像帧的场景。

对应的开发指南及样例可参考[视频解码](../../media/avcodec/video-decoding.md)。

**系统能力：** SystemCapability.Multimedia.Media.VideoDecoder

**起始版本：** 9

## 文件汇总

| 名称 | 描述 |
| -- | -- |
| [native_avcodec_videodecoder.h](capi-native-avcodec-videodecoder-h.md) | 声明用于视频解码的Native API。 |
