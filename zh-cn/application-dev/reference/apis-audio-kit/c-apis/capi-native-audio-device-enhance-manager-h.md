# native_audio_device_enhance_manager.h

## 概述

声明音频设备增强管理器相关接口。本文件中的接口用于获取OH_AudioDeviceEnhanceManager句柄，为应用或音频流切换输入输出设备，以及执行其他与音频设备或路由相关的增强功能。

**库：** libohaudio.so

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 26.0.0

**相关模块：** [OHAudio](capi-ohaudio.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_AudioDeviceEnhanceManager](capi-ohaudio-oh-audiodeviceenhancemanager.md) | OH_AudioDeviceEnhanceManager | 定义音频设备增强管理器的句柄类型，音频设备增强管理功能，用于应用级音频设备选择及流维度音频设备选择。 |

### 函数

| 名称 | 描述 |
| -- | -- |
| [OH_AudioCommon_Result OH_AudioManager_GetAudioDeviceEnhanceManager(OH_AudioDeviceEnhanceManager **audioDeviceEnhanceManager)](#oh_audiomanager_getaudiodeviceenhancemanager) | 获取音频设备增强管理器句柄。 |
| [OH_AudioCommon_Result OH_AudioDeviceEnhanceManager_IsEnhancedRoutingSupported(OH_AudioDeviceEnhanceManager *audioDeviceEnhanceManager, bool *supported)](#oh_audiodeviceenhancemanager_isenhancedroutingsupported) | 查询系统是否支持当前管理器提供的增强路由功能。 |
| [OH_AudioCommon_Result OH_AudioDeviceEnhanceManager_SelectOutputDevice(OH_AudioDeviceEnhanceManager *audioDeviceEnhanceManager, OH_AudioDeviceDescriptor *deviceDescriptor)](#oh_audiodeviceenhancemanager_selectoutputdevice) | 为应用选择输出设备。 |
| [OH_AudioCommon_Result OH_AudioDeviceEnhanceManager_SelectInputDevice(OH_AudioDeviceEnhanceManager *audioDeviceEnhanceManager, OH_AudioDeviceDescriptor *deviceDescriptor)](#oh_audiodeviceenhancemanager_selectinputdevice) | 为应用选择输入设备。 |
| [OH_AudioCommon_Result OH_AudioDeviceEnhanceManager_SelectOutputDeviceForAudioRenderer(OH_AudioDeviceEnhanceManager *audioDeviceEnhanceManager, OH_AudioRenderer *renderer, OH_AudioDeviceDescriptor *deviceDescriptor)](#oh_audiodeviceenhancemanager_selectoutputdeviceforaudiorenderer) | 为指定音频播放流选择输出设备。 |
| [OH_AudioCommon_Result OH_AudioDeviceEnhanceManager_SelectInputDeviceForAudioCapturer(OH_AudioDeviceEnhanceManager *audioDeviceEnhanceManager, OH_AudioCapturer *capturer, OH_AudioDeviceDescriptor *deviceDescriptor)](#oh_audiodeviceenhancemanager_selectinputdeviceforaudiocapturer) | 为指定音频录制流选择输入设备。 |

## 函数说明

### OH_AudioManager_GetAudioDeviceEnhanceManager()

```c
OH_AudioCommon_Result OH_AudioManager_GetAudioDeviceEnhanceManager(OH_AudioDeviceEnhanceManager **audioDeviceEnhanceManager)
```

**描述**

获取音频设备增强管理器句柄。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioDeviceEnhanceManager](capi-ohaudio-oh-audiodeviceenhancemanager.md) **audioDeviceEnhanceManager | 指向OH_AudioDeviceEnhanceManager句柄的指针，用于接收函数返回的管理器实例。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | AUDIOCOMMON_RESULT_SUCCESS: 函数执行成功。<br>     <br>AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM: 参数audioDeviceEnhanceManager为nullptr。 |

### OH_AudioDeviceEnhanceManager_IsEnhancedRoutingSupported()

```c
OH_AudioCommon_Result OH_AudioDeviceEnhanceManager_IsEnhancedRoutingSupported(OH_AudioDeviceEnhanceManager *audioDeviceEnhanceManager, bool *supported)
```

**描述**

查询系统是否支持当前管理器提供的增强路由功能。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioDeviceEnhanceManager](capi-ohaudio-oh-audiodeviceenhancemanager.md) *audioDeviceEnhanceManager | 通过[OH_AudioManager_GetAudioDeviceEnhanceManager](capi-native-audio-device-enhance-manager-h.md#oh_audiomanager_getaudiodeviceenhancemanager)获取的音频设备增强管理器句柄。 |
| bool *supported | 查询结果，即系统是否支持音频设备增强管理功能。true表示支持，false表示不支持。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | AUDIOCOMMON_RESULT_SUCCESS: 函数执行成功。<br>     <br>AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM: 参数audioDeviceEnhanceManager或supported为nullptr。<br>     <br>AUDIOCOMMON_RESULT_ERROR_SYSTEM: 音频客户端调用音频服务失败或系统错误。 |

### OH_AudioDeviceEnhanceManager_SelectOutputDevice()

```c
OH_AudioCommon_Result OH_AudioDeviceEnhanceManager_SelectOutputDevice(OH_AudioDeviceEnhanceManager *audioDeviceEnhanceManager, OH_AudioDeviceDescriptor *deviceDescriptor)
```

**描述**

为应用选择输出设备。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioDeviceEnhanceManager](capi-ohaudio-oh-audiodeviceenhancemanager.md) *audioDeviceEnhanceManager | 通过[OH_AudioManager_GetAudioDeviceEnhanceManager](capi-native-audio-device-enhance-manager-h.md#oh_audiomanager_getaudiodeviceenhancemanager)获取的音频设备增强管理器句柄。 |
| [OH_AudioDeviceDescriptor](capi-ohaudio-oh-audiodevicedescriptor.md) *deviceDescriptor | 目标设备。可用设备需从{@link OH_AudioRoutingManager_GetAvailableDevices}返回的设备列表中获取。传入nullptr时，系统会清除上一次选择，并为应用恢复默认输出设备。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | AUDIOCOMMON_RESULT_SUCCESS: 函数执行成功。<br>     <br>AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM: 参数audioDeviceEnhanceManager为nullptr，<br>     <br>参数deviceDescriptor无效或指定输出设备已离线。<br>     <br>AUDIOCOMMON_RESULT_ERROR_SYSTEM: 音频客户端调用音频服务失败或系统错误。 |

### OH_AudioDeviceEnhanceManager_SelectInputDevice()

```c
OH_AudioCommon_Result OH_AudioDeviceEnhanceManager_SelectInputDevice(OH_AudioDeviceEnhanceManager *audioDeviceEnhanceManager, OH_AudioDeviceDescriptor *deviceDescriptor)
```

**描述**

为应用选择输入设备。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioDeviceEnhanceManager](capi-ohaudio-oh-audiodeviceenhancemanager.md) *audioDeviceEnhanceManager | 通过[OH_AudioManager_GetAudioDeviceEnhanceManager](capi-native-audio-device-enhance-manager-h.md#oh_audiomanager_getaudiodeviceenhancemanager)获取的音频设备增强管理器句柄。 |
| [OH_AudioDeviceDescriptor](capi-ohaudio-oh-audiodevicedescriptor.md) *deviceDescriptor | 目标设备。可用设备需从{@link OH_AudioRoutingManager_GetAvailableDevices}返回的设备列表中获取。传入nullptr时，系统会清除上一次选择，并为应用恢复默认输入设备。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | AUDIOCOMMON_RESULT_SUCCESS: 函数执行成功。<br>     <br>AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM: 参数audioDeviceEnhanceManager为nullptr，<br>     <br>参数deviceDescriptor无效或指定输入设备已离线。<br>     <br>AUDIOCOMMON_RESULT_ERROR_SYSTEM: 音频客户端调用音频服务失败或系统错误。 |

### OH_AudioDeviceEnhanceManager_SelectOutputDeviceForAudioRenderer()

```c
OH_AudioCommon_Result OH_AudioDeviceEnhanceManager_SelectOutputDeviceForAudioRenderer(OH_AudioDeviceEnhanceManager *audioDeviceEnhanceManager, OH_AudioRenderer *renderer, OH_AudioDeviceDescriptor *deviceDescriptor)
```

**描述**

为指定音频播放流选择输出设备。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioDeviceEnhanceManager](capi-ohaudio-oh-audiodeviceenhancemanager.md) *audioDeviceEnhanceManager | 通过[OH_AudioManager_GetAudioDeviceEnhanceManager](capi-native-audio-device-enhance-manager-h.md#oh_audiomanager_getaudiodeviceenhancemanager)获取的音频设备增强管理器句柄。 |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorendererstruct.md) *renderer | 通过{@link OH_AudioStreamBuilder_GenerateRenderer}创建的音频播放流实例。 |
| [OH_AudioDeviceDescriptor](capi-ohaudio-oh-audiodevicedescriptor.md) *deviceDescriptor | 目标设备。可用设备需从{@link OH_AudioRoutingManager_GetAvailableDevices}返回的设备列表中获取。传入nullptr时，系统会清除上一次选择，并为该音频播放流恢复默认输出设备。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | AUDIOCOMMON_RESULT_SUCCESS: 函数执行成功。<br>     <br>AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM: 参数audioDeviceEnhanceManager或renderer为nullptr，<br>     <br>参数deviceDescriptor无效或指定输出设备已离线。<br>     <br>AUDIOCOMMON_RESULT_ERROR_SYSTEM: 音频客户端调用音频服务失败或系统错误。 |

### OH_AudioDeviceEnhanceManager_SelectInputDeviceForAudioCapturer()

```c
OH_AudioCommon_Result OH_AudioDeviceEnhanceManager_SelectInputDeviceForAudioCapturer(OH_AudioDeviceEnhanceManager *audioDeviceEnhanceManager, OH_AudioCapturer *capturer, OH_AudioDeviceDescriptor *deviceDescriptor)
```

**描述**

为指定音频录制流选择输入设备。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioDeviceEnhanceManager](capi-ohaudio-oh-audiodeviceenhancemanager.md) *audioDeviceEnhanceManager | 通过[OH_AudioManager_GetAudioDeviceEnhanceManager](capi-native-audio-device-enhance-manager-h.md#oh_audiomanager_getaudiodeviceenhancemanager)获取的音频设备增强管理器句柄。 |
| [OH_AudioCapturer](capi-ohaudio-oh-audiocapturerstruct.md) *capturer | 通过{@link OH_AudioStreamBuilder_GenerateCapturer}创建的音频录制流实例。 |
| [OH_AudioDeviceDescriptor](capi-ohaudio-oh-audiodevicedescriptor.md) *deviceDescriptor | 目标设备。可用设备需从{@link OH_AudioRoutingManager_GetAvailableDevices}返回的设备列表中获取。传入nullptr时，系统会清除上一次选择，并为该音频录制流恢复默认输入设备。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | AUDIOCOMMON_RESULT_SUCCESS: 函数执行成功。<br>     <br>AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM: 参数audioDeviceEnhanceManager或capturer为nullptr，<br>     <br>参数deviceDescriptor无效或指定输入设备已离线。<br>     <br>AUDIOCOMMON_RESULT_ERROR_SYSTEM: 音频客户端调用音频服务失败或系统错误。 |


