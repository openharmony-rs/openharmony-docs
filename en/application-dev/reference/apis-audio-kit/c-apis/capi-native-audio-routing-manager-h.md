# native_audio_routing_manager.h

## Overview

Declare audio routing manager related interfaces.<br> This file interface is used for the creation of audioRoutingManager as well as the registration and deregistration functions when the device connection status changes as well as the release of pointer arrays storing device information.

**Library**: libohaudio.so

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 10

**Related module**: [OHAudio](capi-ohaudio.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AudioRoutingManager](capi-ohaudio-oh-audioroutingmanager.md) | OH_AudioRoutingManager | Declaring the audio routing manager. The handle of audio routing manager used for routing and device related functions. |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef int32_t (\*OH_AudioRoutingManager_OnDeviceChangedCallback)(OH_AudioDevice_ChangeType type, OH_AudioDeviceDescriptorArray *audioDeviceDescriptorArray)](#oh_audioroutingmanager_ondevicechangedcallback) | OH_AudioRoutingManager_OnDeviceChangedCallback | This function pointer will point to the callback function that is used to return the changing audio device descriptors. There may be more than one audio device descriptor returned. |
| [typedef int32_t (\*OH_AudioRoutingManager_OnPreferredOutputDeviceChangedCallback)(OH_AudioDeviceDescriptorArray *audioDeviceDescriptorArray)](#oh_audioroutingmanager_onpreferredoutputdevicechangedcallback) | OH_AudioRoutingManager_OnPreferredOutputDeviceChangedCallback | This callback function pointer is used to return the preferred audio output device descriptors. Multiple audio device descriptors may be returned. |
| [typedef int32_t (\*OH_AudioRoutingManager_OnPreferredInputDeviceChangedCallback)(OH_AudioDeviceDescriptorArray *audioDeviceDescriptorArray)](#oh_audioroutingmanager_onpreferredinputdevicechangedcallback) | OH_AudioRoutingManager_OnPreferredInputDeviceChangedCallback | This callback function pointer is used to return the preferred audio input device descriptors. Multiple audio device descriptors may be returned. |
| [OH_AudioCommon_Result OH_AudioManager_GetAudioRoutingManager(OH_AudioRoutingManager **audioRoutingManager)](#oh_audiomanager_getaudioroutingmanager) | - | Query the audio routing manager handle. which should be set as the first parameter in routing releated functions. |
| [OH_AudioCommon_Result OH_AudioRoutingManager_GetDevices(OH_AudioRoutingManager *audioRoutingManager, OH_AudioDevice_Flag deviceFlag, OH_AudioDeviceDescriptorArray **audioDeviceDescriptorArray)](#oh_audioroutingmanager_getdevices) | - | Query the available devices according to the input deviceFlag. |
| [OH_AudioCommon_Result OH_AudioRoutingManager_GetAvailableDevices(OH_AudioRoutingManager *audioRoutingManager, OH_AudioDevice_Usage deviceUsage, OH_AudioDeviceDescriptorArray **audioDeviceDescriptorArray)](#oh_audioroutingmanager_getavailabledevices) | - | Get available devices by device usage. |
| [OH_AudioCommon_Result OH_AudioRoutingManager_GetPreferredOutputDevice(OH_AudioRoutingManager *audioRoutingManager, OH_AudioStream_Usage streamUsage, OH_AudioDeviceDescriptorArray **audioDeviceDescriptorArray)](#oh_audioroutingmanager_getpreferredoutputdevice) | - | Get preferred output devices by audio usage. |
| [OH_AudioCommon_Result OH_AudioRoutingManager_GetPreferredInputDevice(OH_AudioRoutingManager *audioRoutingManager, OH_AudioStream_SourceType sourceType, OH_AudioDeviceDescriptorArray **audioDeviceDescriptorArray)](#oh_audioroutingmanager_getpreferredinputdevice) | - | Get preferred input devices by audio source type. |
| [OH_AudioCommon_Result OH_AudioRoutingManager_RegisterDeviceChangeCallback(OH_AudioRoutingManager *audioRoutingManager, OH_AudioDevice_Flag deviceFlag, OH_AudioRoutingManager_OnDeviceChangedCallback callback)](#oh_audioroutingmanager_registerdevicechangecallback) | - | Register the device change callback of the audio routing manager. |
| [OH_AudioCommon_Result OH_AudioRoutingManager_UnregisterDeviceChangeCallback(OH_AudioRoutingManager *audioRoutingManager, OH_AudioRoutingManager_OnDeviceChangedCallback callback)](#oh_audioroutingmanager_unregisterdevicechangecallback) | - | Unregister the device change callback of the audio routing manager. |
| [OH_AudioCommon_Result OH_AudioRoutingManager_RegisterPreferredOutputDevicesChangeCallback(OH_AudioRoutingManager *audioRoutingManager, OH_AudioStream_Usage streamUsage, OH_AudioRoutingManager_OnPreferredOutputDeviceChangedCallback callback)](#oh_audioroutingmanager_registerpreferredoutputdeviceschangecallback) | - | Subscribes to preferred output device change events. When the preferred output device for the target audio stream usage changes, registered clients will receive the callback. To avoid resource waste or other abnormal situations, when your application no longer needs this callback, you must release it by calling [OH_AudioRoutingManager_UnregisterPreferredOutputDevicesChangeCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_unregisterpreferredoutputdeviceschangecallback). |
| [OH_AudioCommon_Result OH_AudioRoutingManager_UnregisterPreferredOutputDevicesChangeCallback(OH_AudioRoutingManager *audioRoutingManager, OH_AudioRoutingManager_OnPreferredOutputDeviceChangedCallback callback)](#oh_audioroutingmanager_unregisterpreferredoutputdeviceschangecallback) | - | Unsubscribes from the preferred output device change events that were registered via [OH_AudioRoutingManager_RegisterPreferredOutputDevicesChangeCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_registerpreferredoutputdeviceschangecallback). |
| [OH_AudioCommon_Result OH_AudioRoutingManager_RegisterPreferredInputDevicesChangeCallback(OH_AudioRoutingManager *audioRoutingManager, OH_AudioStream_SourceType sourceType, OH_AudioRoutingManager_OnPreferredInputDeviceChangedCallback callback)](#oh_audioroutingmanager_registerpreferredinputdeviceschangecallback) | - | Subscribes to preferred input device change events. When preferred input device for target audio stream source type changes, registered clients will receive the callback. To avoid resource waste or other abnormal situations, when your application no longer needs this callback, you must release it by calling [OH_AudioRoutingManager_UnregisterPreferredInputDevicesChangeCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_unregisterpreferredinputdeviceschangecallback). |
| [OH_AudioCommon_Result OH_AudioRoutingManager_UnregisterPreferredInputDevicesChangeCallback(OH_AudioRoutingManager *audioRoutingManager, OH_AudioRoutingManager_OnPreferredInputDeviceChangedCallback callback)](#oh_audioroutingmanager_unregisterpreferredinputdeviceschangecallback) | - | Unsubscribes from the preferred input device change events that were registered via [OH_AudioRoutingManager_RegisterPreferredInputDevicesChangeCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_registerpreferredinputdeviceschangecallback). |
| [OH_AudioCommon_Result OH_AudioRoutingManager_ReleaseDevices(OH_AudioRoutingManager *audioRoutingManager, OH_AudioDeviceDescriptorArray *audioDeviceDescriptorArray)](#oh_audioroutingmanager_releasedevices) | - | Release the audio device descriptor array object. |
| [typedef void (\*OH_AudioRoutingManager_OnDeviceBlockStatusCallback)(OH_AudioDeviceDescriptorArray *audioDeviceDescriptorArray, OH_AudioDevice_BlockStatus status, void *userData)](#oh_audioroutingmanager_ondeviceblockstatuscallback) | OH_AudioRoutingManager_OnDeviceBlockStatusCallback | This type defines the callback function that is used to receive the audio devices' block status. |
| [OH_AudioCommon_Result OH_AudioRoutingManager_IsMicBlockDetectionSupported(OH_AudioRoutingManager *audioRoutingManager, bool *supported)](#oh_audioroutingmanager_ismicblockdetectionsupported) | - | Query whether microphone block detection is supported on current device. |
| [OH_AudioCommon_Result OH_AudioRoutingManager_SetMicBlockStatusCallback(OH_AudioRoutingManager *audioRoutingManager, OH_AudioRoutingManager_OnDeviceBlockStatusCallback callback, void *userData)](#oh_audioroutingmanager_setmicblockstatuscallback) | - | Set the microphone block status callback. Before using this function, users should query whether block detection is supported on current device. The caller will receive the callback only when it is recording and the used microphones' block status have changed. Currently, block detecting is only support for microphones located on the local device. |

### Variable

| Name | Description |
| -- | -- |
| int32_t (*OH_AudioRoutingManager_OnDeviceChangedCallback) ( OH_AudioDevice_ChangeType type, OH_AudioDeviceDescriptorArray *audioDeviceDescriptorArray ) | This function pointer will point to the callback function that is used to return the changing audio device descriptors. There may be more than one audio device descriptor returned.<br>**Since**: 12 |
| int32_t (*OH_AudioRoutingManager_OnPreferredOutputDeviceChangedCallback) ( OH_AudioDeviceDescriptorArray *audioDeviceDescriptorArray) | This callback function pointer is used to return the preferred audio output device descriptors. Multiple audio device descriptors may be returned.<br>**Since**: 26.0.0 |
| int32_t (*OH_AudioRoutingManager_OnPreferredInputDeviceChangedCallback) ( OH_AudioDeviceDescriptorArray *audioDeviceDescriptorArray) | This callback function pointer is used to return the preferred audio input device descriptors. Multiple audio device descriptors may be returned.<br>**Since**: 26.0.0 |
| void (*OH_AudioRoutingManager_OnDeviceBlockStatusCallback)( OH_AudioDeviceDescriptorArray *audioDeviceDescriptorArray, OH_AudioDevice_BlockStatus status, void *userData) | This type defines the callback function that is used to receive the audio devices' block status.<br>**Since**: 13 |

## Function description

### OH_AudioRoutingManager_OnDeviceChangedCallback()

```c
typedef int32_t (*OH_AudioRoutingManager_OnDeviceChangedCallback)(OH_AudioDevice_ChangeType type, OH_AudioDeviceDescriptorArray *audioDeviceDescriptorArray)
```

**Description**

This function pointer will point to the callback function that is used to return the changing audio device descriptors. There may be more than one audio device descriptor returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioDevice_ChangeType type | the {@link OH_AudioDevice_ChangeType} is connect or disconnect. |
| OH_AudioDeviceDescriptorArray \*audioDeviceDescriptorArray | the {@link OH_AudioDeviceDescriptorArray} pointer variable which will be set the audio device descriptors value. Do not release the audioDeviceDescriptorArray pointer separately instead call [OH_AudioRoutingManager_ReleaseDevices](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_releasedevices) to release the DeviceDescriptor array when it is no use anymore. |

### OH_AudioRoutingManager_OnPreferredOutputDeviceChangedCallback()

```c
typedef int32_t (*OH_AudioRoutingManager_OnPreferredOutputDeviceChangedCallback)(OH_AudioDeviceDescriptorArray *audioDeviceDescriptorArray)
```

**Description**

This callback function pointer is used to return the preferred audio output device descriptors. Multiple audio device descriptors may be returned.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioDeviceDescriptorArray \*audioDeviceDescriptorArray | a pointer to {@link OH_AudioDeviceDescriptorArray} that will be populated with the audio output device descriptor values. Do not release this pointer separately; instead, call [OH_AudioRoutingManager_ReleaseDevices](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_releasedevices) to release the device descriptor array when it is no longer needed. |

### OH_AudioRoutingManager_OnPreferredInputDeviceChangedCallback()

```c
typedef int32_t (*OH_AudioRoutingManager_OnPreferredInputDeviceChangedCallback)(OH_AudioDeviceDescriptorArray *audioDeviceDescriptorArray)
```

**Description**

This callback function pointer is used to return the preferred audio input device descriptors. Multiple audio device descriptors may be returned.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioDeviceDescriptorArray \*audioDeviceDescriptorArray | pointer to {@link OH_AudioDeviceDescriptorArray} that will be populated with the audio input device descriptor values. Do not release this pointer separately; instead, call [OH_AudioRoutingManager_ReleaseDevices](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_releasedevices) to release the device descriptor array when it is no longer needed. |

### OH_AudioManager_GetAudioRoutingManager()

```c
OH_AudioCommon_Result OH_AudioManager_GetAudioRoutingManager(OH_AudioRoutingManager **audioRoutingManager)
```

**Description**

Query the audio routing manager handle. which should be set as the first parameter in routing releated functions.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioRoutingManager](capi-ohaudio-oh-audioroutingmanager.md) **audioRoutingManager | the [OH_AudioRoutingManager](capi-ohaudio-oh-audioroutingmanager.md) handle returned by [OH_AudioManager_GetAudioRoutingManager](capi-native-audio-routing-manager-h.md#oh_audiomanager_getaudioroutingmanager). |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | Function result code:          {@link AUDIOCOMMON_RESULT_SUCCESS} If the execution is successful. |

### OH_AudioRoutingManager_GetDevices()

```c
OH_AudioCommon_Result OH_AudioRoutingManager_GetDevices(OH_AudioRoutingManager *audioRoutingManager, OH_AudioDevice_Flag deviceFlag, OH_AudioDeviceDescriptorArray **audioDeviceDescriptorArray)
```

**Description**

Query the available devices according to the input deviceFlag.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioRoutingManager](capi-ohaudio-oh-audioroutingmanager.md) *audioRoutingManager | the [OH_AudioRoutingManager](capi-ohaudio-oh-audioroutingmanager.md) handle returned by [OH_AudioManager_GetAudioRoutingManager](capi-native-audio-routing-manager-h.md#oh_audiomanager_getaudioroutingmanager). |
| OH_AudioDevice_Flag deviceFlag | the {@link OH_AudioDevice_DeviceFlag} which is used as the filter parameter for selecting the target devices. |
| OH_AudioDeviceDescriptorArray **audioDeviceDescriptorArray | the {@link OH_AudioDeviceDescriptorArray} pointer variable which will be set the audio device descriptors value Do not release the audioDeviceDescriptorArray pointer separately instead call [OH_AudioRoutingManager_ReleaseDevices](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_releasedevices) to release the DeviceDescriptor array when it is no use anymore. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | Function result code:          {@link AUDIOCOMMON_RESULT_SUCCESS} If the execution is successful.<br>        {@link AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM}:<br>                                                       1.The param of audioRoutingManager is nullptr;<br>                                                       2.The param of deviceFlag invalid;<br>                                                       3.The param of audioDeviceDescriptorArray is nullptr.<br>        {@link AUDIOCOMMON_RESULT_ERROR_NO_MEMORY} The param of audioDeviceDescriptorArray is nullptr. |

### OH_AudioRoutingManager_GetAvailableDevices()

```c
OH_AudioCommon_Result OH_AudioRoutingManager_GetAvailableDevices(OH_AudioRoutingManager *audioRoutingManager, OH_AudioDevice_Usage deviceUsage, OH_AudioDeviceDescriptorArray **audioDeviceDescriptorArray)
```

**Description**

Get available devices by device usage.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioRoutingManager](capi-ohaudio-oh-audioroutingmanager.md) *audioRoutingManager | the [OH_AudioRoutingManager](capi-ohaudio-oh-audioroutingmanager.md) handle returned by [OH_AudioManager_GetAudioRoutingManager](capi-native-audio-routing-manager-h.md#oh_audiomanager_getaudioroutingmanager). |
| OH_AudioDevice_Usage deviceUsage | the {@link OH_AudioDevice_Usage}. |
| OH_AudioDeviceDescriptorArray **audioDeviceDescriptorArray | the {@link OH_AudioDeviceDescriptorArray} pointer variable which will be set the audio device descriptors value Do not release the audioDeviceDescriptorArray pointer separately instead call [OH_AudioRoutingManager_ReleaseDevices](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_releasedevices) to release the DeviceDescriptor array when it is no use anymore. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | Function result code:          {@link AUDIOCOMMON_RESULT_SUCCESS} If the execution is successful.<br>        {@link AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM}:<br>                                                       1.The param of audioRoutingManager is nullptr;<br>                                                       2.The param of deviceUsage is invalid;<br>                                                       3.The param of audioDeviceDescriptorArray is nullptr.<br>        {@link AUDIOCOMMON_RESULT_ERROR_NO_MEMORY} No memory error. |

### OH_AudioRoutingManager_GetPreferredOutputDevice()

```c
OH_AudioCommon_Result OH_AudioRoutingManager_GetPreferredOutputDevice(OH_AudioRoutingManager *audioRoutingManager, OH_AudioStream_Usage streamUsage, OH_AudioDeviceDescriptorArray **audioDeviceDescriptorArray)
```

**Description**

Get preferred output devices by audio usage.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioRoutingManager](capi-ohaudio-oh-audioroutingmanager.md) *audioRoutingManager | the [OH_AudioRoutingManager](capi-ohaudio-oh-audioroutingmanager.md) handle returned by [OH_AudioManager_GetAudioRoutingManager](capi-native-audio-routing-manager-h.md#oh_audiomanager_getaudioroutingmanager). |
| OH_AudioStream_Usage streamUsage | the {@link OH_AudioStream_Usage}. |
| OH_AudioDeviceDescriptorArray **audioDeviceDescriptorArray | the {@link OH_AudioDeviceDescriptorArray} pointer variable which will be set the audio device descriptors value Do not release the audioDeviceDescriptorArray pointer separately instead call [OH_AudioRoutingManager_ReleaseDevices](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_releasedevices) to release the DeviceDescriptor array when it is no use anymore. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | Function result code:          {@link AUDIOCOMMON_RESULT_SUCCESS} If the execution is successful.<br>        {@link AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM}:<br>                                                       1.The param of audioRoutingManager is nullptr;<br>                                                       2.The param of streamUsage is invalid;<br>                                                       3.The param of audioDeviceDescriptorArray is nullptr.<br>        {@link AUDIOCOMMON_RESULT_ERROR_NO_MEMORY} No memory error. |

### OH_AudioRoutingManager_GetPreferredInputDevice()

```c
OH_AudioCommon_Result OH_AudioRoutingManager_GetPreferredInputDevice(OH_AudioRoutingManager *audioRoutingManager, OH_AudioStream_SourceType sourceType, OH_AudioDeviceDescriptorArray **audioDeviceDescriptorArray)
```

**Description**

Get preferred input devices by audio source type.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioRoutingManager](capi-ohaudio-oh-audioroutingmanager.md) *audioRoutingManager | the [OH_AudioRoutingManager](capi-ohaudio-oh-audioroutingmanager.md) handle returned by [OH_AudioManager_GetAudioRoutingManager](capi-native-audio-routing-manager-h.md#oh_audiomanager_getaudioroutingmanager). |
| OH_AudioStream_SourceType sourceType | the {@link OH_AudioStream_SourceType}. |
| OH_AudioDeviceDescriptorArray **audioDeviceDescriptorArray | the {@link OH_AudioDeviceDescriptorArray} pointer variable which will be set the audio device descriptors value Do not release the audioDeviceDescriptorArray pointer separately instead call [OH_AudioRoutingManager_ReleaseDevices](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_releasedevices) to release the DeviceDescriptor array when it is no use anymore. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | Function result code:          {@link AUDIOCOMMON_RESULT_SUCCESS} If the execution is successful.<br>        {@link AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM}:<br>                                                       1.The param of audioRoutingManager is nullptr;<br>                                                       2.The param of sourceType is invalid;<br>                                                       3.The param of audioDeviceDescriptorArray is nullptr.<br>        {@link AUDIOCOMMON_RESULT_ERROR_NO_MEMORY} No memory error. |

### OH_AudioRoutingManager_RegisterDeviceChangeCallback()

```c
OH_AudioCommon_Result OH_AudioRoutingManager_RegisterDeviceChangeCallback(OH_AudioRoutingManager *audioRoutingManager, OH_AudioDevice_Flag deviceFlag, OH_AudioRoutingManager_OnDeviceChangedCallback callback)
```

**Description**

Register the device change callback of the audio routing manager.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioRoutingManager](capi-ohaudio-oh-audioroutingmanager.md) *audioRoutingManager | the [OH_AudioRoutingManager](capi-ohaudio-oh-audioroutingmanager.md) handle returned by [OH_AudioManager_GetAudioRoutingManager](capi-native-audio-routing-manager-h.md#oh_audiomanager_getaudioroutingmanager). |
| OH_AudioDevice_Flag deviceFlag | the {@link OH_AudioDevice_DeviceFlag} which is used to register callback. |
| [OH_AudioRoutingManager_OnDeviceChangedCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_ondevicechangedcallback) callback | the [OH_AudioRoutingManager_OnDeviceChangedCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_ondevicechangedcallback) Callback function which will be called when devices changed. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | Function result code:          {@link AUDIOCOMMON_RESULT_SUCCESS} If the execution is successful.<br>        {@link AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM}:                                                         1.The param of audioRoutingManager is nullptr;                                                         2.The param of deviceFlag invalid;                                                         3.The param of callback is nullptr. |

### OH_AudioRoutingManager_UnregisterDeviceChangeCallback()

```c
OH_AudioCommon_Result OH_AudioRoutingManager_UnregisterDeviceChangeCallback(OH_AudioRoutingManager *audioRoutingManager, OH_AudioRoutingManager_OnDeviceChangedCallback callback)
```

**Description**

Unregister the device change callback of the audio routing manager.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioRoutingManager](capi-ohaudio-oh-audioroutingmanager.md) *audioRoutingManager | the [OH_AudioRoutingManager](capi-ohaudio-oh-audioroutingmanager.md) handle returned by [OH_AudioManager_GetAudioRoutingManager](capi-native-audio-routing-manager-h.md#oh_audiomanager_getaudioroutingmanager). |
| [OH_AudioRoutingManager_OnDeviceChangedCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_ondevicechangedcallback) callback | the [OH_AudioRoutingManager_OnDeviceChangedCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_ondevicechangedcallback) Callback function which will be called when devices changed. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | Function result code:          {@link AUDIOCOMMON_RESULT_SUCCESS} If the execution is successful.<br>        {@link AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM}:                                                         1.The param of audioRoutingManager is nullptr;                                                         2.The param of callback is nullptr. |

### OH_AudioRoutingManager_RegisterPreferredOutputDevicesChangeCallback()

```c
OH_AudioCommon_Result OH_AudioRoutingManager_RegisterPreferredOutputDevicesChangeCallback(OH_AudioRoutingManager *audioRoutingManager, OH_AudioStream_Usage streamUsage, OH_AudioRoutingManager_OnPreferredOutputDeviceChangedCallback callback)
```

**Description**

Subscribes to preferred output device change events. When the preferred output device for the target audio stream usage changes, registered clients will receive the callback. To avoid resource waste or other abnormal situations, when your application no longer needs this callback, you must release it by calling [OH_AudioRoutingManager_UnregisterPreferredOutputDevicesChangeCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_unregisterpreferredoutputdeviceschangecallback).

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioRoutingManager](capi-ohaudio-oh-audioroutingmanager.md) *audioRoutingManager | the [OH_AudioRoutingManager](capi-ohaudio-oh-audioroutingmanager.md) handle returned by [OH_AudioManager_GetAudioRoutingManager](capi-native-audio-routing-manager-h.md#oh_audiomanager_getaudioroutingmanager). |
| OH_AudioStream_Usage streamUsage | the {@link OH_AudioStream_Usage} which is used as the filter parameter for registering the preferred output device change event. |
| [OH_AudioRoutingManager_OnPreferredOutputDeviceChangedCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_onpreferredoutputdevicechangedcallback) callback | the [OH_AudioRoutingManager_OnPreferredOutputDeviceChangedCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_onpreferredoutputdevicechangedcallback) which is used to receive preferred output device change events. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | {@link #AUDIOCOMMON_RESULT_SUCCESS} if execution succeeds,<br>    or {@link #AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM} if parameter validation fails,<br>    or {@link #AUDIOCOMMON_RESULT_ERROR_SYSTEM} Audio client call audio service error, System error. |

### OH_AudioRoutingManager_UnregisterPreferredOutputDevicesChangeCallback()

```c
OH_AudioCommon_Result OH_AudioRoutingManager_UnregisterPreferredOutputDevicesChangeCallback(OH_AudioRoutingManager *audioRoutingManager, OH_AudioRoutingManager_OnPreferredOutputDeviceChangedCallback callback)
```

**Description**

Unsubscribes from the preferred output device change events that were registered via [OH_AudioRoutingManager_RegisterPreferredOutputDevicesChangeCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_registerpreferredoutputdeviceschangecallback).

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioRoutingManager](capi-ohaudio-oh-audioroutingmanager.md) *audioRoutingManager | the [OH_AudioRoutingManager](capi-ohaudio-oh-audioroutingmanager.md) handle returned by [OH_AudioManager_GetAudioRoutingManager](capi-native-audio-routing-manager-h.md#oh_audiomanager_getaudioroutingmanager). |
| [OH_AudioRoutingManager_OnPreferredOutputDeviceChangedCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_onpreferredoutputdevicechangedcallback) callback | the [OH_AudioRoutingManager_OnPreferredOutputDeviceChangedCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_onpreferredoutputdevicechangedcallback) which is used to receive preferred output device change event. When nullptr is passed, the system will unregister all previously registered preferred output device change callbacks. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | {@link #AUDIOCOMMON_RESULT_SUCCESS} if execution succeeds,<br>    or {@link #AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM} if parameter validation fails,<br>    or {@link #AUDIOCOMMON_RESULT_ERROR_SYSTEM} Audio client call audio service error, System error. |

### OH_AudioRoutingManager_RegisterPreferredInputDevicesChangeCallback()

```c
OH_AudioCommon_Result OH_AudioRoutingManager_RegisterPreferredInputDevicesChangeCallback(OH_AudioRoutingManager *audioRoutingManager, OH_AudioStream_SourceType sourceType, OH_AudioRoutingManager_OnPreferredInputDeviceChangedCallback callback)
```

**Description**

Subscribes to preferred input device change events. When preferred input device for target audio stream source type changes, registered clients will receive the callback. To avoid resource waste or other abnormal situations, when your application no longer needs this callback, you must release it by calling [OH_AudioRoutingManager_UnregisterPreferredInputDevicesChangeCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_unregisterpreferredinputdeviceschangecallback).

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioRoutingManager](capi-ohaudio-oh-audioroutingmanager.md) *audioRoutingManager | the [OH_AudioRoutingManager](capi-ohaudio-oh-audioroutingmanager.md) handle returned by [OH_AudioManager_GetAudioRoutingManager](capi-native-audio-routing-manager-h.md#oh_audiomanager_getaudioroutingmanager). |
| OH_AudioStream_SourceType sourceType | the {@link OH_AudioStream_SourceType} which is used as the filter parameter for registering the preferred input devices change event. |
| [OH_AudioRoutingManager_OnPreferredInputDeviceChangedCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_onpreferredinputdevicechangedcallback) callback | the [OH_AudioRoutingManager_OnPreferredInputDeviceChangedCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_onpreferredinputdevicechangedcallback) which is used to receive preferred input device change event. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | {@link #AUDIOCOMMON_RESULT_SUCCESS} if execution succeeds,<br>    or {@link #AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM} if parameter validation fails,<br>    or {@link #AUDIOCOMMON_RESULT_ERROR_SYSTEM} Audio client call audio service error, System error. |

### OH_AudioRoutingManager_UnregisterPreferredInputDevicesChangeCallback()

```c
OH_AudioCommon_Result OH_AudioRoutingManager_UnregisterPreferredInputDevicesChangeCallback(OH_AudioRoutingManager *audioRoutingManager, OH_AudioRoutingManager_OnPreferredInputDeviceChangedCallback callback)
```

**Description**

Unsubscribes from the preferred input device change events that were registered via [OH_AudioRoutingManager_RegisterPreferredInputDevicesChangeCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_registerpreferredinputdeviceschangecallback).

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioRoutingManager](capi-ohaudio-oh-audioroutingmanager.md) *audioRoutingManager | the [OH_AudioRoutingManager](capi-ohaudio-oh-audioroutingmanager.md) handle returned by [OH_AudioManager_GetAudioRoutingManager](capi-native-audio-routing-manager-h.md#oh_audiomanager_getaudioroutingmanager). |
| [OH_AudioRoutingManager_OnPreferredInputDeviceChangedCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_onpreferredinputdevicechangedcallback) callback | the [OH_AudioRoutingManager_OnPreferredInputDeviceChangedCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_onpreferredinputdevicechangedcallback) which is used to receive preferred input device change events. If nullptr is passed, the system will unregister all previously registered preferred input device change callbacks. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | {@link #AUDIOCOMMON_RESULT_SUCCESS} if execution succeeds,<br>    or {@link #AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM} if parameter validation fails,<br>    or {@link #AUDIOCOMMON_RESULT_ERROR_SYSTEM} Audio client call audio service error, System error. |

### OH_AudioRoutingManager_ReleaseDevices()

```c
OH_AudioCommon_Result OH_AudioRoutingManager_ReleaseDevices(OH_AudioRoutingManager *audioRoutingManager, OH_AudioDeviceDescriptorArray *audioDeviceDescriptorArray)
```

**Description**

Release the audio device descriptor array object.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioRoutingManager](capi-ohaudio-oh-audioroutingmanager.md) *audioRoutingManager | the [OH_AudioRoutingManager](capi-ohaudio-oh-audioroutingmanager.md) handle returned by [OH_AudioManager_GetAudioRoutingManager](capi-native-audio-routing-manager-h.md#oh_audiomanager_getaudioroutingmanager). |
| OH_AudioDeviceDescriptorArray *audioDeviceDescriptorArray | Audio device descriptors should be released. and get from [OH_AudioRoutingManager_GetDevices](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_getdevices) |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | Function result code:          {@link AUDIOCOMMON_RESULT_SUCCESS} If the execution is successful.<br>        {@link AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM}:                                                         1.The param of audioRoutingManager is nullptr;                                                         2.The param of audioDeviceDescriptorArray is nullptr. |

### OH_AudioRoutingManager_OnDeviceBlockStatusCallback()

```c
typedef void (*OH_AudioRoutingManager_OnDeviceBlockStatusCallback)(OH_AudioDeviceDescriptorArray *audioDeviceDescriptorArray, OH_AudioDevice_BlockStatus status, void *userData)
```

**Description**

This type defines the callback function that is used to receive the audio devices' block status.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AudioDeviceDescriptorArray \*audioDeviceDescriptorArray | The {@link OH_AudioDeviceDescriptorArray} pointer variable which will be set the audio device descriptors value. Do not release the audioDeviceDescriptorArray pointer separately instead of calling [OH_AudioRoutingManager_ReleaseDevices](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_releasedevices) to release the DeviceDescriptor array when it is no use anymore. |
| OH_AudioDevice_BlockStatus status | The {@link OH_AudioDevice_BlockStatus} is the block status. |
| void \*userData | User data which is passed by user. |

### OH_AudioRoutingManager_IsMicBlockDetectionSupported()

```c
OH_AudioCommon_Result OH_AudioRoutingManager_IsMicBlockDetectionSupported(OH_AudioRoutingManager *audioRoutingManager, bool *supported)
```

**Description**

Query whether microphone block detection is supported on current device.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioRoutingManager](capi-ohaudio-oh-audioroutingmanager.md) *audioRoutingManager | the [OH_AudioRoutingManager](capi-ohaudio-oh-audioroutingmanager.md) handle returned by [OH_AudioManager_GetAudioRoutingManager](capi-native-audio-routing-manager-h.md#oh_audiomanager_getaudioroutingmanager). |
| bool *supported | query result. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | Function result code:      {@link AUDIOCOMMON_RESULT_SUCCESS} If the execution is successful.<br>    {@link AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM}:                                                     1.The param of audioRoutingManager is nullptr;                                                     2.The param of supported is nullptr. |

### OH_AudioRoutingManager_SetMicBlockStatusCallback()

```c
OH_AudioCommon_Result OH_AudioRoutingManager_SetMicBlockStatusCallback(OH_AudioRoutingManager *audioRoutingManager, OH_AudioRoutingManager_OnDeviceBlockStatusCallback callback, void *userData)
```

**Description**

Set the microphone block status callback. Before using this function, users should query whether block detection is supported on current device. The caller will receive the callback only when it is recording and the used microphones' block status have changed. Currently, block detecting is only support for microphones located on the local device.

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioRoutingManager](capi-ohaudio-oh-audioroutingmanager.md) *audioRoutingManager | The [OH_AudioRoutingManager](capi-ohaudio-oh-audioroutingmanager.md) handle returned by [OH_AudioManager_GetAudioRoutingManager](capi-native-audio-routing-manager-h.md#oh_audiomanager_getaudioroutingmanager). |
| [OH_AudioRoutingManager_OnDeviceBlockStatusCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_ondeviceblockstatuscallback) callback | The function pointer will point to the callback function that is used to receive the block status. |
| void *userData | User data which is passed by user. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | Function result code:      {@link AUDIOCOMMON_RESULT_SUCCESS} If the execution is successful.<br>    {@link AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM}:                                                     1.The param of audioRoutingManager is nullptr;                                                     2.The param of callback is nullptr. |


