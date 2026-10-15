# native_audio_device_enhance_manager.h

## 概述

本文件提供音频设备管理增强功能的接口。 <br>相比通用的音频设备管理接口文件仅提供查询设备状态的能力， 本文件提供的接口可支持按应用或按音频流切换输入和输出设备。 适用于需要在应用内实现应用级或流级音频设备切换的场景，例如多音频应用同时运行时的设备管理、 专业音频应用需要指定特定设备、或者用户需要在应用内自定义音频设备选择等场景。 通过精细化控制音频路由，可以提升应用的音频管理灵活性和用户体验。 <br>但这种能力对系统音频底层架构存在依赖，并非所有设备都能支持，因此在使用前建议先调用能力查询接口进行查询。

**库：** libohaudio.so

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 26.0.0

**相关模块：** [OHAudio](capi-ohaudio.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_AudioDeviceEnhanceManager](capi-ohaudio-oh-audiodeviceenhancemanager.md) | OH_AudioDeviceEnhanceManager | 声明音频设备增强管理结构体，该结构体用于调用应用级音频设备选择和音频流级别音频设备选择功能接口。 |

### 函数

| 名称 | 描述 |
| -- | -- |
| [OH_AudioCommon_Result OH_AudioManager_GetAudioDeviceEnhanceManager(OH_AudioDeviceEnhanceManager **audioDeviceEnhanceManager)](#oh_audiomanager_getaudiodeviceenhancemanager) | 获取音频设备增强管理器实例，该实例为单例，用于调用音频设备增强功能接口。 |
| [OH_AudioCommon_Result OH_AudioDeviceEnhanceManager_IsEnhancedRoutingSupported(OH_AudioDeviceEnhanceManager *audioDeviceEnhanceManager, bool *supported)](#oh_audiodeviceenhancemanager_isenhancedroutingsupported) | 查询系统是否支持当前管理器提供的增强路由功能。 |
| [OH_AudioCommon_Result OH_AudioDeviceEnhanceManager_SelectOutputDevice(OH_AudioDeviceEnhanceManager *audioDeviceEnhanceManager, OH_AudioDeviceDescriptor *deviceDescriptor)](#oh_audiodeviceenhancemanager_selectoutputdevice) | 为当前应用选择输出设备。 |
| [OH_AudioCommon_Result OH_AudioDeviceEnhanceManager_SelectInputDevice(OH_AudioDeviceEnhanceManager *audioDeviceEnhanceManager, OH_AudioDeviceDescriptor *deviceDescriptor)](#oh_audiodeviceenhancemanager_selectinputdevice) | 为当前应用选择输入设备。 |
| [OH_AudioCommon_Result OH_AudioDeviceEnhanceManager_SelectOutputDeviceForAudioRenderer(OH_AudioDeviceEnhanceManager *audioDeviceEnhanceManager, OH_AudioRenderer *renderer, OH_AudioDeviceDescriptor *deviceDescriptor)](#oh_audiodeviceenhancemanager_selectoutputdeviceforaudiorenderer) | 为指定音频播放流选择输出设备。 |
| [OH_AudioCommon_Result OH_AudioDeviceEnhanceManager_SelectInputDeviceForAudioCapturer(OH_AudioDeviceEnhanceManager *audioDeviceEnhanceManager, OH_AudioCapturer *capturer, OH_AudioDeviceDescriptor *deviceDescriptor)](#oh_audiodeviceenhancemanager_selectinputdeviceforaudiocapturer) | 为指定音频录制流选择输入设备。 |

## 函数说明

### OH_AudioManager_GetAudioDeviceEnhanceManager()

```c
OH_AudioCommon_Result OH_AudioManager_GetAudioDeviceEnhanceManager(OH_AudioDeviceEnhanceManager **audioDeviceEnhanceManager)
```

**描述：**

获取音频设备增强管理器实例，该实例为单例，用于调用音频设备增强功能接口。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioDeviceEnhanceManager](capi-ohaudio-oh-audiodeviceenhancemanager.md) **audioDeviceEnhanceManager | [out] 指向OH_AudioDeviceEnhanceManager实例的指针，用于接收函数返回的管理器实例。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| OH_AudioCommon_Result | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 函数执行成功。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) 参数audioDeviceEnhanceManager为空指针。</li> </ul> |

### OH_AudioDeviceEnhanceManager_IsEnhancedRoutingSupported()

```c
OH_AudioCommon_Result OH_AudioDeviceEnhanceManager_IsEnhancedRoutingSupported(OH_AudioDeviceEnhanceManager *audioDeviceEnhanceManager, bool *supported)
```

**描述：**

查询系统是否支持当前管理器提供的增强路由功能。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioDeviceEnhanceManager](capi-ohaudio-oh-audiodeviceenhancemanager.md) *audioDeviceEnhanceManager | [in] 通过[OH_AudioManager_GetAudioDeviceEnhanceManager](capi-native-audio-device-enhance-manager-h.md#oh_audiomanager_getaudiodeviceenhancemanager) 获取的音频设备增强管理器实例。 |
| bool *supported | [out] 查询结果，即系统是否支持音频设备增强管理功能。true表示支持，false表示不支持。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| OH_AudioCommon_Result | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 函数执行成功。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) 参数audioDeviceEnhanceManager或supported为空指针。</li> <li>[AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) 音频客户端调用音频服务失败或系统错误。</li> </ul> |

### OH_AudioDeviceEnhanceManager_SelectOutputDevice()

```c
OH_AudioCommon_Result OH_AudioDeviceEnhanceManager_SelectOutputDevice(OH_AudioDeviceEnhanceManager *audioDeviceEnhanceManager, OH_AudioDeviceDescriptor *deviceDescriptor)
```

**描述：**

为当前应用选择输出设备。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioDeviceEnhanceManager](capi-ohaudio-oh-audiodeviceenhancemanager.md) *audioDeviceEnhanceManager | [in] 通过[OH_AudioManager_GetAudioDeviceEnhanceManager](capi-native-audio-device-enhance-manager-h.md#oh_audiomanager_getaudiodeviceenhancemanager) 获取的音频设备增强管理器实例。 |
| [OH_AudioDeviceDescriptor](capi-ohaudio-oh-audiodevicedescriptor.md) *deviceDescriptor | [in] 选择的音频输出设备。可用设备需从[OH_AudioRoutingManager_GetAvailableDevices](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_getavailabledevices) 返回的设备列表中获取。传入空指针时，系统会清除上一次选择，并为应用恢复默认输出设备。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| OH_AudioCommon_Result | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 函数执行成功。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result)参数audioDeviceEnhanceManager为空指针，参数deviceDescriptor无效或指定输出设备已离线。</li> <li>[AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) 音频客户端调用音频服务失败或系统错误。</li> </ul> |

### OH_AudioDeviceEnhanceManager_SelectInputDevice()

```c
OH_AudioCommon_Result OH_AudioDeviceEnhanceManager_SelectInputDevice(OH_AudioDeviceEnhanceManager *audioDeviceEnhanceManager, OH_AudioDeviceDescriptor *deviceDescriptor)
```

**描述：**

为当前应用选择输入设备。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioDeviceEnhanceManager](capi-ohaudio-oh-audiodeviceenhancemanager.md) *audioDeviceEnhanceManager | [in] 通过[OH_AudioManager_GetAudioDeviceEnhanceManager](capi-native-audio-device-enhance-manager-h.md#oh_audiomanager_getaudiodeviceenhancemanager) 获取的音频设备增强管理器实例。 |
| [OH_AudioDeviceDescriptor](capi-ohaudio-oh-audiodevicedescriptor.md) *deviceDescriptor | [in] 选择的音频输入设备。可用设备需从[OH_AudioRoutingManager_GetAvailableDevices](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_getavailabledevices) 返回的设备列表中获取。传入空指针时，系统会清除上一次选择，并为应用恢复默认输入设备。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| OH_AudioCommon_Result | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 函数执行成功。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result)参数audioDeviceEnhanceManager为空指针，参数deviceDescriptor无效或指定输入设备已离线。</li> <li>[AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) 音频客户端调用音频服务失败或系统错误。</li> </ul> |

### OH_AudioDeviceEnhanceManager_SelectOutputDeviceForAudioRenderer()

```c
OH_AudioCommon_Result OH_AudioDeviceEnhanceManager_SelectOutputDeviceForAudioRenderer(OH_AudioDeviceEnhanceManager *audioDeviceEnhanceManager, OH_AudioRenderer *renderer, OH_AudioDeviceDescriptor *deviceDescriptor)
```

**描述：**

为指定音频播放流选择输出设备。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioDeviceEnhanceManager](capi-ohaudio-oh-audiodeviceenhancemanager.md) *audioDeviceEnhanceManager | [in] 通过[OH_AudioManager_GetAudioDeviceEnhanceManager](capi-native-audio-device-enhance-manager-h.md#oh_audiomanager_getaudiodeviceenhancemanager) 获取的音频设备增强管理器实例。 |
| OH_AudioRenderer *renderer | [in] 目标音频播放流，是通过[OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer)创建的音频播放流实例。 |
| [OH_AudioDeviceDescriptor](capi-ohaudio-oh-audiodevicedescriptor.md) *deviceDescriptor | [in] 选择的音频输出设备。可用设备需从[OH_AudioRoutingManager_GetAvailableDevices](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_getavailabledevices) 返回的设备列表中获取。传入空指针时， 系统会清除上一次选择，并为该音频播放流恢复默认输出设备。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| OH_AudioCommon_Result | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 函数执行成功。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result)参数audioDeviceEnhanceManager或renderer为空指针，参数deviceDescriptor无效或指定输出设备已离线。</li> <li>[AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) 音频客户端调用音频服务失败或系统错误。</li> </ul> |

