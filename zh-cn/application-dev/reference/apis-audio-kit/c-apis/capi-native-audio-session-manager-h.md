# native_audio_session_manager.h

## 概述

本文件提供音频会话管理功能的接口。 <br>在介绍音频会话能力前，需要先了解如下概念： <br>音频焦点：系统用于管理多个音频竞争的机制，决定了音频播放的优先级，高优先级的音频可以中断或压低低优先级的音频。 <br>音频会话：表示应用的音频业务，开发者可以通过音频会话管理应用内所有音频的焦点和设备选择策略。 音频会话的配置会影响应用内的所有音频流。<br> <br>音频会话的主要使用场景： <br>a) 系统默认的焦点策略不能满足开发者要求，可使用音频会话修改策略。 <br>b) 应用音频业务流程涉及切换不同音频流（如短视频切换），要保证切换过程中焦点不丢失，可使用场景级音频会话。 此类会话激活过程中，焦点不会随音频流停止而丢失。 <br>c) 设置应用当前音频业务的播放输出设备或录音输入设备偏好。<br> <br>音频会话有两种使用模式： <br>a) 音频流级会话：不使用[OH_AudioSessionManager_SetScene](capi-native-audio-session-manager-h.md#oh_audiosessionmanager_setscene)接口设置场景时，音频系统会按会话维度管理音频流， 但音频业务的生命周期还是与音频流状态绑定。因此焦点的请求和释放， 仍是跟随音频流的启动和停止。 <br>b) 场景级会话：使用[OH_AudioSessionManager_SetScene](capi-native-audio-session-manager-h.md#oh_audiosessionmanager_setscene)接口设置场景后， 音频系统会将音频业务的生命周期与音频会话状态绑定，焦点的请求和释放，会跟随音频会话的激活和停止。 <br>推荐开发者优先选择场景级音频会话，以便更灵活的控制业务生效的时机。 <br>本文件提供的接口，支持的主要功能包括配置音频会话，激活/停用音频会话、监听音频会话停用事件、 设置应用输入设备偏好等。

**库：** libohaudio.so

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 12

**相关模块：** [OHAudio](capi-ohaudio.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_AudioSession_DeactivatedEvent](capi-ohaudio-oh-audiosession-deactivatedevent.md) | - | 定义音频会话已停用事件结构体， 该结构体用于在[OH_AudioSession_DeactivatedCallback](capi-native-audio-session-manager-h.md#oh_audiosession_deactivatedcallback) 回调函数内传递会话停用事件的详细信息。 |
| [OH_AudioSession_StateChangedEvent](capi-ohaudio-oh-audiosession-statechangedevent.md) | - | 声明音频会话状态变更事件结构体， 该结构体用于在[OH_AudioSession_StateChangedCallback](capi-native-audio-session-manager-h.md#oh_audiosession_statechangedcallback) 回调函数内传递会话状态变更事件的详细信息。 |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) | OH_AudioSessionManager | 声明音频会话管理结构体，该结构体用于调用音频会话控制功能接口。 |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_AudioSession_Scene](#oh_audiosession_scene) | OH_AudioSession_Scene | 音频会话场景。 |
| [OH_AudioSession_StateChangeHint](#oh_audiosession_statechangehint) | OH_AudioSession_StateChangeHint | 音频会话状态变更的提示信息。 |
| [OH_AudioSession_OutputDeviceChangeRecommendedAction](#oh_audiosession_outputdevicechangerecommendedaction) | OH_AudioSession_OutputDeviceChangeRecommendedAction | 输出设备变更后推荐的操作。 <br>常见场景示例：耳机设备和外放设备之间进行切换。当佩戴耳机时，从外放设备切换到耳机设备，系统会推荐继续播放， 提示应用无需停止当前播放。当摘下耳机设备切换到外放设备时，系统会推荐停止播放。 |
| [OH_AudioSession_DeactivatedReason](#oh_audiosession_deactivatedreason) | OH_AudioSession_DeactivatedReason | 音频会话停用原因。 |
| [OH_AudioSession_BluetoothAndNearlinkPreferredRecordCategory](#oh_audiosession_bluetoothandnearlinkpreferredrecordcategory) | OH_AudioSession_BluetoothAndNearlinkPreferredRecordCategory | 在使用蓝牙或星闪进行录音时，应用程序的设备偏好分类。 |

### 函数

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [typedef void (\*OH_AudioSession_StateChangedCallback)(OH_AudioSession_StateChangedEvent event)](#oh_audiosession_statechangedcallback) | OH_AudioSession_StateChangedCallback | 音频会话状态变更回调函数的原型定义。 |
| [typedef void (\*OH_AudioSession_AvailableDeviceChangedCallback)(OH_AudioDevice_ChangeType type, OH_AudioDeviceDescriptorArray *audioDeviceDescriptorArray)](#oh_audiosession_availabledevicechangedcallback) | OH_AudioSession_AvailableDeviceChangedCallback | 音频可用设备设备变化回调函数的原型定义。 |
| [typedef void (\*OH_AudioSession_CurrentInputDeviceChangedCallback)(OH_AudioDeviceDescriptorArray *devices, OH_AudioStream_DeviceChangeReason changeReason)](#oh_audiosession_currentinputdevicechangedcallback) | OH_AudioSession_CurrentInputDeviceChangedCallback | 当前输入设备变化回调函数的原型定义。 |
| [typedef void (\*OH_AudioSession_CurrentOutputDeviceChangedCallback)(OH_AudioDeviceDescriptorArray *devices, OH_AudioStream_DeviceChangeReason changeReason, OH_AudioSession_OutputDeviceChangeRecommendedAction recommendedAction)](#oh_audiosession_currentoutputdevicechangedcallback) | OH_AudioSession_CurrentOutputDeviceChangedCallback | 当前输出设备变化回调函数的原型定义。 |
| [typedef int32_t (\*OH_AudioSession_DeactivatedCallback)(OH_AudioSession_DeactivatedEvent event)](#oh_audiosession_deactivatedcallback) | OH_AudioSession_DeactivatedCallback | 音频会话停用事件回调函数的原型定义。 |
| [OH_AudioCommon_Result OH_AudioManager_GetAudioSessionManager(OH_AudioSessionManager **audioSessionManager)](#oh_audiomanager_getaudiosessionmanager) | - | 获取音频会话管理器实例，该实例为单例，用于调用音频会话功能接口。 |
| [OH_AudioCommon_Result OH_AudioSessionManager_ActivateAudioSession(OH_AudioSessionManager *audioSessionManager, const OH_AudioSession_Strategy *strategy)](#oh_audiosessionmanager_activateaudiosession) | - | 激活音频会话。 |
| [OH_AudioCommon_Result OH_AudioSessionManager_DeactivateAudioSession(OH_AudioSessionManager *audioSessionManager)](#oh_audiosessionmanager_deactivateaudiosession) | - | 停用音频会话。 |
| [bool OH_AudioSessionManager_IsAudioSessionActivated(OH_AudioSessionManager *audioSessionManager)](#oh_audiosessionmanager_isaudiosessionactivated) | - | 检查音频会话是否已激活。 |
| [OH_AudioCommon_Result OH_AudioSessionManager_RegisterSessionDeactivatedCallback(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_DeactivatedCallback callback)](#oh_audiosessionmanager_registersessiondeactivatedcallback) | - | 注册音频会话停用事件回调。 |
| [OH_AudioCommon_Result OH_AudioSessionManager_UnregisterSessionDeactivatedCallback(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_DeactivatedCallback callback)](#oh_audiosessionmanager_unregistersessiondeactivatedcallback) | - | 取消注册音频会话停用事件回调。 |
| [OH_AudioCommon_Result OH_AudioSessionManager_SetScene(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_Scene scene)](#oh_audiosessionmanager_setscene) | - | 设置音频会话场景参数。 <br>设置会话场景后，音频会话将进入场景级模式，音频业务的生命周期与音频会话状态绑定， 焦点的请求和释放会跟随音频会话的激活和停止。 |
| [OH_AudioCommon_Result OH_AudioSessionManager_RegisterStateChangeCallback(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_StateChangedCallback callback)](#oh_audiosessionmanager_registerstatechangecallback) | - | 注册音频会话状态变更事件回调。 |
| [OH_AudioCommon_Result OH_AudioSessionManager_UnregisterStateChangeCallback(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_StateChangedCallback callback)](#oh_audiosessionmanager_unregisterstatechangecallback) | - | 取消音频会话状态变更事件回调。 |
| [OH_AudioCommon_Result OH_AudioSessionManager_SetDefaultOutputDevice(OH_AudioSessionManager *audioSessionManager, OH_AudioDevice_Type deviceType)](#oh_audiosessionmanager_setdefaultoutputdevice) | - | 设置默认本机内置发声设备。 |
| [OH_AudioCommon_Result OH_AudioSessionManager_GetDefaultOutputDevice(OH_AudioSessionManager *audioSessionManager, OH_AudioDevice_Type *deviceType)](#oh_audiosessionmanager_getdefaultoutputdevice) | - | 获取通过[OH_AudioSessionManager_SetDefaultOutputDevice](capi-native-audio-session-manager-h.md#oh_audiosessionmanager_setdefaultoutputdevice)设置的默认发声设备。 |
| [OH_AudioCommon_Result OH_AudioSessionManager_ReleaseDevices(OH_AudioSessionManager *audioSessionManager, OH_AudioDeviceDescriptorArray *audioDeviceDescriptorArray)](#oh_audiosessionmanager_releasedevices) | - | 释放音频设备描述符数组对象。 |
| [OH_AudioCommon_Result OH_AudioSessionManager_RegisterCurrentOutputDeviceChangeCallback(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_CurrentOutputDeviceChangedCallback callback)](#oh_audiosessionmanager_registercurrentoutputdevicechangecallback) | - | 注册当前输出设备变化回调。 |
| [OH_AudioCommon_Result OH_AudioSessionManager_UnregisterCurrentOutputDeviceChangeCallback(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_CurrentOutputDeviceChangedCallback callback)](#oh_audiosessionmanager_unregistercurrentoutputdevicechangecallback) | - | 取消注册当前输出设备变化回调。 |
| [OH_AudioCommon_Result OH_AudioSessionManager_GetAvailableDevices(OH_AudioSessionManager *audioSessionManager, OH_AudioDevice_Usage deviceUsage, OH_AudioDeviceDescriptorArray **audioDeviceDescriptorArray)](#oh_audiosessionmanager_getavailabledevices) | - | 获取音频可选设备列表。 |
| [OH_AudioCommon_Result OH_AudioSessionManager_RegisterAvailableDevicesChangeCallback(OH_AudioSessionManager *audioSessionManager, OH_AudioDevice_Usage deviceUsage, OH_AudioSession_AvailableDeviceChangedCallback callback)](#oh_audiosessionmanager_registeravailabledeviceschangecallback) | - | 注册可用设备更改回调。 |
| [OH_AudioCommon_Result OH_AudioSessionManager_UnregisterAvailableDevicesChangeCallback(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_AvailableDeviceChangedCallback callback)](#oh_audiosessionmanager_unregisteravailabledeviceschangecallback) | - | 取消注册可用设备更改回调。 |
| [OH_AudioCommon_Result OH_AudioSessionManager_SelectMediaInputDevice(OH_AudioSessionManager *audioSessionManager, OH_AudioDeviceDescriptor *deviceDescriptor)](#oh_audiosessionmanager_selectmediainputdevice) | - | 设置媒体输入设备。此功能不适用于呼叫录音，即[OH_AudioStream_SourceType](capi-native-audiostream-base-h.md#oh_audiostream_sourcetype) 为SOURCE_TYPE_VOICE_COMMUNICATION的场景不适用。 <br>在存在更高优先级的并发录音流的场景中，应用程序实际使用的输入设备可能与所选设备不同。 <br>应用程序可以使用[OH_AudioSessionManager_RegisterCurrentInputDeviceChangeCallback](capi-native-audio-session-manager-h.md#oh_audiosessionmanager_registercurrentinputdevicechangecallback) 注册一个回调来监听实际的输入设备。 |
| [OH_AudioCommon_Result OH_AudioSessionManager_GetSelectedMediaInputDevice(OH_AudioSessionManager *audioSessionManager, OH_AudioDeviceDescriptor **audioDeviceDescriptor)](#oh_audiosessionmanager_getselectedmediainputdevice) | - | 获得通过[OH_AudioSessionManager_SelectMediaInputDevice](capi-native-audio-session-manager-h.md#oh_audiosessionmanager_selectmediainputdevice)设置的媒体输入设备。 |
| [OH_AudioCommon_Result OH_AudioSessionManager_SetBluetoothAndNearlinkPreferredRecordCategory(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_BluetoothAndNearlinkPreferredRecordCategory category)](#oh_audiosessionmanager_setbluetoothandnearlinkpreferredrecordcategory) | - | 设置在使用蓝牙或星闪进行录音时，应用程序的设备偏好分类。应用程序可以在蓝牙或星闪连接之前设置此分类， 系统将在设备连接时优先使用蓝牙或星闪进行录音。 <br>在更高优先级的并发录音流的场景中，应用程序实际使用的输入设备可能与当前设置的偏好设备不同。 <br>应用程序可以使用[OH_AudioSessionManager_RegisterCurrentInputDeviceChangeCallback](capi-native-audio-session-manager-h.md#oh_audiosessionmanager_registercurrentinputdevicechangecallback) 注册一个回调来监听实际的输入设备。 |
| [OH_AudioCommon_Result OH_AudioSessionManager_GetBluetoothAndNearlinkPreferredRecordCategory(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_BluetoothAndNearlinkPreferredRecordCategory *category)](#oh_audiosessionmanager_getbluetoothandnearlinkpreferredrecordcategory) | - | 获取应用程序设置的在使用蓝牙或星闪进行录音时的设备偏好分类。 |
| [OH_AudioCommon_Result OH_AudioSessionManager_RegisterCurrentInputDeviceChangeCallback(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_CurrentInputDeviceChangedCallback callback)](#oh_audiosessionmanager_registercurrentinputdevicechangecallback) | - | 注册音频会话管理器的输入设备更改回调。 |
| [OH_AudioCommon_Result OH_AudioSessionManager_UnregisterCurrentInputDeviceChangeCallback(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_CurrentInputDeviceChangedCallback callback)](#oh_audiosessionmanager_unregistercurrentinputdevicechangecallback) | - | 取消注册音频会话管理器的输入设备更改回调。 |
| [OH_AudioCommon_Result OH_AudioSessionManager_ReleaseDevice(OH_AudioSessionManager *audioSessionManager, OH_AudioDeviceDescriptor *audioDeviceDescriptor)](#oh_audiosessionmanager_releasedevice) | - | 释放音频设备描述符对象。 |
| [OH_AudioCommon_Result OH_AudioSessionManager_EnableMuteSuggestionWhenMixWithOthers(OH_AudioSessionManager *audioSessionManager, bool enable)](#oh_audiosessionmanager_enablemutesuggestionwhenmixwithothers) | - | 启用混音播放下接收静音播放建议通知功能。 通常，当使用混音模式时，如果有其他应用的音频同时播放，此时两者会混合播放。 部分场景下（如游戏或广播），应用可以通过启用静音建议通知，以为用户提供更好的体验。如果启用此功能， 当订阅音频会话状态更改事件后静音建议和取消静音建议提示将通过[OH_AudioSession_StateChangedCallback](capi-native-audio-session-manager-h.md#oh_audiosession_statechangedcallback)回调发送， 该回调由 [OH_AudioSessionManager_RegisterStateChangeCallback](capi-native-audio-session-manager-h.md#oh_audiosessionmanager_registerstatechangecallback)注册。 <br>收到静音建议表示其他应用程序开始播放音频，且播放的音频和本应用的音频不能混音。 此功能仅支持已设置[OH_AudioSession_Scene](capi-native-audio-session-manager-h.md#oh_audiosession_scene)并激活模式为 [OH_AudioSession_ConcurrencyMode](capi-native-audio-session-base-h.md#oh_audiosession_concurrencymode).CONCURRENCY_MIX_WITH_OTHERS的音频会话使用。 <br>并且仅在激活音频会话期间生效一次，每次激活音频会话前都必须重新启用。 |
| [bool OH_AudioSessionManager_IsOtherMediaPlaying(OH_AudioSessionManager *audioSessionManager)](#oh_audiosessionmanager_isothermediaplaying) | - | 检查是否有其他应用正在播放音乐、视频、听书、游戏四种媒体类型的音频，已激活的媒体场景音频会话也将会被计入。 |
| [OH_AudioCommon_Result OH_AudioSessionManager_SetCaptureMuteHint(OH_AudioSessionManager *audioSessionManager, bool mute)](#oh_audiosessionmanager_setcapturemutehint) | - | 应用将当前音频会话内录音流的自身静音状态传递给系统音频模块。 <br>该接口用于向系统音频模块上报当前音频会话内录音流的静音状态，不会改变录音流的实际静音状态。 <br>系统音频模块在设备底层能力支持的情况下，根据设置的状态调整策略以降低功耗。 <br>该接口仅在当前音频会话存在运行中的录音流时允许调用，否则返回错误码AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE。 <br>若某条录音流同时调用了流级接口和本接口，流级接口设置优先级更高，以流级接口设置值为准。 |
| [OH_AudioCommon_Result OH_AudioSessionManager_SetBehavior(OH_AudioSessionManager *audioSessionManager, uint32_t behavior)](#oh_audiosessionmanager_setbehavior) | - | 设置音频会话行为参数（支持多种标志位的组合使用）。 当音频会话在激活状态时调用此接口后，必须重新调用接口[OH_AudioSessionManager_ActivateAudioSession](capi-native-audio-session-manager-h.md#oh_audiosessionmanager_activateaudiosession)使其生效。 若未调用此接口，系统将使用默认行为参数。 |

### 变量

| 名称 | 描述 |
| -- | -- |
| void (*OH_AudioSession_StateChangedCallback) ( OH_AudioSession_StateChangedEvent event) | 音频会话状态变更回调函数的原型定义。<br>**起始版本：** 20<br>**系统能力：** SystemCapability.Multimedia.Audio.Core |
| void (*OH_AudioSession_AvailableDeviceChangedCallback) ( OH_AudioDevice_ChangeType type, OH_AudioDeviceDescriptorArray *audioDeviceDescriptorArray) | 音频可用设备设备变化回调函数的原型定义。<br>**起始版本：** 21<br>**系统能力：** SystemCapability.Multimedia.Audio.Core |
| void (*OH_AudioSession_CurrentInputDeviceChangedCallback) ( OH_AudioDeviceDescriptorArray *devices, OH_AudioStream_DeviceChangeReason changeReason) | 当前输入设备变化回调函数的原型定义。<br>**起始版本：** 21<br>**系统能力：** SystemCapability.Multimedia.Audio.Core |
| void (*OH_AudioSession_CurrentOutputDeviceChangedCallback) ( OH_AudioDeviceDescriptorArray *devices, OH_AudioStream_DeviceChangeReason changeReason, OH_AudioSession_OutputDeviceChangeRecommendedAction recommendedAction) | 当前输出设备变化回调函数的原型定义。<br>**起始版本：** 20<br>**系统能力：** SystemCapability.Multimedia.Audio.Core |
| int32_t (*OH_AudioSession_DeactivatedCallback) ( OH_AudioSession_DeactivatedEvent event) | 音频会话停用事件回调函数的原型定义。<br>**起始版本：** 12<br>**系统能力：** SystemCapability.Multimedia.Audio.Core |

## 枚举类型说明

### OH_AudioSession_Scene

```c
enum OH_AudioSession_Scene
```

**描述：**

音频会话场景。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 20

| 枚举项 | 描述 |
| -- | -- |
| AUDIO_SESSION_SCENE_MEDIA = 0 | 媒体音频会话场景。 |
| AUDIO_SESSION_SCENE_GAME = 1 | 游戏音频会话场景。 |
| AUDIO_SESSION_SCENE_VOICE_COMMUNICATION = 2 | VoIP语音通话音频会话场景。 |
| AUDIO_SESSION_SCENE_VOICE_MESSAGE = 3 | 语音消息音频会话场景。<br>**起始版本：** 26.0.1 |

### OH_AudioSession_StateChangeHint

```c
enum OH_AudioSession_StateChangeHint
```

**描述：**

音频会话状态变更的提示信息。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 20

| 枚举项 | 描述 |
| -- | -- |
| AUDIO_SESSION_STATE_CHANGE_HINT_RESUME = 0 | 提示音频会话恢复，应用可主动触发开始渲染等相关操作。 |
| AUDIO_SESSION_STATE_CHANGE_HINT_PAUSE = 1 | 提示音频会话暂停，暂时失去音频焦点。当焦点再次可用时，会收到AUDIO_SESSION_STATE_CHANGE_HINT_RESUME事件。 |
| AUDIO_SESSION_STATE_CHANGE_HINT_STOP = 2 | 提示音频会话在焦点被抢占后停止，彻底失去音频焦点。 |
| AUDIO_SESSION_STATE_CHANGE_HINT_TIME_OUT_STOP = 3 | 提示长时间没有音频业务，音频会话将被系统停止，彻底失去音频焦点。 |
| AUDIO_SESSION_STATE_CHANGE_HINT_DUCK = 4 | 提示音频会话躲避开始，降低音量播放。 如果已启用[OH_AudioSessionManager_EnableMuteSuggestionWhenMixWithOthers](capi-native-audio-session-manager-h.md#oh_audiosessionmanager_enablemutesuggestionwhenmixwithothers)，此时可以选择执行静音操作。 |
| AUDIO_SESSION_STATE_CHANGE_HINT_UNDUCK = 5 | 提示音频会话躲避结束，恢复音量播放。 如果已启用[OH_AudioSessionManager_EnableMuteSuggestionWhenMixWithOthers](capi-native-audio-session-manager-h.md#oh_audiosessionmanager_enablemutesuggestionwhenmixwithothers)，此时可取消静音。 |
| AUDIO_SESSION_STATE_CHANGE_HINT_MUTE_SUGGESTION = 6 | 静音播放建议。当其他应用程序开始播放不可混音的音频时，应用程序可以自行决定是否静音。<br>**起始版本：** 23 |
| AUDIO_SESSION_STATE_CHANGE_HINT_UNMUTE_SUGGESTION = 7 | 取消静音播放建议。当其他应用程序不可混音的音频已结束，该应用程序可自行决定是否取消静音。<br>**起始版本：** 23 |
| AUDIO_SESSION_STATE_CHANGE_HINT_MUTE = 8 | 提示音频会话静音。该提示仅在以下条件满足后才会收到： 通过接口[OH_AudioSessionManager_SetBehavior](capi-native-audio-session-manager-h.md#oh_audiosessionmanager_setbehavior)设置参数 [OH_AudioSession_BehaviorFlags](capi-native-audio-session-base-h.md#oh_audiosession_behaviorflags).MUTE_WHEN_INTERRUPTED， 并已调用[OH_AudioSessionManager_SetScene](capi-native-audio-session-manager-h.md#oh_audiosessionmanager_setscene)，且音频会话已激活。<br>**起始版本：** 24 |
| AUDIO_SESSION_STATE_CHANGE_HINT_UNMUTE = 9 | 提示音频会话解除静音。该提示仅在以下条件满足后才会收到： 通过接口[OH_AudioSessionManager_SetBehavior](capi-native-audio-session-manager-h.md#oh_audiosessionmanager_setbehavior)设置参数 [OH_AudioSession_BehaviorFlags](capi-native-audio-session-base-h.md#oh_audiosession_behaviorflags).MUTE_WHEN_INTERRUPTED， 并已调用[OH_AudioSessionManager_SetScene](capi-native-audio-session-manager-h.md#oh_audiosessionmanager_setscene)，且音频会话已激活。<br>**起始版本：** 24 |

### OH_AudioSession_OutputDeviceChangeRecommendedAction

```c
enum OH_AudioSession_OutputDeviceChangeRecommendedAction
```

**描述：**

输出设备变更后推荐的操作。 <br>常见场景示例：耳机设备和外放设备之间进行切换。当佩戴耳机时，从外放设备切换到耳机设备，系统会推荐继续播放， 提示应用无需停止当前播放。当摘下耳机设备切换到外放设备时，系统会推荐停止播放。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 20

| 枚举项 | 描述 |
| -- | -- |
| DEVICE_CHANGE_RECOMMEND_TO_CONTINUE = 0 | 推荐继续播放（该事件作为播放维持提示，作用是告知应用本次设备变动音频无需停止播放， 但不可将其作为启动音频播放的判断依据）。 |
| DEVICE_CHANGE_RECOMMEND_TO_STOP = 1 | 推荐停止播放。 |

### OH_AudioSession_DeactivatedReason

```c
enum OH_AudioSession_DeactivatedReason
```

**描述：**

音频会话停用原因。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| DEACTIVATED_LOWER_PRIORITY = 0 | 应用焦点被抢占。 |
| DEACTIVATED_TIMEOUT = 1 | 应用停流后超时。 |

### OH_AudioSession_BluetoothAndNearlinkPreferredRecordCategory

```c
enum OH_AudioSession_BluetoothAndNearlinkPreferredRecordCategory
```

**描述：**

在使用蓝牙或星闪进行录音时，应用程序的设备偏好分类。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 21

| 枚举项 | 描述 |
| -- | -- |
| PREFERRED_NONE = 0 | 无指定设备偏好。 |
| PREFERRED_DEFAULT = 1 | 更偏好使用蓝牙或星闪录音。是否使用低延迟或高质量录音取决于系统。 |
| PREFERRED_LOW_LATENCY = 2 | 更偏好使用蓝牙或星闪低延迟模式进行录音。 |
| PREFERRED_HIGH_QUALITY = 3 | 更偏好使用蓝牙或星闪高质量模式进行录音。 |


## 函数说明

### OH_AudioSession_StateChangedCallback()

```c
typedef void (*OH_AudioSession_StateChangedCallback)(OH_AudioSession_StateChangedEvent event)
```

**描述：**

音频会话状态变更回调函数的原型定义。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSession_StateChangedEvent](capi-ohaudio-oh-audiosession-statechangedevent.md) event | 音频会话状态变更事件。 |

### OH_AudioSession_AvailableDeviceChangedCallback()

```c
typedef void (*OH_AudioSession_AvailableDeviceChangedCallback)(OH_AudioDevice_ChangeType type, OH_AudioDeviceDescriptorArray *audioDeviceDescriptorArray)
```

**描述：**

音频可用设备设备变化回调函数的原型定义。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioDevice_ChangeType](capi-native-audio-device-base-h.md#oh_audiodevice_changetype) type | 设备连接状态类型，已连接或断开。 |
| [OH_AudioDeviceDescriptorArray](capi-ohaudio-oh-audiodevicedescriptorarray.md) *audioDeviceDescriptorArray | 音频设备描述符数组。 <br>不再继续使用audioDeviceDescriptorArray指针时，请使用[OH_AudioSessionManager_ReleaseDevices](capi-native-audio-session-manager-h.md#oh_audiosessionmanager_releasedevices)进行释放。 |

### OH_AudioSession_CurrentInputDeviceChangedCallback()

```c
typedef void (*OH_AudioSession_CurrentInputDeviceChangedCallback)(OH_AudioDeviceDescriptorArray *devices, OH_AudioStream_DeviceChangeReason changeReason)
```

**描述：**

当前输入设备变化回调函数的原型定义。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioDeviceDescriptorArray](capi-ohaudio-oh-audiodevicedescriptorarray.md) *devices | 音频设备描述符数组。 <br>不再继续使用devices指针时，请使用[OH_AudioSessionManager_ReleaseDevices](capi-native-audio-session-manager-h.md#oh_audiosessionmanager_releasedevices)进行释放。 |
| [OH_AudioStream_DeviceChangeReason](capi-native-audiostream-base-h.md#oh_audiostream_devicechangereason) changeReason | 设备变更原因。 |

### OH_AudioSession_CurrentOutputDeviceChangedCallback()

```c
typedef void (*OH_AudioSession_CurrentOutputDeviceChangedCallback)(OH_AudioDeviceDescriptorArray *devices, OH_AudioStream_DeviceChangeReason changeReason, OH_AudioSession_OutputDeviceChangeRecommendedAction recommendedAction)
```

**描述：**

当前输出设备变化回调函数的原型定义。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioDeviceDescriptorArray](capi-ohaudio-oh-audiodevicedescriptorarray.md) *devices | 音频设备描述符数组。 <br>不再继续使用devices指针时，请使用[OH_AudioSessionManager_ReleaseDevices](capi-native-audio-session-manager-h.md#oh_audiosessionmanager_releasedevices)进行释放。 |
| [OH_AudioStream_DeviceChangeReason](capi-native-audiostream-base-h.md#oh_audiostream_devicechangereason) changeReason | 指向[OH_AudioStream_DeviceChangeReason](capi-native-audiostream-base-h.md#oh_audiostream_devicechangereason)，用于接收设备变更原因。 |
| [OH_AudioSession_OutputDeviceChangeRecommendedAction](capi-native-audio-session-manager-h.md#oh_audiosession_outputdevicechangerecommendedaction) recommendedAction | 指向[OH_AudioSession_OutputDeviceChangeRecommendedAction](capi-native-audio-session-manager-h.md#oh_audiosession_outputdevicechangerecommendedaction)， 用于接收设备变更后推荐的操作。 |

### OH_AudioSession_DeactivatedCallback()

```c
typedef int32_t (*OH_AudioSession_DeactivatedCallback)(OH_AudioSession_DeactivatedEvent event)
```

**描述：**

音频会话停用事件回调函数的原型定义。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSession_DeactivatedEvent](capi-ohaudio-oh-audiosession-deactivatedevent.md) event | 音频会话已停用事件。 |

### OH_AudioManager_GetAudioSessionManager()

```c
OH_AudioCommon_Result OH_AudioManager_GetAudioSessionManager(OH_AudioSessionManager **audioSessionManager)
```

**描述：**

获取音频会话管理器实例，该实例为单例，用于调用音频会话功能接口。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) **audioSessionManager | [out] 用于接收获取的音频会话管理器实例。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 函数执行成功。</li> <li>[AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) 系统错误。</li> </ul> |

### OH_AudioSessionManager_ActivateAudioSession()

```c
OH_AudioCommon_Result OH_AudioSessionManager_ActivateAudioSession(OH_AudioSessionManager *audioSessionManager, const OH_AudioSession_Strategy *strategy)
```

**描述：**

激活音频会话。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | [in] 指向[OH_AudioManager_GetAudioSessionManager](capi-native-audio-session-manager-h.md#oh_audiomanager_getaudiosessionmanager)创建的音频会话管理实例。 |
| [const OH_AudioSession_Strategy](capi-ohaudio-oh-audiosession-strategy.md) *strategy | [in] 用于设置音频会话策略。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | 函数返回值：<br>AUDIOCOMMON_RESULT_SUCCESS：函数执行成功。<br>AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM：<br>1. 参数audioSessionManager为空指针；<br>2. 参数strategy无效。<br>AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE：非法状态。 |

### OH_AudioSessionManager_DeactivateAudioSession()

```c
OH_AudioCommon_Result OH_AudioSessionManager_DeactivateAudioSession(OH_AudioSessionManager *audioSessionManager)
```

**描述：**

停用音频会话。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | [in] 指向[OH_AudioManager_GetAudioSessionManager](capi-native-audio-session-manager-h.md#oh_audiomanager_getaudiosessionmanager)创建的音频会话管理实例。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 函数执行成功。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) 参数audioSessionManager为空指针。</li> <li>[AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE](capi-native-audio-common-h.md#oh_audiocommon_result) 非法状态。</li> </ul> |

### OH_AudioSessionManager_IsAudioSessionActivated()

```c
bool OH_AudioSessionManager_IsAudioSessionActivated(OH_AudioSessionManager *audioSessionManager)
```

**描述：**

检查音频会话是否已激活。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | [in] 指向[OH_AudioManager_GetAudioSessionManager](capi-native-audio-session-manager-h.md#oh_audiomanager_getaudiosessionmanager)创建的音频会话管理实例。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| bool | 用于返回当前应用的音频会话是否已激活，true表示已激活，false表示已停用。 |

### OH_AudioSessionManager_RegisterSessionDeactivatedCallback()

```c
OH_AudioCommon_Result OH_AudioSessionManager_RegisterSessionDeactivatedCallback(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_DeactivatedCallback callback)
```

**描述：**

注册音频会话停用事件回调。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | [in] 指向[OH_AudioManager_GetAudioSessionManager](capi-native-audio-session-manager-h.md#oh_audiomanager_getaudiosessionmanager)创建的音频会话管理实例。 |
| [OH_AudioSession_DeactivatedCallback](capi-native-audio-session-manager-h.md#oh_audiosession_deactivatedcallback) callback | [in] 用于接收音频会话已停用事件。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 函数执行成功。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) 1. 参数audioSessionManager为空指针；2. 参数callback为空指针。</li> </ul> |

### OH_AudioSessionManager_UnregisterSessionDeactivatedCallback()

```c
OH_AudioCommon_Result OH_AudioSessionManager_UnregisterSessionDeactivatedCallback(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_DeactivatedCallback callback)
```

**描述：**

取消注册音频会话停用事件回调。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | [in] 指向[OH_AudioManager_GetAudioSessionManager](capi-native-audio-session-manager-h.md#oh_audiomanager_getaudiosessionmanager)创建的音频会话管理实例。 |
| [OH_AudioSession_DeactivatedCallback](capi-native-audio-session-manager-h.md#oh_audiosession_deactivatedcallback) callback | [in] 用于接收音频会话已停用事件。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 函数执行成功。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) 1. 参数audioSessionManager为空指针；2. 参数callback为空指针。</li> </ul> |

### OH_AudioSessionManager_SetScene()

```c
OH_AudioCommon_Result OH_AudioSessionManager_SetScene(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_Scene scene)
```

**描述：**

设置音频会话场景参数。 <br>设置会话场景后，音频会话将进入场景级模式，音频业务的生命周期与音频会话状态绑定， 焦点的请求和释放会跟随音频会话的激活和停止。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | [in] 指向[OH_AudioManager_GetAudioSessionManager](capi-native-audio-session-manager-h.md#oh_audiomanager_getaudiosessionmanager)创建的音频会话管理实例。 |
| [OH_AudioSession_Scene](capi-native-audio-session-manager-h.md#oh_audiosession_scene) scene | [in] 要设置的音频会话场景。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 函数执行成功。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) 1. 参数audioSessionManager为空指针；2. 参数scene为枚举范围外的值。</li> <li>[AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE](capi-native-audio-common-h.md#oh_audiocommon_result) 系统当前状态下不允许设置，例如音频会话状态异常。</li> <li>[AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) 系统异常，例如系统服务异常退出等。</li> </ul> |

### OH_AudioSessionManager_RegisterStateChangeCallback()

```c
OH_AudioCommon_Result OH_AudioSessionManager_RegisterStateChangeCallback(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_StateChangedCallback callback)
```

**描述：**

注册音频会话状态变更事件回调。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | [in] 指向[OH_AudioManager_GetAudioSessionManager](capi-native-audio-session-manager-h.md#oh_audiomanager_getaudiosessionmanager)创建的音频会话管理实例。 |
| [OH_AudioSession_StateChangedCallback](capi-native-audio-session-manager-h.md#oh_audiosession_statechangedcallback) callback | [in] 用于接收音频会话状态变更事件。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 函数执行成功。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) 1. 参数audioSessionManager为空指针；2. 参数callback为空指针。</li> <li>[AUDIOCOMMON_RESULT_ERROR_NO_MEMORY](capi-native-audio-common-h.md#oh_audiocommon_result) 系统内存申请异常。</li> <li>[AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) 系统异常，例如系统服务异常退出等。</li> </ul> |

### OH_AudioSessionManager_UnregisterStateChangeCallback()

```c
OH_AudioCommon_Result OH_AudioSessionManager_UnregisterStateChangeCallback(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_StateChangedCallback callback)
```

**描述：**

取消音频会话状态变更事件回调。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | [in] 指向[OH_AudioManager_GetAudioSessionManager](capi-native-audio-session-manager-h.md#oh_audiomanager_getaudiosessionmanager)创建的音频会话管理实例。 |
| [OH_AudioSession_StateChangedCallback](capi-native-audio-session-manager-h.md#oh_audiosession_statechangedcallback) callback | [in] 用于接收音频会话状态变更事件。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 函数执行成功。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) 1. 参数audioSessionManager为空指针；2. 参数callback为空指针。</li> <li>[AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) 系统异常，例如系统服务异常退出等。</li> </ul> |

### OH_AudioSessionManager_SetDefaultOutputDevice()

```c
OH_AudioCommon_Result OH_AudioSessionManager_SetDefaultOutputDevice(OH_AudioSessionManager *audioSessionManager, OH_AudioDevice_Type deviceType)
```

**描述：**

设置默认本机内置发声设备。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | [in] 指向[OH_AudioManager_GetAudioSessionManager](capi-native-audio-session-manager-h.md#oh_audiomanager_getaudiosessionmanager)创建的音频会话管理实例。 |
| [OH_AudioDevice_Type](capi-native-audio-device-base-h.md#oh_audiodevice_type) deviceType | [in] 指向[OH_AudioDevice_Type](capi-native-audio-device-base-h.md#oh_audiodevice_type)用于设置发声设备类型。可设置的设备类型包括： <br>AUDIO_DEVICE_TYPE_EARPIECE：听筒。 <br>AUDIO_DEVICE_TYPE_SPEAKER：扬声器。 <br>AUDIO_DEVICE_TYPE_DEFAULT：系统默认设备。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 函数执行成功。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) 1. 参数audioSessionManager为空指针；2. 参数deviceType超出枚举OH_AudioDevice_Type范围。</li> <li>[AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) 系统异常，例如系统服务异常退出等。</li> </ul> |

### OH_AudioSessionManager_GetDefaultOutputDevice()

```c
OH_AudioCommon_Result OH_AudioSessionManager_GetDefaultOutputDevice(OH_AudioSessionManager *audioSessionManager, OH_AudioDevice_Type *deviceType)
```

**描述：**

获取通过[OH_AudioSessionManager_SetDefaultOutputDevice](capi-native-audio-session-manager-h.md#oh_audiosessionmanager_setdefaultoutputdevice)设置的默认发声设备。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | [in] 指向[OH_AudioManager_GetAudioSessionManager](capi-native-audio-session-manager-h.md#oh_audiomanager_getaudiosessionmanager)创建的音频会话管理实例。 |
| [OH_AudioDevice_Type](capi-native-audio-device-base-h.md#oh_audiodevice_type) *deviceType | [out] 用于接收获取的发声设备类型。可返回的设备类型包括： <br>AUDIO_DEVICE_TYPE_EARPIECE：听筒。 <br>AUDIO_DEVICE_TYPE_SPEAKER：扬声器。 <br>AUDIO_DEVICE_TYPE_DEFAULT：系统默认设备。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 函数执行成功。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) 1. 参数audioSessionManager为空指针；2. 参数deviceType为空指针。</li> <li>[AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE](capi-native-audio-common-h.md#oh_audiocommon_result)系统当前状态下不允许获取默认设备类型，例如例如音频会话状态异常。</li> </ul> |

### OH_AudioSessionManager_ReleaseDevices()

```c
OH_AudioCommon_Result OH_AudioSessionManager_ReleaseDevices(OH_AudioSessionManager *audioSessionManager, OH_AudioDeviceDescriptorArray *audioDeviceDescriptorArray)
```

**描述：**

释放音频设备描述符数组对象。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | [in] 指向[OH_AudioManager_GetAudioSessionManager](capi-native-audio-session-manager-h.md#oh_audiomanager_getaudiosessionmanager)创建的音频会话管理实例。 |
| [OH_AudioDeviceDescriptorArray](capi-ohaudio-oh-audiodevicedescriptorarray.md) *audioDeviceDescriptorArray | [in] 需要释放的音频设备描述符数组。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 函数执行成功。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) 1. 参数audioSessionManager为空指针；2. 参数audioDeviceDescriptorArray为空指针。</li> </ul> |

### OH_AudioSessionManager_RegisterCurrentOutputDeviceChangeCallback()

```c
OH_AudioCommon_Result OH_AudioSessionManager_RegisterCurrentOutputDeviceChangeCallback(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_CurrentOutputDeviceChangedCallback callback)
```

**描述：**

注册当前输出设备变化回调。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | [in] 指向[OH_AudioManager_GetAudioSessionManager](capi-native-audio-session-manager-h.md#oh_audiomanager_getaudiosessionmanager)创建的音频会话管理实例。 |
| [OH_AudioSession_CurrentOutputDeviceChangedCallback](capi-native-audio-session-manager-h.md#oh_audiosession_currentoutputdevicechangedcallback) callback | [in] 用于返回音频设备变更信息的回调函数。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 函数执行成功。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) 1. 参数audioSessionManager为空指针；2. 参数callback为空指针。</li> <li>[AUDIOCOMMON_RESULT_ERROR_NO_MEMORY](capi-native-audio-common-h.md#oh_audiocommon_result) 系统内存申请异常。</li> <li>[AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) 系统异常，例如系统服务异常退出等。</li> </ul> |

### OH_AudioSessionManager_UnregisterCurrentOutputDeviceChangeCallback()

```c
OH_AudioCommon_Result OH_AudioSessionManager_UnregisterCurrentOutputDeviceChangeCallback(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_CurrentOutputDeviceChangedCallback callback)
```

**描述：**

取消注册当前输出设备变化回调。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | [in] 指向[OH_AudioManager_GetAudioSessionManager](capi-native-audio-session-manager-h.md#oh_audiomanager_getaudiosessionmanager)创建的音频会话管理实例。 |
| [OH_AudioSession_CurrentOutputDeviceChangedCallback](capi-native-audio-session-manager-h.md#oh_audiosession_currentoutputdevicechangedcallback) callback | [in] 用于返回音频设备变更信息的回调函数。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 函数执行成功。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) 1. 参数audioSessionManager为空指针；2. 参数callback为空指针。</li> <li>[AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) 系统异常，例如系统服务异常退出等。</li> </ul> |

### OH_AudioSessionManager_GetAvailableDevices()

```c
OH_AudioCommon_Result OH_AudioSessionManager_GetAvailableDevices(OH_AudioSessionManager *audioSessionManager, OH_AudioDevice_Usage deviceUsage, OH_AudioDeviceDescriptorArray **audioDeviceDescriptorArray)
```

**描述：**

获取音频可选设备列表。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | [in] 指向[OH_AudioManager_GetAudioSessionManager](capi-native-audio-session-manager-h.md#oh_audiomanager_getaudiosessionmanager)创建的音频会话管理实例。 |
| [OH_AudioDevice_Usage](capi-native-audio-device-base-h.md#oh_audiodevice_usage) deviceUsage | [in] 用于设置要获取的设备种类。 |
| [OH_AudioDeviceDescriptorArray](capi-ohaudio-oh-audiodevicedescriptorarray.md) **audioDeviceDescriptorArray | [out] 获取的可用音频设备描述符数组。 <br>不再继续使用audioDeviceDescriptorArray指针时，请使用[OH_AudioSessionManager_ReleaseDevices](capi-native-audio-session-manager-h.md#oh_audiosessionmanager_releasedevices)进行释放。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 函数执行成功。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) 1.参数audioSessionManager为空指针；2.参数deviceUsage无效；3.参数audioDeviceDescriptorArray为空指针。</li> <li>[AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) 系统异常，例如系统服务异常退出等。</li> </ul> |

### OH_AudioSessionManager_RegisterAvailableDevicesChangeCallback()

```c
OH_AudioCommon_Result OH_AudioSessionManager_RegisterAvailableDevicesChangeCallback(OH_AudioSessionManager *audioSessionManager, OH_AudioDevice_Usage deviceUsage, OH_AudioSession_AvailableDeviceChangedCallback callback)
```

**描述：**

注册可用设备更改回调。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | [in] 指向[OH_AudioManager_GetAudioSessionManager](capi-native-audio-session-manager-h.md#oh_audiomanager_getaudiosessionmanager)创建的音频会话管理实例。 |
| [OH_AudioDevice_Usage](capi-native-audio-device-base-h.md#oh_audiodevice_usage) deviceUsage | [in] 用于设置要获取的设备种类。 |
| [OH_AudioSession_AvailableDeviceChangedCallback](capi-native-audio-session-manager-h.md#oh_audiosession_availabledevicechangedcallback) callback | [in] 用于返回可用音频设备变更信息的回调函数。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 函数执行成功。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) 1. 参数audioSessionManager为空指针；2. 参数deviceUsage无效；3. 参数callback为空指针。</li> <li>[AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) 系统异常，例如系统服务异常退出等。</li> </ul> |

### OH_AudioSessionManager_UnregisterAvailableDevicesChangeCallback()

```c
OH_AudioCommon_Result OH_AudioSessionManager_UnregisterAvailableDevicesChangeCallback(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_AvailableDeviceChangedCallback callback)
```

**描述：**

取消注册可用设备更改回调。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | [in] 指向[OH_AudioManager_GetAudioSessionManager](capi-native-audio-session-manager-h.md#oh_audiomanager_getaudiosessionmanager)创建的音频会话管理实例。 |
| [OH_AudioSession_AvailableDeviceChangedCallback](capi-native-audio-session-manager-h.md#oh_audiosession_availabledevicechangedcallback) callback | [in] 用于返回可用音频设备变更信息的回调函数。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 函数执行成功。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) 1. 参数audioSessionManager为空指针；2. 参数callback为空指针。</li> <li>[AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) 系统异常，例如系统服务异常退出等。</li> </ul> |

### OH_AudioSessionManager_SelectMediaInputDevice()

```c
OH_AudioCommon_Result OH_AudioSessionManager_SelectMediaInputDevice(OH_AudioSessionManager *audioSessionManager, OH_AudioDeviceDescriptor *deviceDescriptor)
```

**描述：**

设置媒体输入设备。此功能不适用于呼叫录音，即[OH_AudioStream_SourceType](capi-native-audiostream-base-h.md#oh_audiostream_sourcetype) 为SOURCE_TYPE_VOICE_COMMUNICATION的场景不适用。 <br>在存在更高优先级的并发录音流的场景中，应用程序实际使用的输入设备可能与所选设备不同。 <br>应用程序可以使用[OH_AudioSessionManager_RegisterCurrentInputDeviceChangeCallback](capi-native-audio-session-manager-h.md#oh_audiosessionmanager_registercurrentinputdevicechangecallback) 注册一个回调来监听实际的输入设备。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | [in] 指向[OH_AudioManager_GetAudioSessionManager](capi-native-audio-session-manager-h.md#oh_audiomanager_getaudiosessionmanager)创建的音频会话管理实例。 |
| [OH_AudioDeviceDescriptor](capi-ohaudio-oh-audiodevicedescriptor.md) *deviceDescriptor | [in] 要设置的输入设备。可选设备必须在[OH_AudioSessionManager_GetAvailableDevices](capi-native-audio-session-manager-h.md#oh_audiosessionmanager_getavailabledevices) 返回的数组范围内。 <br>当设置空指针时，系统将清除上一次的设置。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 函数执行成功。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) 参数audioSessionManager为空指针。</li> <li>[AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) 系统异常，例如系统服务异常退出等。</li> </ul> |

### OH_AudioSessionManager_GetSelectedMediaInputDevice()

```c
OH_AudioCommon_Result OH_AudioSessionManager_GetSelectedMediaInputDevice(OH_AudioSessionManager *audioSessionManager, OH_AudioDeviceDescriptor **audioDeviceDescriptor)
```

**描述：**

获得通过[OH_AudioSessionManager_SelectMediaInputDevice](capi-native-audio-session-manager-h.md#oh_audiosessionmanager_selectmediainputdevice)设置的媒体输入设备。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | [in] 指向[OH_AudioManager_GetAudioSessionManager](capi-native-audio-session-manager-h.md#oh_audiomanager_getaudiosessionmanager)创建的音频会话管理实例。 |
| [OH_AudioDeviceDescriptor](capi-ohaudio-oh-audiodevicedescriptor.md) **audioDeviceDescriptor | [out] 通过[OH_AudioSessionManager_SelectMediaInputDevice](capi-native-audio-session-manager-h.md#oh_audiosessionmanager_selectmediainputdevice)设置的媒体设备， 如果没有设置， 返回一个类型为AUDIO_DEVICE_TYPE_INVALID的设备。 <br>不再继续使用audioDeviceDescriptor指针时，请使用[OH_AudioSessionManager_ReleaseDevice](capi-native-audio-session-manager-h.md#oh_audiosessionmanager_releasedevice)进行释放。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 函数执行成功。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) 1. 参数audioSessionManager为空指针；2. 参数audioDeviceDescriptor为空指针。</li> <li>[AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) 系统异常，例如系统服务异常退出等。</li> </ul> |

### OH_AudioSessionManager_SetBluetoothAndNearlinkPreferredRecordCategory()

```c
OH_AudioCommon_Result OH_AudioSessionManager_SetBluetoothAndNearlinkPreferredRecordCategory(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_BluetoothAndNearlinkPreferredRecordCategory category)
```

**描述：**

设置在使用蓝牙或星闪进行录音时，应用程序的设备偏好分类。应用程序可以在蓝牙或星闪连接之前设置此分类， 系统将在设备连接时优先使用蓝牙或星闪进行录音。 <br>在更高优先级的并发录音流的场景中，应用程序实际使用的输入设备可能与当前设置的偏好设备不同。 <br>应用程序可以使用[OH_AudioSessionManager_RegisterCurrentInputDeviceChangeCallback](capi-native-audio-session-manager-h.md#oh_audiosessionmanager_registercurrentinputdevicechangecallback) 注册一个回调来监听实际的输入设备。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | [in] 指向[OH_AudioManager_GetAudioSessionManager](capi-native-audio-session-manager-h.md#oh_audiomanager_getaudiosessionmanager)创建的音频会话管理实例。 |
| [OH_AudioSession_BluetoothAndNearlinkPreferredRecordCategory](capi-native-audio-session-manager-h.md#oh_audiosession_bluetoothandnearlinkpreferredrecordcategory) category | [in] 在使用蓝牙或星闪进行录音时，应用程序的设备偏好分类。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 函数执行成功。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) 1. 参数audioSessionManager为空指针；2. 参数category错误。</li> <li>[AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) 系统异常，例如系统服务异常退出等。</li> </ul> |

### OH_AudioSessionManager_GetBluetoothAndNearlinkPreferredRecordCategory()

```c
OH_AudioCommon_Result OH_AudioSessionManager_GetBluetoothAndNearlinkPreferredRecordCategory(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_BluetoothAndNearlinkPreferredRecordCategory *category)
```

**描述：**

获取应用程序设置的在使用蓝牙或星闪进行录音时的设备偏好分类。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | [in] 指向[OH_AudioManager_GetAudioSessionManager](capi-native-audio-session-manager-h.md#oh_audiomanager_getaudiosessionmanager)创建的音频会话管理实例。 |
| [OH_AudioSession_BluetoothAndNearlinkPreferredRecordCategory](capi-native-audio-session-manager-h.md#oh_audiosession_bluetoothandnearlinkpreferredrecordcategory) *category | [out] 在使用蓝牙或星闪进行录音时，应用程序的设备偏好分类。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 函数执行成功。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) 1. 参数audioSessionManager为空指针；2. 参数category为空指针。</li> <li>[AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) 系统异常，例如系统服务异常退出等。</li> </ul> |

### OH_AudioSessionManager_RegisterCurrentInputDeviceChangeCallback()

```c
OH_AudioCommon_Result OH_AudioSessionManager_RegisterCurrentInputDeviceChangeCallback(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_CurrentInputDeviceChangedCallback callback)
```

**描述：**

注册音频会话管理器的输入设备更改回调。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | [in] 指向[OH_AudioManager_GetAudioSessionManager](capi-native-audio-session-manager-h.md#oh_audiomanager_getaudiosessionmanager)创建的音频会话管理实例。 |
| [OH_AudioSession_CurrentInputDeviceChangedCallback](capi-native-audio-session-manager-h.md#oh_audiosession_currentinputdevicechangedcallback) callback | [in] 用于返回音频输入设备变更信息的回调函数。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 函数执行成功。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) 1. 参数audioSessionManager为空指针；2. 参数callback为空指针。</li> <li>[AUDIOCOMMON_RESULT_ERROR_NO_MEMORY](capi-native-audio-common-h.md#oh_audiocommon_result) 内存不足。</li> <li>[AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) 系统异常，例如系统服务异常退出等。</li> </ul> |

### OH_AudioSessionManager_UnregisterCurrentInputDeviceChangeCallback()

```c
OH_AudioCommon_Result OH_AudioSessionManager_UnregisterCurrentInputDeviceChangeCallback(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_CurrentInputDeviceChangedCallback callback)
```

**描述：**

取消注册音频会话管理器的输入设备更改回调。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | [in] 指向[OH_AudioManager_GetAudioSessionManager](capi-native-audio-session-manager-h.md#oh_audiomanager_getaudiosessionmanager)创建的音频会话管理实例。 |
| [OH_AudioSession_CurrentInputDeviceChangedCallback](capi-native-audio-session-manager-h.md#oh_audiosession_currentinputdevicechangedcallback) callback | [in] 用于返回音频输入设备变更信息的回调函数。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 函数执行成功。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) 1. 参数audioSessionManager为空指针；2. 参数callback为空指针。</li> <li>[AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) 系统异常，例如系统服务异常退出等。</li> </ul> |

### OH_AudioSessionManager_ReleaseDevice()

```c
OH_AudioCommon_Result OH_AudioSessionManager_ReleaseDevice(OH_AudioSessionManager *audioSessionManager, OH_AudioDeviceDescriptor *audioDeviceDescriptor)
```

**描述：**

释放音频设备描述符对象。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | [in] 指向[OH_AudioManager_GetAudioSessionManager](capi-native-audio-session-manager-h.md#oh_audiomanager_getaudiosessionmanager)创建的音频会话管理实例。 |
| [OH_AudioDeviceDescriptor](capi-ohaudio-oh-audiodevicedescriptor.md) *audioDeviceDescriptor | [in] 需要被释放的音频设备描述符对象。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 函数执行成功。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) 1. 参数audioSessionManager为空指针；2. 参数audioDeviceDescriptor为空指针。</li> </ul> |

### OH_AudioSessionManager_EnableMuteSuggestionWhenMixWithOthers()

```c
OH_AudioCommon_Result OH_AudioSessionManager_EnableMuteSuggestionWhenMixWithOthers(OH_AudioSessionManager *audioSessionManager, bool enable)
```

**描述：**

启用混音播放下接收静音播放建议通知功能。 通常，当使用混音模式时，如果有其他应用的音频同时播放，此时两者会混合播放。 部分场景下（如游戏或广播），应用可以通过启用静音建议通知，以为用户提供更好的体验。如果启用此功能， 当订阅音频会话状态更改事件后静音建议和取消静音建议提示将通过[OH_AudioSession_StateChangedCallback](capi-native-audio-session-manager-h.md#oh_audiosession_statechangedcallback)回调发送， 该回调由 [OH_AudioSessionManager_RegisterStateChangeCallback](capi-native-audio-session-manager-h.md#oh_audiosessionmanager_registerstatechangecallback)注册。 <br>收到静音建议表示其他应用程序开始播放音频，且播放的音频和本应用的音频不能混音。 此功能仅支持已设置[OH_AudioSession_Scene](capi-native-audio-session-manager-h.md#oh_audiosession_scene)并激活模式为 [OH_AudioSession_ConcurrencyMode](capi-native-audio-session-base-h.md#oh_audiosession_concurrencymode).CONCURRENCY_MIX_WITH_OTHERS的音频会话使用。 <br>并且仅在激活音频会话期间生效一次，每次激活音频会话前都必须重新启用。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | [in] 指向[OH_AudioManager_GetAudioSessionManager](capi-native-audio-session-manager-h.md#oh_audiomanager_getaudiosessionmanager)创建的音频会话管理实例。 |
| bool enable | [in] 表示是否启用静音建议回调功能。true表示启用，false表示不启用。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 函数执行成功。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) 参数audioSessionManager为空指针。</li> <li>[AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE](capi-native-audio-common-h.md#oh_audiocommon_result) 1. 未设置音频会话场景。2. 音频会话激活后调用此函数。</li> <li>[AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) 系统异常，例如系统服务异常退出等。</li> </ul> |

### OH_AudioSessionManager_IsOtherMediaPlaying()

```c
bool OH_AudioSessionManager_IsOtherMediaPlaying(OH_AudioSessionManager *audioSessionManager)
```

**描述：**

检查是否有其他应用正在播放音乐、视频、听书、游戏四种媒体类型的音频，已激活的媒体场景音频会话也将会被计入。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 23

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | [in] 指向[OH_AudioManager_GetAudioSessionManager](capi-native-audio-session-manager-h.md#oh_audiomanager_getaudiosessionmanager)创建的音频会话管理实例。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| bool | 是否有其他应用正在播放媒体类型的音频。true表示有，false表示没有。 |

### OH_AudioSessionManager_SetCaptureMuteHint()

```c
OH_AudioCommon_Result OH_AudioSessionManager_SetCaptureMuteHint(OH_AudioSessionManager *audioSessionManager, bool mute)
```

**描述：**

应用将当前音频会话内录音流的自身静音状态传递给系统音频模块。 <br>该接口用于向系统音频模块上报当前音频会话内录音流的静音状态，不会改变录音流的实际静音状态。 <br>系统音频模块在设备底层能力支持的情况下，根据设置的状态调整策略以降低功耗。 <br>该接口仅在当前音频会话存在运行中的录音流时允许调用，否则返回错误码AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE。 <br>若某条录音流同时调用了流级接口和本接口，流级接口设置优先级更高，以流级接口设置值为准。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | [in] 指向[OH_AudioManager_GetAudioSessionManager](capi-native-audio-session-manager-h.md#oh_audiomanager_getaudiosessionmanager)返回的音频会话管理实例。 |
| bool mute | [in] 当应用自身已将录音流静音时，传入true，表示将当前应用下的录音流标记为静音。解除静音时，传入false。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 函数执行成功。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) 参数audioSessionManager为空指针。</li> <li>[AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE](capi-native-audio-common-h.md#oh_audiocommon_result) 操作状态异常，当前进程不存在运行中的录音流。</li> <li>[AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) 系统异常，例如系统服务异常退出等。</li> </ul> |

### OH_AudioSessionManager_SetBehavior()

```c
OH_AudioCommon_Result OH_AudioSessionManager_SetBehavior(OH_AudioSessionManager *audioSessionManager, uint32_t behavior)
```

**描述：**

设置音频会话行为参数（支持多种标志位的组合使用）。 当音频会话在激活状态时调用此接口后，必须重新调用接口[OH_AudioSessionManager_ActivateAudioSession](capi-native-audio-session-manager-h.md#oh_audiosessionmanager_activateaudiosession)使其生效。 若未调用此接口，系统将使用默认行为参数。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | [in] 指向[OH_AudioManager_GetAudioSessionManager](capi-native-audio-session-manager-h.md#oh_audiomanager_getaudiosessionmanager)创建的音频会话管理实例。 |
| uint32_t behavior | [in] 音频会话行为标志，可以是单个标志，也可以是多个标志的按位OR组合。 当前支持的音频会话行为详见[OH_AudioSession_BehaviorFlags](capi-native-audio-session-base-h.md#oh_audiosession_behaviorflags)。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 函数执行成功。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) 参数为空指针或超出范围。</li> <li>[AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE](capi-native-audio-common-h.md#oh_audiocommon_result) 非法状态。</li> </ul> |


