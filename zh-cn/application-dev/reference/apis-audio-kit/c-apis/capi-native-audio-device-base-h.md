# native_audio_device_base.h

## 概述

本文件提供音频设备管理模块所依赖的基础枚举和结构体定义， 包括音频设备类型、音频设备描述结构体以及从设备描述结构体查询具体设备参数的接口。 <br>该模块为音频设备管理提供基础数据结构和查询能力， 支持获取音频设备的角色、类型、ID、名称、地址、采样率、声道数、编码类型等信息， 适用于需要查询和管理音频设备属性的场景。

**库：** libohaudio.so

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 12

**相关模块：** [OHAudio](capi-ohaudio.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_AudioDeviceDescriptorArray](capi-ohaudio-oh-audiodevicedescriptorarray.md) | - | 声明音频设备描述符数组的结构体，该结构体表示一组音频设备描述符，通过每个描述符可查询设备详细信息。 |
| [OH_AudioDeviceDescriptor](capi-ohaudio-oh-audiodevicedescriptor.md) | OH_AudioDeviceDescriptor | 声明音频设备描述结构体，该结构体用于查询音频设备详细信息。 |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_AudioDevice_ChangeType](#oh_audiodevice_changetype) | OH_AudioDevice_ChangeType | 定义音频设备更改类型。 |
| [OH_AudioDevice_Role](#oh_audiodevice_role) | OH_AudioDevice_Role | 定义音频设备角色。 |
| [OH_AudioDevice_Type](#oh_audiodevice_type) | OH_AudioDevice_Type | 定义音频设备类型。 |
| [OH_AudioDevice_Flag](#oh_audiodevice_flag) | OH_AudioDevice_Flag | 定义音频设备标志。 |
| [OH_AudioDevice_Usage](#oh_audiodevice_usage) | OH_AudioDevice_Usage | 定义可获取的设备种类。 |
| [OH_AudioDevice_BlockStatus](#oh_audiodevice_blockstatus) | OH_AudioDevice_BlockStatus | 定义音频设备的堵塞状态，主要用于表示内置麦克风的堵塞。默认情况下，音频设备是未堵塞状态。 |

### 函数

| 名称 | 描述 |
| -- | -- |
| [OH_AudioCommon_Result OH_AudioDeviceDescriptor_GetDeviceRole(OH_AudioDeviceDescriptor *audioDeviceDescriptor, OH_AudioDevice_Role *deviceRole)](#oh_audiodevicedescriptor_getdevicerole) | 查询目标音频设备描述符的设备角色。 |
| [OH_AudioCommon_Result OH_AudioDeviceDescriptor_GetDeviceType(OH_AudioDeviceDescriptor *audioDeviceDescriptor, OH_AudioDevice_Type *deviceType)](#oh_audiodevicedescriptor_getdevicetype) | 查询目标音频设备描述符的设备类型。 |
| [OH_AudioCommon_Result OH_AudioDeviceDescriptor_GetDeviceId(OH_AudioDeviceDescriptor *audioDeviceDescriptor, uint32_t *id)](#oh_audiodevicedescriptor_getdeviceid) | 查询目标音频设备描述符的设备ID。 |
| [OH_AudioCommon_Result OH_AudioDeviceDescriptor_GetDeviceName(OH_AudioDeviceDescriptor *audioDeviceDescriptor, char **name)](#oh_audiodevicedescriptor_getdevicename) | 查询目标音频设备描述符的设备名称。 |
| [OH_AudioCommon_Result OH_AudioDeviceDescriptor_GetDeviceAddress(OH_AudioDeviceDescriptor *audioDeviceDescriptor, char **address)](#oh_audiodevicedescriptor_getdeviceaddress) | 查询目标音频设备描述符的设备地址。 |
| [OH_AudioCommon_Result OH_AudioDeviceDescriptor_GetDeviceSampleRates(OH_AudioDeviceDescriptor *audioDeviceDescriptor, uint32_t **sampleRates, uint32_t *size)](#oh_audiodevicedescriptor_getdevicesamplerates) | 查询目标音频设备描述符的支持采样率数组。 |
| [OH_AudioCommon_Result OH_AudioDeviceDescriptor_GetDeviceChannelCounts(OH_AudioDeviceDescriptor *audioDeviceDescriptor, uint32_t **channelCounts, uint32_t *size)](#oh_audiodevicedescriptor_getdevicechannelcounts) | 查询目标音频设备描述符的支持声道数数组。 |
| [OH_AudioCommon_Result OH_AudioDeviceDescriptor_GetDeviceDisplayName(OH_AudioDeviceDescriptor *audioDeviceDescriptor, char **displayName)](#oh_audiodevicedescriptor_getdevicedisplayname) | 查询目标音频设备描述符的显示名称。 <br>此名称为目标音频设备所属产品设备的名称，如扬声器所属手机的设备名称。主要用于分布式音频场景下设备选择列表的显示。 |
| [OH_AudioCommon_Result OH_AudioDeviceDescriptor_GetDeviceEncodingTypes(OH_AudioDeviceDescriptor *audioDeviceDescriptor, OH_AudioStream_EncodingType **encodingTypes, uint32_t *size)](#oh_audiodevicedescriptor_getdeviceencodingtypes) | 查询目标音频设备描述符的支持编码类型数组。 |

## 枚举类型说明

### OH_AudioDevice_ChangeType

```c
enum OH_AudioDevice_ChangeType
```

**描述：**

定义音频设备更改类型。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| AUDIO_DEVICE_CHANGE_TYPE_CONNECT = 0 | 设备连接。 |
| AUDIO_DEVICE_CHANGE_TYPE_DISCONNECT = 1 | 设备断开。 |

### OH_AudioDevice_Role

```c
enum OH_AudioDevice_Role
```

**描述：**

定义音频设备角色。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| AUDIO_DEVICE_ROLE_INPUT = 1 | 输入设备。 |
| AUDIO_DEVICE_ROLE_OUTPUT = 2 | 输出设备。 |

### OH_AudioDevice_Type

```c
enum OH_AudioDevice_Type
```

**描述：**

定义音频设备类型。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| AUDIO_DEVICE_TYPE_INVALID = 0 | 无效设备。 |
| AUDIO_DEVICE_TYPE_EARPIECE = 1 | 内置听筒。 |
| AUDIO_DEVICE_TYPE_SPEAKER = 2 | 内置扬声器。 |
| AUDIO_DEVICE_TYPE_WIRED_HEADSET = 3 | 带话筒的有线耳机。 |
| AUDIO_DEVICE_TYPE_WIRED_HEADPHONES = 4 | 无话筒的有线耳机。 |
| AUDIO_DEVICE_TYPE_BLUETOOTH_SCO = 7 | 使用面向同步连接链路（SCO）的蓝牙设备。 |
| AUDIO_DEVICE_TYPE_BLUETOOTH_A2DP = 8 | 使用高级音频分布模式（A2DP）的蓝牙设备。 |
| AUDIO_DEVICE_TYPE_MIC = 15 | 内置麦克风。 |
| AUDIO_DEVICE_TYPE_USB_HEADSET = 22 | USB音频耳机。 |
| AUDIO_DEVICE_TYPE_DISPLAY_PORT = 23 | 显示端口（DisplayPort）设备。 |
| AUDIO_DEVICE_TYPE_REMOTE_CAST = 24 | 音频被系统应用投送到其他远程的设备。 |
| AUDIO_DEVICE_TYPE_USB_DEVICE = 25 | USB设备（不包含USB耳机）。<br>**起始版本：** 18 |
| AUDIO_DEVICE_TYPE_ACCESSORY = 26 | 附件设备，如遥控器上的麦克风。<br>**起始版本：** 19 |
| AUDIO_DEVICE_TYPE_HDMI = 27 | HDMI设备（例如HDMI、ARC、eARC等）。<br>**起始版本：** 19 |
| AUDIO_DEVICE_TYPE_LINE_DIGITAL = 28 | 有线数字设备（例如S/PDIF等）。<br>**起始版本：** 19 |
| AUDIO_DEVICE_TYPE_HEARING_AID = 30 | 助听器设备。<br>**起始版本：** 20 |
| AUDIO_DEVICE_TYPE_NEARLINK = 31 | 星闪设备。<br>**起始版本：** 20 |
| AUDIO_DEVICE_TYPE_DEFAULT = 1000 | 默认设备类型。 |

### OH_AudioDevice_Flag

```c
enum OH_AudioDevice_Flag
```

**描述：**

定义音频设备标志。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| AUDIO_DEVICE_FLAG_NONE = 0 | 无设备。 |
| AUDIO_DEVICE_FLAG_OUTPUT = 1 | 输出设备。 |
| AUDIO_DEVICE_FLAG_INPUT = 2 | 输入设备。 |
| AUDIO_DEVICE_FLAG_ALL = 3 | 所有设备。 |

### OH_AudioDevice_Usage

```c
enum OH_AudioDevice_Usage
```

**描述：**

定义可获取的设备种类。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| AUDIO_DEVICE_USAGE_MEDIA_OUTPUT = 1 | 媒体输出设备。<br>**起始版本：** 12 |
| AUDIO_DEVICE_USAGE_MEDIA_INPUT = 2 | 媒体输入设备。<br>**起始版本：** 12 |
| AUDIO_DEVICE_USAGE_MEDIA_ALL = 3 | 所有媒体设备。<br>**起始版本：** 12 |
| AUDIO_DEVICE_USAGE_CALL_OUTPUT = 4 | 通话输出设备。<br>**起始版本：** 12 |
| AUDIO_DEVICE_USAGE_CALL_INPUT = 8 | 通话输入设备。<br>**起始版本：** 12 |
| AUDIO_DEVICE_USAGE_CALL_ALL = 12 | 所有通话设备。<br>**起始版本：** 12 |

### OH_AudioDevice_BlockStatus

```c
enum OH_AudioDevice_BlockStatus
```

**描述：**

定义音频设备的堵塞状态，主要用于表示内置麦克风的堵塞。默认情况下，音频设备是未堵塞状态。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 13

| 枚举项 | 描述 |
| -- | -- |
| AUDIO_DEVICE_UNBLOCKED = 0 | 音频设备未被堵塞。<br>**起始版本：** 13 |
| AUDIO_DEVICE_BLOCKED = 1 | 音频设备被堵塞。<br>**起始版本：** 13 |


## 函数说明

### OH_AudioDeviceDescriptor_GetDeviceRole()

```c
OH_AudioCommon_Result OH_AudioDeviceDescriptor_GetDeviceRole(OH_AudioDeviceDescriptor *audioDeviceDescriptor, OH_AudioDevice_Role *deviceRole)
```

**描述：**

查询目标音频设备描述符的设备角色。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioDeviceDescriptor](capi-ohaudio-oh-audiodevicedescriptor.md) *audioDeviceDescriptor | [in] 音频设备描述符。可通过 [OH_AudioRoutingManager](capi-ohaudio-oh-audioroutingmanager.md) 的设备查询或监听接口获取。 |
| [OH_AudioDevice_Role](capi-native-audio-device-base-h.md#oh_audiodevice_role) *deviceRole | [out] 获取设备角色的指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul> <li>AUDIOCOMMON_RESULT_SUCCESS：函数执行成功。</li> <li>AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM：参数 audioDeviceDescriptor 或 deviceRole 为空指针。</li> </ul> |

### OH_AudioDeviceDescriptor_GetDeviceType()

```c
OH_AudioCommon_Result OH_AudioDeviceDescriptor_GetDeviceType(OH_AudioDeviceDescriptor *audioDeviceDescriptor, OH_AudioDevice_Type *deviceType)
```

**描述：**

查询目标音频设备描述符的设备类型。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioDeviceDescriptor](capi-ohaudio-oh-audiodevicedescriptor.md) *audioDeviceDescriptor | [in] 音频设备描述符。可通过 [OH_AudioRoutingManager](capi-ohaudio-oh-audioroutingmanager.md) 的设备查询或监听接口获取。 |
| [OH_AudioDevice_Type](capi-native-audio-device-base-h.md#oh_audiodevice_type) *deviceType | [out] 获取设备类型的指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul> <li>AUDIOCOMMON_RESULT_SUCCESS：函数执行成功。</li> <li>AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM：参数 audioDeviceDescriptor 或 deviceType 为空指针。</li> </ul> |

### OH_AudioDeviceDescriptor_GetDeviceId()

```c
OH_AudioCommon_Result OH_AudioDeviceDescriptor_GetDeviceId(OH_AudioDeviceDescriptor *audioDeviceDescriptor, uint32_t *id)
```

**描述：**

查询目标音频设备描述符的设备ID。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioDeviceDescriptor](capi-ohaudio-oh-audiodevicedescriptor.md) *audioDeviceDescriptor | [in] 音频设备描述符。可通过 [OH_AudioRoutingManager](capi-ohaudio-oh-audioroutingmanager.md) 的设备查询或监听接口获取。 |
| uint32_t *id | [out] 获取设备ID的指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul> <li>AUDIOCOMMON_RESULT_SUCCESS：函数执行成功。</li> <li>AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM：参数 audioDeviceDescriptor 或 id 为空指针。</li> </ul> |

### OH_AudioDeviceDescriptor_GetDeviceName()

```c
OH_AudioCommon_Result OH_AudioDeviceDescriptor_GetDeviceName(OH_AudioDeviceDescriptor *audioDeviceDescriptor, char **name)
```

**描述：**

查询目标音频设备描述符的设备名称。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioDeviceDescriptor](capi-ohaudio-oh-audiodevicedescriptor.md) *audioDeviceDescriptor | [in] 音频设备描述符。可通过 [OH_AudioRoutingManager](capi-ohaudio-oh-audioroutingmanager.md) 的设备查询或监听接口获取。 |
| char **name | [out] 获取设备名称字符串的指针。 <br>不要单独释放此指针指向的内存，而是调用 OH_AudioRoutingManager_ReleaseDevices 在不使用时释放所有内存。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul> <li>AUDIOCOMMON_RESULT_SUCCESS：函数执行成功。</li> <li>AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM：参数 audioDeviceDescriptor 或 name 为空指针。</li> </ul> |

### OH_AudioDeviceDescriptor_GetDeviceAddress()

```c
OH_AudioCommon_Result OH_AudioDeviceDescriptor_GetDeviceAddress(OH_AudioDeviceDescriptor *audioDeviceDescriptor, char **address)
```

**描述：**

查询目标音频设备描述符的设备地址。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioDeviceDescriptor](capi-ohaudio-oh-audiodevicedescriptor.md) *audioDeviceDescriptor | [in] 音频设备描述符。可通过 [OH_AudioRoutingManager](capi-ohaudio-oh-audioroutingmanager.md) 的设备查询或监听接口获取。 |
| char **address | [out] 获取设备地址字符串的指针。 <br>不要单独释放此指针指向的内存，而是调用OH_AudioRoutingManager_ReleaseDevices，在不使用时释放所有内存。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul> <li>AUDIOCOMMON_RESULT_SUCCESS：函数执行成功。</li> <li>AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM：参数 audioDeviceDescriptor 或 address 为空指针。</li> </ul> |

### OH_AudioDeviceDescriptor_GetDeviceSampleRates()

```c
OH_AudioCommon_Result OH_AudioDeviceDescriptor_GetDeviceSampleRates(OH_AudioDeviceDescriptor *audioDeviceDescriptor, uint32_t **sampleRates, uint32_t *size)
```

**描述：**

查询目标音频设备描述符的支持采样率数组。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioDeviceDescriptor](capi-ohaudio-oh-audiodevicedescriptor.md) *audioDeviceDescriptor | [in] 音频设备描述符。可通过 [OH_AudioRoutingManager](capi-ohaudio-oh-audioroutingmanager.md) 的设备查询或监听接口获取。 |
| uint32_t **sampleRates | [out] 获取采样率数组的指针，单位为Hz。 <br>不要单独释放此指针指向的内存，而是调用OH_AudioRoutingManager_ReleaseDevices，在不使用时释放所有内存。 |
| uint32_t *size | [out] 获取采样率数组长度的指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul> <li>AUDIOCOMMON_RESULT_SUCCESS：函数执行成功。</li> <li>AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM：参数 audioDeviceDescriptor、sampleRates 或 size 为空指针。</li> </ul> |

### OH_AudioDeviceDescriptor_GetDeviceChannelCounts()

```c
OH_AudioCommon_Result OH_AudioDeviceDescriptor_GetDeviceChannelCounts(OH_AudioDeviceDescriptor *audioDeviceDescriptor, uint32_t **channelCounts, uint32_t *size)
```

**描述：**

查询目标音频设备描述符的支持声道数数组。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioDeviceDescriptor](capi-ohaudio-oh-audiodevicedescriptor.md) *audioDeviceDescriptor | [in] 音频设备描述符。可通过 [OH_AudioRoutingManager](capi-ohaudio-oh-audioroutingmanager.md) 的设备查询或监听接口获取。 |
| uint32_t **channelCounts | [out] 获取声道数数组的指针。 <br>不要单独释放此指针指向的内存，而是调用OH_AudioRoutingManager_ReleaseDevices 在不使用时释放所有内存。 |
| uint32_t *size | [out] 获取声道数数组长度的指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul> <li>AUDIOCOMMON_RESULT_SUCCESS：函数执行成功。</li> <li>AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM：参数 audioDeviceDescriptor、channelCounts 或 size 为空指针。</li> </ul> |

### OH_AudioDeviceDescriptor_GetDeviceDisplayName()

```c
OH_AudioCommon_Result OH_AudioDeviceDescriptor_GetDeviceDisplayName(OH_AudioDeviceDescriptor *audioDeviceDescriptor, char **displayName)
```

**描述：**

查询目标音频设备描述符的显示名称。 <br>此名称为目标音频设备所属产品设备的名称，如扬声器所属手机的设备名称。主要用于分布式音频场景下设备选择列表的显示。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioDeviceDescriptor](capi-ohaudio-oh-audiodevicedescriptor.md) *audioDeviceDescriptor | [in] 音频设备描述符。可通过 [OH_AudioRoutingManager](capi-ohaudio-oh-audioroutingmanager.md) 的设备查询或监听接口获取。 |
| char **displayName | [out] 获取显示名称值字符串的指针。 <br>不要单独释放此指针指向的内存，而是调用OH_AudioRoutingManager_ReleaseDevices，在不使用时释放所有内存。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul> <li>AUDIOCOMMON_RESULT_SUCCESS：函数执行成功。</li> <li>AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM：参数 audioDeviceDescriptor 或 displayName 为空指针。</li> </ul> |

### OH_AudioDeviceDescriptor_GetDeviceEncodingTypes()

```c
OH_AudioCommon_Result OH_AudioDeviceDescriptor_GetDeviceEncodingTypes(OH_AudioDeviceDescriptor *audioDeviceDescriptor, OH_AudioStream_EncodingType **encodingTypes, uint32_t *size)
```

**描述：**

查询目标音频设备描述符的支持编码类型数组。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioDeviceDescriptor](capi-ohaudio-oh-audiodevicedescriptor.md) *audioDeviceDescriptor | [in] 音频设备描述符。可通过 [OH_AudioRoutingManager](capi-ohaudio-oh-audioroutingmanager.md) 的设备查询或监听接口获取。 |
| [OH_AudioStream_EncodingType](capi-native-audiostream-base-h.md#oh_audiostream_encodingtype) **encodingTypes | [out] 获取音频编码类型数组的指针。 <br>不要单独释放此指针指向的内存，而是调用OH_AudioRoutingManager_ReleaseDevices，在不使用时释放所有内存。 |
| uint32_t *size | [out] 获取编码类型大小值的指针变量。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul> <li>AUDIOCOMMON_RESULT_SUCCESS：函数执行成功。</li> <li>AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM：参数 audioDeviceDescriptor、encodingTypes 或 size 为空指针。</li> </ul> |


