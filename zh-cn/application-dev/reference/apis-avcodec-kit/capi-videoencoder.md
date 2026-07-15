# VideoEncoder
<!--Kit: AVCodec Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @zhanghongran-->
<!--Designer: @dpy2650-->
<!--Tester: @cyakee-->
<!--Adviser: @w_Machine_cc-->

## 模块简介

VideoEncoder 模块提供用于视频编码的 C API。开发者通过本模块可以创建视频编码器实例，配置编码参数，异步或同步处理编码输入输出，实现原始视频帧到压缩视频码流的编码。

本模块提供的主要能力包括：

- **编码器创建与销毁**：根据 MIME 类型或编码器名称创建视频编码器实例，支持创建带前处理功能的主编码器和副编码器，实现一入二出双路编码，销毁编码器实例释放资源。
- **编码参数配置**：配置编码视频的描述信息（分辨率、帧率、像素格式、码率、档次等），支持分层编码、长期参考帧、B 帧等特性配置。
- **异步回调机制**：注册回调函数，响应编码器生成的错误、流变化、输入缓冲区请求、输出缓冲区就绪等事件。
- **随帧参数配置**：在 Surface 模式下，通过回调设置帧级编码参数（如帧级 QPMin/QPMax、LTR 参考帧）。
- **编码控制**：启动、停止、刷新、重置编码器，控制编码流程状态，通知输入流结束。
- **输入输出处理**：提交填充数据的输入缓冲区，释放输出缓冲区，支持 Buffer 模式和 Surface 模式。
- **同步模式支持**：查询并获取可用的输入输出缓冲区，实现同步编码流程。
- **动态参数设置**：在编码运行时设置编码器动态参数（如请求 I 帧、量化参数范围）。
- **前处理与双路编码**：支持视频编码前处理（降采样、裁剪），支持从主编码器创建副编码器实现一入二出双路编码。

适用场景包括：视频录制、视频直播推流、视频会议、视频通话、屏幕录制等需要将原始视频帧编码为压缩码流的场景。

本模块包含头文件 `native_avcodec_videoencoder.h`，提供函数指针类型 `OH_VideoEncoder_OnNeedInputParameter`，枚举 `OH_VideoEncodeBitrateMode`，以及创建、配置、控制、输入输出处理等函数。

## 关键术语

### 历史帧重复编码
视频编码器的特殊能力。在码流中断或需要时自动重复发送历史编码帧，通过OH_MD_KEY_VIDEO_ENCODER_REPEAT_PREVIOUS_FRAME_AFTER触发重复发送，OH_MD_KEY_VIDEO_ENCODER_REPEAT_PREVIOUS_MAX_COUNT限制最大重复次数。

### 编码器输入描述 (GetInputDescription)
编码器输入缓冲区的元数据信息。包含宽跨距、高跨距、像素格式等，通过OH_VideoEncoder_GetInputDescription获取，用于Buffer模式下正确处理内存对齐的图像数据。

### 随帧参数通路 (Per-Frame Parameter Pathway)
Surface模式下逐帧配置编码参数的回调机制。通过OH_VideoEncoder_RegisterParameterCallback注册回调，在每帧编码前配置随帧参数，通过OH_VideoEncoder_PushInputParameter推送生效，适用于IDR请求、LTR标记等场景。

## 概述

VideoEncoder模块提供用于视频编码的接口，可用于将原始视频数据编码为指定格式的视频码流，适用于视频录制、视频处理、实时通信等需要压缩视频数据的场景，帮助开发者降低数据存储和传输成本。

开发者可根据实际的开发需求，参考对应的开发指南及样例：

- [视频编码](../../media/avcodec/video-encoding.md)
- [时域可分层视频编码](../../media/avcodec/video-encoding-temporal-scalability.md)

**系统能力：** SystemCapability.Multimedia.Media.VideoEncoder

**起始版本：** 9

## 文件汇总

| 名称 | 描述 |
| -- | -- |
| [native_avcodec_videoencoder.h](capi-native-avcodec-videoencoder-h.md) | 声明用于视频编码的接口。 |
