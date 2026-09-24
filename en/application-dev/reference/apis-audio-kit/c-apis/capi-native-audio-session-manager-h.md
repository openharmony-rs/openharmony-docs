# native_audio_session_manager.h

## Overview

Declare audio session manager related interfaces.<br> This file interfaces are used for the creation of audioSessionManager as well as activating/deactivating the audio session as well as checking and listening the audio session deactivated events.

**Library**: libohaudio.so

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 10

**Related module**: [OHAudio](capi-ohaudio.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AudioSession_DeactivatedEvent](capi-ohaudio-oh-audiosession-deactivatedevent.md) | OH_AudioSession_DeactivatedEvent | declare the audio session deactivated event |
| [OH_AudioSession_StateChangedEvent](capi-ohaudio-oh-audiosession-statechangedevent.md) | OH_AudioSession_StateChangedEvent | declare the audio session state change event |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) | OH_AudioSessionManager | Declare the audio session manager. The handle of audio session manager is used for audio session related functions. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AudioSession_Scene](#oh_audiosession_scene) | OH_AudioSession_Scene | Declare the audio session scene. |
| [OH_AudioSession_StateChangeHint](#oh_audiosession_statechangehint) | OH_AudioSession_StateChangeHint | Declare the audio session state change hints. |
| [OH_AudioSession_OutputDeviceChangeRecommendedAction](#oh_audiosession_outputdevicechangerecommendedaction) | OH_AudioSession_OutputDeviceChangeRecommendedAction | Declare the recommend action when device change. |
| [OH_AudioSession_DeactivatedReason](#oh_audiosession_deactivatedreason) | OH_AudioSession_DeactivatedReason | Declare the audio deactivated reasons. |
| [OH_AudioSession_BluetoothAndNearlinkPreferredRecordCategory](#oh_audiosession_bluetoothandnearlinkpreferredrecordcategory) | OH_AudioSession_BluetoothAndNearlinkPreferredRecordCategory | Enumerates the categories application prefer to use when recording with bluetooth and nearlink. |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef void (\*OH_AudioSession_StateChangedCallback)(OH_AudioSession_StateChangedEvent event)](#oh_audiosession_statechangedcallback) | OH_AudioSession_StateChangedCallback | This function pointer will point to the callback function that is used to return the audio session state change event. |
| [typedef void (\*OH_AudioSession_AvailableDeviceChangedCallback)(OH_AudioDevice_ChangeType type, OH_AudioDeviceDescriptorArray *audioDeviceDescriptorArray)](#oh_audiosession_availabledevicechangedcallback) | OH_AudioSession_AvailableDeviceChangedCallback | This function pointer will point to the callback function that is used to return the changing audio device descriptors. There may be more than one audio device descriptor returned. |
| [typedef void (\*OH_AudioSession_CurrentInputDeviceChangedCallback)(OH_AudioDeviceDescriptorArray *devices, OH_AudioStream_DeviceChangeReason changeReason)](#oh_audiosession_currentinputdevicechangedcallback) | OH_AudioSession_CurrentInputDeviceChangedCallback | This function pointer will point to the callback function that is used to return the audio session input device change event. |
| [typedef void (\*OH_AudioSession_CurrentOutputDeviceChangedCallback)(OH_AudioDeviceDescriptorArray *devices, OH_AudioStream_DeviceChangeReason changeReason, OH_AudioSession_OutputDeviceChangeRecommendedAction recommendedAction)](#oh_audiosession_currentoutputdevicechangedcallback) | OH_AudioSession_CurrentOutputDeviceChangedCallback | This function pointer will point to the callback function that is used to return the audio session device change event. |
| [typedef int32_t (\*OH_AudioSession_DeactivatedCallback)(OH_AudioSession_DeactivatedEvent event)](#oh_audiosession_deactivatedcallback) | OH_AudioSession_DeactivatedCallback | This function pointer will point to the callback function that is used to return the audio session deactivated event. |
| [OH_AudioCommon_Result OH_AudioManager_GetAudioSessionManager(OH_AudioSessionManager **audioSessionManager)](#oh_audiomanager_getaudiosessionmanager) | - | Fetch the audio session manager handle. The audio session manager handle should be the first parameter in audio session related functions |
| [OH_AudioCommon_Result OH_AudioSessionManager_ActivateAudioSession(OH_AudioSessionManager *audioSessionManager, const OH_AudioSession_Strategy *strategy)](#oh_audiosessionmanager_activateaudiosession) | - | Activate the audio session for the current pid application. If [OH_AudioSessionManager_SetScene](capi-native-audio-session-manager-h.md#oh_audiosessionmanager_setscene) is called, it will take focus when calling this method. If you want to take focus again after [OH_AudioSessionManager_DeactivateAudioSession](capi-native-audio-session-manager-h.md#oh_audiosessionmanager_deactivateaudiosession) is called, you must call [OH_AudioSessionManager_SetScene](capi-native-audio-session-manager-h.md#oh_audiosessionmanager_setscene) again. |
| [OH_AudioCommon_Result OH_AudioSessionManager_DeactivateAudioSession(OH_AudioSessionManager *audioSessionManager)](#oh_audiosessionmanager_deactivateaudiosession) | - | Deactivate the audio session for the current pid application. |
| [bool OH_AudioSessionManager_IsAudioSessionActivated(OH_AudioSessionManager *audioSessionManager)](#oh_audiosessionmanager_isaudiosessionactivated) | - | Querying whether the current pid application has an activated audio session. |
| [OH_AudioCommon_Result OH_AudioSessionManager_RegisterSessionDeactivatedCallback(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_DeactivatedCallback callback)](#oh_audiosessionmanager_registersessiondeactivatedcallback) | - | Register the audio session deactivated event callback. |
| [OH_AudioCommon_Result OH_AudioSessionManager_UnregisterSessionDeactivatedCallback(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_DeactivatedCallback callback)](#oh_audiosessionmanager_unregistersessiondeactivatedcallback) | - | Unregister the audio session deactivated event callback. |
| [OH_AudioCommon_Result OH_AudioSessionManager_SetScene(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_Scene scene)](#oh_audiosessionmanager_setscene) | - | Set scene for audio session. |
| [OH_AudioCommon_Result OH_AudioSessionManager_RegisterStateChangeCallback(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_StateChangedCallback callback)](#oh_audiosessionmanager_registerstatechangecallback) | - | Register the audio session state change event callback. |
| [OH_AudioCommon_Result OH_AudioSessionManager_UnregisterStateChangeCallback(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_StateChangedCallback callback)](#oh_audiosessionmanager_unregisterstatechangecallback) | - | Unregister the audio session state change event callback. |
| [OH_AudioCommon_Result OH_AudioSessionManager_SetDefaultOutputDevice(OH_AudioSessionManager *audioSessionManager, OH_AudioDevice_Type deviceType)](#oh_audiosessionmanager_setdefaultoutputdevice) | - | Sets the default output device. This function applys on audiorenderers whose StreamUsage are STREAM_USAGE_VOICE_COMMUNICATION/STREAM_USAGE_VIDEO_COMMUNICATION/STREAM_USAGE_VOICE_MESSAGE. Setting the device will only takes effect if no other accessory such as headphones are in use |
| [OH_AudioCommon_Result OH_AudioSessionManager_GetDefaultOutputDevice(OH_AudioSessionManager *audioSessionManager, OH_AudioDevice_Type *deviceType)](#oh_audiosessionmanager_getdefaultoutputdevice) | - | Gets the default output device. |
| [OH_AudioCommon_Result OH_AudioSessionManager_ReleaseDevices(OH_AudioSessionManager *audioSessionManager, OH_AudioDeviceDescriptorArray *audioDeviceDescriptorArray)](#oh_audiosessionmanager_releasedevices) | - | Release the audio device descriptor array object. |
| [OH_AudioCommon_Result OH_AudioSessionManager_RegisterCurrentOutputDeviceChangeCallback(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_CurrentOutputDeviceChangedCallback callback)](#oh_audiosessionmanager_registercurrentoutputdevicechangecallback) | - | Register the audio session device change event callback. |
| [OH_AudioCommon_Result OH_AudioSessionManager_UnregisterCurrentOutputDeviceChangeCallback(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_CurrentOutputDeviceChangedCallback callback)](#oh_audiosessionmanager_unregistercurrentoutputdevicechangecallback) | - | Unregister the audio session device change event callback. |
| [OH_AudioCommon_Result OH_AudioSessionManager_GetAvailableDevices(OH_AudioSessionManager *audioSessionManager, OH_AudioDevice_Usage deviceUsage, OH_AudioDeviceDescriptorArray **audioDeviceDescriptorArray)](#oh_audiosessionmanager_getavailabledevices) | - | Get available devices by device usage. |
| [OH_AudioCommon_Result OH_AudioSessionManager_RegisterAvailableDevicesChangeCallback(OH_AudioSessionManager *audioSessionManager, OH_AudioDevice_Usage deviceUsage, OH_AudioSession_AvailableDeviceChangedCallback callback)](#oh_audiosessionmanager_registeravailabledeviceschangecallback) | - | Register available device change event callback. |
| [OH_AudioCommon_Result OH_AudioSessionManager_UnregisterAvailableDevicesChangeCallback(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_AvailableDeviceChangedCallback callback)](#oh_audiosessionmanager_unregisteravailabledeviceschangecallback) | - | Unregister available device change event callback. |
| [OH_AudioCommon_Result OH_AudioSessionManager_SelectMediaInputDevice(OH_AudioSessionManager *audioSessionManager, OH_AudioDeviceDescriptor *deviceDescriptor)](#oh_audiosessionmanager_selectmediainputdevice) | - | Sets the media input device. This function is not valid for call recording, whose SourceType is SOURCE_TYPE_VOICE_CALL or SOURCE_TYPE_VOICE_COMMUNICATION. In scenarios where there are concurrent recording streams with higher priority, the actual input device used by the application may differ from the selected one. The application can use [OH_AudioSessionManager_RegisterCurrentInputDeviceChangeCallback](capi-native-audio-session-manager-h.md#oh_audiosessionmanager_registercurrentinputdevicechangecallback) to register a callback to listen for the actual input device. |
| [OH_AudioCommon_Result OH_AudioSessionManager_GetSelectedMediaInputDevice(OH_AudioSessionManager *audioSessionManager, OH_AudioDeviceDescriptor **audioDeviceDescriptor)](#oh_audiosessionmanager_getselectedmediainputdevice) | - | Gets the selected media input device. |
| [OH_AudioCommon_Result OH_AudioSessionManager_SetBluetoothAndNearlinkPreferredRecordCategory(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_BluetoothAndNearlinkPreferredRecordCategory category)](#oh_audiosessionmanager_setbluetoothandnearlinkpreferredrecordcategory) | - | Sets the preferred record category with bluetooth and nearlink device. The application can set this category before bluetooth and nearlink connected, and the system will prefer to use bluetooth and nearlink to record when the device connected. In scenarios where there are concurrent recording streams with higher priority, the actual input device used by the application may differ from the preferred one. The application can use [OH_AudioSessionManager_RegisterCurrentInputDeviceChangeCallback](capi-native-audio-session-manager-h.md#oh_audiosessionmanager_registercurrentinputdevicechangecallback) to register a callback to listen for the actual input device. |
| [OH_AudioCommon_Result OH_AudioSessionManager_GetBluetoothAndNearlinkPreferredRecordCategory(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_BluetoothAndNearlinkPreferredRecordCategory *category)](#oh_audiosessionmanager_getbluetoothandnearlinkpreferredrecordcategory) | - | Gets the preferred record category with bluetooth and nearlink device. |
| [OH_AudioCommon_Result OH_AudioSessionManager_RegisterCurrentInputDeviceChangeCallback(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_CurrentInputDeviceChangedCallback callback)](#oh_audiosessionmanager_registercurrentinputdevicechangecallback) | - | Register the audio session input device change event callback. |
| [OH_AudioCommon_Result OH_AudioSessionManager_UnregisterCurrentInputDeviceChangeCallback(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_CurrentInputDeviceChangedCallback callback)](#oh_audiosessionmanager_unregistercurrentinputdevicechangecallback) | - | Unregister the audio session input device change event callback. |
| [OH_AudioCommon_Result OH_AudioSessionManager_ReleaseDevice(OH_AudioSessionManager *audioSessionManager, OH_AudioDeviceDescriptor *audioDeviceDescriptor)](#oh_audiosessionmanager_releasedevice) | - | Release the audio device descriptor object. |
| [OH_AudioCommon_Result OH_AudioSessionManager_EnableMuteSuggestionWhenMixWithOthers(OH_AudioSessionManager *audioSessionManager, bool enable)](#oh_audiosessionmanager_enablemutesuggestionwhenmixwithothers) | - | Enables mute suggestion callback function when using [CONCURRENCY_MIX_WITH_OTHERS](capi-native-audio-session-base-h.md#oh_audiosession_concurrencymode) mode. Usually when using mix mode, application won't receive state change event when there is another audio playing simultaneously. But in some scenarios, like game or radio, the application may intend to mute its audio to achieve better user experience. If enabled, the mute and unmute suggestion hint will be sent by [OH_AudioSession_StateChangedCallback](capi-native-audio-session-manager-h.md#oh_audiosession_statechangedcallback) registered by [OH_AudioSessionManager_RegisterStateChangeCallback](capi-native-audio-session-manager-h.md#oh_audiosessionmanager_registerstatechangecallback). Mute suggestion means there is another application starting non-mixable audio. This function only supports audio session with [OH_AudioSession_Scene](capi-native-audio-session-manager-h.md#oh_audiosession_scene) set and activated with [CONCURRENCY_MIX_WITH_OTHERS](capi-native-audio-session-base-h.md#oh_audiosession_concurrencymode) mode. And it takes effect only once during activation, so application need to enable it every time before activation. |
| [bool OH_AudioSessionManager_IsOtherMediaPlaying(OH_AudioSessionManager *audioSessionManager)](#oh_audiosessionmanager_isothermediaplaying) | - | Returns if there is any other application playing audio in media usage, including media session activated. |
| [OH_AudioCommon_Result OH_AudioSessionManager_SetCaptureMuteHint(OH_AudioSessionManager *audioSessionManager, bool mute)](#oh_audiosessionmanager_setcapturemutehint) | - | Sets recording mute state to audio system. This method is used as a hint for power optimization, it does not mute the recording stream, only affects internal processing strategy. Audio system may disable some recording effects when application notifies its muted state to system. Mute hint state can only be set when there is at least one running stream in current process. |
| [OH_AudioCommon_Result OH_AudioSessionManager_SetBehavior(OH_AudioSessionManager *audioSessionManager, uint32_t behavior)](#oh_audiosessionmanager_setbehavior) | - | Set audio session behavior parameters (supporting multiple flag combinations) This interface takes effect only after the interface [OH_AudioSessionManager_SetScene](capi-native-audio-session-manager-h.md#oh_audiosessionmanager_setscene) is called. Each time you call this interface to set parameters, you need to call the interface [OH_AudioSessionManager_ActivateAudioSession](capi-native-audio-session-manager-h.md#oh_audiosessionmanager_activateaudiosession) again for the settings to take effect. |

### Variable

| Name | Description |
| -- | -- |
| void (*OH_AudioSession_StateChangedCallback) ( OH_AudioSession_StateChangedEvent event) | This function pointer will point to the callback function that is used to return the audio session state change event.<br>**Since**: 20 |
| void (*OH_AudioSession_AvailableDeviceChangedCallback) ( OH_AudioDevice_ChangeType type, OH_AudioDeviceDescriptorArray *audioDeviceDescriptorArray) | This function pointer will point to the callback function that is used to return the changing audio device descriptors. There may be more than one audio device descriptor returned.<br>**Since**: 21 |
| void (*OH_AudioSession_CurrentInputDeviceChangedCallback) ( OH_AudioDeviceDescriptorArray *devices, OH_AudioStream_DeviceChangeReason changeReason) | This function pointer will point to the callback function that is used to return the audio session input device change event.<br>**Since**: 21 |
| void (*OH_AudioSession_CurrentOutputDeviceChangedCallback) ( OH_AudioDeviceDescriptorArray *devices, OH_AudioStream_DeviceChangeReason changeReason, OH_AudioSession_OutputDeviceChangeRecommendedAction recommendedAction) | This function pointer will point to the callback function that is used to return the audio session device change event.<br>**Since**: 20 |
| int32_t (*OH_AudioSession_DeactivatedCallback) ( OH_AudioSession_DeactivatedEvent event) | This function pointer will point to the callback function that is used to return the audio session deactivated event.<br>**Since**: 12 |

## Enum type description

### OH_AudioSession_Scene

```c
enum OH_AudioSession_Scene
```

**Description**

Declare the audio session scene.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 20

| Enum item | Description |
| -- | -- |
| AUDIO_SESSION_SCENE_MEDIA = 0 | scene for media |
| AUDIO_SESSION_SCENE_GAME = 1 | scene for game |
| AUDIO_SESSION_SCENE_VOICE_COMMUNICATION = 2 | scene for voice communication |

### OH_AudioSession_StateChangeHint

```c
enum OH_AudioSession_StateChangeHint
```

**Description**

Declare the audio session state change hints.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 20

| Enum item | Description |
| -- | -- |
| AUDIO_SESSION_STATE_CHANGE_HINT_RESUME = 0 | Resume the playback |
| AUDIO_SESSION_STATE_CHANGE_HINT_PAUSE = 1 | paused/pause the playback |
| AUDIO_SESSION_STATE_CHANGE_HINT_STOP = 2 | stopped/stop the playback. |
| AUDIO_SESSION_STATE_CHANGE_HINT_TIME_OUT_STOP = 3 | stopped/stop the playback due to no audio stream for a long time. |
| AUDIO_SESSION_STATE_CHANGE_HINT_DUCK = 4 | Ducked the playback. (In ducking, the audio volume is reduced, but not silenced.) |
| AUDIO_SESSION_STATE_CHANGE_HINT_UNDUCK = 5 | Unducked the playback. |
| AUDIO_SESSION_STATE_CHANGE_HINT_MUTE_SUGGESTION = 6 | Suggests to mute the playback because there is another application begin to play nonmixable audio, application can decide whether to mute. If interrupt strategy is duck, [AUDIO_SESSION_STATE_CHANGE_HINT_DUCK](capi-native-audio-session-manager-h.md#oh_audiosession_statechangehint) will replace mute suggestion event, but application can still decide to mute when receive hint duck.<br>**Since**: 23 |
| AUDIO_SESSION_STATE_CHANGE_HINT_UNMUTE_SUGGESTION = 7 | Suggest to unmute the playback because another application's nonmixable audio ends, application can decide whether to mute. If interrupt strategy is unduck, [AUDIO_SESSION_STATE_CHANGE_HINT_UNDUCK](capi-native-audio-session-manager-h.md#oh_audiosession_statechangehint) will replace unmute suggestion event, but application can still decide to unmute when receive hint unduck.<br>**Since**: 23 |
| AUDIO_SESSION_STATE_CHANGE_HINT_MUTE = 8 | The hint can be received only after the parameter {@link #OH_AudioSession_BehaviorFlags.MUTE_WHEN_INTERRUPTED} has been set by the interface [OH_AudioSessionManager_SetBehavior](capi-native-audio-session-manager-h.md#oh_audiosessionmanager_setbehavior)<br>and [OH_AudioSessionManager_SetScene](capi-native-audio-session-manager-h.md#oh_audiosessionmanager_setscene) has been called, and the audio session has been activated. After the hint is received, the audio stream is muted.<br>**Since**: 24 |
| AUDIO_SESSION_STATE_CHANGE_HINT_UNMUTE = 9 | The hint can be received only after the parameter {@link #OH_AudioSession_BehaviorFlags.MUTE_WHEN_INTERRUPTED} has been set by the interface [OH_AudioSessionManager_SetBehavior](capi-native-audio-session-manager-h.md#oh_audiosessionmanager_setbehavior)<br>and [OH_AudioSessionManager_SetScene](capi-native-audio-session-manager-h.md#oh_audiosessionmanager_setscene) has been called, and the audio session has been activated. When the hint is received, the audio stream is unmuted.<br>**Since**: 24 |

### OH_AudioSession_OutputDeviceChangeRecommendedAction

```c
enum OH_AudioSession_OutputDeviceChangeRecommendedAction
```

**Description**

Declare the recommend action when device change.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 20

| Enum item | Description |
| -- | -- |
| DEVICE_CHANGE_RECOMMEND_TO_CONTINUE = 0 | Recommend to continue the playback. This event indicates that the application does not need to stop audio playback when switching devices. However, it should not be used to restart audio playback that has already been paused or stopped. |
| DEVICE_CHANGE_RECOMMEND_TO_STOP = 1 | recommend to stop the playback. |

### OH_AudioSession_DeactivatedReason

```c
enum OH_AudioSession_DeactivatedReason
```

**Description**

Declare the audio deactivated reasons.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 12

| Enum item | Description |
| -- | -- |
| DEACTIVATED_LOWER_PRIORITY = 0 | deactivated because of lower priority |
| DEACTIVATED_TIMEOUT = 1 | deactivated because of timing out |

### OH_AudioSession_BluetoothAndNearlinkPreferredRecordCategory

```c
enum OH_AudioSession_BluetoothAndNearlinkPreferredRecordCategory
```

**Description**

Enumerates the categories application prefer to use when recording with bluetooth and nearlink.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 21

| Enum item | Description |
| -- | -- |
| PREFERRED_NONE = 0 | Not prefer to use bluetooth and nearlink record. |
| PREFERRED_DEFAULT = 1 | Prefer to use bluetooth and nearlink record. However, whether to use low latency or high quality recording depends on system. |
| PREFERRED_LOW_LATENCY = 2 | Prefer to use bluetooth and nearlink low latency mode to record. |
| PREFERRED_HIGH_QUALITY = 3 | Prefer to use bluetooth and nearlink high quality mode to record. |


## Function description

### OH_AudioSession_StateChangedCallback()

```c
typedef void (*OH_AudioSession_StateChangedCallback)(OH_AudioSession_StateChangedEvent event)
```

**Description**

This function pointer will point to the callback function that is used to return the audio session state change event.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioSession_StateChangedEvent](capi-ohaudio-oh-audiosession-statechangedevent.md) event | the [OH_AudioSession_StateChangedEvent](capi-ohaudio-oh-audiosession-statechangedevent.md) state change triggering event. |

### OH_AudioSession_AvailableDeviceChangedCallback()

```c
typedef void (*OH_AudioSession_AvailableDeviceChangedCallback)(OH_AudioDevice_ChangeType type, OH_AudioDeviceDescriptorArray *audioDeviceDescriptorArray)
```

**Description**

This function pointer will point to the callback function that is used to return the changing audio device descriptors. There may be more than one audio device descriptor returned.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioDevice_ChangeType type | the [OH_AudioDevice_ChangeType](capi-native-audio-device-base-h.md#oh_audiodevice_changetype) is connect or disconnect. |
| OH_AudioDeviceDescriptorArray \*audioDeviceDescriptorArray | the [OH_AudioDeviceDescriptorArray](capi-ohaudio-oh-audiodevicedescriptorarray.md) pointer variable which will be set the audio device descriptors value. Do not release the audioDeviceDescriptorArray pointer separately instead call [OH_AudioSessionManager_ReleaseDevices](capi-native-audio-session-manager-h.md#oh_audiosessionmanager_releasedevices) to release the DeviceDescriptor array when it is no use anymore. |

### OH_AudioSession_CurrentInputDeviceChangedCallback()

```c
typedef void (*OH_AudioSession_CurrentInputDeviceChangedCallback)(OH_AudioDeviceDescriptorArray *devices, OH_AudioStream_DeviceChangeReason changeReason)
```

**Description**

This function pointer will point to the callback function that is used to return the audio session input device change event.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| audioDeviceDescriptorArray | the [OH_AudioDeviceDescriptorArray](capi-ohaudio-oh-audiodevicedescriptorarray.md) pointer variable which will be set the audio input device descriptors value. Do not release the audioDeviceDescriptorArray pointer separately instead call [OH_AudioSessionManager_ReleaseDevices](capi-native-audio-session-manager-h.md#oh_audiosessionmanager_releasedevices) to release the DeviceDescriptor array when it is no use anymore. |
| OH_AudioStream_DeviceChangeReason changeReason | the [OH_AudioStream_DeviceChangeReason](capi-native-audiostream-base-h.md#oh_audiostream_devicechangereason) indicates that why does the input device changes. |

### OH_AudioSession_CurrentOutputDeviceChangedCallback()

```c
typedef void (*OH_AudioSession_CurrentOutputDeviceChangedCallback)(OH_AudioDeviceDescriptorArray *devices, OH_AudioStream_DeviceChangeReason changeReason, OH_AudioSession_OutputDeviceChangeRecommendedAction recommendedAction)
```

**Description**

This function pointer will point to the callback function that is used to return the audio session device change event.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| audioDeviceDescriptorArray | the [OH_AudioDeviceDescriptorArray](capi-ohaudio-oh-audiodevicedescriptorarray.md) pointer variable which will be set the audio device descriptors value. Do not release the audioDeviceDescriptorArray pointer separately instead call [OH_AudioSessionManager_ReleaseDevices](capi-native-audio-session-manager-h.md#oh_audiosessionmanager_releasedevices) to release the DeviceDescriptor array when it is no use anymore. |
| OH_AudioStream_DeviceChangeReason changeReason | the [OH_AudioStream_DeviceChangeReason](capi-native-audiostream-base-h.md#oh_audiostream_devicechangereason) indicates that why does the device changes. |
| [OH_AudioSession_OutputDeviceChangeRecommendedAction](capi-native-audio-session-manager-h.md#oh_audiosession_outputdevicechangerecommendedaction) recommendedAction | the [OH_AudioSession_OutputDeviceChangeRecommendedAction](capi-native-audio-session-manager-h.md#oh_audiosession_outputdevicechangerecommendedaction) recommend action when device change. |

### OH_AudioSession_DeactivatedCallback()

```c
typedef int32_t (*OH_AudioSession_DeactivatedCallback)(OH_AudioSession_DeactivatedEvent event)
```

**Description**

This function pointer will point to the callback function that is used to return the audio session deactivated event.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioSession_DeactivatedEvent](capi-ohaudio-oh-audiosession-deactivatedevent.md) event | the [OH_AudioSession_DeactivatedEvent](capi-ohaudio-oh-audiosession-deactivatedevent.md) deactivated triggering event. |

### OH_AudioManager_GetAudioSessionManager()

```c
OH_AudioCommon_Result OH_AudioManager_GetAudioSessionManager(OH_AudioSessionManager **audioSessionManager)
```

**Description**

Fetch the audio session manager handle. The audio session manager handle should be the first parameter in audio session related functions

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) **audioSessionManager | the [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) which will be returned as the output parameter |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | [AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) if execution succeeds  or [AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) if system state error |

### OH_AudioSessionManager_ActivateAudioSession()

```c
OH_AudioCommon_Result OH_AudioSessionManager_ActivateAudioSession(OH_AudioSessionManager *audioSessionManager, const OH_AudioSession_Strategy *strategy)
```

**Description**

Activate the audio session for the current pid application. If [OH_AudioSessionManager_SetScene](capi-native-audio-session-manager-h.md#oh_audiosessionmanager_setscene) is called, it will take focus when calling this method. If you want to take focus again after [OH_AudioSessionManager_DeactivateAudioSession](capi-native-audio-session-manager-h.md#oh_audiosessionmanager_deactivateaudiosession) is called, you must call [OH_AudioSessionManager_SetScene](capi-native-audio-session-manager-h.md#oh_audiosessionmanager_setscene) again.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | the [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) returned by the [OH_AudioManager_GetAudioSessionManager](capi-native-audio-session-manager-h.md#oh_audiomanager_getaudiosessionmanager) |
| const OH_AudioSession_Strategy *strategy | pointer of [OH_AudioSession_Strategy](capi-ohaudio-oh-audiosession-strategy.md) which is used for setting audio session strategy |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | <ul><li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) if execution succeeds</li><li>     [AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) if parameter validation fails</li><li>     [AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE](capi-native-audio-common-h.md#oh_audiocommon_result) if system illegal state</li></ul> |

### OH_AudioSessionManager_DeactivateAudioSession()

```c
OH_AudioCommon_Result OH_AudioSessionManager_DeactivateAudioSession(OH_AudioSessionManager *audioSessionManager)
```

**Description**

Deactivate the audio session for the current pid application.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | the [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) returned by the [OH_AudioManager_GetAudioSessionManager](capi-native-audio-session-manager-h.md#oh_audiomanager_getaudiosessionmanager) |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | <ul><li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) if execution succeeds</li><li>     [AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) if parameter validation fails</li><li>     [AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE](capi-native-audio-common-h.md#oh_audiocommon_result) if system illegal state</li></ul> |

### OH_AudioSessionManager_IsAudioSessionActivated()

```c
bool OH_AudioSessionManager_IsAudioSessionActivated(OH_AudioSessionManager *audioSessionManager)
```

**Description**

Querying whether the current pid application has an activated audio session.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | the [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) returned by the [OH_AudioManager_GetAudioSessionManager](capi-native-audio-session-manager-h.md#oh_audiomanager_getaudiosessionmanager) |

**Returns**:

| Type | Description |
| -- | -- |
| bool | True when the current pid application has an activated audio session  False when it does not |

### OH_AudioSessionManager_RegisterSessionDeactivatedCallback()

```c
OH_AudioCommon_Result OH_AudioSessionManager_RegisterSessionDeactivatedCallback(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_DeactivatedCallback callback)
```

**Description**

Register the audio session deactivated event callback.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | the [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) returned by the [OH_AudioManager_GetAudioSessionManager](capi-native-audio-session-manager-h.md#oh_audiomanager_getaudiosessionmanager) |
| [OH_AudioSession_DeactivatedCallback](capi-native-audio-session-manager-h.md#oh_audiosession_deactivatedcallback) callback | the [OH_AudioSession_DeactivatedCallback](capi-native-audio-session-manager-h.md#oh_audiosession_deactivatedcallback) which is used to receive the deactivated event |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | [AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) if execution succeeds  or [AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) if parameter validation fails |

### OH_AudioSessionManager_UnregisterSessionDeactivatedCallback()

```c
OH_AudioCommon_Result OH_AudioSessionManager_UnregisterSessionDeactivatedCallback(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_DeactivatedCallback callback)
```

**Description**

Unregister the audio session deactivated event callback.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | the [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) returned by the [OH_AudioManager_GetAudioSessionManager](capi-native-audio-session-manager-h.md#oh_audiomanager_getaudiosessionmanager) |
| [OH_AudioSession_DeactivatedCallback](capi-native-audio-session-manager-h.md#oh_audiosession_deactivatedcallback) callback | the [OH_AudioSession_DeactivatedCallback](capi-native-audio-session-manager-h.md#oh_audiosession_deactivatedcallback) which is used to receive the deactivated event |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | [AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) if execution succeeds  or [AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) if parameter validation fails |

### OH_AudioSessionManager_SetScene()

```c
OH_AudioCommon_Result OH_AudioSessionManager_SetScene(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_Scene scene)
```

**Description**

Set scene for audio session.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | the [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) returned by the [OH_AudioManager_GetAudioSessionManager](capi-native-audio-session-manager-h.md#oh_audiomanager_getaudiosessionmanager) |
| [OH_AudioSession_Scene](capi-native-audio-session-manager-h.md#oh_audiosession_scene) scene | the [OH_AudioSession_Scene](capi-native-audio-session-manager-h.md#oh_audiosession_scene) |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | [AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) if execution succeeds  or [AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) if parameter validation fails  or [AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE](capi-native-audio-common-h.md#oh_audiocommon_result) if system illegal state  or [AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) if system state error |

### OH_AudioSessionManager_RegisterStateChangeCallback()

```c
OH_AudioCommon_Result OH_AudioSessionManager_RegisterStateChangeCallback(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_StateChangedCallback callback)
```

**Description**

Register the audio session state change event callback.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | the [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) returned by the [OH_AudioManager_GetAudioSessionManager](capi-native-audio-session-manager-h.md#oh_audiomanager_getaudiosessionmanager) |
| [OH_AudioSession_StateChangedCallback](capi-native-audio-session-manager-h.md#oh_audiosession_statechangedcallback) callback | the [OH_AudioSession_StateChangedCallback](capi-native-audio-session-manager-h.md#oh_audiosession_statechangedcallback) which is used to receive the state change event |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | [AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) if execution succeeds  or [AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) if parameter validation fails  or [AUDIOCOMMON_RESULT_ERROR_NO_MEMORY](capi-native-audio-common-h.md#oh_audiocommon_result) No memory error  or [AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) if system state error |

### OH_AudioSessionManager_UnregisterStateChangeCallback()

```c
OH_AudioCommon_Result OH_AudioSessionManager_UnregisterStateChangeCallback(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_StateChangedCallback callback)
```

**Description**

Unregister the audio session state change event callback.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | the [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) returned by the [OH_AudioManager_GetAudioSessionManager](capi-native-audio-session-manager-h.md#oh_audiomanager_getaudiosessionmanager) |
| [OH_AudioSession_StateChangedCallback](capi-native-audio-session-manager-h.md#oh_audiosession_statechangedcallback) callback | the [OH_AudioSession_StateChangedCallback](capi-native-audio-session-manager-h.md#oh_audiosession_statechangedcallback) which is used to receive the state change event |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | [AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) if execution succeeds  or [AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) if parameter validation fails  or [AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) if system state error |

### OH_AudioSessionManager_SetDefaultOutputDevice()

```c
OH_AudioCommon_Result OH_AudioSessionManager_SetDefaultOutputDevice(OH_AudioSessionManager *audioSessionManager, OH_AudioDevice_Type deviceType)
```

**Description**

Sets the default output device. This function applys on audiorenderers whose StreamUsage are STREAM_USAGE_VOICE_COMMUNICATION/STREAM_USAGE_VIDEO_COMMUNICATION/STREAM_USAGE_VOICE_MESSAGE. Setting the device will only takes effect if no other accessory such as headphones are in use

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | the [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) returned by the [OH_AudioManager_GetAudioSessionManager](capi-native-audio-session-manager-h.md#oh_audiomanager_getaudiosessionmanager) |
| OH_AudioDevice_Type deviceType | The target device. The available deviceTypes are: EARPIECE: Built-in earpiece SPEAKER: Built-in speaker DEFAULT: System default output device |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | [AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) if execution succeeds  or [AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) if parameter validation fails  or [AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) if system state error |

### OH_AudioSessionManager_GetDefaultOutputDevice()

```c
OH_AudioCommon_Result OH_AudioSessionManager_GetDefaultOutputDevice(OH_AudioSessionManager *audioSessionManager, OH_AudioDevice_Type *deviceType)
```

**Description**

Gets the default output device.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | the [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) returned by the [OH_AudioManager_GetAudioSessionManager](capi-native-audio-session-manager-h.md#oh_audiomanager_getaudiosessionmanager) |
| OH_AudioDevice_Type *deviceType | The target device.The available deviceTypes are: EARPIECE: Built-in earpiece SPEAKER: Built-in speaker DEFAULT: System default output device |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | [AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) if execution succeeds  or [AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) if parameter validation fails  or [AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE](capi-native-audio-common-h.md#oh_audiocommon_result) if system illegal state |

### OH_AudioSessionManager_ReleaseDevices()

```c
OH_AudioCommon_Result OH_AudioSessionManager_ReleaseDevices(OH_AudioSessionManager *audioSessionManager, OH_AudioDeviceDescriptorArray *audioDeviceDescriptorArray)
```

**Description**

Release the audio device descriptor array object.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | the [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) returned by the [OH_AudioManager_GetAudioSessionManager](capi-native-audio-session-manager-h.md#oh_audiomanager_getaudiosessionmanager) |
| OH_AudioDeviceDescriptorArray *audioDeviceDescriptorArray | Audio device descriptors should be released. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | [AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) If the execution is successful.  or [AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) if parameter validation fails               1.The param of audioSessionManager is nullptr;               2.The param of audioDeviceDescriptorArray is nullptr. |

### OH_AudioSessionManager_RegisterCurrentOutputDeviceChangeCallback()

```c
OH_AudioCommon_Result OH_AudioSessionManager_RegisterCurrentOutputDeviceChangeCallback(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_CurrentOutputDeviceChangedCallback callback)
```

**Description**

Register the audio session device change event callback.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | the [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) returned by the [OH_AudioManager_GetAudioSessionManager](capi-native-audio-session-manager-h.md#oh_audiomanager_getaudiosessionmanager) |
| [OH_AudioSession_CurrentOutputDeviceChangedCallback](capi-native-audio-session-manager-h.md#oh_audiosession_currentoutputdevicechangedcallback) callback | the [OH_AudioSession_CurrentOutputDeviceChangedCallback](capi-native-audio-session-manager-h.md#oh_audiosession_currentoutputdevicechangedcallback) which is used to receive the device change event |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | [AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) if execution succeeds  or [AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) if parameter validation fails  or [AUDIOCOMMON_RESULT_ERROR_NO_MEMORY](capi-native-audio-common-h.md#oh_audiocommon_result) No memory error  or [AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) if system state error |

### OH_AudioSessionManager_UnregisterCurrentOutputDeviceChangeCallback()

```c
OH_AudioCommon_Result OH_AudioSessionManager_UnregisterCurrentOutputDeviceChangeCallback(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_CurrentOutputDeviceChangedCallback callback)
```

**Description**

Unregister the audio session device change event callback.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | the [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) returned by the [OH_AudioManager_GetAudioSessionManager](capi-native-audio-session-manager-h.md#oh_audiomanager_getaudiosessionmanager) |
| [OH_AudioSession_CurrentOutputDeviceChangedCallback](capi-native-audio-session-manager-h.md#oh_audiosession_currentoutputdevicechangedcallback) callback | the [OH_AudioSession_CurrentOutputDeviceChangedCallback](capi-native-audio-session-manager-h.md#oh_audiosession_currentoutputdevicechangedcallback) which is used to receive the device change event |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | [AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) if execution succeeds  or [AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) if parameter validation fails  or [AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) if system state error |

### OH_AudioSessionManager_GetAvailableDevices()

```c
OH_AudioCommon_Result OH_AudioSessionManager_GetAvailableDevices(OH_AudioSessionManager *audioSessionManager, OH_AudioDevice_Usage deviceUsage, OH_AudioDeviceDescriptorArray **audioDeviceDescriptorArray)
```

**Description**

Get available devices by device usage.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | the [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) handle returned by [OH_AudioManager_GetAudioSessionManager](capi-native-audio-session-manager-h.md#oh_audiomanager_getaudiosessionmanager). |
| OH_AudioDevice_Usage deviceUsage | the [OH_AudioDevice_Usage](capi-native-audio-device-base-h.md#oh_audiodevice_usage) which is used as the filter parameter for get the available devices. |
| OH_AudioDeviceDescriptorArray **audioDeviceDescriptorArray | the [OH_AudioDeviceDescriptorArray](capi-ohaudio-oh-audiodevicedescriptorarray.md) pointer variable which will be set the audio device descriptors value Do not release the audioDeviceDescriptorArray pointer separately instead call [OH_AudioSessionManager_ReleaseDevices](capi-native-audio-session-manager-h.md#oh_audiosessionmanager_releasedevices) to release the DeviceDescriptor array when it is no use anymore. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | [AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) if execution succeeds.      or [AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) if parameter validation fails.      or [AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) Audio client call audio service error, System error. |

### OH_AudioSessionManager_RegisterAvailableDevicesChangeCallback()

```c
OH_AudioCommon_Result OH_AudioSessionManager_RegisterAvailableDevicesChangeCallback(OH_AudioSessionManager *audioSessionManager, OH_AudioDevice_Usage deviceUsage, OH_AudioSession_AvailableDeviceChangedCallback callback)
```

**Description**

Register available device change event callback.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | the [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) returned by the [OH_AudioManager_GetAudioSessionManager](capi-native-audio-session-manager-h.md#oh_audiomanager_getaudiosessionmanager) |
| OH_AudioDevice_Usage deviceUsage | the [OH_AudioDevice_Usage](capi-native-audio-device-base-h.md#oh_audiodevice_usage) which is used as the filter parameter for register the available devices change event. |
| [OH_AudioSession_AvailableDeviceChangedCallback](capi-native-audio-session-manager-h.md#oh_audiosession_availabledevicechangedcallback) callback | the [OH_AudioSession_AvailableDeviceChangedCallback](capi-native-audio-session-manager-h.md#oh_audiosession_availabledevicechangedcallback) which is used to receive available device change event. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | [AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) if execution succeeds.      or [AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) if parameter validation fails.      or [AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) Audio client call audio service error, System error. |

### OH_AudioSessionManager_UnregisterAvailableDevicesChangeCallback()

```c
OH_AudioCommon_Result OH_AudioSessionManager_UnregisterAvailableDevicesChangeCallback(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_AvailableDeviceChangedCallback callback)
```

**Description**

Unregister available device change event callback.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | the [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) returned by the [OH_AudioManager_GetAudioSessionManager](capi-native-audio-session-manager-h.md#oh_audiomanager_getaudiosessionmanager). |
| [OH_AudioSession_AvailableDeviceChangedCallback](capi-native-audio-session-manager-h.md#oh_audiosession_availabledevicechangedcallback) callback | the [OH_AudioSession_AvailableDeviceChangedCallback](capi-native-audio-session-manager-h.md#oh_audiosession_availabledevicechangedcallback) which is used to receive the device change event. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | [AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) if execution succeeds.      or [AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) if parameter validation fails.      or [AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) Audio client call audio service error, System error. |

### OH_AudioSessionManager_SelectMediaInputDevice()

```c
OH_AudioCommon_Result OH_AudioSessionManager_SelectMediaInputDevice(OH_AudioSessionManager *audioSessionManager, OH_AudioDeviceDescriptor *deviceDescriptor)
```

**Description**

Sets the media input device. This function is not valid for call recording, whose SourceType is SOURCE_TYPE_VOICE_CALL or SOURCE_TYPE_VOICE_COMMUNICATION. In scenarios where there are concurrent recording streams with higher priority, the actual input device used by the application may differ from the selected one. The application can use [OH_AudioSessionManager_RegisterCurrentInputDeviceChangeCallback](capi-native-audio-session-manager-h.md#oh_audiosessionmanager_registercurrentinputdevicechangecallback) to register a callback to listen for the actual input device.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | the [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) handle returned by [OH_AudioManager_GetAudioSessionManager](capi-native-audio-session-manager-h.md#oh_audiomanager_getaudiosessionmanager). |
| OH_AudioDeviceDescriptor *deviceDescriptor | The target device. The available device must be in the array returned by [OH_AudioSessionManager_GetAvailableDevices](capi-native-audio-session-manager-h.md#oh_audiosessionmanager_getavailabledevices). When the nullptr is passed, system will clear the last selection. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | [AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) if execution succeeds.      or [AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) if parameter validation fails.      or [AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) Audio client call audio service error, System error. |

### OH_AudioSessionManager_GetSelectedMediaInputDevice()

```c
OH_AudioCommon_Result OH_AudioSessionManager_GetSelectedMediaInputDevice(OH_AudioSessionManager *audioSessionManager, OH_AudioDeviceDescriptor **audioDeviceDescriptor)
```

**Description**

Gets the selected media input device.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | the [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) returned by the [OH_AudioManager_GetAudioSessionManager](capi-native-audio-session-manager-h.md#oh_audiomanager_getaudiosessionmanager). |
| OH_AudioDeviceDescriptor **audioDeviceDescriptor | The target device set by [OH_AudioSessionManager_SelectMediaInputDevice](capi-native-audio-session-manager-h.md#oh_audiosessionmanager_selectmediainputdevice) or device with AUDIO_DEVICE_TYPE_INVALID if not set yet. Do not release the audioDeviceDescriptor pointer separately, instead call [OH_AudioSessionManager_ReleaseDevice](capi-native-audio-session-manager-h.md#oh_audiosessionmanager_releasedevice) to release it when it is no use anymore. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | [AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) if execution succeeds.      or [AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) if parameter validation fails.      or [AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) Audio client call audio service error, System error. |

### OH_AudioSessionManager_SetBluetoothAndNearlinkPreferredRecordCategory()

```c
OH_AudioCommon_Result OH_AudioSessionManager_SetBluetoothAndNearlinkPreferredRecordCategory(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_BluetoothAndNearlinkPreferredRecordCategory category)
```

**Description**

Sets the preferred record category with bluetooth and nearlink device. The application can set this category before bluetooth and nearlink connected, and the system will prefer to use bluetooth and nearlink to record when the device connected. In scenarios where there are concurrent recording streams with higher priority, the actual input device used by the application may differ from the preferred one. The application can use [OH_AudioSessionManager_RegisterCurrentInputDeviceChangeCallback](capi-native-audio-session-manager-h.md#oh_audiosessionmanager_registercurrentinputdevicechangecallback) to register a callback to listen for the actual input device.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | the [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) handle returned by [OH_AudioManager_GetAudioSessionManager](capi-native-audio-session-manager-h.md#oh_audiomanager_getaudiosessionmanager). |
| [OH_AudioSession_BluetoothAndNearlinkPreferredRecordCategory](capi-native-audio-session-manager-h.md#oh_audiosession_bluetoothandnearlinkpreferredrecordcategory) category | The category application prefer to use when recording with bluetooth and nearlink. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | [AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) if execution succeeds.      or [AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) if parameter validation fails.      or [AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) Audio client call audio service error, System error. |

### OH_AudioSessionManager_GetBluetoothAndNearlinkPreferredRecordCategory()

```c
OH_AudioCommon_Result OH_AudioSessionManager_GetBluetoothAndNearlinkPreferredRecordCategory(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_BluetoothAndNearlinkPreferredRecordCategory *category)
```

**Description**

Gets the preferred record category with bluetooth and nearlink device.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | the [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) handle returned by [OH_AudioManager_GetAudioSessionManager](capi-native-audio-session-manager-h.md#oh_audiomanager_getaudiosessionmanager). |
| [OH_AudioSession_BluetoothAndNearlinkPreferredRecordCategory](capi-native-audio-session-manager-h.md#oh_audiosession_bluetoothandnearlinkpreferredrecordcategory) *category | The category application prefer to use when recording with bluetooth and nearlink. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | [AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) if execution succeeds.      or [AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) if parameter validation fails.      or [AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) Audio client call audio service error, System error. |

### OH_AudioSessionManager_RegisterCurrentInputDeviceChangeCallback()

```c
OH_AudioCommon_Result OH_AudioSessionManager_RegisterCurrentInputDeviceChangeCallback(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_CurrentInputDeviceChangedCallback callback)
```

**Description**

Register the audio session input device change event callback.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | the [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) returned by the [OH_AudioManager_GetAudioSessionManager](capi-native-audio-session-manager-h.md#oh_audiomanager_getaudiosessionmanager). |
| [OH_AudioSession_CurrentInputDeviceChangedCallback](capi-native-audio-session-manager-h.md#oh_audiosession_currentinputdevicechangedcallback) callback | the [OH_AudioSession_CurrentInputDeviceChangedCallback](capi-native-audio-session-manager-h.md#oh_audiosession_currentinputdevicechangedcallback) which is used to receive the input device change event. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | [AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) if execution succeeds.      or [AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) if parameter validation fails.      or [AUDIOCOMMON_RESULT_ERROR_NO_MEMORY](capi-native-audio-common-h.md#oh_audiocommon_result) No memory error.      or [AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) Audio client call audio service error, System error. |

### OH_AudioSessionManager_UnregisterCurrentInputDeviceChangeCallback()

```c
OH_AudioCommon_Result OH_AudioSessionManager_UnregisterCurrentInputDeviceChangeCallback(OH_AudioSessionManager *audioSessionManager, OH_AudioSession_CurrentInputDeviceChangedCallback callback)
```

**Description**

Unregister the audio session input device change event callback.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | the [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) returned by the [OH_AudioManager_GetAudioSessionManager](capi-native-audio-session-manager-h.md#oh_audiomanager_getaudiosessionmanager). |
| [OH_AudioSession_CurrentInputDeviceChangedCallback](capi-native-audio-session-manager-h.md#oh_audiosession_currentinputdevicechangedcallback) callback | the [OH_AudioSession_CurrentInputDeviceChangedCallback](capi-native-audio-session-manager-h.md#oh_audiosession_currentinputdevicechangedcallback) which is used to receive the input device change event. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | [AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) if execution succeeds.      or [AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) if parameter validation fails.      or [AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) Audio client call audio service error, System error. |

### OH_AudioSessionManager_ReleaseDevice()

```c
OH_AudioCommon_Result OH_AudioSessionManager_ReleaseDevice(OH_AudioSessionManager *audioSessionManager, OH_AudioDeviceDescriptor *audioDeviceDescriptor)
```

**Description**

Release the audio device descriptor object.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | the [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) returned by the [OH_AudioManager_GetAudioSessionManager](capi-native-audio-session-manager-h.md#oh_audiomanager_getaudiosessionmanager) |
| OH_AudioDeviceDescriptor *audioDeviceDescriptor | Audio device descriptor to release. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | [AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) If the execution is successful.      or [AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) if parameter validation fails |

### OH_AudioSessionManager_EnableMuteSuggestionWhenMixWithOthers()

```c
OH_AudioCommon_Result OH_AudioSessionManager_EnableMuteSuggestionWhenMixWithOthers(OH_AudioSessionManager *audioSessionManager, bool enable)
```

**Description**

Enables mute suggestion callback function when using [CONCURRENCY_MIX_WITH_OTHERS](capi-native-audio-session-base-h.md#oh_audiosession_concurrencymode) mode. Usually when using mix mode, application won't receive state change event when there is another audio playing simultaneously. But in some scenarios, like game or radio, the application may intend to mute its audio to achieve better user experience. If enabled, the mute and unmute suggestion hint will be sent by [OH_AudioSession_StateChangedCallback](capi-native-audio-session-manager-h.md#oh_audiosession_statechangedcallback) registered by [OH_AudioSessionManager_RegisterStateChangeCallback](capi-native-audio-session-manager-h.md#oh_audiosessionmanager_registerstatechangecallback). Mute suggestion means there is another application starting non-mixable audio. This function only supports audio session with [OH_AudioSession_Scene](capi-native-audio-session-manager-h.md#oh_audiosession_scene) set and activated with [CONCURRENCY_MIX_WITH_OTHERS](capi-native-audio-session-base-h.md#oh_audiosession_concurrencymode) mode. And it takes effect only once during activation, so application need to enable it every time before activation.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | the [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) returned by the [OH_AudioManager_GetAudioSessionManager](capi-native-audio-session-manager-h.md#oh_audiomanager_getaudiosessionmanager). |
| bool enable | Sets true to enable mute suggestion while registering session state change event callback. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | [AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) If the execution is successful.      or [AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) Parameter validation fails.      or [AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE](capi-native-audio-common-h.md#oh_audiocommon_result) Function is called without setting      [OH_AudioSession_Scene](capi-native-audio-session-manager-h.md#oh_audiosession_scene) or called after audio session activation.      or [AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) Audio client call audio service error, system internal error. |

### OH_AudioSessionManager_IsOtherMediaPlaying()

```c
bool OH_AudioSessionManager_IsOtherMediaPlaying(OH_AudioSessionManager *audioSessionManager)
```

**Description**

Returns if there is any other application playing audio in media usage, including media session activated.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | the [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) returned by the [OH_AudioManager_GetAudioSessionManager](capi-native-audio-session-manager-h.md#oh_audiomanager_getaudiosessionmanager). |

**Returns**:

| Type | Description |
| -- | -- |
| bool | True if there is other application playing audio in media usage. |

### OH_AudioSessionManager_SetCaptureMuteHint()

```c
OH_AudioCommon_Result OH_AudioSessionManager_SetCaptureMuteHint(OH_AudioSessionManager *audioSessionManager, bool mute)
```

**Description**

Sets recording mute state to audio system. This method is used as a hint for power optimization, it does not mute the recording stream, only affects internal processing strategy. Audio system may disable some recording effects when application notifies its muted state to system. Mute hint state can only be set when there is at least one running stream in current process.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | the [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) returned by the [OH_AudioManager_GetAudioSessionManager](capi-native-audio-session-manager-h.md#oh_audiomanager_getaudiosessionmanager). |
| bool mute | use true if application recording stream muted by application itself. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | Function result code:      [AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) If the execution is successful.      [AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) The param of audioSessionManager is nullptr.      [AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE](capi-native-audio-common-h.md#oh_audiocommon_result) Operation not permitted at current state,          there is no audio capturer running. |

### OH_AudioSessionManager_SetBehavior()

```c
OH_AudioCommon_Result OH_AudioSessionManager_SetBehavior(OH_AudioSessionManager *audioSessionManager, uint32_t behavior)
```

**Description**

Set audio session behavior parameters (supporting multiple flag combinations) This interface takes effect only after the interface [OH_AudioSessionManager_SetScene](capi-native-audio-session-manager-h.md#oh_audiosessionmanager_setscene) is called. Each time you call this interface to set parameters, you need to call the interface [OH_AudioSessionManager_ActivateAudioSession](capi-native-audio-session-manager-h.md#oh_audiosessionmanager_activateaudiosession) again for the settings to take effect.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *audioSessionManager | the [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) returned by the [OH_AudioManager_GetAudioSessionManager](capi-native-audio-session-manager-h.md#oh_audiomanager_getaudiosessionmanager) |
| uint32_t behavior | Audio session behavior flags, which can be a single flag or a bitwise OR combination of multiple flags [OH_AudioSession_BehaviorFlags](capi-native-audio-session-base-h.md#oh_audiosession_behaviorflags) |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | [AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) if execution succeeds      or [AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) if parameter validation fails      or [AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE](capi-native-audio-common-h.md#oh_audiocommon_result) if system illegal state |


