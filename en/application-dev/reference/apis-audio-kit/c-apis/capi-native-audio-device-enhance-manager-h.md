# native_audio_device_enhance_manager.h

## Overview

Declares audio device enhancement manager related interfaces.<br> The interfaces in this file are used for obtaining the OH_AudioDeviceEnhanceManager handle, selecting the input or output devices of your application itself, as well as other enhanced functions related to audio devices or routing.

**Library**: libohaudio.so

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 10

**Related module**: [OHAudio](capi-ohaudio.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AudioDeviceEnhanceManager](capi-ohaudio-oh-audiodeviceenhancemanager.md) | OH_AudioDeviceEnhanceManager | Defines the handle type of the audio device enhancement manager, which is used for enhanced audio device management functions. |

### Function

| Name | Description |
| -- | -- |
| [OH_AudioCommon_Result OH_AudioManager_GetAudioDeviceEnhanceManager(OH_AudioDeviceEnhanceManager **audioDeviceEnhanceManager)](#oh_audiomanager_getaudiodeviceenhancemanager) | Obtains the audio device enhancement manager handle.<br> This handle is used as the first parameter when calling enhanced audio device management functions. The functional APIs of this manager are only available on specific devices. Your application can first call [OH_AudioDeviceEnhanceManager_IsEnhancedRoutingSupported](capi-native-audio-device-enhance-manager-h.md#oh_audiodeviceenhancemanager_isenhancedroutingsupported) to check if the system supports them before using. |
| [OH_AudioCommon_Result OH_AudioDeviceEnhanceManager_IsEnhancedRoutingSupported(OH_AudioDeviceEnhanceManager *audioDeviceEnhanceManager, bool *supported)](#oh_audiodeviceenhancemanager_isenhancedroutingsupported) | Queries whether the system supports the enhanced routing functions provided by this manager.<br> The enhanced routing functions support selecting input and output devices for the application or audio streams. You are advised to call this API to check system support before using the enhanced routing functions. Even for the same type of host device, some models may support these functions while others may not due to hardware limitations. If the system does not support these enhanced routing functions, calling them will have no effect, and the system will select default input/output devices for the application or audio streams instead. |
| [OH_AudioCommon_Result OH_AudioDeviceEnhanceManager_SelectOutputDevice(OH_AudioDeviceEnhanceManager *audioDeviceEnhanceManager, OH_AudioDeviceDescriptor *deviceDescriptor)](#oh_audiodeviceenhancemanager_selectoutputdevice) | Sets the preferred output device for the application.<br> This configuration applies to all playback streams created by the application, unless a specific output device is designated for an individual stream. When the application implements its own UX for output device selection, it can obtain the list of available output devices through [OH_AudioRoutingManager_GetAvailableDevices](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_getavailabledevices), and use the<br>[OH_AudioRoutingManager_GetPreferredOutputDevice](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_getpreferredoutputdevice) API to obtain the currently selected output device. The application can register a callback via {@link OH_AudioDeviceEnhanceManager_RegisterCurrentOutputDeviceChangeCallback} to listen for changes to the actual output device. The selection becomes invalid when the application exits or the selected device goes offline. After the application restarts or the device comes back online, the selection must be re-issued to take effect. If the system does not support this function, it will select a default output device for the application. |
| [OH_AudioCommon_Result OH_AudioDeviceEnhanceManager_SelectInputDevice(OH_AudioDeviceEnhanceManager *audioDeviceEnhanceManager, OH_AudioDeviceDescriptor *deviceDescriptor)](#oh_audiodeviceenhancemanager_selectinputdevice) | Sets the preferred input device for the application.<br> This setting applies to all recording streams created by the application, unless a specific input device is designated for an individual stream. When the application implements its own UX for input device selection, it can obtain the list of available input devices through [OH_AudioRoutingManager_GetAvailableDevices](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_getavailabledevices),<br>and use the [OH_AudioRoutingManager_GetPreferredInputDevice](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_getpreferredinputdevice) API to obtain the currently selected input device. Your application can register a callback via {@link OH_AudioDeviceEnhanceManager_RegisterCurrentInputDeviceChangeCallback} to listen for changes to the actual input device. The selection becomes invalid when the application exits or the selected device goes offline. After the application restarts or the device comes back online, you must re-issue the selection for it to take effect. If the system does not support this function, a default input device will be selected automatically. |
| [OH_AudioCommon_Result OH_AudioDeviceEnhanceManager_SelectOutputDeviceForAudioRenderer(OH_AudioDeviceEnhanceManager *audioDeviceEnhanceManager, OH_AudioRenderer *renderer, OH_AudioDeviceDescriptor *deviceDescriptor)](#oh_audiodeviceenhancemanager_selectoutputdeviceforaudiorenderer) | Sets the preferred output device for a specific audio renderer.<br> Your application must ensure that the specified renderer is valid. This selection only applies to the designated stream; other playback streams in your application will use the application's forced selection or the system's default output device. The selection becomes invalid when the application exits or the selected device goes offline. After the application restarts or the device comes back online, you must re-issue the selection for it to take effect. If the system does not support this function, it will select a default output device for the renderer. |
| [OH_AudioCommon_Result OH_AudioDeviceEnhanceManager_SelectInputDeviceForAudioCapturer(OH_AudioDeviceEnhanceManager *audioDeviceEnhanceManager, OH_AudioCapturer *capturer, OH_AudioDeviceDescriptor *deviceDescriptor)](#oh_audiodeviceenhancemanager_selectinputdeviceforaudiocapturer) | Sets the preferred input device for a specific audio capturer.<br> Your application must ensure that the specified capturer is valid. This selection only applies to the designated stream; other recording streams in your application will use the application's forced selection or the system's default input device. The selection becomes invalid when the application exits or the selected device goes offline. After the application restarts or the device comes back online, you must re-issue the selection for it to take effect. If the system does not support this function, it will select a default input device for the capturer. |

## Function description

### OH_AudioManager_GetAudioDeviceEnhanceManager()

```c
OH_AudioCommon_Result OH_AudioManager_GetAudioDeviceEnhanceManager(OH_AudioDeviceEnhanceManager **audioDeviceEnhanceManager)
```

**Description**

Obtains the audio device enhancement manager handle.<br> This handle is used as the first parameter when calling enhanced audio device management functions. The functional APIs of this manager are only available on specific devices. Your application can first call [OH_AudioDeviceEnhanceManager_IsEnhancedRoutingSupported](capi-native-audio-device-enhance-manager-h.md#oh_audiodeviceenhancemanager_isenhancedroutingsupported) to check if the system supports them before using.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioDeviceEnhanceManager](capi-ohaudio-oh-audiodeviceenhancemanager.md) **audioDeviceEnhanceManager | Indicates the pointer to the [OH_AudioDeviceEnhanceManager](capi-ohaudio-oh-audiodeviceenhancemanager.md) handle obtained by this function. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | [AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) If the execution is successful,      or [AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) if the input audioDeviceEnhanceManager      pointer is NULL. |

### OH_AudioDeviceEnhanceManager_IsEnhancedRoutingSupported()

```c
OH_AudioCommon_Result OH_AudioDeviceEnhanceManager_IsEnhancedRoutingSupported(OH_AudioDeviceEnhanceManager *audioDeviceEnhanceManager, bool *supported)
```

**Description**

Queries whether the system supports the enhanced routing functions provided by this manager.<br> The enhanced routing functions support selecting input and output devices for the application or audio streams. You are advised to call this API to check system support before using the enhanced routing functions. Even for the same type of host device, some models may support these functions while others may not due to hardware limitations. If the system does not support these enhanced routing functions, calling them will have no effect, and the system will select default input/output devices for the application or audio streams instead.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioDeviceEnhanceManager](capi-ohaudio-oh-audiodeviceenhancemanager.md) *audioDeviceEnhanceManager | the [OH_AudioDeviceEnhanceManager](capi-ohaudio-oh-audiodeviceenhancemanager.md) handle returned by [OH_AudioManager_GetAudioDeviceEnhanceManager](capi-native-audio-device-enhance-manager-h.md#oh_audiomanager_getaudiodeviceenhancemanager). |
| bool *supported | query result, true means the system supports the enhanced functions, false means not supported. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | [AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) if execution succeeds,      or [AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) if audioDeviceEnhanceManager is NULL or      supported is NULL,      or [AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) Audio service error occurs, such as the service died. |

### OH_AudioDeviceEnhanceManager_SelectOutputDevice()

```c
OH_AudioCommon_Result OH_AudioDeviceEnhanceManager_SelectOutputDevice(OH_AudioDeviceEnhanceManager *audioDeviceEnhanceManager, OH_AudioDeviceDescriptor *deviceDescriptor)
```

**Description**

Sets the preferred output device for the application.<br> This configuration applies to all playback streams created by the application, unless a specific output device is designated for an individual stream. When the application implements its own UX for output device selection, it can obtain the list of available output devices through [OH_AudioRoutingManager_GetAvailableDevices](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_getavailabledevices), and use the<br>[OH_AudioRoutingManager_GetPreferredOutputDevice](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_getpreferredoutputdevice) API to obtain the currently selected output device. The application can register a callback via {@link OH_AudioDeviceEnhanceManager_RegisterCurrentOutputDeviceChangeCallback} to listen for changes to the actual output device. The selection becomes invalid when the application exits or the selected device goes offline. After the application restarts or the device comes back online, the selection must be re-issued to take effect. If the system does not support this function, it will select a default output device for the application.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioDeviceEnhanceManager](capi-ohaudio-oh-audiodeviceenhancemanager.md) *audioDeviceEnhanceManager | the [OH_AudioDeviceEnhanceManager](capi-ohaudio-oh-audiodeviceenhancemanager.md) handle returned by [OH_AudioManager_GetAudioDeviceEnhanceManager](capi-native-audio-device-enhance-manager-h.md#oh_audiomanager_getaudiodeviceenhancemanager). |
| OH_AudioDeviceDescriptor *deviceDescriptor | The target device. The available device must be in the array returned by [OH_AudioRoutingManager_GetAvailableDevices](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_getavailabledevices). If nullptr is passed, system will clear the last selection and select a default output device for your application. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | [AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) if execution succeeds,      or [AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result)  if audioDeviceEnhanceManager is NULL,      deviceDescriptor is invalid, or the specified device has gone offline,      or [AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) Audio service error occurs, such as the service died. |

### OH_AudioDeviceEnhanceManager_SelectInputDevice()

```c
OH_AudioCommon_Result OH_AudioDeviceEnhanceManager_SelectInputDevice(OH_AudioDeviceEnhanceManager *audioDeviceEnhanceManager, OH_AudioDeviceDescriptor *deviceDescriptor)
```

**Description**

Sets the preferred input device for the application.<br> This setting applies to all recording streams created by the application, unless a specific input device is designated for an individual stream. When the application implements its own UX for input device selection, it can obtain the list of available input devices through [OH_AudioRoutingManager_GetAvailableDevices](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_getavailabledevices),<br>and use the [OH_AudioRoutingManager_GetPreferredInputDevice](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_getpreferredinputdevice) API to obtain the currently selected input device. Your application can register a callback via {@link OH_AudioDeviceEnhanceManager_RegisterCurrentInputDeviceChangeCallback} to listen for changes to the actual input device. The selection becomes invalid when the application exits or the selected device goes offline. After the application restarts or the device comes back online, you must re-issue the selection for it to take effect. If the system does not support this function, a default input device will be selected automatically.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioDeviceEnhanceManager](capi-ohaudio-oh-audiodeviceenhancemanager.md) *audioDeviceEnhanceManager | the [OH_AudioDeviceEnhanceManager](capi-ohaudio-oh-audiodeviceenhancemanager.md) handle returned by [OH_AudioManager_GetAudioDeviceEnhanceManager](capi-native-audio-device-enhance-manager-h.md#oh_audiomanager_getaudiodeviceenhancemanager). |
| OH_AudioDeviceDescriptor *deviceDescriptor | The target device. The available device must be in the array returned by [OH_AudioRoutingManager_GetAvailableDevices](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_getavailabledevices). If nullptr is passed, system will clear the last selection and select a default input device for your application. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | [AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) if execution succeeds,      or [AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) if audioDeviceEnhanceManager is NULL,      deviceDescriptor is invalid, or the specified input device has gone offline,      or [AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) Audio service error occurs, such as the service died. |

### OH_AudioDeviceEnhanceManager_SelectOutputDeviceForAudioRenderer()

```c
OH_AudioCommon_Result OH_AudioDeviceEnhanceManager_SelectOutputDeviceForAudioRenderer(OH_AudioDeviceEnhanceManager *audioDeviceEnhanceManager, OH_AudioRenderer *renderer, OH_AudioDeviceDescriptor *deviceDescriptor)
```

**Description**

Sets the preferred output device for a specific audio renderer.<br> Your application must ensure that the specified renderer is valid. This selection only applies to the designated stream; other playback streams in your application will use the application's forced selection or the system's default output device. The selection becomes invalid when the application exits or the selected device goes offline. After the application restarts or the device comes back online, you must re-issue the selection for it to take effect. If the system does not support this function, it will select a default output device for the renderer.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioDeviceEnhanceManager](capi-ohaudio-oh-audiodeviceenhancemanager.md) *audioDeviceEnhanceManager | the [OH_AudioDeviceEnhanceManager](capi-ohaudio-oh-audiodeviceenhancemanager.md) handle returned by [OH_AudioManager_GetAudioDeviceEnhanceManager](capi-native-audio-device-enhance-manager-h.md#oh_audiomanager_getaudiodeviceenhancemanager). |
| OH_AudioRenderer *renderer | Indicates the renderer reference created by [OH_AudioStreamBuilder_GenerateRenderer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generaterenderer). |
| OH_AudioDeviceDescriptor *deviceDescriptor | The target device. The available device must be in the array returned by [OH_AudioRoutingManager_GetAvailableDevices](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_getavailabledevices). If nullptr is passed, system will clear the last selection and select a default output device for the renderer. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | [AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) if execution succeeds,      or [AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) if audioDeviceEnhanceManager is NULL, renderer is NULL,      deviceDescriptor is invalid, or the specified output device has gone offline,      or [AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) Audio service error occurs, such as the service died. |

### OH_AudioDeviceEnhanceManager_SelectInputDeviceForAudioCapturer()

```c
OH_AudioCommon_Result OH_AudioDeviceEnhanceManager_SelectInputDeviceForAudioCapturer(OH_AudioDeviceEnhanceManager *audioDeviceEnhanceManager, OH_AudioCapturer *capturer, OH_AudioDeviceDescriptor *deviceDescriptor)
```

**Description**

Sets the preferred input device for a specific audio capturer.<br> Your application must ensure that the specified capturer is valid. This selection only applies to the designated stream; other recording streams in your application will use the application's forced selection or the system's default input device. The selection becomes invalid when the application exits or the selected device goes offline. After the application restarts or the device comes back online, you must re-issue the selection for it to take effect. If the system does not support this function, it will select a default input device for the capturer.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioDeviceEnhanceManager](capi-ohaudio-oh-audiodeviceenhancemanager.md) *audioDeviceEnhanceManager | the [OH_AudioDeviceEnhanceManager](capi-ohaudio-oh-audiodeviceenhancemanager.md) handle returned by [OH_AudioManager_GetAudioDeviceEnhanceManager](capi-native-audio-device-enhance-manager-h.md#oh_audiomanager_getaudiodeviceenhancemanager). |
| OH_AudioCapturer *capturer | Indicates the capturer reference created by [OH_AudioStreamBuilder_GenerateCapturer](capi-native-audiostreambuilder-h.md#oh_audiostreambuilder_generatecapturer). |
| OH_AudioDeviceDescriptor *deviceDescriptor | The target device. The available device must be in the array returned by [OH_AudioRoutingManager_GetAvailableDevices](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_getavailabledevices). If nullptr is passed, system will clear the last selection and select a default input device for the capturer. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | [AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) if execution succeeds,      or [AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) if audioDeviceEnhanceManager is NULL, capturer is NULL,      deviceDescriptor is invalid, or the specified input device has gone offline,      or [AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) Audio service error occurs, such as the service died. |


