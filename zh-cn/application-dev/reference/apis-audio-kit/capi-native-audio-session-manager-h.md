# native_audio_session_manager.h
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @caixuejiang; @hao-liangfei; @zhanganxiang-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

## 概述

声明音频会话管理相关的接口。<br> 包含创建音频会话管理器、激活/停用音频会话、检查音频会话是否已激活，以及监听音频会话停用事件。

**引用文件：** <ohaudio/native_audio_session_manager.h>

**库：** libohaudio.so

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 12

**相关模块：** [OHAudio](capi-ohaudio.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_AudioSession_Strategy](capi-ohaudio-oh-audiosession-strategy.md) | OH_AudioSession_Strategy | 音频会话策略。 |
| [OH_AudioSession_DeactivatedEvent](capi-ohaudio-oh-audiosession-deactivatedevent.md) | OH_AudioSession_DeactivatedEvent | 音频会话已停用事件。 |
| [OH_AudioSession_StateChangedEvent](capi-ohaudio-oh-audiosession-statechangedevent.md) | OH_AudioSession_StateChangedEvent | 音频会话状态变更事件。 |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) | OH_AudioSessionManager | 声明音频会话管理器。<br> 用于管理音频会话相关功能。 |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_AudioSession_ConcurrencyMode](#oh_audiosession_concurrencymode) | OH_AudioSession_ConcurrencyMode | 音频并发模式。 |
| [OH_AudioSession_Scene](#oh_audiosession_scene) | OH_AudioSession_Scene | 音频会话场景。 |
| [OH_AudioSession_StateChangeHint](#oh_audiosession_statechangehint) | OH_AudioSession_StateChangeHint | 音频会话状态变更的提示信息。 |
| [OH_AudioSession_OutputDeviceChangeRecommendedAction](#oh_audiosession_outputdevicechangerecommendedaction) | OH_AudioSession_OutputDeviceChangeRecommendedAction | 输出设备变更后推荐的操作。 |
| [OH_AudioSession_DeactivatedReason](#oh_audiosession_deactivatedreason) | OH_AudioSession_DeactivatedReason | 音频会话停用原因。 |
| [OH_AudioSession_BluetoothAndNearlinkPreferredRecordCategory](#oh_audiosession_bluetoothandnearlinkpreferredrecordcategory) | OH_AudioSession_BluetoothAndNearlinkPreferredRecordCategory | 在使用蓝牙或星闪进行录音时，应用程序的设备偏好分类。 |

### 函数

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [typedef void (\*OH_AudioSession_StateChangedCallback)(OH_AudioSession_StateChangedEvent event)](#oh_audiosession_statechangedcallback) | OH_AudioSession_StateChangedCallback | 这个函数指针将指向用于监听音频会话状态变更事件的回调函数。 |
| [typedef void (\*OH_AudioSession_AvailableDeviceChangedCallback)(OH_AudioDevice_ChangeType type, OH_AudioDeviceDescriptorArray *audioDeviceDescriptorArray)](#oh_audiosession_availabledevicechangedcallback) | OH_AudioSession_AvailableDeviceChangedCallback | 此函数指针将指向用于返回变化的音频设备描述符的回调函数，可能会返回多个音频设备描述符。 |
| [typedef void (\*OH_AudioSession_CurrentInputDeviceChangedCallback)(OH_AudioDeviceDescriptorArray *devices, OH_AudioStream_DeviceChangeReason changeReason)](#oh_audiosession_currentinputdevicechangedcallback) | OH_AudioSession_CurrentInputDeviceChangedCallback | 这个函数指针将指向用于监听当前输入设备变化事件的回调函数。 |
| [typedef void (\*OH_AudioSession_CurrentOutputDeviceChangedCallback)(OH_AudioDeviceDescriptorArray *devices, OH_AudioStream_DeviceChangeReason changeReason, OH_AudioSession_OutputDeviceChangeRecommendedAction recommendedAction)](#oh_audiosession_currentoutputdevicechangedcallback) | OH_AudioSession_CurrentOutputDeviceChangedCallback | 这个函数指针将指向用于监听当前输出设备变化事件的回调函数。 |
| [typedef int32_t (\*OH_AudioSession_DeactivatedCallback)(OH_AudioSession_DeactivatedEvent event)](#oh_audiosession_deactivatedcallback) | OH_AudioSession_DeactivatedCallback | 这个函数指针将指向用于监听音频会话停用事件的回调函数。 |
| [OH_AudioCommon_Result OH_AudioManager_GetAudioSessionManager(OH_AudioSessionManager **audioSessionManager)](#oh_audiomanager_getaudiosessionmanager) | - | 获取音频会话管理器。使用音频会话管理器相关功能，首先需要获取音频会话管理器实例。 |
| [OH_AudioCommon_Result OH_AudioSessionManager_ActivateAudioSession(OH_AudioSessionManager *audioSessionManager, const OH_AudioSession_Strategy *strategy)](#oh_audiosessionmanager_activateaudiosession) | - | 激活音频会话。 |
| [OH_AudioCommon_Result OH_AudioSessionManager_DeactivateAudioSession(OH_AudioSessionManager *audioSessionManager)](#oh_audiosessionmanager_deactivateaudiosession) | - | 停用音频会话。 |
| [bool OH_AudioSessionManager_IsAudioSessionActivated(OH_AudioSessionManager *audioSessionManager)](#oh_audiosessionmanager_isaudiosessionactivated) | - | 检查音频会话是否已激活。 |
| [OH_AudioCommon_Result OH_AudioSessionManager_RegisterSessionDeactivatedCallback(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_DeactivatedCallback callback)](#oh_audiosessionmanager_registersessiondeactivatedcallback) | - | 注册音频会话停用事件回调。 |
| [OH_AudioCommon_Result OH_AudioSessionManager_UnregisterSessionDeactivatedCallback(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_DeactivatedCallback callback)](#oh_audiosessionmanager_unregistersessiondeactivatedcallback) | - | 取消注册音频会话停用事件回调。 |
| [OH_AudioCommon_Result OH_AudioSessionManager_SetScene(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_Scene scene)](#oh_audiosessionmanager_setscene) | - | 设置音频会话场景参数。 |
| [OH_AudioCommon_Result OH_AudioSessionManager_RegisterStateChangeCallback(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_StateChangedCallback callback)](#oh_audiosessionmanager_registerstatechangecallback) | - | 注册音频会话状态变更事件回调。 |
| [OH_AudioCommon_Result OH_AudioSessionManager_UnregisterStateChangeCallback(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_StateChangedCallback callback)](#oh_audiosessionmanager_unregisterstatechangecallback) | - | 取消音频会话状态变更事件回调。 |
| [OH_AudioCommon_Result OH_AudioSessionManager_SetDefaultOutputDevice(OH_AudioSessionManager *audioSessionManager, OH_AudioDevice_Type deviceType)](#oh_audiosessionmanager_setdefaultoutputdevice) | - | 设置默认本机内置发声设备。 |
| [OH_AudioCommon_Result OH_AudioSessionManager_GetDefaultOutputDevice(OH_AudioSessionManager *audioSessionManager, OH_AudioDevice_Type *deviceType)](#oh_audiosessionmanager_getdefaultoutputdevice) | - | 获取通过[OH_AudioSessionManager_SetDefaultOutputDevice](#oh_audiosessionmanager_setdefaultoutputdevice)设置的默认发声设备。 |
| [OH_AudioCommon_Result OH_AudioSessionManager_ReleaseDevices(OH_AudioSessionManager *audioSessionManager, OH_AudioDeviceDescriptorArray *audioDeviceDescriptorArray)](#oh_audiosessionmanager_releasedevices) | - | 释放音频设备描述符数组对象。 |
| [OH_AudioCommon_Result OH_AudioSessionManager_RegisterCurrentOutputDeviceChangeCallback(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_CurrentOutputDeviceChangedCallback callback)](#oh_audiosessionmanager_registercurrentoutputdevicechangecallback) | - | 注册当前输出设备变化回调。 |
| [OH_AudioCommon_Result OH_AudioSessionManager_UnregisterCurrentOutputDeviceChangeCallback(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_CurrentOutputDeviceChangedCallback callback)](#oh_audiosessionmanager_unregistercurrentoutputdevicechangecallback) | - | 取消注册当前输出设备变化回调。 |
| [OH_AudioCommon_Result OH_AudioSessionManager_GetAvailableDevices(OH_AudioSessionManager *audioSessionManager, OH_AudioDevice_Usage deviceUsage, OH_AudioDeviceDescriptorArray **audioDeviceDescriptorArray)](#oh_audiosessionmanager_getavailabledevices) | - | 获取音频可选设备列表。 |
| [OH_AudioCommon_Result OH_AudioSessionManager_RegisterAvailableDevicesChangeCallback(OH_AudioSessionManager *audioSessionManager, OH_AudioDevice_Usage deviceUsage, OH_AudioSession_AvailableDeviceChangedCallback callback)](#oh_audiosessionmanager_registeravailabledeviceschangecallback) | - | 注册可用设备更改回调。 |
| [OH_AudioCommon_Result OH_AudioSessionManager_UnregisterAvailableDevicesChangeCallback(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_AvailableDeviceChangedCallback callback)](#oh_audiosessionmanager_unregisteravailabledeviceschangecallback) | - | 取消注册可用设备更改回调。 |
| [OH_AudioCommon_Result OH_AudioSessionManager_SelectMediaInputDevice(OH_AudioSessionManager *audioSessionManager, OH_AudioDeviceDescriptor *deviceDescriptor)](#oh_audiosessionmanager_selectmediainputdevice) | - | 设置媒体输入设备。此功能不适用于呼叫录音，即[SourceType](capi-native-audiostream-base-h.md#oh_audiostream_sourcetype)为SOURCE_TYPE_VOICE_CMMUNICATION的场景不适用。<br> 在存在更高优先级的并发录音流的场景中，应用程序实际使用的输入设备可能与所选设备不同。<br> 应用程序可以使用[OH_AudioSessionManager_RegisterCurrentInputDeviceChangeCallback](#oh_audiosessionmanager_registercurrentinputdevicechangecallback)注册一个回调来监听实际的输入设备。 |
| [OH_AudioCommon_Result OH_AudioSessionManager_GetSelectedMediaInputDevice(OH_AudioSessionManager *audioSessionManager, OH_AudioDeviceDescriptor **audioDeviceDescriptor)](#oh_audiosessionmanager_getselectedmediainputdevice) | - | 获得通过[OH_AudioSessionManager_SelectMediaInputDevice](#oh_audiosessionmanager_selectmediainputdevice)设置的媒体输入设备。 |
| [OH_AudioCommon_Result OH_AudioSessionManager_SetBluetoothAndNearlinkPreferredRecordCategory(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_BluetoothAndNearlinkPreferredRecordCategory category)](#oh_audiosessionmanager_setbluetoothandnearlinkpreferredrecordcategory) | - | 设置在使用蓝牙或星闪进行录音时，应用程序的设备偏好分类。应用程序可以在蓝牙或星闪连接之前设置此分类，系统将在设备连接时优先使用蓝牙或星闪进行录音。<br> 在更高优先级的并发录音流的场景中，应用程序实际使用的输入设备可能与当前设置的偏好设备不同。<br> 应用程序可以使用[OH_AudioSessionManager_RegisterCurrentInputDeviceChangeCallback](#oh_audiosessionmanager_registercurrentinputdevicechangecallback)注册一个回调来监听实际的输入设备。 |
| [OH_AudioCommon_Result OH_AudioSessionManager_GetBluetoothAndNearlinkPreferredRecordCategory(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_BluetoothAndNearlinkPreferredRecordCategory *category)](#oh_audiosessionmanager_getbluetoothandnearlinkpreferredrecordcategory) | - | 获取应用程序设置的在使用蓝牙或星闪进行录音时的设备偏好分类。 |
| [OH_AudioCommon_Result OH_AudioSessionManager_RegisterCurrentInputDeviceChangeCallback(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_CurrentInputDeviceChangedCallback callback)](#oh_audiosessionmanager_registercurrentinputdevicechangecallback) | - | 注册音频会话管理器的输入设备更改回调。 |
| [OH_AudioCommon_Result OH_AudioSessionManager_UnregisterCurrentInputDeviceChangeCallback(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_CurrentInputDeviceChangedCallback callback)](#oh_audiosessionmanager_unregistercurrentinputdevicechangecallback) | - | 取消注册音频会话管理器的输入设备更改回调。 |
| [OH_AudioCommon_Result OH_AudioSessionManager_ReleaseDevice(OH_AudioSessionManager *audioSessionManager, OH_AudioDeviceDescriptor *audioDeviceDescriptor)](#oh_audiosessionmanager_releasedevice) | - | 释放音频设备描述符对象。 |

## 枚举类型说明

### OH_AudioSession_ConcurrencyMode

```
enum OH_AudioSession_ConcurrencyMode
```

**描述**

音频并发模式。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| CONCURRENCY_DEFAULT = 0 | 默认使用系统策略。 |
| CONCURRENCY_MIX_WITH_OTHERS = 1 | 和其它正在播放应用进行混音。 |
| CONCURRENCY_DUCK_OTHERS = 2 | 后来播放应用压低正在播放应用的音量。 |
| CONCURRENCY_PAUSE_OTHERS = 3 | 后来播放应用暂停正在播放应用。 |

### OH_AudioSession_Scene

```
enum OH_AudioSession_Scene
```

**描述**

音频会话场景。

**起始版本：** 20

| 枚举项 | 描述 |
| -- | -- |
| AUDIO_SESSION_SCENE_MEDIA = 0 | 媒体音频会话场景。 |
| AUDIO_SESSION_SCENE_GAME = 1 | 游戏音频会话场景。 |
| AUDIO_SESSION_SCENE_VOICE_COMMUNICATION = 2 | VoIP语音通话音频会话场景。 |

### OH_AudioSession_StateChangeHint

```
enum OH_AudioSession_StateChangeHint
```

**描述**

音频会话状态变更的提示信息。

**起始版本：** 20

| 枚举项 | 描述 |
| -- | -- |
| AUDIO_SESSION_STATE_CHANGE_HINT_RESUME = 0 | 提示音频会话恢复，应用可主动触发开始渲染等相关操作。 |
| AUDIO_SESSION_STATE_CHANGE_HINT_PAUSE = 1 | 提示音频会话暂停，暂时失去音频焦点。当焦点再次可用时，会收到AUDIO_SESSION_STATE_CHANGE_HINT_RESUME事件。 |
| AUDIO_SESSION_STATE_CHANGE_HINT_STOP = 2 | 提示音频会话在焦点被抢占后停止，彻底失去音频焦点。 |
| AUDIO_SESSION_STATE_CHANGE_HINT_TIME_OUT_STOP = 3 | 提示长时间没有音频业务，音频会话将被系统停止，彻底失去音频焦点。 |
| AUDIO_SESSION_STATE_CHANGE_HINT_DUCK = 4 | 提示音频会话躲避开始，降低音量播放。 |
| AUDIO_SESSION_STATE_CHANGE_HINT_UNDUCK = 5 | 提示音频会话躲避结束，恢复音量播放。 |

### OH_AudioSession_OutputDeviceChangeRecommendedAction

```
enum OH_AudioSession_OutputDeviceChangeRecommendedAction
```

**描述**

输出设备变更后推荐的操作。

**起始版本：** 20

| 枚举项 | 描述 |
| -- | -- |
| DEVICE_CHANGE_RECOMMEND_TO_CONTINUE = 0 | 推荐继续播放。 |
| DEVICE_CHANGE_RECOMMEND_TO_STOP = 1 | 推荐停止播放。 |

### OH_AudioSession_DeactivatedReason

```
enum OH_AudioSession_DeactivatedReason
```

**描述**

音频会话停用原因。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| DEACTIVATED_LOWER_PRIORITY = 0 | 应用焦点被抢占。 |
| DEACTIVATED_TIMEOUT = 1 | 应用停流后超时。 |

### OH_AudioSession_BluetoothAndNearlinkPreferredRecordCategory

```
enum OH_AudioSession_BluetoothAndNearlinkPreferredRecordCategory
```

**描述**

在使用蓝牙或星闪进行录音时，应用程序的设备偏好分类。

**起始版本：** 21

| 枚举项 | 描述 |
| -- | -- |
| PREFERRED_NONE = 0 | 无指定设备偏好。 |
| PREFERRED_DEFAULT = 1 | 更偏好使用蓝牙或星闪录音。是否使用低延迟或高质量录音取决于系统。 |
| PREFERRED_LOW_LATENCY = 2 | 更偏好使用蓝牙或星闪低延迟模式进行录音。 |
| PREFERRED_HIGH_QUALITY = 3 | 更偏好使用蓝牙或星闪高质量模式进行录音。 |


## 函数说明

### OH_AudioSession_StateChangedCallback()

```
typedef void (*OH_AudioSession_StateChangedCallback)(OH_AudioSession_StateChangedEvent event)
```

**描述**

这个函数指针将指向用于监听音频会话状态变更事件的回调函数。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSession_StateChangedEvent](capi-ohaudio-oh-audiosession-statechangedevent.md) event | 音频会话状态变更事件。 |

### OH_AudioSession_AvailableDeviceChangedCallback()

```
typedef void (*OH_AudioSession_AvailableDeviceChangedCallback)(OH_AudioDevice_ChangeType type, OH_AudioDeviceDescriptorArray *audioDeviceDescriptorArray)
```

**描述**

此函数指针将指向用于返回变化的音频设备描述符的回调函数，可能会返回多个音频设备描述符。

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioDevice_ChangeType](capi-native-audio-device-base-h.md#oh_audiodevice_changetype) type | 设备连接状态类型，已连接或断开。 |
| [OH_AudioDeviceDescriptorArray](capi-ohaudio-oh-audiodevicedescriptorarray.md) *audioDeviceDescriptorArray | 音频设备描述符数组。不再继续使用audioDeviceDescriptorArray指针时，请使用[OH_AudioSessionManager_ReleaseDevices](#oh_audiosessionmanager_releasedevices)进行释放。 |

### OH_AudioSession_CurrentInputDeviceChangedCallback()

```
typedef void (*OH_AudioSession_CurrentInputDeviceChangedCallback)(OH_AudioDeviceDescriptorArray *devices, OH_AudioStream_DeviceChangeReason changeReason)
```

**描述**

这个函数指针将指向用于监听当前输入设备变化事件的回调函数。

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioDeviceDescriptorArray](capi-ohaudio-oh-audiodevicedescriptorarray.md) *devices | 音频设备描述符数组。不再继续使用devices指针时，请使用[OH_AudioSessionManager_ReleaseDevices](#oh_audiosessionmanager_releasedevices)进行释放。 |
| [OH_AudioStream_DeviceChangeReason](capi-native-audiostream-base-h.md#oh_audiostream_devicechangereason) changeReason | 设备变更原因。 |

### OH_AudioSession_CurrentOutputDeviceChangedCallback()

```
typedef void (*OH_AudioSession_CurrentOutputDeviceChangedCallback)(OH_AudioDeviceDescriptorArray *devices, OH_AudioStream_DeviceChangeReason changeReason, OH_AudioSession_OutputDeviceChangeRecommendedAction recommendedAction)
```

**描述**

这个函数指针将指向用于监听当前输出设备变化事件的回调函数。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioDeviceDescriptorArray](capi-ohaudio-oh-audiodevicedescriptorarray.md) *devices | 音频设备描述符数组，指向[OH_AudioDeviceDescriptorArray](capi-ohaudio-oh-audiodevicedescriptorarray.md)设置音频设备描述符值的指针变量，不要单独释放audioDeviceDescriptorArray指针，而是调用[OH_AudioSessionManager_ReleaseDevices](#oh_audiosessionmanager_releasedevices)来释放DeviceDescriptor数组。 |
| [OH_AudioStream_DeviceChangeReason](capi-native-audiostream-base-h.md#oh_audiostream_devicechangereason) changeReason | 指向[OH_AudioStream_DeviceChangeReason](capi-native-audiostream-base-h.md#oh_audiostream_devicechangereason)，用于接收设备变更原因。 |
| [OH_AudioSession_OutputDeviceChangeRecommendedAction](#oh_audiosession_outputdevicechangerecommendedaction) recommendedAction | 指向[OH_AudioSession_OutputDeviceChangeRecommendedAction](#oh_audiosession_outputdevicechangerecommendedaction)，用于接收设备变更后推荐的操作。 |

### OH_AudioSession_DeactivatedCallback()

```
typedef int32_t (*OH_AudioSession_DeactivatedCallback)(OH_AudioSession_DeactivatedEvent event)
```

**描述**

这个函数指针将指向用于监听音频会话停用事件的回调函数。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSession_DeactivatedEvent](capi-ohaudio-oh-audiosession-deactivatedevent.md) event | 音频会话已停用事件。 |

### OH_AudioManager_GetAudioSessionManager()

```
OH_AudioCommon_Result OH_AudioManager_GetAudioSessionManager(OH_AudioSessionManager **audioSessionManager)
```

**描述**

获取音频会话管理器。使用音频会话管理器相关功能，首先需要获取音频会话管理器实例。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) **audioSessionManager | 音频会话管理器实例。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | AUDIOCOMMON_RESULT_SUCCESS：函数执行成功。<br>         AUDIOCOMMON_RESULT_ERROR_SYSTEM：系统错误。 |

### OH_AudioSessionManager_ActivateAudioSession()

```
OH_AudioCommon_Result OH_AudioSessionManager_ActivateAudioSession(OH_AudioSessionManager *audioSessionManager, const OH_AudioSession_Strategy *strategy)
```

**描述**

激活音频会话。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | 指向[OH_AudioManager_GetAudioSessionManager](#oh_audiomanager_getaudiosessionmanager)创建的音频会话管理实例。 |
| const [OH_AudioSession_Strategy](capi-ohaudio-oh-audiosession-strategy.md) *strategy | 指向[OH_AudioSession_Strategy](capi-ohaudio-oh-audiosession-strategy.md)，用于设置音频会话策略。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | 函数返回值：<br>         AUDIOCOMMON_RESULT_SUCCESS：函数执行成功。<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM：<br>                                                        1. 参数audioSessionManager为nullptr；<br>                                                        2. 参数strategy无效。<br>         AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE：非法状态。 |

### OH_AudioSessionManager_DeactivateAudioSession()

```
OH_AudioCommon_Result OH_AudioSessionManager_DeactivateAudioSession(OH_AudioSessionManager *audioSessionManager)
```

**描述**

停用音频会话。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | 指向[OH_AudioManager_GetAudioSessionManager](#oh_audiomanager_getaudiosessionmanager)创建的音频会话管理实例。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | AUDIOCOMMON_RESULT_SUCCESS：函数执行成功。<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM：参数audioSessionManager为nullptr。<br>         AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE：非法状态。 |

### OH_AudioSessionManager_IsAudioSessionActivated()

```
bool OH_AudioSessionManager_IsAudioSessionActivated(OH_AudioSessionManager *audioSessionManager)
```

**描述**

检查音频会话是否已激活。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | 指向[OH_AudioManager_GetAudioSessionManager](#oh_audiomanager_getaudiosessionmanager)创建的音频会话管理实例。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| bool | 用于返回当前应用的音频会话是否已激活，true表示已激活，false表示已停用。 |

### OH_AudioSessionManager_RegisterSessionDeactivatedCallback()

```
OH_AudioCommon_Result OH_AudioSessionManager_RegisterSessionDeactivatedCallback(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_DeactivatedCallback callback)
```

**描述**

注册音频会话停用事件回调。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | 指向[OH_AudioManager_GetAudioSessionManager](#oh_audiomanager_getaudiosessionmanager)创建的音频会话管理实例。 |
| [OH_AudioSession_DeactivatedCallback](#oh_audiosession_deactivatedcallback) callback | 用于接收音频会话已停用事件。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | AUDIOCOMMON_RESULT_SUCCESS：函数执行成功。<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM：<br>                                                        1. 参数audioSessionManager为nullptr；<br>                                                        2. 参数callback为nullptr。 |

### OH_AudioSessionManager_UnregisterSessionDeactivatedCallback()

```
OH_AudioCommon_Result OH_AudioSessionManager_UnregisterSessionDeactivatedCallback(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_DeactivatedCallback callback)
```

**描述**

取消注册音频会话停用事件回调。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | 指向[OH_AudioManager_GetAudioSessionManager](#oh_audiomanager_getaudiosessionmanager)创建的音频会话管理实例。 |
| [OH_AudioSession_DeactivatedCallback](#oh_audiosession_deactivatedcallback) callback | 用于接收音频会话已停用事件。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | AUDIOCOMMON_RESULT_SUCCESS：函数执行成功。<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM：<br>                                                        1. 参数audioSessionManager为nullptr；<br>                                                        2. 参数callback为nullptr。 |

### OH_AudioSessionManager_SetScene()

```
OH_AudioCommon_Result OH_AudioSessionManager_SetScene(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_Scene scene)
```

**描述**

设置音频会话场景参数。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | 指向[OH_AudioManager_GetAudioSessionManager](#oh_audiomanager_getaudiosessionmanager)创建的音频会话管理实例。 |
| [OH_AudioSession_Scene](#oh_audiosession_scene) scene | 音频会话场景。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | AUDIOCOMMON_RESULT_SUCCESS：函数执行成功。<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM：<br>                                                        1. 参数audioSessionManager为nullptr；<br>                                                        2. 参数scene为枚举范围外的值。<br>         AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE：系统当前状态下不允许设置，例如audio session未处于ready态。<br>         AUDIOCOMMON_RESULT_ERROR_SYSTEM：系统异常，例如系统服务异常退出等。 |

### OH_AudioSessionManager_RegisterStateChangeCallback()

```
OH_AudioCommon_Result OH_AudioSessionManager_RegisterStateChangeCallback(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_StateChangedCallback callback)
```

**描述**

注册音频会话状态变更事件回调。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | 指向[OH_AudioManager_GetAudioSessionManager](#oh_audiomanager_getaudiosessionmanager)创建的音频会话管理实例。 |
| [OH_AudioSession_StateChangedCallback](#oh_audiosession_statechangedcallback) callback | 用于接收音频会话状态变更事件。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | AUDIOCOMMON_RESULT_SUCCESS：函数执行成功。<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM：<br>                                                        1. 参数audioSessionManager为nullptr；<br>                                                        2. 参数callback为nullptr。<br>         AUDIOCOMMON_RESULT_ERROR_NO_MEMORY：系统内存申请异常。<br>         AUDIOCOMMON_RESULT_ERROR_SYSTEM：系统异常，例如系统服务异常退出等。 |

### OH_AudioSessionManager_UnregisterStateChangeCallback()

```
OH_AudioCommon_Result OH_AudioSessionManager_UnregisterStateChangeCallback(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_StateChangedCallback callback)
```

**描述**

取消音频会话状态变更事件回调。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | 指向[OH_AudioManager_GetAudioSessionManager](#oh_audiomanager_getaudiosessionmanager)创建的音频会话管理实例。 |
| [OH_AudioSession_StateChangedCallback](#oh_audiosession_statechangedcallback) callback | 用于接收音频会话状态变更事件。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | AUDIOCOMMON_RESULT_SUCCESS：函数执行成功。<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM：<br>                                                        1. 参数audioSessionManager为nullptr；<br>                                                        2. 参数callback为nullptr。<br>         AUDIOCOMMON_RESULT_ERROR_SYSTEM：系统异常，例如系统服务异常退出等。 |

### OH_AudioSessionManager_SetDefaultOutputDevice()

```
OH_AudioCommon_Result OH_AudioSessionManager_SetDefaultOutputDevice(OH_AudioSessionManager *audioSessionManager, OH_AudioDevice_Type deviceType)
```

**描述**

设置默认本机内置发声设备。
> **说明：**
> 本接口适用范围如下：
>
> - 当设置的[OH_AudioSession_Scene](#oh_audiosession_scene)为VoIP场景时，激活AudioSession后立即生效；如果OH_AudioSession_Scene为非VoIP场景，激活AudioSession时不会生效，直到启动播放的[OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage)为语音消息、VoIP语音通话或VoIP视频通话时才生效。支持听筒、扬声器和系统默认设备。
> - 本接口允许在[OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) 创建后随时调用。系统记录应用设置的默认本机内置发声设备，但只有激活AudioSession后才能生效。应用启动播放时，若外接设备如蓝牙耳机或有线耳机已接入，系统优先从外接设备发声；否则，系统遵循应用设置的默认本机内置发声设备。
> - 本接口优先级低于[AVCastPicker](../apis-avsession-kit/ohos-multimedia-avcastpicker.md#avcastpicker)。如果使用AVCastPicker切换过发声设备，再次调用本接口切换设备将不生效。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | 指向[OH_AudioManager_GetAudioSessionManager](#oh_audiomanager_getaudiosessionmanager)创建的音频会话管理实例。 |
| [OH_AudioDevice_Type](capi-native-audio-device-base-h.md#oh_audiodevice_type) deviceType | 指向[OH_AudioDevice_Type](capi-native-audio-device-base-h.md#oh_audiodevice_type)用于设置发声设备类型。可设置的设备类型包括：<br>                                          AUDIO_DEVICE_TYPE_EARPIECE：听筒。<br>                                          AUDIO_DEVICE_TYPE_SPEAKER：扬声器。<br>                                          AUDIO_DEVICE_TYPE_DEFAULT：系统默认设备。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | AUDIOCOMMON_RESULT_SUCCESS：函数执行成功。<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM：<br>                                                        1. 参数audioSessionManager为nullptr；<br>                                                        2. 参数deviceType超出枚举OH_AudioDevice_Type范围。<br>         AUDIOCOMMON_RESULT_ERROR_SYSTEM：系统异常，例如系统服务异常退出等。 |

### OH_AudioSessionManager_GetDefaultOutputDevice()

```
OH_AudioCommon_Result OH_AudioSessionManager_GetDefaultOutputDevice(OH_AudioSessionManager *audioSessionManager, OH_AudioDevice_Type *deviceType)
```

**描述**

获取通过[OH_AudioSessionManager_SetDefaultOutputDevice](#oh_audiosessionmanager_setdefaultoutputdevice)设置的默认发声设备。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | 指向[OH_AudioManager_GetAudioSessionManager](#oh_audiomanager_getaudiosessionmanager)创建的音频会话管理实例。 |
| [OH_AudioDevice_Type](capi-native-audio-device-base-h.md#oh_audiodevice_type) *deviceType | 指向[OH_AudioDevice_Type](capi-native-audio-device-base-h.md#oh_audiodevice_type)用于获取发声设备类型参数指针。返回的设备类型包括：<br>                                          AUDIO_DEVICE_TYPE_EARPIECE：听筒。<br>                                          AUDIO_DEVICE_TYPE_SPEAKER：扬声器。<br>                                          AUDIO_DEVICE_TYPE_DEFAULT：系统默认设备。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | AUDIOCOMMON_RESULT_SUCCESS：函数执行成功。<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM：<br>                                                        1. 参数audioSessionManager为nullptr；<br>                                                        2. 参数deviceType为nullptr。<br>         AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE：系统当前状态下不允许获取默认设备类型，例如audio session未处于ready态。 |

### OH_AudioSessionManager_ReleaseDevices()

```
OH_AudioCommon_Result OH_AudioSessionManager_ReleaseDevices(OH_AudioSessionManager *audioSessionManager, OH_AudioDeviceDescriptorArray *audioDeviceDescriptorArray)
```

**描述**

释放音频设备描述符数组对象。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | 指向[OH_AudioManager_GetAudioSessionManager](#oh_audiomanager_getaudiosessionmanager)创建的音频会话管理实例。 |
| [OH_AudioDeviceDescriptorArray](capi-ohaudio-oh-audiodevicedescriptorarray.md) *audioDeviceDescriptorArray |  需要释放的音频设备描述符数组。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | AUDIOCOMMON_RESULT_SUCCESS：函数执行成功。<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM：<br>                                                        1. 参数audioSessionManager为nullptr；<br>                                                        2. 参数audioDeviceDescriptorArray为nullptr。 |

### OH_AudioSessionManager_RegisterCurrentOutputDeviceChangeCallback()

```
OH_AudioCommon_Result OH_AudioSessionManager_RegisterCurrentOutputDeviceChangeCallback(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_CurrentOutputDeviceChangedCallback callback)
```

**描述**

注册当前输出设备变化回调。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | 指向[OH_AudioManager_GetAudioSessionManager](#oh_audiomanager_getaudiosessionmanager)创建的音频会话管理实例。 |
| [OH_AudioSession_CurrentOutputDeviceChangedCallback](#oh_audiosession_currentoutputdevicechangedcallback) callback | 用于返回音频设备变更信息的回调函数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | AUDIOCOMMON_RESULT_SUCCESS：函数执行成功。<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM：<br>                                                        1. 参数audioSessionManager为nullptr；<br>                                                        2. 参数callback为nullptr。<br>         AUDIOCOMMON_RESULT_ERROR_NO_MEMORY：系统内存申请异常。<br>         AUDIOCOMMON_RESULT_ERROR_SYSTEM：系统异常，例如系统服务异常退出等。 |

### OH_AudioSessionManager_UnregisterCurrentOutputDeviceChangeCallback()

```
OH_AudioCommon_Result OH_AudioSessionManager_UnregisterCurrentOutputDeviceChangeCallback(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_CurrentOutputDeviceChangedCallback callback)
```

**描述**

取消注册当前输出设备变化回调。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | 指向[OH_AudioManager_GetAudioSessionManager](#oh_audiomanager_getaudiosessionmanager)创建的音频会话管理实例。 |
| [OH_AudioSession_CurrentOutputDeviceChangedCallback](#oh_audiosession_currentoutputdevicechangedcallback) callback | 用于返回音频设备变更信息的回调函数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | AUDIOCOMMON_RESULT_SUCCESS：函数执行成功。<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM：<br>                                                        1. 参数audioSessionManager为nullptr；<br>                                                        2. 参数callback为nullptr。<br>         AUDIOCOMMON_RESULT_ERROR_SYSTEM：系统异常，例如系统服务异常退出等。 |

### OH_AudioSessionManager_GetAvailableDevices()

```
OH_AudioCommon_Result OH_AudioSessionManager_GetAvailableDevices(OH_AudioSessionManager *audioSessionManager, OH_AudioDevice_Usage deviceUsage, OH_AudioDeviceDescriptorArray **audioDeviceDescriptorArray)
```

**描述**

获取音频可选设备列表。

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | 指向[OH_AudioManager_GetAudioSessionManager](#oh_audiomanager_getaudiosessionmanager)创建的音频会话管理实例。 |
| [OH_AudioDevice_Usage](capi-native-audio-device-base-h.md#oh_audiodevice_usage) deviceUsage | 用于设置要获取的设备种类。 |
| [OH_AudioDeviceDescriptorArray](capi-ohaudio-oh-audiodevicedescriptorarray.md) **audioDeviceDescriptorArray | 音频设备描述符数组。<br> 不再继续使用audioDeviceDescriptorArray指针时，请使用[OH_AudioSessionManager_ReleaseDevices](#oh_audiosessionmanager_releasedevices)进行释放。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | AUDIOCOMMON_RESULT_SUCCESS：函数执行成功。<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM：<br>                                                        1.参数audioSessionManager为nullptr；<br>                                                        2.参数deviceUsage无效;<br>                                                        3.参数audioDeviceDescriptorArray为nullptr。<br>         AUDIOCOMMON_RESULT_ERROR_SYSTEM：系统异常，例如系统服务异常退出等。 |

### OH_AudioSessionManager_RegisterAvailableDevicesChangeCallback()

```
OH_AudioCommon_Result OH_AudioSessionManager_RegisterAvailableDevicesChangeCallback(OH_AudioSessionManager *audioSessionManager, OH_AudioDevice_Usage deviceUsage, OH_AudioSession_AvailableDeviceChangedCallback callback)
```

**描述**

注册可用设备更改回调。

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | 指向[OH_AudioManager_GetAudioSessionManager](#oh_audiomanager_getaudiosessionmanager)创建的音频会话管理实例。 |
| [OH_AudioDevice_Usage](capi-native-audio-device-base-h.md#oh_audiodevice_usage) deviceUsage | 用于设置要获取的设备种类。 |
| [OH_AudioSession_AvailableDeviceChangedCallback](#oh_audiosession_availabledevicechangedcallback) callback | 用于返回可用音频设备变更信息的回调函数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | AUDIOCOMMON_RESULT_SUCCESS：函数执行成功。<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM：<br>                                                        1. 参数audioSessionManager为nullptr；<br>                                                        2. 参数deviceUsage无效；<br>                                                        3. 参数callback为nullptr。<br>         AUDIOCOMMON_RESULT_ERROR_SYSTEM：系统异常，例如系统服务异常退出等。 |

### OH_AudioSessionManager_UnregisterAvailableDevicesChangeCallback()

```
OH_AudioCommon_Result OH_AudioSessionManager_UnregisterAvailableDevicesChangeCallback(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_AvailableDeviceChangedCallback callback)
```

**描述**

取消注册可用设备更改回调。

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | 指向[OH_AudioManager_GetAudioSessionManager](#oh_audiomanager_getaudiosessionmanager)创建的音频会话管理实例。 |
| [OH_AudioSession_AvailableDeviceChangedCallback](#oh_audiosession_availabledevicechangedcallback) callback | 用于返回可用音频设备变更信息的回调函数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | AUDIOCOMMON_RESULT_SUCCESS：函数执行成功。<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM：<br>                                                        1. 参数audioSessionManager为nullptr；<br>                                                        2. 参数callback为nullptr。<br>         AUDIOCOMMON_RESULT_ERROR_SYSTEM：系统异常，例如系统服务异常退出等。 |

### OH_AudioSessionManager_SelectMediaInputDevice()

```
OH_AudioCommon_Result OH_AudioSessionManager_SelectMediaInputDevice(OH_AudioSessionManager *audioSessionManager, OH_AudioDeviceDescriptor *deviceDescriptor)
```

**描述**

设置媒体输入设备。此功能不适用于呼叫录音，即[SourceType](capi-native-audiostream-base-h.md#oh_audiostream_sourcetype)为SOURCE_TYPE_VOICE_CMMUNICATION的场景不适用。<br> 在存在更高优先级的并发录音流的场景中，应用程序实际使用的输入设备可能与所选设备不同。<br> 应用程序可以使用[OH_AudioSessionManager_RegisterCurrentInputDeviceChangeCallback](#oh_audiosessionmanager_registercurrentinputdevicechangecallback)注册一个回调来监听实际的输入设备。

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | 指向[OH_AudioManager_GetAudioSessionManager](#oh_audiomanager_getaudiosessionmanager)创建的音频会话管理实例。 |
| [OH_AudioDeviceDescriptor](capi-ohaudio-oh-audiodevicedescriptor.md) *deviceDescriptor | 目标设备。可用设备必须位于由[OH_AudioSessionManager_GetAvailableDevices](#oh_audiosessionmanager_getavailabledevices)返回的数组中。<br> 当传递nullptr时，系统将清除上一次的设置。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | AUDIOCOMMON_RESULT_SUCCESS：函数执行成功。<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM：参数audioSessionManager为nullptr。<br>         AUDIOCOMMON_RESULT_ERROR_SYSTEM：系统异常，例如系统服务异常退出等。 |

### OH_AudioSessionManager_GetSelectedMediaInputDevice()

```
OH_AudioCommon_Result OH_AudioSessionManager_GetSelectedMediaInputDevice(OH_AudioSessionManager *audioSessionManager, OH_AudioDeviceDescriptor **audioDeviceDescriptor)
```

**描述**

获得通过[OH_AudioSessionManager_SelectMediaInputDevice](#oh_audiosessionmanager_selectmediainputdevice)设置的媒体输入设备。

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | 指向[OH_AudioManager_GetAudioSessionManager](#oh_audiomanager_getaudiosessionmanager)创建的音频会话管理实例。 |
| [OH_AudioDeviceDescriptor](capi-ohaudio-oh-audiodevicedescriptor.md) **audioDeviceDescriptor | 通过[OH_AudioSessionManager_SelectMediaInputDevice](#oh_audiosessionmanager_selectmediainputdevice)设置的媒体设备，如果没有设置，返回一个类型为AUDIO_DEVICE_TYPE_INVALID的设备。<br> 不再继续使用audioDeviceDescriptor指针时，请使用[OH_AudioSessionManager_ReleaseDevice](#oh_audiosessionmanager_releasedevice)进行释放。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | AUDIOCOMMON_RESULT_SUCCESS：函数执行成功。<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM：<br>                                                        1. 参数audioSessionManager为nullptr；<br>                                                        2. 参数audioDeviceDescriptor为nullptr。<br>         AUDIOCOMMON_RESULT_ERROR_SYSTEM：系统异常，例如系统服务异常退出等。 |

### OH_AudioSessionManager_SetBluetoothAndNearlinkPreferredRecordCategory()

```
OH_AudioCommon_Result OH_AudioSessionManager_SetBluetoothAndNearlinkPreferredRecordCategory(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_BluetoothAndNearlinkPreferredRecordCategory category)
```

**描述**

设置在使用蓝牙或星闪进行录音时，应用程序的设备偏好分类。应用程序可以在蓝牙或星闪连接之前设置此分类，系统将在设备连接时优先使用蓝牙或星闪进行录音。<br> 在更高优先级的并发录音流的场景中，应用程序实际使用的输入设备可能与当前设置的偏好设备不同。<br> 应用程序可以使用[OH_AudioSessionManager_RegisterCurrentInputDeviceChangeCallback](#oh_audiosessionmanager_registercurrentinputdevicechangecallback)注册一个回调来监听实际的输入设备。

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | 指向[OH_AudioManager_GetAudioSessionManager](#oh_audiomanager_getaudiosessionmanager)创建的音频会话管理实例。 |
| [OH_AudioSession_BluetoothAndNearlinkPreferredRecordCategory](#oh_audiosession_bluetoothandnearlinkpreferredrecordcategory) category | 在使用蓝牙或星闪进行录音时，应用程序的设备偏好分类。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | AUDIOCOMMON_RESULT_SUCCESS：函数执行成功。<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM：<br>                                                        1. 参数audioSessionManager为nullptr；<br>                                                        2. 参数category错误。<br>         AUDIOCOMMON_RESULT_ERROR_SYSTEM：系统异常，例如系统服务异常退出等。 |

### OH_AudioSessionManager_GetBluetoothAndNearlinkPreferredRecordCategory()

```
OH_AudioCommon_Result OH_AudioSessionManager_GetBluetoothAndNearlinkPreferredRecordCategory(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_BluetoothAndNearlinkPreferredRecordCategory *category)
```

**描述**

获取应用程序设置的在使用蓝牙或星闪进行录音时的设备偏好分类。

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | 指向[OH_AudioManager_GetAudioSessionManager](#oh_audiomanager_getaudiosessionmanager)创建的音频会话管理实例。 |
| [OH_AudioSession_BluetoothAndNearlinkPreferredRecordCategory](#oh_audiosession_bluetoothandnearlinkpreferredrecordcategory) *category | 在使用蓝牙或星闪进行录音时，应用程序的设备偏好分类。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | AUDIOCOMMON_RESULT_SUCCESS：函数执行成功。<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM：<br>                                                        1. 参数audioSessionManager为nullptr；<br>                                                        2. 参数category为nullptr。<br>         AUDIOCOMMON_RESULT_ERROR_SYSTEM：系统异常，例如系统服务异常退出等。 |

### OH_AudioSessionManager_RegisterCurrentInputDeviceChangeCallback()

```
OH_AudioCommon_Result OH_AudioSessionManager_RegisterCurrentInputDeviceChangeCallback(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_CurrentInputDeviceChangedCallback callback)
```

**描述**

注册音频会话管理器的输入设备更改回调。

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | 指向[OH_AudioManager_GetAudioSessionManager](#oh_audiomanager_getaudiosessionmanager)创建的音频会话管理实例。 |
| [OH_AudioSession_CurrentInputDeviceChangedCallback](#oh_audiosession_currentinputdevicechangedcallback) callback | 用于返回音频输入设备变更信息的回调函数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | AUDIOCOMMON_RESULT_SUCCESS：函数执行成功。<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM：<br>                                                        1. 参数audioSessionManager为nullptr；<br>                                                        2. 参数callback为nullptr。<br>         AUDIOCOMMON_RESULT_ERROR_NO_MEMORY：内存不足。<br>         AUDIOCOMMON_RESULT_ERROR_SYSTEM：系统异常，例如系统服务异常退出等。 |

### OH_AudioSessionManager_UnregisterCurrentInputDeviceChangeCallback()

```
OH_AudioCommon_Result OH_AudioSessionManager_UnregisterCurrentInputDeviceChangeCallback(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_CurrentInputDeviceChangedCallback callback)
```

**描述**

取消注册音频会话管理器的输入设备更改回调。

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | 指向[OH_AudioManager_GetAudioSessionManager](#oh_audiomanager_getaudiosessionmanager)创建的音频会话管理实例。 |
| [OH_AudioSession_CurrentInputDeviceChangedCallback](#oh_audiosession_currentinputdevicechangedcallback) callback | 用于返回音频输入设备变更信息的回调函数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | AUDIOCOMMON_RESULT_SUCCESS：函数执行成功。<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM：<br>                                                        1. 参数audioSessionManager为nullptr；<br>                                                        2. 参数callback为nullptr。<br>         AUDIOCOMMON_RESULT_ERROR_SYSTEM：系统异常，例如系统服务异常退出等。 |

### OH_AudioSessionManager_ReleaseDevice()

```
OH_AudioCommon_Result OH_AudioSessionManager_ReleaseDevice(OH_AudioSessionManager *audioSessionManager, OH_AudioDeviceDescriptor *audioDeviceDescriptor)
```

**描述**

释放音频设备描述符对象。

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | 指向[OH_AudioManager_GetAudioSessionManager](#oh_audiomanager_getaudiosessionmanager)创建的音频会话管理实例。 |
| [OH_AudioDeviceDescriptor](capi-ohaudio-oh-audiodevicedescriptor.md) *audioDeviceDescriptor | 需要被释放的音频设备描述符对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | AUDIOCOMMON_RESULT_SUCCESS：函数执行成功。<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM：<br>                                                        1. 参数audioSessionManager为nullptr；<br>                                                        2. 参数audioDeviceDescriptor为nullptr。 |


