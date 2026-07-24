# native_audio_device_base.h

<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @zhanganxiang1-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=1961de06e85063963f633ec54a8a4baaf5cb7dc8 translatedAt=2026-07-21T03:53:11.442Z pushedAt=2026-07-21T08:21:20.516Z -->

## Overview

The file declares the types of audio device parameters and the functions for obtaining these parameters.

**Library**: libohaudio.so

**File to include**: <ohaudio/native_audio_device_base.h>

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 12

**Related module**: [OHAudio](capi-ohaudio.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_AudioDeviceDescriptorArray](capi-ohaudio-oh-audiodevicedescriptorarray.md) | OH_AudioDeviceDescriptorArray | Describes an array of audio device descriptors.|
| [OH_AudioDeviceDescriptor](capi-ohaudio-oh-audiodevicedescriptor.md) | OH_AudioDeviceDescriptor | Declares an audio device descriptor, which is used to obtain detailed attribute information of an audio device. |

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_AudioDevice_ChangeType](#oh_audiodevice_changetype) | OH_AudioDevice_ChangeType | Enumerates the types of audio device changes.|
| [OH_AudioDevice_Role](#oh_audiodevice_role) | OH_AudioDevice_Role | Enumerates the roles of audio devices.|
| [OH_AudioDevice_Type](#oh_audiodevice_type) | OH_AudioDevice_Type | Enumerates the types of audio devices.|
| [OH_AudioDevice_Flag](#oh_audiodevice_flag) | OH_AudioDevice_Flag | Enumerates the flags of audio devices.|
| [OH_AudioDevice_Usage](#oh_audiodevice_usage) | OH_AudioDevice_Usage | Enumerates the usage scenarios of audio devices.|
| [OH_AudioDevice_BlockStatus](#oh_audiodevice_blockstatus) | OH_AudioDevice_BlockStatus | Enumerates the blocking statuses of an audio device. By default, an audio device is considered unblocked. |

### Functions

| Name| Description|
| -- | -- |
| [OH_AudioCommon_Result OH_AudioDeviceDescriptor_GetDeviceRole(OH_AudioDeviceDescriptor *audioDeviceDescriptor, OH_AudioDevice_Role *deviceRole)](#oh_audiodevicedescriptor_getdevicerole) | Obtains the device role based on an audio device descriptor.|
| [OH_AudioCommon_Result OH_AudioDeviceDescriptor_GetDeviceType(OH_AudioDeviceDescriptor *audioDeviceDescriptor, OH_AudioDevice_Type *deviceType)](#oh_audiodevicedescriptor_getdevicetype) | Obtains the device type based on an audio device descriptor.|
| [OH_AudioCommon_Result OH_AudioDeviceDescriptor_GetDeviceId(OH_AudioDeviceDescriptor *audioDeviceDescriptor, uint32_t *id)](#oh_audiodevicedescriptor_getdeviceid) | Obtains the device ID of the target audio device descriptor. |
| [OH_AudioCommon_Result OH_AudioDeviceDescriptor_GetDeviceName(OH_AudioDeviceDescriptor *audioDeviceDescriptor, char **name)](#oh_audiodevicedescriptor_getdevicename) | Obtains the device name based on an audio device descriptor.|
| [OH_AudioCommon_Result OH_AudioDeviceDescriptor_GetDeviceAddress(OH_AudioDeviceDescriptor *audioDeviceDescriptor, char **address)](#oh_audiodevicedescriptor_getdeviceaddress) | Obtains the device address based on an audio device descriptor.|
| [OH_AudioCommon_Result OH_AudioDeviceDescriptor_GetDeviceSampleRates(OH_AudioDeviceDescriptor *audioDeviceDescriptor, uint32_t **sampleRates, uint32_t *size)](#oh_audiodevicedescriptor_getdevicesamplerates) | Obtains the sample rates based on an audio device descriptor.|
| [OH_AudioCommon_Result OH_AudioDeviceDescriptor_GetDeviceChannelCounts(OH_AudioDeviceDescriptor *audioDeviceDescriptor, uint32_t **channelCounts, uint32_t *size)](#oh_audiodevicedescriptor_getdevicechannelcounts) | Obtains an array that holds the number of device channels based on an audio device descriptor.|
| [OH_AudioCommon_Result OH_AudioDeviceDescriptor_GetDeviceDisplayName(OH_AudioDeviceDescriptor *audioDeviceDescriptor, char **displayName)](#oh_audiodevicedescriptor_getdevicedisplayname) | Obtains the device display name based on an audio device descriptor.|
| [OH_AudioCommon_Result OH_AudioDeviceDescriptor_GetDeviceEncodingTypes(OH_AudioDeviceDescriptor *audioDeviceDescriptor, OH_AudioStream_EncodingType **encodingTypes, uint32_t *size)](#oh_audiodevicedescriptor_getdeviceencodingtypes) | Obtains the device encoding types based on an audio device descriptor.|

## Enum Description

### OH_AudioDevice_ChangeType

```c
enum OH_AudioDevice_ChangeType
```

**Description**

Enumerates the types of audio device changes.

**Since**: 12

| Enum Item| Description|
| -- | -- |
| AUDIO_DEVICE_CHANGE_TYPE_CONNECT = 0 | Device connected.|
| AUDIO_DEVICE_CHANGE_TYPE_DISCONNECT = 1 | Device disconnected.|

### OH_AudioDevice_Role

```c
enum OH_AudioDevice_Role
```

**Description**

Enumerates the roles of audio devices.

**Since**: 12

| Enum Item| Description|
| -- | -- |
| AUDIO_DEVICE_ROLE_INPUT = 1 | Input device.|
| AUDIO_DEVICE_ROLE_OUTPUT = 2 | Output device.|

### OH_AudioDevice_Type

```c
enum OH_AudioDevice_Type
```

**Description**

Enumerates the types of audio devices.

**Since**: 12

| Enum Item| Description|
| -- | -- |
| AUDIO_DEVICE_TYPE_INVALID = 0 | Invalid device.|
| AUDIO_DEVICE_TYPE_EARPIECE = 1 | Earpiece.|
| AUDIO_DEVICE_TYPE_SPEAKER = 2 | Speaker.|
| AUDIO_DEVICE_TYPE_WIRED_HEADSET = 3 | Wired headset with a microphone.|
| AUDIO_DEVICE_TYPE_WIRED_HEADPHONES = 4 | Wired headset without a microphone.|
| AUDIO_DEVICE_TYPE_BLUETOOTH_SCO = 7 | Bluetooth device using Synchronous Connection-oriented (SCO) links.|
| AUDIO_DEVICE_TYPE_BLUETOOTH_A2DP = 8 | Bluetooth device using Advanced Audio Distribution Profile (A2DP) links.|
| AUDIO_DEVICE_TYPE_MIC = 15 | Microphone.|
| AUDIO_DEVICE_TYPE_USB_HEADSET = 22 | USB headset.|
| AUDIO_DEVICE_TYPE_DISPLAY_PORT = 23 | Display port device.|
| AUDIO_DEVICE_TYPE_REMOTE_CAST = 24 | Remote cast device.|
| AUDIO_DEVICE_TYPE_USB_DEVICE = 25 | USB device (excluding USB headsets).<br>**Since**: 18|
| AUDIO_DEVICE_TYPE_ACCESSORY = 26 | Accessory device, such as the microphone on a remote control.<br>**Since**: 19|
| AUDIO_DEVICE_TYPE_HDMI = 27 | HDMI device (such as HDMI, ARC, and eARC).<br>**Since**: 19|
| AUDIO_DEVICE_TYPE_LINE_DIGITAL = 28 | Wired digital device (such as S/PDIF).<br>**Since**: 19|
| AUDIO_DEVICE_TYPE_HEARING_AID = 30 | Hearing aid device.<br>**Since**: 20|
| AUDIO_DEVICE_TYPE_NEARLINK = 31 | NearLink device.<br>**Since**: 20|
| AUDIO_DEVICE_TYPE_DEFAULT = 1000 | Default device type.|

### OH_AudioDevice_Flag

```c
enum OH_AudioDevice_Flag
```

**Description**

Enumerates the flags of audio devices.

**Since**: 12

| Enum Item| Description|
| -- | -- |
| AUDIO_DEVICE_FLAG_NONE = 0 | No device.|
| AUDIO_DEVICE_FLAG_OUTPUT = 1 | Output device.|
| AUDIO_DEVICE_FLAG_INPUT = 2 | Input device.|
| AUDIO_DEVICE_FLAG_ALL = 3 | All devices.|

### OH_AudioDevice_Usage

```c
enum OH_AudioDevice_Usage
```

**Description**

Enumerates the usage scenarios of audio devices.

**Since**: 12

| Enum Item| Description|
| -- | -- |
| AUDIO_DEVICE_USAGE_MEDIA_OUTPUT = 1 | Media output device.|
| AUDIO_DEVICE_USAGE_MEDIA_INPUT = 2 | Media input device.|
| AUDIO_DEVICE_USAGE_MEDIA_ALL = 3 | All media devices.|
| AUDIO_DEVICE_USAGE_CALL_OUTPUT = 4 | Call output device.|
| AUDIO_DEVICE_USAGE_CALL_INPUT = 8 | Call input device.|
| AUDIO_DEVICE_USAGE_CALL_ALL = 12 | All call devices.|

### OH_AudioDevice_BlockStatus

```c
enum OH_AudioDevice_BlockStatus
```

**Description**

Enumerates the blocking statuses of an audio device. By default, the audio device is considered unblocked.

**Since**: 13

| Enum Item| Description|
| -- | -- |
| AUDIO_DEVICE_UNBLOCKED = 0 | The audio device is not blocked.|
| AUDIO_DEVICE_BLOCKED = 1 | The audio device is blocked.|

## Function Description

### OH_AudioDeviceDescriptor_GetDeviceRole()

```c
OH_AudioCommon_Result OH_AudioDeviceDescriptor_GetDeviceRole(OH_AudioDeviceDescriptor *audioDeviceDescriptor,OH_AudioDevice_Role *deviceRole)
```

**Description**

Obtains the device role based on an audio device descriptor.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioDeviceDescriptor](capi-ohaudio-oh-audiodevicedescriptor.md) *audioDeviceDescriptor | Pointer to an audio device descriptor, which is obtained by calling [OH_AudioRoutingManager_GetDevices](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_getdevices) or [OH_AudioRoutingManager_OnDeviceChangedCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_ondevicechangedcallback).|
| [OH_AudioDevice_Role](#oh_audiodevice_role) *deviceRole | Pointer to the device role. It points to the variable used to receive the device role value. For details, see [OH_AudioDevice_Role](#oh_audiodevice_role). |

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | Operation result. **AUDIOCOMMON_RESULT_SUCCESS** is returned if the operation is successful; **AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM** is returned otherwise.|

### OH_AudioDeviceDescriptor_GetDeviceType()

```c
OH_AudioCommon_Result OH_AudioDeviceDescriptor_GetDeviceType(OH_AudioDeviceDescriptor *audioDeviceDescriptor,OH_AudioDevice_Type *deviceType)
```

**Description**

Obtains the device type based on an audio device descriptor.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioDeviceDescriptor](capi-ohaudio-oh-audiodevicedescriptor.md) *audioDeviceDescriptor | Pointer to an audio device descriptor, which is obtained by calling [OH_AudioRoutingManager_GetDevices](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_getdevices) or [OH_AudioRoutingManager_OnDeviceChangedCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_ondevicechangedcallback).|
| [OH_AudioDevice_Type](#oh_audiodevice_type) *deviceType | Pointer to the device type. It points to the variable used to receive the device type value. For details, see [OH_AudioDevice_Type](capi-native-audio-device-base-h.md#oh_audiodevice_type). |

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | Operation result. **AUDIOCOMMON_RESULT_SUCCESS** is returned if the operation is successful; **AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM** is returned otherwise.|

### OH_AudioDeviceDescriptor_GetDeviceId()

```c
OH_AudioCommon_Result OH_AudioDeviceDescriptor_GetDeviceId(OH_AudioDeviceDescriptor *audioDeviceDescriptor,uint32_t *id)
```

**Description**

Queries the device ID of the target audio device descriptor.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioDeviceDescriptor](capi-ohaudio-oh-audiodevicedescriptor.md) *audioDeviceDescriptor | Pointer to an audio device descriptor, which is obtained by calling [OH_AudioRoutingManager_GetDevices](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_getdevices) or [OH_AudioRoutingManager_OnDeviceChangedCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_ondevicechangedcallback).|
| uint32_t *id | Pointer to the variable used to receive the device ID value. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | Operation result. **AUDIOCOMMON_RESULT_SUCCESS** is returned if the operation is successful; **AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM** is returned otherwise.|

### OH_AudioDeviceDescriptor_GetDeviceName()

```c
OH_AudioCommon_Result OH_AudioDeviceDescriptor_GetDeviceName(OH_AudioDeviceDescriptor *audioDeviceDescriptor,char **name)
```

**Description**

Obtains the device name based on an audio device descriptor.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioDeviceDescriptor](capi-ohaudio-oh-audiodevicedescriptor.md) *audioDeviceDescriptor | Pointer to an audio device descriptor, which is obtained by calling [OH_AudioRoutingManager_GetDevices](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_getdevices) or [OH_AudioRoutingManager_OnDeviceChangedCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_ondevicechangedcallback).|
| char **name | Device name pointer, which points to a variable used to receive the device name value.<br>Do not release the audio device name pointer separately. Instead, call [OH_AudioRoutingManager_ReleaseDevices](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_releasedevices) to release all **DeviceDescriptor** arrays when they are no longer needed. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | Operation result. **AUDIOCOMMON_RESULT_SUCCESS** is returned if the operation is successful; **AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM** is returned otherwise.|

### OH_AudioDeviceDescriptor_GetDeviceAddress()

```c
OH_AudioCommon_Result OH_AudioDeviceDescriptor_GetDeviceAddress(OH_AudioDeviceDescriptor *audioDeviceDescriptor,char **address)
```

**Description**

Obtains the device address based on an audio device descriptor.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioDeviceDescriptor](capi-ohaudio-oh-audiodevicedescriptor.md) *audioDeviceDescriptor | Pointer to an audio device descriptor, which is obtained by calling [OH_AudioRoutingManager_GetDevices](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_getdevices) or [OH_AudioRoutingManager_OnDeviceChangedCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_ondevicechangedcallback).|
| char **address | Double pointer to the device address, which points to a variable used to receive the device address value.<br>Do not release the audio device address pointer separately. Instead, call [OH_AudioRoutingManager_ReleaseDevices](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_releasedevices) to release all **DeviceDescriptor** arrays when they are no longer needed. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | Operation result. **AUDIOCOMMON_RESULT_SUCCESS** is returned if the operation is successful; **AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM** is returned otherwise.|

### OH_AudioDeviceDescriptor_GetDeviceSampleRates()

```c
OH_AudioCommon_Result OH_AudioDeviceDescriptor_GetDeviceSampleRates(OH_AudioDeviceDescriptor *audioDeviceDescriptor,uint32_t **sampleRates, uint32_t *size)
```

**Description**

Obtains the sample rates based on an audio device descriptor.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioDeviceDescriptor](capi-ohaudio-oh-audiodevicedescriptor.md) *audioDeviceDescriptor | Pointer to an audio device descriptor, which is obtained by calling [OH_AudioRoutingManager_GetDevices](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_getdevices) or [OH_AudioRoutingManager_OnDeviceChangedCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_ondevicechangedcallback).|
| uint32_t **sampleRates | Double pointer to the array of sample rates.<br>Do not release the pointer to the sample rates separately. Instead, call [OH_AudioRoutingManager_ReleaseDevices](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_releasedevices) to release all the device descriptors when they are no longer needed.|
| uint32_t *size | Pointer to the size of the array.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | Operation result. **AUDIOCOMMON_RESULT_SUCCESS** is returned if the operation is successful; **AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM** is returned otherwise.|

### OH_AudioDeviceDescriptor_GetDeviceChannelCounts()

```c
OH_AudioCommon_Result OH_AudioDeviceDescriptor_GetDeviceChannelCounts(OH_AudioDeviceDescriptor *audioDeviceDescriptor,uint32_t **channelCounts, uint32_t *size)
```

**Description**

Obtains an array that holds the number of device channels based on an audio device descriptor.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioDeviceDescriptor](capi-ohaudio-oh-audiodevicedescriptor.md) *audioDeviceDescriptor | Pointer to an audio device descriptor, which is obtained by calling [OH_AudioRoutingManager_GetDevices](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_getdevices) or [OH_AudioRoutingManager_OnDeviceChangedCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_ondevicechangedcallback).|
| uint32_t **channelCounts | Double pointer to the array that holds the channel counts.<br>Do not release the pointer to the channel counts separately. Instead, call [OH_AudioRoutingManager_ReleaseDevices](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_releasedevices) to release all the device descriptors when they are no longer needed.|
| uint32_t *size |  Pointer to the size of the array.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | Operation result. **AUDIOCOMMON_RESULT_SUCCESS** is returned if the operation is successful; **AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM** is returned otherwise.|

### OH_AudioDeviceDescriptor_GetDeviceDisplayName()

```c
OH_AudioCommon_Result OH_AudioDeviceDescriptor_GetDeviceDisplayName(OH_AudioDeviceDescriptor *audioDeviceDescriptor,char **displayName)
```

**Description**

Obtains the device display name based on an audio device descriptor.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioDeviceDescriptor](capi-ohaudio-oh-audiodevicedescriptor.md) *audioDeviceDescriptor | Pointer to an audio device descriptor, which is obtained by calling [OH_AudioRoutingManager_GetDevices](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_getdevices) or [OH_AudioRoutingManager_OnDeviceChangedCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_ondevicechangedcallback).|
| char **displayName | Double pointer to the display name.<br>Do not release the pointer to the display name separately. Instead, call [OH_AudioRoutingManager_ReleaseDevices](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_releasedevices) to release all the device descriptors when they are no longer needed.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | Operation result. **AUDIOCOMMON_RESULT_SUCCESS** is returned if the operation is successful; **AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM** is returned otherwise.|

### OH_AudioDeviceDescriptor_GetDeviceEncodingTypes()

```c
OH_AudioCommon_Result OH_AudioDeviceDescriptor_GetDeviceEncodingTypes(OH_AudioDeviceDescriptor *audioDeviceDescriptor,OH_AudioStream_EncodingType **encodingTypes, uint32_t *size)
```

**Description**

Obtains the device encoding types based on an audio device descriptor.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_AudioDeviceDescriptor](capi-ohaudio-oh-audiodevicedescriptor.md) *audioDeviceDescriptor | Pointer to an audio device descriptor, which is obtained by calling [OH_AudioRoutingManager_GetDevices](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_getdevices) or [OH_AudioRoutingManager_OnDeviceChangedCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_ondevicechangedcallback).|
| [OH_AudioStream_EncodingType](capi-native-audiostream-base-h.md#oh_audiostream_encodingtype) **encodingTypes | Pointer to the audio device encoding type, which points to the variable used to receive the encoding type array. For details, see [OH_AudioStream_EncodingType](capi-native-audiostream-base-h.md#oh_audiostream_encodingtype).<br>Do not release the pointer to the audio device encoding type separately. Instead, call [OH_AudioRoutingManager_ReleaseDevices](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_releasedevices) to release all **DeviceDescriptor** arrays when they are no longer needed. |
| uint32_t *size |  Pointer to the size of the device encoding type.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | Operation result. **AUDIOCOMMON_RESULT_SUCCESS** is returned if the operation is successful; **AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM** is returned otherwise.|