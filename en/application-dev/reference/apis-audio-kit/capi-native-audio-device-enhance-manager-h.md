# native_audio_device_enhance_manager.h
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @zhanganxiang1-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=1961de06e85063963f633ec54a8a4baaf5cb7dc8 translatedAt=2026-07-21T03:52:27.157Z pushedAt=2026-07-21T08:55:05.314Z -->

## Overview

Declares the interfaces related to the audio device enhancement manager. The interfaces in this file are used to obtain an OH_AudioDeviceEnhanceManager handle, switch input and output devices for an app or audio stream, and perform other enhancement functions related to audio devices or routing.

**File to include:** <ohaudio/native_audio_device_enhance_manager.h>

**Library:** libohaudio.so

**System capability:** SystemCapability.Multimedia.Audio.Core

**Since:** 26.0.0

**Related module:** [OHAudio](capi-ohaudio.md)

## Summary

### Structs

| Name | typedef Keyword | Description |
| -- | -- | -- |
| [OH_AudioDeviceEnhanceManager](capi-ohaudio-oh-audiodeviceenhancemanager.md) | OH_AudioDeviceEnhanceManager | Defines the handle type of the audio device enhancement manager, which provides audio device enhancement management for app-level audio device selection and stream-level audio device selection. |

### Functions