### OH_AudioDeviceEnhanceManager_SelectInputDeviceForAudioCapturer()

```c
OH_AudioCommon_Result OH_AudioDeviceEnhanceManager_SelectInputDeviceForAudioCapturer(OH_AudioDeviceEnhanceManager *audioDeviceEnhanceManager, OH_AudioCapturer *capturer, OH_AudioDeviceDescriptor *deviceDescriptor)
```

**描述：**

为指定音频录制流选择输入设备。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioDeviceEnhanceManager](capi-ohaudio-oh-audiodeviceenhancemanager.md) *audioDeviceEnhanceManager | [in] 通过[OH_AudioManager_GetAudioDeviceEnhanceManager](capi-native-audio-device-enhance-manager-h.md#oh_audiomanager_getaudiodeviceenhancemanager) 获取的音频设备增强管理器实例。 |
| OH_AudioCapturer *capturer | [in] 目标音频录制流，是通过[OH_AudioStreamBuilder_GenerateCapturer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generatecapturer)创建的音频录制流实例。 |
| [OH_AudioDeviceDescriptor](capi-ohaudio-oh-audiodevicedescriptor.md) *deviceDescriptor | [in] 选择的音频输入设备。可用设备需从[OH_AudioRoutingManager_GetAvailableDevices](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_getavailabledevices) 返回的设备列表中获取。传入空指针时， 系统会清除上一次选择，并为该音频录制流恢复默认输入设备。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| OH_AudioCommon_Result | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 函数执行成功。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result)参数audioDeviceEnhanceManager或capturer为空指针，参数deviceDescriptor无效或指定输入设备已离线。</li> <li>[AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) 音频客户端调用音频服务失败或系统错误。</li> </ul> |


