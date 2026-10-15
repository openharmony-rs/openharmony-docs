# native_audio_routing_manager.h

## 概述

本文件提供音频路由管理功能的接口。 <br>音频系统会为每个音频流选择默认的输入输出设备。对于音频播放流，系统会根据播放流的[OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage)， 在可用的输出设备中选择； 对于音频录制流，系统会根据录制流的 [OH_AudioStream_SourceType](capi-native-audiostream-base-h.md#oh_audiostream_sourcetype)，在可用的输入设备中选择。 <br>本文件提供的接口，支持开发者查询在线设备，监听设备在线状态变化，查询首选输入或输出设备，监听首选设备变化， 查询麦克风堵塞状态等。 当前并不提供主动选择设备的能力。

**库：** libohaudio.so

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 12

**相关模块：** [OHAudio](capi-ohaudio.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_AudioRoutingManager](capi-ohaudio-oh-audioroutingmanager.md) | OH_AudioRoutingManager | 声明音频路由管理结构体，该结构体用于调用音频设备和路由信息查询功能接口。 |

### 函数

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [typedef int32_t (\*OH_AudioRoutingManager_OnDeviceChangedCallback)(OH_AudioDevice_ChangeType type, OH_AudioDeviceDescriptorArray *audioDeviceDescriptorArray)](#oh_audioroutingmanager_ondevicechangedcallback) | OH_AudioRoutingManager_OnDeviceChangedCallback | 音频设备在线状态变化回调函数的原型定义，用于[OH_AudioRoutingManager_RegisterDeviceChangeCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_registerdevicechangecallback)和 [OH_AudioRoutingManager_UnregisterDeviceChangeCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_unregisterdevicechangecallback)接口。 <br>可能存在多个音频设备同时发生状态变化。 |
| [typedef int32_t (\*OH_AudioRoutingManager_OnPreferredOutputDeviceChangedCallback)(OH_AudioDeviceDescriptorArray *audioDeviceDescriptorArray)](#oh_audioroutingmanager_onpreferredoutputdevicechangedcallback) | OH_AudioRoutingManager_OnPreferredOutputDeviceChangedCallback | 首选输出设备变化回调函数的原型定义， 用于[OH_AudioRoutingManager_RegisterPreferredOutputDevicesChangeCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_registerpreferredoutputdeviceschangecallback)和 [OH_AudioRoutingManager_UnregisterPreferredOutputDevicesChangeCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_unregisterpreferredoutputdeviceschangecallback)接口。 <br>首选设备可以是多个音频输出设备。 |
| [typedef int32_t (\*OH_AudioRoutingManager_OnPreferredInputDeviceChangedCallback)(OH_AudioDeviceDescriptorArray *audioDeviceDescriptorArray)](#oh_audioroutingmanager_onpreferredinputdevicechangedcallback) | OH_AudioRoutingManager_OnPreferredInputDeviceChangedCallback | 首选输入设备变化回调函数的原型定义， 用于[OH_AudioRoutingManager_RegisterPreferredInputDevicesChangeCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_registerpreferredinputdeviceschangecallback)和 [OH_AudioRoutingManager_UnregisterPreferredInputDevicesChangeCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_unregisterpreferredinputdeviceschangecallback)接口。 <br>首选设备可以是多个音频输入设备。 |
| [OH_AudioCommon_Result OH_AudioManager_GetAudioRoutingManager(OH_AudioRoutingManager **audioRoutingManager)](#oh_audiomanager_getaudioroutingmanager) | - | 获取音频路由管理器实例，该实例为单例，用于调用音频设备状态和路由变化查询功能接口。 |
| [OH_AudioCommon_Result OH_AudioRoutingManager_GetDevices(OH_AudioRoutingManager *audioRoutingManager, OH_AudioDevice_Flag deviceFlag, OH_AudioDeviceDescriptorArray **audioDeviceDescriptorArray)](#oh_audioroutingmanager_getdevices) | - | 查询在线的音频设备，支持按照输入输出维度查询。 <br>在线设备包括内置的音频设备和连接的外设。 |
| [OH_AudioCommon_Result OH_AudioRoutingManager_GetAvailableDevices(OH_AudioRoutingManager *audioRoutingManager, OH_AudioDevice_Usage deviceUsage, OH_AudioDeviceDescriptorArray **audioDeviceDescriptorArray)](#oh_audioroutingmanager_getavailabledevices) | - | 查询指定场景的可用音频设备，支持按照设备使用场景和输入输出维度查询。 <br>音频系统会根据使用场景选择不同的输入输出设备，主要分为媒体和通话场景。 |
| [OH_AudioCommon_Result OH_AudioRoutingManager_GetPreferredOutputDevice(OH_AudioRoutingManager *audioRoutingManager, OH_AudioStream_Usage streamUsage, OH_AudioDeviceDescriptorArray **audioDeviceDescriptorArray)](#oh_audioroutingmanager_getpreferredoutputdevice) | - | 查询首选音频输出设备。 <br>音频系统会根据播放流的[OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage)确定不同的首选输出设备。 |
| [OH_AudioCommon_Result OH_AudioRoutingManager_GetPreferredInputDevice(OH_AudioRoutingManager *audioRoutingManager, OH_AudioStream_SourceType sourceType, OH_AudioDeviceDescriptorArray **audioDeviceDescriptorArray)](#oh_audioroutingmanager_getpreferredinputdevice) | - | 查询首选音频输入设备。 <br>音频系统会根据录制流的[OH_AudioStream_SourceType](capi-native-audiostream-base-h.md#oh_audiostream_sourcetype)确定不同的首选输入设备。 |
| [OH_AudioCommon_Result OH_AudioRoutingManager_RegisterDeviceChangeCallback(OH_AudioRoutingManager *audioRoutingManager, OH_AudioDevice_Flag deviceFlag, OH_AudioRoutingManager_OnDeviceChangedCallback callback)](#oh_audioroutingmanager_registerdevicechangecallback) | - | 注册音频在线设备变化回调。 <br>当音频外设连接和断连时，系统会触发此回调。 <br>为避免资源浪费或其他异常情况，当应用程序不再需要此回调时， 必须通过调用[OH_AudioRoutingManager_UnregisterDeviceChangeCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_unregisterdevicechangecallback) 来释放回调。 |
| [OH_AudioCommon_Result OH_AudioRoutingManager_UnregisterDeviceChangeCallback(OH_AudioRoutingManager *audioRoutingManager, OH_AudioRoutingManager_OnDeviceChangedCallback callback)](#oh_audioroutingmanager_unregisterdevicechangecallback) | - | 取消通过[OH_AudioRoutingManager_RegisterDeviceChangeCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_registerdevicechangecallback)注册的音频在线设备变化回调。 |
| [OH_AudioCommon_Result OH_AudioRoutingManager_RegisterPreferredOutputDevicesChangeCallback(OH_AudioRoutingManager *audioRoutingManager, OH_AudioStream_Usage streamUsage, OH_AudioRoutingManager_OnPreferredOutputDeviceChangedCallback callback)](#oh_audioroutingmanager_registerpreferredoutputdeviceschangecallback) | - | 注册音频首选输出设备变化回调。 <br>当指定播放流使用场景类型的首选输出设备发生变化时，系统会触发此回调。 <br>音频系统会根据播放流的[OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage)确定不同的首选输出设备。 <br>为避免资源浪费或其他异常情况，当应用程序不再需要此回调时， 必须通过调用[OH_AudioRoutingManager_UnregisterPreferredOutputDevicesChangeCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_unregisterpreferredoutputdeviceschangecallback)来释放回调。 |
| [OH_AudioCommon_Result OH_AudioRoutingManager_UnregisterPreferredOutputDevicesChangeCallback(OH_AudioRoutingManager *audioRoutingManager, OH_AudioRoutingManager_OnPreferredOutputDeviceChangedCallback callback)](#oh_audioroutingmanager_unregisterpreferredoutputdeviceschangecallback) | - | 取消通过[OH_AudioRoutingManager_RegisterPreferredOutputDevicesChangeCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_registerpreferredoutputdeviceschangecallback) 注册的音频首选输出设备变化回调。 |
| [OH_AudioCommon_Result OH_AudioRoutingManager_RegisterPreferredInputDevicesChangeCallback(OH_AudioRoutingManager *audioRoutingManager, OH_AudioStream_SourceType sourceType, OH_AudioRoutingManager_OnPreferredInputDeviceChangedCallback callback)](#oh_audioroutingmanager_registerpreferredinputdeviceschangecallback) | - | 注册音频首选输入设备变化回调。 <br>当指定录制流使用场景类型的首选输入设备发生变化时，系统会触发此回调。 <br>音频系统会根据录制流的[OH_AudioStream_SourceType](capi-native-audiostream-base-h.md#oh_audiostream_sourcetype)确定不同的首选输入设备。 <br>为避免资源浪费或其他异常情况，当应用程序不再需要此回调时， 必须通过调用[OH_AudioRoutingManager_UnregisterPreferredInputDevicesChangeCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_unregisterpreferredinputdeviceschangecallback)来释放回调。 |
| [OH_AudioCommon_Result OH_AudioRoutingManager_UnregisterPreferredInputDevicesChangeCallback(OH_AudioRoutingManager *audioRoutingManager, OH_AudioRoutingManager_OnPreferredInputDeviceChangedCallback callback)](#oh_audioroutingmanager_unregisterpreferredinputdeviceschangecallback) | - | 取消通过[OH_AudioRoutingManager_RegisterPreferredInputDevicesChangeCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_registerpreferredinputdeviceschangecallback) 注册的音频首选输入设备变更回调。 |
| [OH_AudioCommon_Result OH_AudioRoutingManager_ReleaseDevices(OH_AudioRoutingManager *audioRoutingManager, OH_AudioDeviceDescriptorArray *audioDeviceDescriptorArray)](#oh_audioroutingmanager_releasedevices) | - | 释放音频设备描述符数组对象。 <br>音频路由管理的查询和监听接口，返回的OH_AudioDeviceDescriptorArray均由系统侧申请内存。 开发者不应通过free或delete释放OH_AudioDeviceDescriptorArray指针指向的内存，而需要调用此接口释放。 |
| [typedef void (\*OH_AudioRoutingManager_OnDeviceBlockStatusCallback)(OH_AudioDeviceDescriptorArray *audioDeviceDescriptorArray, OH_AudioDevice_BlockStatus status, void *userData)](#oh_audioroutingmanager_ondeviceblockstatuscallback) | OH_AudioRoutingManager_OnDeviceBlockStatusCallback | 音频设备堵塞状态变化回调函数的原型定义，用于[OH_AudioRoutingManager_SetMicBlockStatusCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_setmicblockstatuscallback)接口。 |
| [OH_AudioCommon_Result OH_AudioRoutingManager_IsMicBlockDetectionSupported(OH_AudioRoutingManager *audioRoutingManager, bool *supported)](#oh_audioroutingmanager_ismicblockdetectionsupported) | - | 查询当前设备是否支持麦克风堵塞状态检测。 |
| [OH_AudioCommon_Result OH_AudioRoutingManager_SetMicBlockStatusCallback(OH_AudioRoutingManager *audioRoutingManager, OH_AudioRoutingManager_OnDeviceBlockStatusCallback callback, void *userData)](#oh_audioroutingmanager_setmicblockstatuscallback) | - | 设置麦克风是否堵塞状态回调。 <br>当应用正在使用麦克风录音，此场景下麦克风堵塞状态发生变化，系统才会触发此回调。 <br>在使用此功能之前，应通过[OH_AudioRoutingManager_IsMicBlockDetectionSupported](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_ismicblockdetectionsupported)查询当前设备是否支持检测。 <br>目前此检测功能仅支持本地设备的内置麦克风。 |

### 变量

| 名称 | 描述 |
| -- | -- |
| int32_t (*OH_AudioRoutingManager_OnDeviceChangedCallback) ( OH_AudioDevice_ChangeType type, OH_AudioDeviceDescriptorArray *audioDeviceDescriptorArray ) | 音频设备在线状态变化回调函数的原型定义，用于[OH_AudioRoutingManager_RegisterDeviceChangeCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_registerdevicechangecallback)和 [OH_AudioRoutingManager_UnregisterDeviceChangeCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_unregisterdevicechangecallback)接口。 <br>可能存在多个音频设备同时发生状态变化。<br>**起始版本：** 12<br>**系统能力：** SystemCapability.Multimedia.Audio.Core |
| int32_t (*OH_AudioRoutingManager_OnPreferredOutputDeviceChangedCallback) ( OH_AudioDeviceDescriptorArray *audioDeviceDescriptorArray) | 首选输出设备变化回调函数的原型定义， 用于[OH_AudioRoutingManager_RegisterPreferredOutputDevicesChangeCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_registerpreferredoutputdeviceschangecallback)和 [OH_AudioRoutingManager_UnregisterPreferredOutputDevicesChangeCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_unregisterpreferredoutputdeviceschangecallback)接口。 <br>首选设备可以是多个音频输出设备。<br>**起始版本：** 26.0.0<br>**系统能力：** SystemCapability.Multimedia.Audio.Core |
| int32_t (*OH_AudioRoutingManager_OnPreferredInputDeviceChangedCallback) ( OH_AudioDeviceDescriptorArray *audioDeviceDescriptorArray) | 首选输入设备变化回调函数的原型定义， 用于[OH_AudioRoutingManager_RegisterPreferredInputDevicesChangeCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_registerpreferredinputdeviceschangecallback)和 [OH_AudioRoutingManager_UnregisterPreferredInputDevicesChangeCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_unregisterpreferredinputdeviceschangecallback)接口。 <br>首选设备可以是多个音频输入设备。<br>**起始版本：** 26.0.0<br>**系统能力：** SystemCapability.Multimedia.Audio.Core |
| void (*OH_AudioRoutingManager_OnDeviceBlockStatusCallback)( OH_AudioDeviceDescriptorArray *audioDeviceDescriptorArray, OH_AudioDevice_BlockStatus status, void *userData) | 音频设备堵塞状态变化回调函数的原型定义，用于[OH_AudioRoutingManager_SetMicBlockStatusCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_setmicblockstatuscallback)接口。<br>**起始版本：** 13<br>**系统能力：** SystemCapability.Multimedia.Audio.Core |

## 函数说明

### OH_AudioRoutingManager_OnDeviceChangedCallback()

```c
typedef int32_t (*OH_AudioRoutingManager_OnDeviceChangedCallback)(OH_AudioDevice_ChangeType type, OH_AudioDeviceDescriptorArray *audioDeviceDescriptorArray)
```

**描述：**

音频设备在线状态变化回调函数的原型定义，用于[OH_AudioRoutingManager_RegisterDeviceChangeCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_registerdevicechangecallback)和 [OH_AudioRoutingManager_UnregisterDeviceChangeCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_unregisterdevicechangecallback)接口。 <br>可能存在多个音频设备同时发生状态变化。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioDevice_ChangeType](capi-native-audio-device-base-h.md#oh_audiodevice_changetype) type | 设备连接状态，连接或断开。 |
| [OH_AudioDeviceDescriptorArray](capi-ohaudio-oh-audiodevicedescriptorarray.md) *audioDeviceDescriptorArray | 发生状态变化的音频设备描述符数组。 <br>不要单独释放此指针指向的内存，而是调用[OH_AudioRoutingManager_ReleaseDevices](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_releasedevices)，在不使用时释放所有内存。 |

### OH_AudioRoutingManager_OnPreferredOutputDeviceChangedCallback()

```c
typedef int32_t (*OH_AudioRoutingManager_OnPreferredOutputDeviceChangedCallback)(OH_AudioDeviceDescriptorArray *audioDeviceDescriptorArray)
```

**描述：**

首选输出设备变化回调函数的原型定义， 用于[OH_AudioRoutingManager_RegisterPreferredOutputDevicesChangeCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_registerpreferredoutputdeviceschangecallback)和 [OH_AudioRoutingManager_UnregisterPreferredOutputDevicesChangeCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_unregisterpreferredoutputdeviceschangecallback)接口。 <br>首选设备可以是多个音频输出设备。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioDeviceDescriptorArray](capi-ohaudio-oh-audiodevicedescriptorarray.md) *audioDeviceDescriptorArray | 变化后的首选音频输出设备描述符数组。 <br>不要单独释放此指针指向的内存，而是调用[OH_AudioRoutingManager_ReleaseDevices](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_releasedevices)，在不使用时释放所有内存。 |

### OH_AudioRoutingManager_OnPreferredInputDeviceChangedCallback()

```c
typedef int32_t (*OH_AudioRoutingManager_OnPreferredInputDeviceChangedCallback)(OH_AudioDeviceDescriptorArray *audioDeviceDescriptorArray)
```

**描述：**

首选输入设备变化回调函数的原型定义， 用于[OH_AudioRoutingManager_RegisterPreferredInputDevicesChangeCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_registerpreferredinputdeviceschangecallback)和 [OH_AudioRoutingManager_UnregisterPreferredInputDevicesChangeCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_unregisterpreferredinputdeviceschangecallback)接口。 <br>首选设备可以是多个音频输入设备。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioDeviceDescriptorArray](capi-ohaudio-oh-audiodevicedescriptorarray.md) *audioDeviceDescriptorArray | 变化后的首选音频输入设备描述符数组。 <br>不要单独释放此指针指向的内存，而是调用[OH_AudioRoutingManager_ReleaseDevices](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_releasedevices)，在不使用时释放所有内存。 |

### OH_AudioManager_GetAudioRoutingManager()

```c
OH_AudioCommon_Result OH_AudioManager_GetAudioRoutingManager(OH_AudioRoutingManager **audioRoutingManager)
```

**描述：**

获取音频路由管理器实例，该实例为单例，用于调用音频设备状态和路由变化查询功能接口。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioRoutingManager](capi-ohaudio-oh-audioroutingmanager.md) **audioRoutingManager | [out] 指向OH_AudioRoutingManager指针的地址，用于接收获取的音频路由管理器实例。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| OH_AudioCommon_Result | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 函数执行成功。</li> </ul> |

### OH_AudioRoutingManager_GetDevices()

```c
OH_AudioCommon_Result OH_AudioRoutingManager_GetDevices(OH_AudioRoutingManager *audioRoutingManager, OH_AudioDevice_Flag deviceFlag, OH_AudioDeviceDescriptorArray **audioDeviceDescriptorArray)
```

**描述：**

查询在线的音频设备，支持按照输入输出维度查询。 <br>在线设备包括内置的音频设备和连接的外设。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioRoutingManager](capi-ohaudio-oh-audioroutingmanager.md) *audioRoutingManager | [in] 指向通过[OH_AudioManager_GetAudioRoutingManager](capi-native-audio-routing-manager-h.md#oh_audiomanager_getaudioroutingmanager)获取的音频路由管理器实例。 |
| [OH_AudioDevice_Flag](capi-native-audio-device-base-h.md#oh_audiodevice_flag) deviceFlag | [in] 音频设备标志，用于过滤输入或输出设备。 |
| [OH_AudioDeviceDescriptorArray](capi-ohaudio-oh-audiodevicedescriptorarray.md) **audioDeviceDescriptorArray | [out] 音频设备描述符数组。 <br>不要单独释放此指针指向的内存，而是调用[OH_AudioRoutingManager_ReleaseDevices](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_releasedevices)，在不使用时释放所有内存。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| OH_AudioCommon_Result | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 函数执行成功。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) 1. 参数audioRoutingManager为空指针；2. 参数deviceFlag无效；3. 参数audioDeviceDescriptorArray为空指针。</li> <li>[AUDIOCOMMON_RESULT_ERROR_NO_MEMORY](capi-native-audio-common-h.md#oh_audiocommon_result) 内存不足。</li> </ul> |

### OH_AudioRoutingManager_GetAvailableDevices()

```c
OH_AudioCommon_Result OH_AudioRoutingManager_GetAvailableDevices(OH_AudioRoutingManager *audioRoutingManager, OH_AudioDevice_Usage deviceUsage, OH_AudioDeviceDescriptorArray **audioDeviceDescriptorArray)
```

**描述：**

查询指定场景的可用音频设备，支持按照设备使用场景和输入输出维度查询。 <br>音频系统会根据使用场景选择不同的输入输出设备，主要分为媒体和通话场景。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioRoutingManager](capi-ohaudio-oh-audioroutingmanager.md) *audioRoutingManager | [in] 指向通过[OH_AudioManager_GetAudioRoutingManager](capi-native-audio-routing-manager-h.md#oh_audiomanager_getaudioroutingmanager)获取的音频路由管理器实例。 |
| [OH_AudioDevice_Usage](capi-native-audio-device-base-h.md#oh_audiodevice_usage) deviceUsage | [in] 要查询设备的使用场景和输入输出类型。 |
| [OH_AudioDeviceDescriptorArray](capi-ohaudio-oh-audiodevicedescriptorarray.md) **audioDeviceDescriptorArray | [out] 可用音频设备的描述符数组。 <br>不要单独释放此指针指向的内存，而是调用[OH_AudioRoutingManager_ReleaseDevices](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_releasedevices)，在不使用时释放所有内存。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| OH_AudioCommon_Result | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 函数执行成功。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) 1. 参数audioRoutingManager为空指针；2. 参数deviceUsage无效；3. 参数audioDeviceDescriptorArray为空指针。</li> <li>[AUDIOCOMMON_RESULT_ERROR_NO_MEMORY](capi-native-audio-common-h.md#oh_audiocommon_result) 内存不足。</li> </ul> |

### OH_AudioRoutingManager_GetPreferredOutputDevice()

```c
OH_AudioCommon_Result OH_AudioRoutingManager_GetPreferredOutputDevice(OH_AudioRoutingManager *audioRoutingManager, OH_AudioStream_Usage streamUsage, OH_AudioDeviceDescriptorArray **audioDeviceDescriptorArray)
```

**描述：**

查询首选音频输出设备。 <br>音频系统会根据播放流的[OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage)确定不同的首选输出设备。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioRoutingManager](capi-ohaudio-oh-audioroutingmanager.md) *audioRoutingManager | [in] 指向通过[OH_AudioManager_GetAudioRoutingManager](capi-native-audio-routing-manager-h.md#oh_audiomanager_getaudioroutingmanager)获取的音频路由管理器实例。 |
| OH_AudioStream_Usage streamUsage | [in] 用于确定首选设备的音频播放流使用场景。 |
| [OH_AudioDeviceDescriptorArray](capi-ohaudio-oh-audiodevicedescriptorarray.md) **audioDeviceDescriptorArray | [out] 首选音频输出设备描述符数组。 <br>不要单独释放此指针指向的内存，而是调用[OH_AudioRoutingManager_ReleaseDevices](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_releasedevices)，在不使用时释放所有内存。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| OH_AudioCommon_Result | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 函数执行成功。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) 1. 参数audioRoutingManager为空指针；2. 参数streamUsage无效；3. 参数audioDeviceDescriptorArray为空指针。</li> <li>[AUDIOCOMMON_RESULT_ERROR_NO_MEMORY](capi-native-audio-common-h.md#oh_audiocommon_result) 内存不足。</li> </ul> |

### OH_AudioRoutingManager_GetPreferredInputDevice()

```c
OH_AudioCommon_Result OH_AudioRoutingManager_GetPreferredInputDevice(OH_AudioRoutingManager *audioRoutingManager, OH_AudioStream_SourceType sourceType, OH_AudioDeviceDescriptorArray **audioDeviceDescriptorArray)
```

**描述：**

查询首选音频输入设备。 <br>音频系统会根据录制流的[OH_AudioStream_SourceType](capi-native-audiostream-base-h.md#oh_audiostream_sourcetype)确定不同的首选输入设备。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioRoutingManager](capi-ohaudio-oh-audioroutingmanager.md) *audioRoutingManager | [in] 指向通过[OH_AudioManager_GetAudioRoutingManager](capi-native-audio-routing-manager-h.md#oh_audiomanager_getaudioroutingmanager)获取的音频路由管理器实例。 |
| OH_AudioStream_SourceType sourceType | [in] 用于确定首选设备的音频录制流使用场景。 |
| [OH_AudioDeviceDescriptorArray](capi-ohaudio-oh-audiodevicedescriptorarray.md) **audioDeviceDescriptorArray | [out] 首选音频输入设备描述符数组。 <br>不要单独释放此指针指向的内存，而是调用[OH_AudioRoutingManager_ReleaseDevices](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_releasedevices)，在不使用时释放所有内存。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| OH_AudioCommon_Result | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 函数执行成功。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) 1. 参数audioRoutingManager为空指针；2. 参数sourceType无效；3. 参数audioDeviceDescriptorArray为空指针。</li> <li>[AUDIOCOMMON_RESULT_ERROR_NO_MEMORY](capi-native-audio-common-h.md#oh_audiocommon_result) 内存不足。</li> </ul> |

### OH_AudioRoutingManager_RegisterDeviceChangeCallback()

```c
OH_AudioCommon_Result OH_AudioRoutingManager_RegisterDeviceChangeCallback(OH_AudioRoutingManager *audioRoutingManager, OH_AudioDevice_Flag deviceFlag, OH_AudioRoutingManager_OnDeviceChangedCallback callback)
```

**描述：**

注册音频在线设备变化回调。 <br>当音频外设连接和断连时，系统会触发此回调。 <br>为避免资源浪费或其他异常情况，当应用程序不再需要此回调时， 必须通过调用[OH_AudioRoutingManager_UnregisterDeviceChangeCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_unregisterdevicechangecallback) 来释放回调。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioRoutingManager](capi-ohaudio-oh-audioroutingmanager.md) *audioRoutingManager | [in] 指向通过[OH_AudioManager_GetAudioRoutingManager](capi-native-audio-routing-manager-h.md#oh_audiomanager_getaudioroutingmanager)获取的音频路由管理器实例。 |
| [OH_AudioDevice_Flag](capi-native-audio-device-base-h.md#oh_audiodevice_flag) deviceFlag | [in] 音频设备标志，用来筛选输入输出。 |
| [OH_AudioRoutingManager_OnDeviceChangedCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_ondevicechangedcallback) callback | [in] 音频设备在线状态变化回调函数指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| OH_AudioCommon_Result | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 函数执行成功。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) 1. 参数audioRoutingManager为空指针；2. 参数deviceFlag无效；3. 参数callback为空指针。</li> </ul> |

### OH_AudioRoutingManager_UnregisterDeviceChangeCallback()

```c
OH_AudioCommon_Result OH_AudioRoutingManager_UnregisterDeviceChangeCallback(OH_AudioRoutingManager *audioRoutingManager, OH_AudioRoutingManager_OnDeviceChangedCallback callback)
```

**描述：**

取消通过[OH_AudioRoutingManager_RegisterDeviceChangeCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_registerdevicechangecallback)注册的音频在线设备变化回调。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioRoutingManager](capi-ohaudio-oh-audioroutingmanager.md) *audioRoutingManager | [in] 指向通过[OH_AudioManager_GetAudioRoutingManager](capi-native-audio-routing-manager-h.md#oh_audiomanager_getaudioroutingmanager)获取的音频路由管理器实例。 |
| [OH_AudioRoutingManager_OnDeviceChangedCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_ondevicechangedcallback) callback | [in] 已注册的音频设备在线状态变化回调函数指针，用于取消。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| OH_AudioCommon_Result | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 函数执行成功。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) 1. 参数audioRoutingManager为空指针；2. 参数callback为空指针。</li> </ul> |

### OH_AudioRoutingManager_RegisterPreferredOutputDevicesChangeCallback()

```c
OH_AudioCommon_Result OH_AudioRoutingManager_RegisterPreferredOutputDevicesChangeCallback(OH_AudioRoutingManager *audioRoutingManager, OH_AudioStream_Usage streamUsage, OH_AudioRoutingManager_OnPreferredOutputDeviceChangedCallback callback)
```

**描述：**

注册音频首选输出设备变化回调。 <br>当指定播放流使用场景类型的首选输出设备发生变化时，系统会触发此回调。 <br>音频系统会根据播放流的[OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage)确定不同的首选输出设备。 <br>为避免资源浪费或其他异常情况，当应用程序不再需要此回调时， 必须通过调用[OH_AudioRoutingManager_UnregisterPreferredOutputDevicesChangeCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_unregisterpreferredoutputdeviceschangecallback)来释放回调。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioRoutingManager](capi-ohaudio-oh-audioroutingmanager.md) *audioRoutingManager | [in] 指向通过[OH_AudioManager_GetAudioRoutingManager](capi-native-audio-routing-manager-h.md#oh_audiomanager_getaudioroutingmanager)获取的音频路由管理器实例。 |
| OH_AudioStream_Usage streamUsage | [in] 用于确定首选设备的音频播放流使用场景。 |
| [OH_AudioRoutingManager_OnPreferredOutputDeviceChangedCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_onpreferredoutputdevicechangedcallback) callback | [in] 指向OH_AudioRoutingManager_OnPreferredOutputDeviceChangedCallback， 用于接收首选输出设备变化事件。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| OH_AudioCommon_Result | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 函数执行成功。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) 参数校验失败。</li> <li>[AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) 音频客户端在调用音频服务的过程中遇到系统错误，导致调用失败。</li> </ul> |

### OH_AudioRoutingManager_UnregisterPreferredOutputDevicesChangeCallback()

```c
OH_AudioCommon_Result OH_AudioRoutingManager_UnregisterPreferredOutputDevicesChangeCallback(OH_AudioRoutingManager *audioRoutingManager, OH_AudioRoutingManager_OnPreferredOutputDeviceChangedCallback callback)
```

**描述：**

取消通过[OH_AudioRoutingManager_RegisterPreferredOutputDevicesChangeCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_registerpreferredoutputdeviceschangecallback) 注册的音频首选输出设备变化回调。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioRoutingManager](capi-ohaudio-oh-audioroutingmanager.md) *audioRoutingManager | [in] 指向通过[OH_AudioManager_GetAudioRoutingManager](capi-native-audio-routing-manager-h.md#oh_audiomanager_getaudioroutingmanager)获取的音频路由管理器实例。 |
| [OH_AudioRoutingManager_OnPreferredOutputDeviceChangedCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_onpreferredoutputdevicechangedcallback) callback | [in] 已注册的音频首选输出设备变化回调函数指针，用于取消。 传入空指针时，系统将取消所有已注册的首选输出设备变化回调。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| OH_AudioCommon_Result | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 函数执行成功。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) 参数校验失败。</li> <li>[AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) 音频客户端在调用音频服务的过程中遇到系统错误，导致调用失败。</li> </ul> |

### OH_AudioRoutingManager_RegisterPreferredInputDevicesChangeCallback()

```c
OH_AudioCommon_Result OH_AudioRoutingManager_RegisterPreferredInputDevicesChangeCallback(OH_AudioRoutingManager *audioRoutingManager, OH_AudioStream_SourceType sourceType, OH_AudioRoutingManager_OnPreferredInputDeviceChangedCallback callback)
```

**描述：**

注册音频首选输入设备变化回调。 <br>当指定录制流使用场景类型的首选输入设备发生变化时，系统会触发此回调。 <br>音频系统会根据录制流的[OH_AudioStream_SourceType](capi-native-audiostream-base-h.md#oh_audiostream_sourcetype)确定不同的首选输入设备。 <br>为避免资源浪费或其他异常情况，当应用程序不再需要此回调时， 必须通过调用[OH_AudioRoutingManager_UnregisterPreferredInputDevicesChangeCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_unregisterpreferredinputdeviceschangecallback)来释放回调。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioRoutingManager](capi-ohaudio-oh-audioroutingmanager.md) *audioRoutingManager | [in] 指向通过[OH_AudioManager_GetAudioRoutingManager](capi-native-audio-routing-manager-h.md#oh_audiomanager_getaudioroutingmanager)获取的音频路由管理器实例。 |
| OH_AudioStream_SourceType sourceType | [in] 用于确定首选设备的音频录制流使用场景。 |
| [OH_AudioRoutingManager_OnPreferredInputDeviceChangedCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_onpreferredinputdevicechangedcallback) callback | [in] 指向OH_AudioRoutingManager_OnPreferredInputDeviceChangedCallback，用于接收首选输入设备变化事件。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| OH_AudioCommon_Result | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 函数执行成功。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) 参数校验失败。</li> <li>[AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) 音频客户端在调用音频服务的过程中遇到系统错误，导致调用失败。</li> </ul> |

### OH_AudioRoutingManager_UnregisterPreferredInputDevicesChangeCallback()

```c
OH_AudioCommon_Result OH_AudioRoutingManager_UnregisterPreferredInputDevicesChangeCallback(OH_AudioRoutingManager *audioRoutingManager, OH_AudioRoutingManager_OnPreferredInputDeviceChangedCallback callback)
```

**描述：**

取消通过[OH_AudioRoutingManager_RegisterPreferredInputDevicesChangeCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_registerpreferredinputdeviceschangecallback) 注册的音频首选输入设备变更回调。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioRoutingManager](capi-ohaudio-oh-audioroutingmanager.md) *audioRoutingManager | [in] 指向通过[OH_AudioManager_GetAudioRoutingManager](capi-native-audio-routing-manager-h.md#oh_audiomanager_getaudioroutingmanager)获取的音频路由管理器实例。 |
| [OH_AudioRoutingManager_OnPreferredInputDeviceChangedCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_onpreferredinputdevicechangedcallback) callback | [in] 已注册的音频首选输入设备变化回调函数指针，用于取消。 传入空指针时，系统将取消所有已注册的首选输入设备变化回调。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| OH_AudioCommon_Result | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 函数执行成功。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) 参数校验失败。</li> <li>[AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) 音频客户端在调用音频服务的过程中遇到系统错误，导致调用失败。</li> </ul> |

### OH_AudioRoutingManager_ReleaseDevices()

```c
OH_AudioCommon_Result OH_AudioRoutingManager_ReleaseDevices(OH_AudioRoutingManager *audioRoutingManager, OH_AudioDeviceDescriptorArray *audioDeviceDescriptorArray)
```

**描述：**

释放音频设备描述符数组对象。 <br>音频路由管理的查询和监听接口，返回的OH_AudioDeviceDescriptorArray均由系统侧申请内存。 开发者不应通过free或delete释放OH_AudioDeviceDescriptorArray指针指向的内存，而需要调用此接口释放。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioRoutingManager](capi-ohaudio-oh-audioroutingmanager.md) *audioRoutingManager | [in] 指向通过[OH_AudioManager_GetAudioRoutingManager](capi-native-audio-routing-manager-h.md#oh_audiomanager_getaudioroutingmanager)获取的音频路由管理器实例。 |
| [OH_AudioDeviceDescriptorArray](capi-ohaudio-oh-audiodevicedescriptorarray.md) *audioDeviceDescriptorArray | [in] 待释放的音频设备描述符数组。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| OH_AudioCommon_Result | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 函数执行成功。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) 1. 参数audioRoutingManager为空指针；2. 参数audioDeviceDescriptorArray为空指针。</li> </ul> |

### OH_AudioRoutingManager_OnDeviceBlockStatusCallback()

```c
typedef void (*OH_AudioRoutingManager_OnDeviceBlockStatusCallback)(OH_AudioDeviceDescriptorArray *audioDeviceDescriptorArray, OH_AudioDevice_BlockStatus status, void *userData)
```

**描述：**

音频设备堵塞状态变化回调函数的原型定义，用于[OH_AudioRoutingManager_SetMicBlockStatusCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_setmicblockstatuscallback)接口。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 13

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioDeviceDescriptorArray](capi-ohaudio-oh-audiodevicedescriptorarray.md) *audioDeviceDescriptorArray | 发生状态变化的音频设备描述符数组。 <br>不要单独释放此指针指向的内存，而是调用[OH_AudioRoutingManager_ReleaseDevices](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_releasedevices)，在不使用时释放所有内存。 |
| [OH_AudioDevice_BlockStatus](capi-native-audio-device-base-h.md#oh_audiodevice_blockstatus) status | 音频设备的堵塞状态。 |
| void *userData | 指向开发者在[OH_AudioRoutingManager_SetMicBlockStatusCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_setmicblockstatuscallback)接口传入的userData数据。 |

### OH_AudioRoutingManager_IsMicBlockDetectionSupported()

```c
OH_AudioCommon_Result OH_AudioRoutingManager_IsMicBlockDetectionSupported(OH_AudioRoutingManager *audioRoutingManager, bool *supported)
```

**描述：**

查询当前设备是否支持麦克风堵塞状态检测。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 13

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioRoutingManager](capi-ohaudio-oh-audioroutingmanager.md) *audioRoutingManager | [in] 指向通过[OH_AudioManager_GetAudioRoutingManager](capi-native-audio-routing-manager-h.md#oh_audiomanager_getaudioroutingmanager)获取的音频路由管理器实例。 |
| bool *supported | [out] 获取当前设备是否支持麦克风堵塞状态检测的结果。true表示支持，false表示不支持。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| OH_AudioCommon_Result | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 函数执行成功。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) 1. 参数audioRoutingManager为空指针；2. 参数supported为空指针。</li> </ul> |

### OH_AudioRoutingManager_SetMicBlockStatusCallback()

```c
OH_AudioCommon_Result OH_AudioRoutingManager_SetMicBlockStatusCallback(OH_AudioRoutingManager *audioRoutingManager, OH_AudioRoutingManager_OnDeviceBlockStatusCallback callback, void *userData)
```

**描述：**

设置麦克风是否堵塞状态回调。 <br>当应用正在使用麦克风录音，此场景下麦克风堵塞状态发生变化，系统才会触发此回调。 <br>在使用此功能之前，应通过[OH_AudioRoutingManager_IsMicBlockDetectionSupported](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_ismicblockdetectionsupported)查询当前设备是否支持检测。 <br>目前此检测功能仅支持本地设备的内置麦克风。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 13

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioRoutingManager](capi-ohaudio-oh-audioroutingmanager.md) *audioRoutingManager | [in] 指向通过[OH_AudioManager_GetAudioRoutingManager](capi-native-audio-routing-manager-h.md#oh_audiomanager_getaudioroutingmanager)获取的音频路由管理器实例。 |
| [OH_AudioRoutingManager_OnDeviceBlockStatusCallback](capi-native-audio-routing-manager-h.md#oh_audioroutingmanager_ondeviceblockstatuscallback) callback | [in] 用于接受麦克风堵塞状态变化事件的回调函数。 |
| void *userData | [in] 用户自定义数据指针，回调函数触发时会携带。若无需传递数据，可传入空指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| OH_AudioCommon_Result | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 函数执行成功。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) 1. 参数audioRoutingManager为空指针；2. 参数callback为空指针。</li> </ul> |


