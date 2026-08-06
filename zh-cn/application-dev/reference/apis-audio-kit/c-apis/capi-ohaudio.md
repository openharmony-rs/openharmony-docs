# OHAudio

## 概述

Provide the definition of the C interface for the audio module.

**起始版本：** 12
## 文件汇总

| 名称 | 描述 |
| -- | -- |
| [native_audio_device_base.h](capi-native-audio-device-base-h.md) | 定义音频设备参数的类型以及获取每个设备参数的接口。 |
| [native_audio_common.h](capi-native-audio-common-h.md) | 声明音频公共基础数据结构。<br>定义音频接口的公共返回值的类型。 |
| [native_audiostreambuilder.h](capi-native-audiostreambuilder-h.md) | Declare audio stream builder related interfaces. |
| [native_audio_session_base.h](capi-native-audio-session-base-h.md) | 声明音频会话基础数据结构。 |
| [native_audio_accessory_common.h](capi-native-audio-accessory-common-h.md) | Declare common types for external audio accessory device interfaces. |
| [native_audiostream_base.h](capi-native-audiostream-base-h.md) | 声明OHAudio基础的数据结构。 |
| [native_audio_manager.h](capi-native-audio-manager-h.md) | 声明音频管理相关的接口。 |
| [native_audio_session_manager.h](capi-native-audio-session-manager-h.md) | 声明音频会话管理相关的接口。<br>包含创建音频会话管理器、激活/停用音频会话、检查音频会话是否已激活，以及监听音频会话停用事件。 |
| [native_audio_volume_manager.h](capi-native-audio-volume-manager-h.md) | 声明音频音量管理器接口。<br>该文件接口用于创建AudioVolumeManager。 |
| [native_audio_stream_manager.h](capi-native-audio-stream-manager-h.md) | 声明音频流管理器相关的接口。<br>该文件接口用于创建AudioStreamManager以及音频流设置和管理。 |
| [native_audio_resource_manager.h](capi-native-audio-resource-manager-h.md) | 声明音频资源管理相关的接口。 |
| [native_audio_debugging_manager.h](capi-native-audio-debugging-manager-h.md) | Declare audio debugging manager related interfaces.The interfaces in this file are used for audio debugging, helping the developers toanalyze issues when implementing audio related functions more efficiently. |
| [native_audio_device_enhance_manager.h](capi-native-audio-device-enhance-manager-h.md) | 声明音频设备增强管理器相关接口。本文件中的接口用于获取OH_AudioDeviceEnhanceManager句柄，为应用或音频流切换输入输出设备，以及执行其他与音频设备或路由相关的增强功能。 |
| [native_audio_routing_manager.h](capi-native-audio-routing-manager-h.md) | 声明与音频路由管理器相关的接口。<br>包含用于创建audioRoutingManager，设备连接状态发生变化时的注册和注销功能，以及存储设备信息的指针数组的释放。 |
