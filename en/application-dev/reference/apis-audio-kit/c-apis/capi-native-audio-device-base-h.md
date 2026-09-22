# native_audio_device_base.h

## Overview

Declare audio device related interfaces for audio device descriptor.<br> Defines the types of audio device parameters and the interfaces for obtaining the parameters of each device.

**Library**: libohaudio.so

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 10

**Related module**: [OHAudio](capi-ohaudio.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AudioDeviceDescriptorArray](capi-ohaudio-oh-audiodevicedescriptorarray.md) | OH_AudioDeviceDescriptorArray | Declaring the audio device descriptor array. |
| [OH_AudioDeviceDescriptor](capi-ohaudio-oh-audiodevicedescriptor.md) | OH_AudioDeviceDescriptor | Declaring the audio device descriptor. The instance is used to get more audio device detail attributes. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AudioDevice_ChangeType](#oh_audiodevice_changetype) | OH_AudioDevice_ChangeType | Defines the audio device change type. |
| [OH_AudioDevice_Role](#oh_audiodevice_role) | OH_AudioDevice_Role | Defines the audio device role. |
| [OH_AudioDevice_Type](#oh_audiodevice_type) | OH_AudioDevice_Type | Defines the audio device type. |
| [OH_AudioDevice_Flag](#oh_audiodevice_flag) | OH_AudioDevice_Flag | Defines the audio device flag. |
| [OH_AudioDevice_Usage](#oh_audiodevice_usage) | OH_AudioDevice_Usage | Defines the audio device usage. |
| [OH_AudioDevice_BlockStatus](#oh_audiodevice_blockstatus) | OH_AudioDevice_BlockStatus | Declaring the audio device blocked status. By default, the audio device is considered as unblocked. |

### Function

| Name | Description |
| -- | -- |
| [OH_AudioCommon_Result OH_AudioDeviceDescriptor_GetDeviceRole(OH_AudioDeviceDescriptor *audioDeviceDescriptor, OH_AudioDevice_Role *deviceRole)](#oh_audiodevicedescriptor_getdevicerole) | Query the device role of the target audio device descriptor. |
| [OH_AudioCommon_Result OH_AudioDeviceDescriptor_GetDeviceType(OH_AudioDeviceDescriptor *audioDeviceDescriptor, OH_AudioDevice_Type *deviceType)](#oh_audiodevicedescriptor_getdevicetype) | Query the device type of the target audio device descriptor. |
| [OH_AudioCommon_Result OH_AudioDeviceDescriptor_GetDeviceId(OH_AudioDeviceDescriptor *audioDeviceDescriptor, uint32_t *id)](#oh_audiodevicedescriptor_getdeviceid) | Query the device id of the target audio device descriptor. |
| [OH_AudioCommon_Result OH_AudioDeviceDescriptor_GetDeviceName(OH_AudioDeviceDescriptor *audioDeviceDescriptor, char **name)](#oh_audiodevicedescriptor_getdevicename) | Query the device name of the target audio device descriptor. |
| [OH_AudioCommon_Result OH_AudioDeviceDescriptor_GetDeviceAddress(OH_AudioDeviceDescriptor *audioDeviceDescriptor, char **address)](#oh_audiodevicedescriptor_getdeviceaddress) | Query the device address of the target audio device descriptor. |
| [OH_AudioCommon_Result OH_AudioDeviceDescriptor_GetDeviceSampleRates(OH_AudioDeviceDescriptor *audioDeviceDescriptor, uint32_t **sampleRates, uint32_t *size)](#oh_audiodevicedescriptor_getdevicesamplerates) | Query the sample rate array of the target audio device descriptor. |
| [OH_AudioCommon_Result OH_AudioDeviceDescriptor_GetDeviceChannelCounts(OH_AudioDeviceDescriptor *audioDeviceDescriptor, uint32_t **channelCounts, uint32_t *size)](#oh_audiodevicedescriptor_getdevicechannelcounts) | Query the device channel count array of the target audio device descriptor. |
| [OH_AudioCommon_Result OH_AudioDeviceDescriptor_GetDeviceDisplayName(OH_AudioDeviceDescriptor *audioDeviceDescriptor, char **displayName)](#oh_audiodevicedescriptor_getdevicedisplayname) | Query the display name of the target audio device descriptor. |
| [OH_AudioCommon_Result OH_AudioDeviceDescriptor_GetDeviceEncodingTypes(OH_AudioDeviceDescriptor *audioDeviceDescriptor, OH_AudioStream_EncodingType **encodingTypes, uint32_t *size)](#oh_audiodevicedescriptor_getdeviceencodingtypes) | Query the encoding type array of the target audio device descriptor. |

## Enum type description

### OH_AudioDevice_ChangeType

```c
enum OH_AudioDevice_ChangeType
```

**Description**

Defines the audio device change type.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 12

| Enum item | Description |
| -- | -- |
| AUDIO_DEVICE_CHANGE_TYPE_CONNECT = 0 | Device connection. |
| AUDIO_DEVICE_CHANGE_TYPE_DISCONNECT = 1 | Device disconnection. |

### OH_AudioDevice_Role

```c
enum OH_AudioDevice_Role
```

**Description**

Defines the audio device role.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 12

| Enum item | Description |
| -- | -- |
| AUDIO_DEVICE_ROLE_INPUT = 1 | Input role. |
| AUDIO_DEVICE_ROLE_OUTPUT = 2 | Output role. |

### OH_AudioDevice_Type

```c
enum OH_AudioDevice_Type
```

**Description**

Defines the audio device type.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 12

| Enum item | Description |
| -- | -- |
| AUDIO_DEVICE_TYPE_INVALID = 0 | Invalid device. |
| AUDIO_DEVICE_TYPE_EARPIECE = 1 | Built-in earpiece. |
| AUDIO_DEVICE_TYPE_SPEAKER = 2 | Built-in speaker. |
| AUDIO_DEVICE_TYPE_WIRED_HEADSET = 3 | Wired headset, which is a combination of a pair of earpieces and a microphone. |
| AUDIO_DEVICE_TYPE_WIRED_HEADPHONES = 4 | A pair of wired headphones. |
| AUDIO_DEVICE_TYPE_BLUETOOTH_SCO = 7 | Bluetooth device using the synchronous connection oriented link (SCO). |
| AUDIO_DEVICE_TYPE_BLUETOOTH_A2DP = 8 | Bluetooth device using advanced audio distibution profile (A2DP). |
| AUDIO_DEVICE_TYPE_MIC = 15 | Built-in microphone. |
| AUDIO_DEVICE_TYPE_USB_HEADSET = 22 | USB audio headset. |
| AUDIO_DEVICE_TYPE_DISPLAY_PORT = 23 | Display port device. |
| AUDIO_DEVICE_TYPE_REMOTE_CAST = 24 | Device type for rerouting audio to other remote devices by system application. |
| AUDIO_DEVICE_TYPE_USB_DEVICE = 25 | Usb audio device.<br>**Since**: 18 |
| AUDIO_DEVICE_TYPE_ACCESSORY = 26 | Accessory device, such as the microphone on a remote control.<br>**Since**: 19 |
| AUDIO_DEVICE_TYPE_HDMI = 27 | HDMI device, such as a device connected through an HDMI, ARC, or eARC interface.<br>**Since**: 19 |
| AUDIO_DEVICE_TYPE_LINE_DIGITAL = 28 | Line-connected, digital audio output device, such as an S/PDIF device.<br>**Since**: 19 |
| AUDIO_DEVICE_TYPE_HEARING_AID = 30 | Hearing aid device.<br>**Since**: 20 |
| AUDIO_DEVICE_TYPE_NEARLINK = 31 | Nearlink device.<br>**Since**: 20 |
| AUDIO_DEVICE_TYPE_DEFAULT = 1000 | Default device type. |

### OH_AudioDevice_Flag

```c
enum OH_AudioDevice_Flag
```

**Description**

Defines the audio device flag.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 12

| Enum item | Description |
| -- | -- |
| AUDIO_DEVICE_FLAG_NONE = 0 | None device. |
| AUDIO_DEVICE_FLAG_OUTPUT = 1 | Output device. |
| AUDIO_DEVICE_FLAG_INPUT = 2 | Input device. |
| AUDIO_DEVICE_FLAG_ALL = 3 | All device. |

### OH_AudioDevice_Usage

```c
enum OH_AudioDevice_Usage
```

**Description**

Defines the audio device usage.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 12

| Enum item | Description |
| -- | -- |
| AUDIO_DEVICE_USAGE_MEDIA_OUTPUT = 1 | Device used for media output.<br>**Since**: 12 |
| AUDIO_DEVICE_USAGE_MEDIA_INPUT = 2 | Device used for media input.<br>**Since**: 12 |
| AUDIO_DEVICE_USAGE_MEDIA_ALL = 3 | Device used for media, including input and output.<br>**Since**: 12 |
| AUDIO_DEVICE_USAGE_CALL_OUTPUT = 4 | Device used for call output.<br>**Since**: 12 |
| AUDIO_DEVICE_USAGE_CALL_INPUT = 8 | Device used for call input.<br>**Since**: 12 |
| AUDIO_DEVICE_USAGE_CALL_ALL = 12 | Device used for call, including input and output.<br>**Since**: 12 |

### OH_AudioDevice_BlockStatus

```c
enum OH_AudioDevice_BlockStatus
```

**Description**

Declaring the audio device blocked status. By default, the audio device is considered as unblocked.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 13

| Enum item | Description |
| -- | -- |
| AUDIO_DEVICE_UNBLOCKED = 0 | Audio device is unblocked.<br>**Since**: 13 |
| AUDIO_DEVICE_BLOCKED = 1 | Audio Device is blocked.<br>**Since**: 13 |


## Function description

### OH_AudioDeviceDescriptor_GetDeviceRole()

```c
OH_AudioCommon_Result OH_AudioDeviceDescriptor_GetDeviceRole(OH_AudioDeviceDescriptor *audioDeviceDescriptor, OH_AudioDevice_Role *deviceRole)
```

**Description**

Query the device role of the target audio device descriptor.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioDeviceDescriptor](capi-ohaudio-oh-audiodevicedescriptor.md) *audioDeviceDescriptor | reference returned by {@link OH_AudioRoutingManager_GetDevices} or<br>{@link OH_AudioRouterManager_OnDeviceChangedCallback}. |
| [OH_AudioDevice_Role](capi-native-audio-device-base-h.md#oh_audiodevice_role) *deviceRole | the pointer [OH_AudioDevice_Role](capi-native-audio-device-base-h.md#oh_audiodevice_role) variable that will be set the device role value. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | [AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) or [AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result). |

### OH_AudioDeviceDescriptor_GetDeviceType()

```c
OH_AudioCommon_Result OH_AudioDeviceDescriptor_GetDeviceType(OH_AudioDeviceDescriptor *audioDeviceDescriptor, OH_AudioDevice_Type *deviceType)
```

**Description**

Query the device type of the target audio device descriptor.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioDeviceDescriptor](capi-ohaudio-oh-audiodevicedescriptor.md) *audioDeviceDescriptor | reference returned by {@link OH_AudioRoutingManager_GetDevices} or<br>{@link OH_AudioRouterManager_OnDeviceChangedCallback}. |
| [OH_AudioDevice_Type](capi-native-audio-device-base-h.md#oh_audiodevice_type) *deviceType | the pointer [OH_AudioDevice_Type](capi-native-audio-device-base-h.md#oh_audiodevice_type) pointer variable that will be set the device type value. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | [AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) or [AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result). |

### OH_AudioDeviceDescriptor_GetDeviceId()

```c
OH_AudioCommon_Result OH_AudioDeviceDescriptor_GetDeviceId(OH_AudioDeviceDescriptor *audioDeviceDescriptor, uint32_t *id)
```

**Description**

Query the device id of the target audio device descriptor.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioDeviceDescriptor](capi-ohaudio-oh-audiodevicedescriptor.md) *audioDeviceDescriptor | reference returned by {@link OH_AudioRoutingManager_GetDevices} or<br>{@link OH_AudioRouterManager_OnDeviceChangedCallback}. |
| uint32_t *id | pointer variable that will be set the device id value. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | [AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) or [AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result). |

### OH_AudioDeviceDescriptor_GetDeviceName()

```c
OH_AudioCommon_Result OH_AudioDeviceDescriptor_GetDeviceName(OH_AudioDeviceDescriptor *audioDeviceDescriptor, char **name)
```

**Description**

Query the device name of the target audio device descriptor.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioDeviceDescriptor](capi-ohaudio-oh-audiodevicedescriptor.md) *audioDeviceDescriptor | reference returned by {@link OH_AudioRoutingManager_GetDevices} or<br>{@link OH_AudioRouterManager_OnDeviceChangedCallback}. |
| char **name | pointer variable that will be set the device name value. Do not release the name pointer separately instead call {@link OH_AudioRoutingManager_ReleaseDevices} to release the DeviceDescriptor array when it is no use anymore. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | [AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) or [AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result). |

### OH_AudioDeviceDescriptor_GetDeviceAddress()

```c
OH_AudioCommon_Result OH_AudioDeviceDescriptor_GetDeviceAddress(OH_AudioDeviceDescriptor *audioDeviceDescriptor, char **address)
```

**Description**

Query the device address of the target audio device descriptor.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioDeviceDescriptor](capi-ohaudio-oh-audiodevicedescriptor.md) *audioDeviceDescriptor | reference returned by {@link OH_AudioRoutingManager_GetDevices} or<br>{@link OH_AudioRouterManager_OnDeviceChangedCallback}. |
| char **address | pointer variable that will be set the device address value. Do not release the address pointer separately instead call {@link OH_AudioRoutingManager_ReleaseDevices} to release the DeviceDescriptor array when it is no use anymore. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | [AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) or [AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result). |

### OH_AudioDeviceDescriptor_GetDeviceSampleRates()

```c
OH_AudioCommon_Result OH_AudioDeviceDescriptor_GetDeviceSampleRates(OH_AudioDeviceDescriptor *audioDeviceDescriptor, uint32_t **sampleRates, uint32_t *size)
```

**Description**

Query the sample rate array of the target audio device descriptor.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioDeviceDescriptor](capi-ohaudio-oh-audiodevicedescriptor.md) *audioDeviceDescriptor | reference returned by {@link OH_AudioRoutingManager_GetDevices} or<br>{@link OH_AudioRouterManager_OnDeviceChangedCallback}. |
| uint32_t **sampleRates | array pointer variable that will be set the sample rate array value. Do not release the sampleRates pointer separately instead call {@link OH_AudioRoutingManager_ReleaseDevices} to release the DeviceDescriptor array when it is no use anymore. |
| uint32_t *size | pointer variable that will be set the sample rate size value. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | [AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) or [AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result). |

### OH_AudioDeviceDescriptor_GetDeviceChannelCounts()

```c
OH_AudioCommon_Result OH_AudioDeviceDescriptor_GetDeviceChannelCounts(OH_AudioDeviceDescriptor *audioDeviceDescriptor, uint32_t **channelCounts, uint32_t *size)
```

**Description**

Query the device channel count array of the target audio device descriptor.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioDeviceDescriptor](capi-ohaudio-oh-audiodevicedescriptor.md) *audioDeviceDescriptor | reference returned by {@link OH_AudioRoutingManager_GetDevices} or<br>{@link OH_AudioRouterManager_OnDeviceChangedCallback}. |
| uint32_t **channelCounts | array pointer variable that will be set the channel count array value. Do not release the channelCounts pointer separately instead call {@link OH_AudioRoutingManager_ReleaseDevices} to release the DeviceDescriptor array when it is no use anymore. |
| uint32_t *size | pointer variable that will be set the channel count size value. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | [AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) or [AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result). |

### OH_AudioDeviceDescriptor_GetDeviceDisplayName()

```c
OH_AudioCommon_Result OH_AudioDeviceDescriptor_GetDeviceDisplayName(OH_AudioDeviceDescriptor *audioDeviceDescriptor, char **displayName)
```

**Description**

Query the display name of the target audio device descriptor.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioDeviceDescriptor](capi-ohaudio-oh-audiodevicedescriptor.md) *audioDeviceDescriptor | reference returned by {@link OH_AudioRoutingManager_GetDevices} or<br>{@link OH_AudioRouterManager_OnDeviceChangedCallback}. |
| char **displayName | pointer variable that will be set the display name value. Do not release the displayName pointer separately instead call {@link OH_AudioRoutingManager_ReleaseDevices} to release the DeviceDescriptor array when it is no use anymore. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | [AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) or [AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result). |

### OH_AudioDeviceDescriptor_GetDeviceEncodingTypes()

```c
OH_AudioCommon_Result OH_AudioDeviceDescriptor_GetDeviceEncodingTypes(OH_AudioDeviceDescriptor *audioDeviceDescriptor, OH_AudioStream_EncodingType **encodingTypes, uint32_t *size)
```

**Description**

Query the encoding type array of the target audio device descriptor.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioDeviceDescriptor](capi-ohaudio-oh-audiodevicedescriptor.md) *audioDeviceDescriptor | reference returned by {@link OH_AudioRoutingManager_GetDevices} or<br>{@link OH_AudioRouterManager_OnDeviceChangedCallback}. |
| OH_AudioStream_EncodingType **encodingTypes | the [OH_AudioStream_EncodingType](capi-native-audiostream-base-h.md#oh_audiostream_encodingtype) Do not release the encodingTypes pointer separately instead call {@link OH_AudioRoutingManager_ReleaseDevices} to release the DeviceDescriptor array when it is no use anymore. |
| uint32_t *size | pointer variable that will be set the encoding type size value. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AudioCommon_Result | [AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) or [AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result). |


