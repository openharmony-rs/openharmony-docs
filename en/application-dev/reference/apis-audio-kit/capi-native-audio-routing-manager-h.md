# native_audio_routing_manager.h
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @zhanganxiang1-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=fe6cafc35b7c2ea1e5b32d816e822fcfb388d90d translatedAt=2026-11-09T10:24:33.167Z pushedAt=2026-11-09T11:24:35.928Z nl=1 -->

## Overview

Declares the APIs related to the audio routing manager.<br>This includes obtaining the audio routing manager, registering and unregistering when the device connection state changes, and releasing the pointer array that stores device information.

**File to include:** <ohaudio/native_audio_routing_manager.h>

**Library**: libohaudio.so

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 12

**Related module**: [OHAudio](capi-ohaudio.md)

## Summary

### Structs

| Name | typedef Keyword | Description |
| -- | -- | -- |
| [OH_AudioRoutingManager](capi-ohaudio-oh-audioroutingmanager.md) | OH_AudioRoutingManager | Declares the audio routing manager, which is used to manage audio routing related functions. |

### Function

| Name | typedef Keyword | Description |
| -- | -- | -- |
| [typedef int32_t (\*OH_AudioRoutingManager_OnDeviceChangedCallback)(OH_AudioDevice_ChangeType type, OH_AudioDeviceDescriptorArray *audioDeviceDescriptorArray)](#oh_audioroutingmanager_ondevicechangedcallback) | OH_AudioRoutingManager_OnDeviceChangedCallback | This function pointer points to the callback function used to return the changed audio device descriptors. Multiple audio device descriptors may be returned. |
| [typedef int32_t (\*OH_AudioRoutingManager_OnPreferredOutputDeviceChangedCallback)(OH_AudioDeviceDescriptorArray *audioDeviceDescriptorArray)](#oh_audioroutingmanager_onpreferredoutputdevicechangedcallback) | OH_AudioRoutingManager_OnPreferredOutputDeviceChangedCallback | This function pointer points to the callback function used to return the output device descriptor with the highest priority. This callback returns one or more audio device descriptors. |
| [typedef int32_t (\*OH_AudioRoutingManager_OnPreferredInputDeviceChangedCallback)(OH_AudioDeviceDescriptorArray *audioDeviceDescriptorArray)](#oh_audioroutingmanager_onpreferredinputdevicechangedcallback) | OH_AudioRoutingManager_OnPreferredInputDeviceChangedCallback | This function pointer points to the callback function used to return the input device descriptor with the highest priority. This callback returns one or more audio device descriptors. |
| [OH_AudioCommon_Result OH_AudioManager_GetAudioRoutingManager(OH_AudioRoutingManager **audioRoutingManager)](#oh_audiomanager_getaudioroutingmanager) | - | Obtains the audio routing manager instance.<br>To use the audio routing manager features, you must first obtain the audio routing manager instance. |
| [OH_AudioCommon_Result OH_AudioRoutingManager_GetDevices(OH_AudioRoutingManager *audioRoutingManager, OH_AudioDevice_Flag deviceFlag, OH_AudioDeviceDescriptorArray **audioDeviceDescriptorArray)](#oh_audioroutingmanager_getdevices) | - | Queries the available devices based on the input deviceFlag. |
| [OH_AudioCommon_Result OH_AudioRoutingManager_GetAvailableDevices(OH_AudioRoutingManager *audioRoutingManager, OH_AudioDevice_Usage deviceUsage, OH_AudioDeviceDescriptorArray **audioDeviceDescriptorArray)](#oh_audioroutingmanager_getavailabledevices) | - | Obtains the list of available audio devices. |
| [OH_AudioCommon_Result OH_AudioRoutingManager_GetPreferredOutputDevice(OH_AudioRoutingManager *audioRoutingManager, OH_AudioStream_Usage streamUsage, OH_AudioDeviceDescriptorArray **audioDeviceDescriptorArray)](#oh_audioroutingmanager_getpreferredoutputdevice) | - | Obtains the output device with the highest priority based on the usage scenario of the audio output stream. |
| [OH_AudioCommon_Result OH_AudioRoutingManager_GetPreferredInputDevice(OH_AudioRoutingManager *audioRoutingManager, OH_AudioStream_SourceType sourceType, OH_AudioDeviceDescriptorArray **audioDeviceDescriptorArray)](#oh_audioroutingmanager_getpreferredinputdevice) | - | Obtains the input device with the highest priority based on the usage scenario of the audio input stream. |
| [OH_AudioCommon_Result OH_AudioRoutingManager_RegisterDeviceChangeCallback(OH_AudioRoutingManager *audioRoutingManager, OH_AudioDevice_Flag deviceFlag, OH_AudioRoutingManager_OnDeviceChangedCallback callback)](#oh_audioroutingmanager_registerdevicechangecallback) | - | Registers the device change callback of the audio routing manager. |
| [OH_AudioCommon_Result OH_AudioRoutingManager_UnregisterDeviceChangeCallback(OH_AudioRoutingManager *audioRoutingManager, OH_AudioRoutingManager_OnDeviceChangedCallback callback)](#oh_audioroutingmanager_unregisterdevicechangecallback) | - | Unregisters the device change callback of the audio routing manager. |
| [OH_AudioCommon_Result OH_AudioRoutingManager_RegisterPreferredOutputDevicesChangeCallback(OH_AudioRoutingManager *audioRoutingManager, OH_AudioStream_Usage streamUsage, OH_AudioRoutingManager_OnPreferredOutputDeviceChangedCallback callback)](#oh_audioroutingmanager_registerpreferredoutputdeviceschangecallback) | - | Registers the callback for the highest-priority output device change of the audio routing manager. When the highest-priority output device of the specified playback stream type changes, the registered client will receive the callback.<br> To avoid resource waste or other exceptions, when the application no longer needs this callback, it must release the callback by calling [OH_AudioRoutingManager_UnregisterPreferredOutputDevicesChangeCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_unregisterpreferredoutputdeviceschangecallback). |
| [OH_AudioCommon_Result OH_AudioRoutingManager_UnregisterPreferredOutputDevicesChangeCallback(OH_AudioRoutingManager *audioRoutingManager, OH_AudioRoutingManager_OnPreferredOutputDeviceChangedCallback callback)](#oh_audioroutingmanager_unregisterpreferredoutputdeviceschangecallback) | - | Unregisters the callback for the highest-priority output device change of the audio routing manager registered through [OH_AudioRoutingManager_RegisterPreferredOutputDevicesChangeCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_registerpreferredoutputdeviceschangecallback). |
| [OH_AudioCommon_Result OH_AudioRoutingManager_RegisterPreferredInputDevicesChangeCallback(OH_AudioRoutingManager *audioRoutingManager, OH_AudioStream_SourceType sourceType, OH_AudioRoutingManager_OnPreferredInputDeviceChangedCallback callback)](#oh_audioroutingmanager_registerpreferredinputdeviceschangecallback) | - | Registers the callback for the highest-priority input device change of the audio routing manager. When the highest-priority input device of the specified playback stream type changes, the registered client will receive the callback.<br> To avoid resource waste or other exceptions, when the application no longer needs this callback, it must release the callback by calling [OH_AudioRoutingManager_UnregisterPreferredInputDevicesChangeCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_unregisterpreferredinputdeviceschangecallback). |
| [OH_AudioCommon_Result OH_AudioRoutingManager_UnregisterPreferredInputDevicesChangeCallback(OH_AudioRoutingManager *audioRoutingManager, OH_AudioRoutingManager_OnPreferredInputDeviceChangedCallback callback)](#oh_audioroutingmanager_unregisterpreferredinputdeviceschangecallback) | - | Unregisters the callback for the highest-priority input device change of the audio routing manager registered through [OH_AudioRoutingManager_RegisterPreferredInputDevicesChangeCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_registerpreferredinputdeviceschangecallback). |
| [OH_AudioCommon_Result OH_AudioRoutingManager_ReleaseDevices(OH_AudioRoutingManager *audioRoutingManager, OH_AudioDeviceDescriptorArray *audioDeviceDescriptorArray)](#oh_audioroutingmanager_releasedevices) | - | Releases the audio device descriptor array object. |
| [typedef void (\*OH_AudioRoutingManager_OnDeviceBlockStatusCallback)(OH_AudioDeviceDescriptorArray *audioDeviceDescriptorArray, OH_AudioDevice_BlockStatus status, void *userData)](#oh_audioroutingmanager_ondeviceblockstatuscallback) | OH_AudioRoutingManager_OnDeviceBlockStatusCallback | This function pointer points to the callback function used to return the block status of audio devices. Multiple audio device descriptors may be returned. |
| [OH_AudioCommon_Result OH_AudioRoutingManager_IsMicBlockDetectionSupported(OH_AudioRoutingManager *audioRoutingManager, bool *supported)](#oh_audioroutingmanager_ismicblockdetectionsupported) | - | Queries whether the current device supports microphone block status detection. |
| [OH_AudioCommon_Result OH_AudioRoutingManager_SetMicBlockStatusCallback(OH_AudioRoutingManager *audioRoutingManager, OH_AudioRoutingManager_OnDeviceBlockStatusCallback callback, void *userData)](#oh_audioroutingmanager_setmicblockstatuscallback) | - | Sets the callback for whether the microphone is blocked.<br>Before using this feature, query whether the current device supports detection. The callback is received only when the application is recording with the microphone and the microphone block status changes. Currently, this detection feature supports only microphones on the local device. |

## Function Description

### OH_AudioRoutingManager_OnDeviceChangedCallback()

```c
typedef int32_t (*OH_AudioRoutingManager_OnDeviceChangedCallback)(OH_AudioDevice_ChangeType type, OH_AudioDeviceDescriptorArray *audioDeviceDescriptorArray
)
```

**Description**

This function pointer points to the callback function used to return the changed audio device descriptors. Multiple audio device descriptors may be returned.

**Since**: 12

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioDevice_ChangeType](capi-native-audio-device-base-h.md#oh_audiodevice_changetype) type | Device connection state type. [OH_AudioDevice_ChangeType](capi-native-audio-device-base-h.md#oh_audiodevice_changetype) connected or disconnected. |
| [OH_AudioDeviceDescriptorArray](capi-ohaudio-oh-audiodevicedescriptorarray.md) *audioDeviceDescriptorArray | Audio device descriptor array, a pointer variable that points to [OH_AudioDeviceDescriptorArray](capi-ohaudio-oh-audiodevicedescriptorarray.md) and sets the audio device descriptor values. Do not release the audioDeviceDescriptorArray pointer separately. Instead, call [OH_AudioRoutingManager_ReleaseDevices()](#oh_audioroutingmanager_releasedevices) to release the device descriptor array. |

### OH_AudioRoutingManager_OnPreferredOutputDeviceChangedCallback()

```c
typedef int32_t (*OH_AudioRoutingManager_OnPreferredOutputDeviceChangedCallback)(OH_AudioDeviceDescriptorArray *audioDeviceDescriptorArray)
```

**Description**

This function pointer points to the callback function used to return the output device descriptor with the highest priority. This callback returns one or more audio device descriptors.

**Since:** 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioDeviceDescriptorArray](capi-ohaudio-oh-audiodevicedescriptorarray.md) *audioDeviceDescriptorArray | Audio device descriptor array.<br> Pointer variable that sets the audio device descriptor value. Do not release the audioDeviceDescriptorArray pointer separately; instead, call [OH_AudioRoutingManager_ReleaseDevices](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_releasedevices) to release the DeviceDescriptor array. |

### OH_AudioRoutingManager_OnPreferredInputDeviceChangedCallback()

```c
typedef int32_t (*OH_AudioRoutingManager_OnPreferredInputDeviceChangedCallback)(OH_AudioDeviceDescriptorArray *audioDeviceDescriptorArray)
```

**Description**

This function pointer points to the callback function used to return the input device descriptor with the highest priority. This callback returns one or more audio device descriptors.

**Since:** 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioDeviceDescriptorArray](capi-ohaudio-oh-audiodevicedescriptorarray.md) *audioDeviceDescriptorArray | Audio device descriptor array.<br> Pointer variable that sets the audio device descriptor value. Do not release the audioDeviceDescriptorArray pointer separately. Instead, call [OH_AudioRoutingManager_ReleaseDevices](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_releasedevices) to release the DeviceDescriptor array. |

### OH_AudioManager_GetAudioRoutingManager()

```c
OH_AudioCommon_Result OH_AudioManager_GetAudioRoutingManager(OH_AudioRoutingManager **audioRoutingManager)
```

**Description**

Obtains the audio routing manager instance.<br>To use the audio routing manager features, you must first obtain the audio routing manager instance.

**Since**: 12


**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioRoutingManager](capi-ohaudio-oh-audioroutingmanager.md) **audioRoutingManager | Address of the pointer to the OH_AudioRoutingManager instance, used to receive the obtained audio routing manager instance. |

**Returns**

| Type | Description |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | Result code.<br> AUDIOCOMMON_RESULT_SUCCESS: the function is executed successfully. |

### OH_AudioRoutingManager_GetDevices()

```c
OH_AudioCommon_Result OH_AudioRoutingManager_GetDevices(OH_AudioRoutingManager *audioRoutingManager, OH_AudioDevice_Flag deviceFlag, OH_AudioDeviceDescriptorArray **audioDeviceDescriptorArray)
```

**Description**

Queries the available devices based on the input deviceFlag.

**Since**: 12


**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioRoutingManager](capi-ohaudio-oh-audioroutingmanager.md) *audioRoutingManager | Pointer to the Audio Routing Manager instance obtained through [OH_AudioManager_GetAudioRoutingManager()](#oh_audiomanager_getaudioroutingmanager). |
| [OH_AudioDevice_Flag](capi-native-audio-device-base-h.md#oh_audiodevice_flag) deviceFlag | Audio device flag, used to select the filter parameters of the target device. |
| [OH_AudioDeviceDescriptorArray](capi-ohaudio-oh-audiodevicedescriptorarray.md) **audioDeviceDescriptorArray | Audio device descriptor array. Pointer variable that stores the audio device descriptor value. Do not release the audioDeviceDescriptorArray pointer separately. Instead, call [OH_AudioRoutingManager_ReleaseDevices()](#oh_audioroutingmanager_releasedevices) to release the DeviceDescriptor array. |

**Returns**

| Type | Description |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | Result code.<br>         AUDIOCOMMON_RESULT_SUCCESS: the function is executed successfully.<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM:<br>                                                        1. The audioRoutingManager parameter is nullptr;<br>                                                        2. The deviceFlag parameter is invalid;<br>                                                        3. The audioDeviceDescriptorArray parameter is nullptr.<br>         AUDIOCOMMON_RESULT_ERROR_NO_MEMORY: insufficient memory. |

### OH_AudioRoutingManager_GetAvailableDevices()

```c
OH_AudioCommon_Result OH_AudioRoutingManager_GetAvailableDevices(OH_AudioRoutingManager *audioRoutingManager, OH_AudioDevice_Usage deviceUsage, OH_AudioDeviceDescriptorArray **audioDeviceDescriptorArray)
```

**Description**

Obtains the list of available audio devices.

**Since**: 12


**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioRoutingManager](capi-ohaudio-oh-audioroutingmanager.md) *audioRoutingManager | Pointer to the Audio Routing Manager instance obtained through [OH_AudioManager_GetAudioRoutingManager()](#oh_audiomanager_getaudioroutingmanager). |
| [OH_AudioDevice_Usage](capi-native-audio-device-base-h.md#oh_audiodevice_usage) deviceUsage | [OH_AudioDevice_Usage](capi-native-audio-device-base-h.md#oh_audiodevice_usage) used to set the type of devices to obtain. |
| [OH_AudioDeviceDescriptorArray](capi-ohaudio-oh-audiodevicedescriptorarray.md) **audioDeviceDescriptorArray | Audio device descriptor array. Pointer variable that stores the audio device descriptor value. Do not release the audioDeviceDescriptorArray pointer separately. Instead, call [OH_AudioRoutingManager_ReleaseDevices()](#oh_audioroutingmanager_releasedevices) to release the DeviceDescriptor array. |

**Returns**

| Type | Description |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | Result code.<br>         AUDIOCOMMON_RESULT_SUCCESS: the function is executed successfully.<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM:<br>                                                        1. The audioRoutingManager parameter is nullptr.<br>                                                        2. The deviceUsage parameter is invalid.<br>                                                        3. The audioDeviceDescriptorArray parameter is nullptr.<br>         AUDIOCOMMON_RESULT_ERROR_NO_MEMORY: insufficient memory. |

### OH_AudioRoutingManager_GetPreferredOutputDevice()

```c
OH_AudioCommon_Result OH_AudioRoutingManager_GetPreferredOutputDevice(OH_AudioRoutingManager *audioRoutingManager, OH_AudioStream_Usage streamUsage, OH_AudioDeviceDescriptorArray **audioDeviceDescriptorArray)
```

**Description**

Obtains the output device with the highest priority based on the usage scenario of the audio output stream.

**Since**: 12


**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioRoutingManager](capi-ohaudio-oh-audioroutingmanager.md) *audioRoutingManager | Pointer to the Audio Routing Manager instance obtained through [OH_AudioManager_GetAudioRoutingManager()](#oh_audiomanager_getaudioroutingmanager). |
| [OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage) streamUsage | [OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage) used to set the usage scenario of the audio output stream. |
| [OH_AudioDeviceDescriptorArray](capi-ohaudio-oh-audiodevicedescriptorarray.md) **audioDeviceDescriptorArray | Audio device descriptor array. Pointer variable that stores the audio device descriptor value. Do not release the audioDeviceDescriptorArray pointer separately. Instead, call [OH_AudioRoutingManager_ReleaseDevices()](#oh_audioroutingmanager_releasedevices) to release the DeviceDescriptor array. |

**Returns**

| Type | Description |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | Result code.<br>         AUDIOCOMMON_RESULT_SUCCESS: the function is executed successfully.<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM:<br>                                                        1. The audioRoutingManager parameter is nullptr.<br>                                                        2. The streamUsage parameter is invalid.<br>                                                        3. The audioDeviceDescriptorArray parameter is nullptr.<br>         AUDIOCOMMON_RESULT_ERROR_NO_MEMORY: insufficient memory. |

### OH_AudioRoutingManager_GetPreferredInputDevice()

```c
OH_AudioCommon_Result OH_AudioRoutingManager_GetPreferredInputDevice(OH_AudioRoutingManager *audioRoutingManager, OH_AudioStream_SourceType sourceType, OH_AudioDeviceDescriptorArray **audioDeviceDescriptorArray)
```

**Description**

Obtains the input device with the highest priority based on the usage scenario of the audio input stream.

**Since**: 12


**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioRoutingManager](capi-ohaudio-oh-audioroutingmanager.md) *audioRoutingManager | Pointer to the Audio Routing Manager instance obtained through [OH_AudioManager_GetAudioRoutingManager()](#oh_audiomanager_getaudioroutingmanager). |
| [OH_AudioStream_SourceType](capi-native-audiostream-base-h.md#oh_audiostream_sourcetype) sourceType | Pointer to [OH_AudioStream_SourceType](capi-native-audiostream-base-h.md#oh_audiostream_sourcetype), used to set the usage scenario of the audio input stream. |
| [OH_AudioDeviceDescriptorArray](capi-ohaudio-oh-audiodevicedescriptorarray.md) **audioDeviceDescriptorArray | Audio device descriptor array. Pointer variable that stores the audio device descriptor value. Do not release the audioDeviceDescriptorArray pointer separately. Instead, call [OH_AudioRoutingManager_ReleaseDevices()](#oh_audioroutingmanager_releasedevices) to release the DeviceDescriptor array. |

**Returns**

| Type | Description |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | Result code.<br>         AUDIOCOMMON_RESULT_SUCCESS: the function is executed successfully.<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM:<br>                                                        1. The audioRoutingManager parameter is nullptr.<br>                                                        2. The sourceType parameter is invalid.<br>                                                        3. The audioDeviceDescriptorArray parameter is nullptr.<br>         AUDIOCOMMON_RESULT_ERROR_NO_MEMORY: insufficient memory. |

### OH_AudioRoutingManager_RegisterDeviceChangeCallback()

```c
OH_AudioCommon_Result OH_AudioRoutingManager_RegisterDeviceChangeCallback(OH_AudioRoutingManager *audioRoutingManager, OH_AudioDevice_Flag deviceFlag, OH_AudioRoutingManager_OnDeviceChangedCallback callback)
```

**Description**

Registers the device change callback of the audio routing manager.

**Since**: 12


**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioRoutingManager](capi-ohaudio-oh-audioroutingmanager.md) *audioRoutingManager | Pointer to the Audio Routing Manager instance obtained through [OH_AudioManager_GetAudioRoutingManager()](#oh_audiomanager_getaudioroutingmanager). |
| [OH_AudioDevice_Flag](capi-native-audio-device-base-h.md#oh_audiodevice_flag) deviceFlag | Audio device flag used to register the callback. |
| [OH_AudioRoutingManager_OnDeviceChangedCallback()](#oh_audioroutingmanager_ondevicechangedcallback) callback | Callback invoked to return the changed audio device descriptors. |

**Returns**

| Type | Description |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | Result code.<br>         AUDIOCOMMON_RESULT_SUCCESS: the function is executed successfully.<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM:<br>                                                        1. The audioRoutingManager parameter is nullptr;<br>                                                        2. The deviceFlag parameter is invalid;<br>                                                        3. The callback parameter is nullptr. |

### OH_AudioRoutingManager_UnregisterDeviceChangeCallback()

```c
OH_AudioCommon_Result OH_AudioRoutingManager_UnregisterDeviceChangeCallback(OH_AudioRoutingManager *audioRoutingManager, OH_AudioRoutingManager_OnDeviceChangedCallback callback)
```

**Description**

Unregisters the device change callback of the audio routing manager.

**Since**: 12


**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioRoutingManager](capi-ohaudio-oh-audioroutingmanager.md) *audioRoutingManager | Pointer to the Audio Routing Manager instance obtained through [OH_AudioManager_GetAudioRoutingManager()](#oh_audiomanager_getaudioroutingmanager). |
| [OH_AudioRoutingManager_OnDeviceChangedCallback()](#oh_audioroutingmanager_ondevicechangedcallback) callback | Callback invoked to return the changed audio device descriptors. |

**Returns**

| Type | Description |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | Result code.<br>         AUDIOCOMMON_RESULT_SUCCESS: the function is executed successfully.<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM:<br>                                                        1. The audioRoutingManager parameter is nullptr.<br>                                                        2. The callback parameter is nullptr. |

### OH_AudioRoutingManager_RegisterPreferredOutputDevicesChangeCallback()

```c
OH_AudioCommon_Result OH_AudioRoutingManager_RegisterPreferredOutputDevicesChangeCallback(OH_AudioRoutingManager *audioRoutingManager, OH_AudioStream_Usage streamUsage, OH_AudioRoutingManager_OnPreferredOutputDeviceChangedCallback callback)
```

**Description**

Registers a callback for changes to the highest-priority output device of the audio routing manager. When the highest-priority output device of the specified playback stream type changes, the registered client receives the callback.<br> To avoid resource waste or other exceptions, when the application no longer needs this callback, it must call [OH_AudioRoutingManager_UnregisterPreferredOutputDevicesChangeCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_unregisterpreferredoutputdeviceschangecallback) to release the callback.

**Since:** 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioRoutingManager](capi-ohaudio-oh-audioroutingmanager.md) *audioRoutingManager | Handle to the audio routing manager. Obtain it through [OH_AudioManager_GetAudioRoutingManager](capi-native-audio-routing-manager-h.md#oh_audiomanager_getaudioroutingmanager). |
| [OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage) streamUsage | Pointer to OH_AudioStream_Usage, used to set the filter parameter for registering the highest-priority output device change event. |
| [OH_AudioRoutingManager_OnPreferredOutputDeviceChangedCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_onpreferredoutputdevicechangedcallback) callback | Pointer to OH_AudioRoutingManager_OnPreferredOutputDeviceChangedCallback, used to receive the highest-priority output device change event. |

**Returns**

| Type | Description |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | Result code.<br>         AUDIOCOMMON_RESULT_SUCCESS: the function is executed successfully.<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM: parameter verification failed.<br>         AUDIOCOMMON_RESULT_ERROR_SYSTEM: the audio client encounters a system error when calling the audio service, causing the call to fail. |

### OH_AudioRoutingManager_UnregisterPreferredOutputDevicesChangeCallback()

```c
OH_AudioCommon_Result OH_AudioRoutingManager_UnregisterPreferredOutputDevicesChangeCallback(OH_AudioRoutingManager *audioRoutingManager, OH_AudioRoutingManager_OnPreferredOutputDeviceChangedCallback callback)
```

**Description**

Unregisters the callback for the highest-priority output device change of the Audio Routing Manager that was registered through [OH_AudioRoutingManager_RegisterPreferredOutputDevicesChangeCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_registerpreferredoutputdeviceschangecallback).

**Since:** 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioRoutingManager](capi-ohaudio-oh-audioroutingmanager.md) *audioRoutingManager | Handle to the audio routing manager. Obtain it through [OH_AudioManager_GetAudioRoutingManager](capi-native-audio-routing-manager-h.md#oh_audiomanager_getaudioroutingmanager). |
| [OH_AudioRoutingManager_OnPreferredOutputDeviceChangedCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_onpreferredoutputdevicechangedcallback) callback | Pointer to OH_AudioRoutingManager_OnPreferredOutputDeviceChangedCallback, used to receive the highest-priority output device change event. When nullptr is passed in, the system cancels all registered highest-priority output device change callbacks. |

**Returns**

| Type | Description |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | Result code.<br>         AUDIOCOMMON_RESULT_SUCCESS: the function is executed successfully.<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM: parameter verification failed.<br>         AUDIOCOMMON_RESULT_ERROR_SYSTEM: the audio client encounters a system error when calling the audio service, causing the call to fail. |

### OH_AudioRoutingManager_RegisterPreferredInputDevicesChangeCallback()

```c
OH_AudioCommon_Result OH_AudioRoutingManager_RegisterPreferredInputDevicesChangeCallback(OH_AudioRoutingManager *audioRoutingManager, OH_AudioStream_SourceType sourceType, OH_AudioRoutingManager_OnPreferredInputDeviceChangedCallback callback)
```

**Description**

Registers a callback for changes to the highest-priority input device of the audio routing manager. When the highest-priority input device of the specified playback stream type changes, registered clients receive the callback.<br> To avoid resource waste or other exceptions, when the application no longer needs this callback, it must release the callback by calling [OH_AudioRoutingManager_UnregisterPreferredInputDevicesChangeCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_unregisterpreferredinputdeviceschangecallback).

**Since:** 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioRoutingManager](capi-ohaudio-oh-audioroutingmanager.md) *audioRoutingManager | Handle to the audio routing manager. Obtain it through [OH_AudioManager_GetAudioRoutingManager](capi-native-audio-routing-manager-h.md#oh_audiomanager_getaudioroutingmanager). |
| [OH_AudioStream_SourceType](capi-native-audiostream-base-h.md#oh_audiostream_sourcetype) sourceType | Pointer to OH_AudioStream_SourceType, used as the filter parameter for registering the highest-priority input device change event. |
| [OH_AudioRoutingManager_OnPreferredInputDeviceChangedCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_onpreferredinputdevicechangedcallback) callback | Pointer to OH_AudioRoutingManager_OnPreferredInputDeviceChangedCallback, used to receive the highest-priority input device change event. |

**Returns**

| Type | Description |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | Result code.<br>         AUDIOCOMMON_RESULT_SUCCESS: the function is executed successfully.<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM: parameter verification failed.<br>         AUDIOCOMMON_RESULT_ERROR_SYSTEM: the audio client encounters a system error when calling the audio service, causing the call to fail. |

### OH_AudioRoutingManager_UnregisterPreferredInputDevicesChangeCallback()

```c
OH_AudioCommon_Result OH_AudioRoutingManager_UnregisterPreferredInputDevicesChangeCallback(OH_AudioRoutingManager *audioRoutingManager, OH_AudioRoutingManager_OnPreferredInputDeviceChangedCallback callback)
```

**Description**

Unregisters the callback for the highest-priority input device change of the Audio Routing Manager that was registered through [OH_AudioRoutingManager_RegisterPreferredInputDevicesChangeCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_registerpreferredinputdeviceschangecallback).

**Since:** 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioRoutingManager](capi-ohaudio-oh-audioroutingmanager.md) *audioRoutingManager | Handle to the audio routing manager. Obtain it through [OH_AudioManager_GetAudioRoutingManager](capi-native-audio-routing-manager-h.md#oh_audiomanager_getaudioroutingmanager). |
| [OH_AudioRoutingManager_OnPreferredInputDeviceChangedCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_onpreferredinputdevicechangedcallback) callback | Callback for the highest-priority input device change event. When nullptr is passed in, the system unregisters all registered callbacks for the highest-priority input device change. |

**Returns**

| Type | Description |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | Result code.<br>         AUDIOCOMMON_RESULT_SUCCESS: the function is executed successfully.<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM: parameter verification failed.<br>         AUDIOCOMMON_RESULT_ERROR_SYSTEM: the audio client encounters a system error when calling the audio service, causing the call to fail. |

### OH_AudioRoutingManager_ReleaseDevices()

```c
OH_AudioCommon_Result OH_AudioRoutingManager_ReleaseDevices(OH_AudioRoutingManager *audioRoutingManager, OH_AudioDeviceDescriptorArray *audioDeviceDescriptorArray)
```

**Description**

Releases the audio device descriptor array object.

**Since**: 12


**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioRoutingManager](capi-ohaudio-oh-audioroutingmanager.md) *audioRoutingManager | Pointer to the Audio Routing Manager instance obtained through [OH_AudioManager_GetAudioRoutingManager()](#oh_audiomanager_getaudioroutingmanager). |
| [OH_AudioDeviceDescriptorArray](capi-ohaudio-oh-audiodevicedescriptorarray.md) *audioDeviceDescriptorArray | Audio device descriptor array to be released. To obtain it, call [OH_AudioRoutingManager_GetDevices()](#oh_audioroutingmanager_getdevices). |

**Returns**

| Type | Description |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | AUDIOCOMMON_RESULT_SUCCESS: the function is executed successfully.<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM:<br>                                                        1. The parameter audioRoutingManager is nullptr;<br>                                                        2. The parameter audioDeviceDescriptorArray is nullptr. |

### OH_AudioRoutingManager_OnDeviceBlockStatusCallback()

```c
typedef void (*OH_AudioRoutingManager_OnDeviceBlockStatusCallback)(OH_AudioDeviceDescriptorArray *audioDeviceDescriptorArray, OH_AudioDevice_BlockStatus status, void *userData)
```

**Description**

This function pointer points to the callback function used to return the block status of audio devices. Multiple audio device descriptors may be returned.

**Since:** 13


**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioDeviceDescriptorArray](capi-ohaudio-oh-audiodevicedescriptorarray.md) *audioDeviceDescriptorArray | Pointer to the audio device descriptor array. It is passed in by the system callback. The caller must call [OH_AudioRoutingManager_ReleaseDevices()](#oh_audioroutingmanager_releasedevices) to release it. |
| [OH_AudioDevice_BlockStatus](capi-native-audio-device-base-h.md#oh_audiodevice_blockstatus) status | Block status of the audio device. |
|  void *userData | Pointer to the user-defined data. |

### OH_AudioRoutingManager_IsMicBlockDetectionSupported()

```c
OH_AudioCommon_Result OH_AudioRoutingManager_IsMicBlockDetectionSupported(OH_AudioRoutingManager *audioRoutingManager, bool *supported)
```

**Description**

Queries whether the current device supports microphone block status detection.

**Since:** 13


**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioRoutingManager](capi-ohaudio-oh-audioroutingmanager.md) *audioRoutingManager | Pointer to the Audio Routing Manager instance obtained through [OH_AudioManager_GetAudioRoutingManager()](#oh_audiomanager_getaudioroutingmanager). |
| bool *supported | Pointer to the result indicating whether the current device supports microphone block status detection. The value **true** indicates supported, and **false** indicates not supported. |

**Returns**

| Type | Description |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | Result code.<br>         AUDIOCOMMON_RESULT_SUCCESS: the function is executed successfully.<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM:<br>                                                    1. The audioRoutingManager parameter is nullptr.<br>                                                    2. The supported parameter is nullptr. |

### OH_AudioRoutingManager_SetMicBlockStatusCallback()

```c
OH_AudioCommon_Result OH_AudioRoutingManager_SetMicBlockStatusCallback(OH_AudioRoutingManager *audioRoutingManager, OH_AudioRoutingManager_OnDeviceBlockStatusCallback callback, void *userData)
```

**Description**

Sets the callback for whether the microphone is blocked.<br>Before using this feature, query whether the current device supports detection. The callback is received only when the application is recording with the microphone and the microphone block status changes. Currently, this detection feature supports only microphones on the local device.

**Since:** 13


**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioRoutingManager](capi-ohaudio-oh-audioroutingmanager.md) *audioRoutingManager | Pointer to the Audio Routing Manager instance obtained through [OH_AudioManager_GetAudioRoutingManager()](#oh_audiomanager_getaudioroutingmanager). |
| [OH_AudioRoutingManager_OnDeviceBlockStatusCallback()](#oh_audioroutingmanager_ondeviceblockstatuscallback) callback | Function pointer to the callback used to return the microphone blocked status of the receiving device [OH_AudioRoutingManager_OnDeviceBlockStatusCallback()](#oh_audioroutingmanager_ondeviceblockstatuscallback). |
| void *userData | Pointer to the user-defined data. |

**Returns**

| Type | Description |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | Result code.<br>         AUDIOCOMMON_RESULT_SUCCESS: the function is executed successfully.<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM:<br>                                                    1. The parameter audioRoutingManager is nullptr.<br>                                                    2. The parameter callback is nullptr. |