| Name | Description |
| -- | -- |
| [OH_AudioCommon_Result OH_AudioManager_GetAudioDeviceEnhanceManager(OH_AudioDeviceEnhanceManager **audioDeviceEnhanceManager)](#oh_audiomanager_getaudiodeviceenhancemanager) | Obtains the Audio Device Enhancement Manager handle. |
| [OH_AudioCommon_Result OH_AudioDeviceEnhanceManager_IsEnhancedRoutingSupported(OH_AudioDeviceEnhanceManager *audioDeviceEnhanceManager, bool *supported)](#oh_audiodeviceenhancemanager_isenhancedroutingsupported) | Queries whether the system supports the Enhancement Routing feature provided by the current manager. |
| [OH_AudioCommon_Result OH_AudioDeviceEnhanceManager_SelectOutputDevice(OH_AudioDeviceEnhanceManager *audioDeviceEnhanceManager, OH_AudioDeviceDescriptor *deviceDescriptor)](#oh_audiodeviceenhancemanager_selectoutputdevice) | Selects an output device for the app. |
| [OH_AudioCommon_Result OH_AudioDeviceEnhanceManager_SelectInputDevice(OH_AudioDeviceEnhanceManager *audioDeviceEnhanceManager, OH_AudioDeviceDescriptor *deviceDescriptor)](#oh_audiodeviceenhancemanager_selectinputdevice) | Selects an input device for the app. |
| [OH_AudioCommon_Result OH_AudioDeviceEnhanceManager_SelectOutputDeviceForAudioRenderer(OH_AudioDeviceEnhanceManager *audioDeviceEnhanceManager, OH_AudioRenderer *renderer, OH_AudioDeviceDescriptor *deviceDescriptor)](#oh_audiodeviceenhancemanager_selectoutputdeviceforaudiorenderer) | Selects an output device for the specified audio playback stream. |
| [OH_AudioCommon_Result OH_AudioDeviceEnhanceManager_SelectInputDeviceForAudioCapturer(OH_AudioDeviceEnhanceManager *audioDeviceEnhanceManager, OH_AudioCapturer *capturer, OH_AudioDeviceDescriptor *deviceDescriptor)](#oh_audiodeviceenhancemanager_selectinputdeviceforaudiocapturer) | Selects an input device for the specified audio recording stream. |

## Function Description

### OH_AudioManager_GetAudioDeviceEnhanceManager()

```c
OH_AudioCommon_Result OH_AudioManager_GetAudioDeviceEnhanceManager(OH_AudioDeviceEnhanceManager **audioDeviceEnhanceManager)
```

**Description**

Obtains the Audio Device Enhancement Manager handle.

> **NOTE**
>
> This handle should be passed as the first parameter of the related APIs for enhanced audio device management.
> The capabilities provided by this manager are available only on specific devices.
> Before using it, the app should call [OH_AudioDeviceEnhanceManager_IsEnhancedRoutingSupported](capi-native-audio-device-enhance-manager-h.md#oh_audiodeviceenhancemanager_isenhancedroutingsupported) to check whether the system supports the audio device enhancement management feature.

**Since:** 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioDeviceEnhanceManager](capi-ohaudio-oh-audiodeviceenhancemanager.md) **audioDeviceEnhanceManager | Pointer to the OH_AudioDeviceEnhanceManager handle, used to receive the manager instance returned by the function. |

**Return**

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | Result code.<br>         AUDIOCOMMON_RESULT_SUCCESS: The function is executed successfully.<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM: The parameter audioDeviceEnhanceManager is nullptr. |

### OH_AudioDeviceEnhanceManager_IsEnhancedRoutingSupported()

```c
OH_AudioCommon_Result OH_AudioDeviceEnhanceManager_IsEnhancedRoutingSupported(OH_AudioDeviceEnhanceManager *audioDeviceEnhanceManager, bool *supported)
```

**Description**

Queries whether the system supports the enhancement routing feature provided by the current manager.

> **NOTE**
> 
> The enhancement routing feature supports selecting input and output devices for apps or audio streams.
> Before calling related enhancement routing APIs, the app should call this API to check whether the system supports the audio device enhancement management feature.
> Even for the same product device, different models may have different support statuses due to hardware limitations.
> When the system does not support the enhancement routing feature, calling related APIs will not take effect, and the default input and output devices will be selected for the app or audio stream.

**Since:** 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioDeviceEnhanceManager](capi-ohaudio-oh-audiodeviceenhancemanager.md) *audioDeviceEnhanceManager | Handle to the Audio Device Enhancement Manager obtained via [OH_AudioManager_GetAudioDeviceEnhanceManager](capi-native-audio-device-enhance-manager-h.md#oh_audiomanager_getaudiodeviceenhancemanager). |
| bool *supported | Pointer to the query result indicating whether the system supports the audio device enhancement management feature. The value **true** indicates supported, and **false** indicates not supported. |

**Return**

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | Result code.<br>         AUDIOCOMMON_RESULT_SUCCESS: function execution successful.<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM: the parameter audioDeviceEnhanceManager or supported is nullptr.<br>         AUDIOCOMMON_RESULT_ERROR_SYSTEM: the audio client fails to call the audio service, or a system error occurs. |

### OH_AudioDeviceEnhanceManager_SelectOutputDevice()

```c
OH_AudioCommon_Result OH_AudioDeviceEnhanceManager_SelectOutputDevice(OH_AudioDeviceEnhanceManager *audioDeviceEnhanceManager, OH_AudioDeviceDescriptor *deviceDescriptor)
```

**Description**

Selects the output device for the app.

> **NOTE**
> 
> This setting takes effect for all playback streams created by the app, except for streams that have been individually assigned a dedicated output device.
> When the app implements the output device selection feature, it can obtain the available output device list through [OH_AudioRoutingManager_GetAvailableDevices](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_getavailabledevices),
> and obtain the current preferred output device through [OH_AudioRoutingManager_GetPreferredOutputDevice](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_getpreferredoutputdevice).
> This selection becomes invalid after the app exits or the selected device goes offline. It requires reconfiguration to take effect after the app restarts or the device comes back online.
> When the system does not support this feature, the default output device is selected for the app.

**Since:** 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioDeviceEnhanceManager](capi-ohaudio-oh-audiodeviceenhancemanager.md) *audioDeviceEnhanceManager | Handle to the Audio Device Enhancement Manager obtained via [OH_AudioManager_GetAudioDeviceEnhanceManager](capi-native-audio-device-enhance-manager-h.md#oh_audiomanager_getaudiodeviceenhancemanager). |
| OH_AudioDeviceDescriptor *deviceDescriptor | Target device. Available devices must be obtained from the device list returned by [OH_AudioRoutingManager_GetAvailableDevices](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_getavailabledevices). When nullptr is passed, the system clears the previous selection and restores the default output device for the app. |

**Return**

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | Result code.<br>         AUDIOCOMMON_RESULT_SUCCESS: Function executed successfully.<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM: The parameter audioDeviceEnhanceManager is nullptr,<br>         the parameter deviceDescriptor is invalid, or the specified output device is offline.<br>         AUDIOCOMMON_RESULT_ERROR_SYSTEM: The audio client failed to call the audio service, or a system error occurred. |

### OH_AudioDeviceEnhanceManager_SelectInputDevice()

```c
OH_AudioCommon_Result OH_AudioDeviceEnhanceManager_SelectInputDevice(OH_AudioDeviceEnhanceManager *audioDeviceEnhanceManager, OH_AudioDeviceDescriptor *deviceDescriptor)
```

**Description**

Selects an input device for the app.

> **NOTE**
>
> This setting takes effect for all recording streams created by the app, unless a specific stream has already been assigned a dedicated input device.
> When the app implements the input device selection feature, you can obtain the available input device list through [OH_AudioRoutingManager_GetAvailableDevices](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_getavailabledevices),
> and obtain the current preferred input device through [OH_AudioRoutingManager_GetPreferredInputDevice](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_getpreferredinputdevice).
> This selection becomes invalid after the app exits or the selected device goes offline. It requires reconfiguration to take effect after the app restarts or the device comes back online.
> When the system does not support this feature, the default input device is selected for the app.

**Since:** 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioDeviceEnhanceManager](capi-ohaudio-oh-audiodeviceenhancemanager.md) *audioDeviceEnhanceManager | Handle to the Audio Device Enhancement Manager obtained via [OH_AudioManager_GetAudioDeviceEnhanceManager](capi-native-audio-device-enhance-manager-h.md#oh_audiomanager_getaudiodeviceenhancemanager). |
| OH_AudioDeviceDescriptor *deviceDescriptor | Target device. Available devices must be obtained from the device list returned by [OH_AudioRoutingManager_GetAvailableDevices](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_getavailabledevices). When nullptr is passed in, the system clears the previous selection and restores the default input device for the app. |

**Return**

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | Result code.<br>         `AUDIOCOMMON_RESULT_SUCCESS`: function execution successful.<br>         `AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM`: the parameter `audioDeviceEnhanceManager` is nullptr,<br>         the parameter `deviceDescriptor` is invalid, or the specified input device is offline.<br>         `AUDIOCOMMON_RESULT_ERROR_SYSTEM`: the audio client fails to call the audio service, or a system error occurs. |

### OH_AudioDeviceEnhanceManager_SelectOutputDeviceForAudioRenderer()

```c
OH_AudioCommon_Result OH_AudioDeviceEnhanceManager_SelectOutputDeviceForAudioRenderer(OH_AudioDeviceEnhanceManager *audioDeviceEnhanceManager, OH_AudioRenderer *renderer, OH_AudioDeviceDescriptor *deviceDescriptor)
```

**Description**

Selects an output device for a specified audio playback stream.

> **NOTE**
> 
> The app must ensure that the specified audio playback stream is valid.
> This selection takes effect only for the specified stream. Other playback streams in the app continue to use the app-level selected device or the system default output device.
> This selection becomes invalid after the app exits or the selected device goes offline. After the app restarts or the device comes back online, reconfiguration is required for the selection to take effect.
> When the system does not support this feature, the default output device is selected for the audio playback stream.

**Since:** 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioDeviceEnhanceManager](capi-ohaudio-oh-audiodeviceenhancemanager.md) *audioDeviceEnhanceManager | Audio device enhancement manager handle obtained via [OH_AudioManager_GetAudioDeviceEnhanceManager](capi-native-audio-device-enhance-manager-h.md#oh_audiomanager_getaudiodeviceenhancemanager). |
| OH_AudioRenderer *renderer | Audio playback stream instance created via [OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer). |
| OH_AudioDeviceDescriptor *deviceDescriptor | Target device. Available devices must be obtained from the device list returned by [OH_AudioRoutingManager_GetAvailableDevices](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_getavailabledevices). When nullptr is passed, the system clears the previous selection and restores the default output device for the audio playback stream. |

**Return**

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | Result code.<br>         AUDIOCOMMON_RESULT_SUCCESS: function executed successfully.<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM: the parameter audioDeviceEnhanceManager or renderer is nullptr,<br>         the parameter deviceDescriptor is invalid, or the specified output device is offline.<br>         AUDIOCOMMON_RESULT_ERROR_SYSTEM: the audio client failed to call the audio service, or a system error occurred. |

### OH_AudioDeviceEnhanceManager_SelectInputDeviceForAudioCapturer()

```c
OH_AudioCommon_Result OH_AudioDeviceEnhanceManager_SelectInputDeviceForAudioCapturer(OH_AudioDeviceEnhanceManager *audioDeviceEnhanceManager, OH_AudioCapturer *capturer, OH_AudioDeviceDescriptor *deviceDescriptor)
```

**Description**

Selects an input device for a specified audio recording stream.

> **NOTE**
> 
> The app must ensure that the specified audio recording stream is valid.
> This selection takes effect only for the specified stream. Other recording streams in the app continue to use the device selected at the app level or the system default input device.
> This selection becomes invalid after the app exits or the selected device goes offline. After the app restarts or the device comes back online, reconfiguration is required for the selection to take effect.
> When the system does not support this feature, the default input device is selected for the audio recording stream.

**Since:** 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioDeviceEnhanceManager](capi-ohaudio-oh-audiodeviceenhancemanager.md) *audioDeviceEnhanceManager | Handle to the Audio Device Enhancement Manager obtained via [OH_AudioManager_GetAudioDeviceEnhanceManager](capi-native-audio-device-enhance-manager-h.md#oh_audiomanager_getaudiodeviceenhancemanager). |
| OH_AudioCapturer *capturer | Audio recording stream instance created via [OH_AudioStreamBuilder_GenerateCapturer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generatecapturer). |
| OH_AudioDeviceDescriptor *deviceDescriptor | Target device. Available devices must be obtained from the device list returned by [OH_AudioRoutingManager_GetAvailableDevices](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_getavailabledevices). When nullptr is passed, the system clears the previous selection and restores the default input device for this audio recording stream. |

**Return**

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | Result code.<br>         AUDIOCOMMON_RESULT_SUCCESS: function execution successful.<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM: the audioDeviceEnhanceManager or capturer parameter is nullptr,<br>         the deviceDescriptor parameter is invalid, or the specified input device is offline.<br>         AUDIOCOMMON_RESULT_ERROR_SYSTEM: the audio client fails to call the audio service, or a system error occurs. |