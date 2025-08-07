# OHAudio
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--SE: @caixuejiang; @hao-liangfei; @zhanganxiang-->
<!--TSE: @Filger-->

## 概述

提供音频模块C接口定义。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 10

## 文件汇总

| 名称 | 描述 |
| -- | -- |
| [native_audiocapturer.h](capi-native-audiocapturer-h.md) | 声明输入类型的音频流相关接口。 |
| [native_audio_manager.h](capi-native-audio-manager-h.md) | 声明音频管理相关的接口。 |
| [native_audio_resource_manager.h](capi-native-audio-resource-manager-h.md) | 声明音频资源管理相关的接口。 |
| [native_audio_routing_manager.h](capi-native-audio-routing-manager-h.md) | 声明与音频路由管理器相关的接口。<br> 包含用于创建audioRoutingManager，设备连接状态发生变化时的注册和注销功能，以及存储设备信息的指针数组的释放。 |
| [native_audio_session_manager.h](capi-native-audio-session-manager-h.md) | 声明音频会话管理相关的接口。<br> 包含创建音频会话管理器、激活/停用音频会话、检查音频会话是否已激活，以及监听音频会话停用事件。 |
| [native_audio_stream_manager.h](capi-native-audio-stream-manager-h.md) | 声明与音频流管理器相关的接口。<br> 该文件接口用于创建audioStreamManager以及音频流设置和管理。 |
| [native_audio_volume_manager.h](capi-native-audio-volume-manager-h.md) | 声明音频音量管理器接口。该文件接口用于创建AudioVolumeManager。 |
| [native_audiorenderer.h](capi-native-audiorenderer-h.md) | 声明输出类型的音频流相关接口。 |
| [native_audio_common.h](capi-native-audio-common-h.md) | 声明音频公共基础数据结构。<br> 定义音频接口的公共返回值的类型。 |
| [native_audio_device_base.h](capi-native-audio-device-base-h.md) | 定义音频设备参数的类型以及获取每个设备参数的接口。 |
| [native_audiostream_base.h](capi-native-audiostream-base-h.md) | 声明OHAudio基础的数据结构。 |
| [native_audiostreambuilder.h](capi-native-audiostreambuilder-h.md) | 声明音频流构造器相关接口。<br> 包含构造和销毁构造器，设置音频流属性，回调等相关接口。 |
