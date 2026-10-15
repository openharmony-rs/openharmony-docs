# native_audio_volume_manager.h

## 概述

本文件提供音频音量管理功能的接口。 <br>在介绍音量管理能力前，需要先了解如下概念： <br>音量类型：系统将不同场景的音频播放流按[OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage)划分。由于OH_AudioStream_Usage种类很多， 为便于管理音量，系统将其进行分组， 每组OH_AudioStream_Usage对应一种音量类型，例如AUDIOSTREAM_USAGE_MUSIC和AUDIOSTREAM_USAGE_MOVIE都对应媒体音量， 当一种类型的音量改变， 此类型对应的所有音频播放流音量都会受到影响。 <br>音量等级：系统是以音量等级为单位进行音量大小调节的，实际的音量增益会基于音量等级计算得出， 确保调节时音量听感变化均匀。 不同的音量类型，可设置的音量等级范围可以是不同的。 <br>铃声模式：系统内用于控制铃声和通知音行为的状态，分为响铃、振动、静音三种模式，通常在具备通话能力的设备中使用。 铃声模式与铃声类型的音量存在联动关系。 <br>本文件提供的接口，支持开发者查询指定OH_AudioStream_Usage下的最大、最小音量等级， 以及当前系统设置的音量等级和静音状态，支持监听系统音量变化，也支持查询和监听系统当前铃声模式信息。 <br>由于系统不希望在没有用户感知的情况下发生音量变化，本文件不提供直接设置系统音量的接口。 如果开发者需要实现调节系统音量的功能，推荐使用AVVolumePanel。 <br>当前系统并未提供录音音量的管理功能，如果开发者需要调整录音音量，可在获取录音原始数据后自行调整数据增益。

**库：** libohaudio.so

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 20

**相关模块：** [OHAudio](capi-ohaudio.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_AudioVolumeManager](capi-ohaudio-oh-audiovolumemanager.md) | OH_AudioVolumeManager | 声明音频音量管理结构体，该结构体用于调用系统音量和铃声模式查询功能接口。 |

### 函数

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [typedef void (\*OH_AudioVolumeManager_OnStreamVolumeChangeCallback)(void *userData, OH_AudioStream_Usage usage, int32_t volumeLevel, bool updateUi)](#oh_audiovolumemanager_onstreamvolumechangecallback) | OH_AudioVolumeManager_OnStreamVolumeChangeCallback | 音量变化回调函数的原型定义，用于传递给[OH_AudioVolumeManager_RegisterStreamVolumeChangeCallback](capi-native-audio-volume-manager-h.md#oh_audiovolumemanager_registerstreamvolumechangecallback)。 |
| [typedef void (\*OH_AudioVolumeManager_OnRingerModeChangeCallback)(void *userData, OH_AudioRingerMode ringerMode)](#oh_audiovolumemanager_onringermodechangecallback) | OH_AudioVolumeManager_OnRingerModeChangeCallback | 铃声模式变化回调函数的原型定义，用于传递给[OH_AudioVolumeManager_RegisterRingerModeChangeCallback](capi-native-audio-volume-manager-h.md#oh_audiovolumemanager_registerringermodechangecallback)。 |
| [OH_AudioCommon_Result OH_AudioManager_GetAudioVolumeManager(OH_AudioVolumeManager **volumeManager)](#oh_audiomanager_getaudiovolumemanager) | - | 获取音量管理器实例，该实例为单例，用于调用系统音量和铃声模式查询和监听功能接口。 |
| [OH_AudioCommon_Result OH_AudioVolumeManager_GetMaxVolumeByUsage(OH_AudioVolumeManager *volumeManager, OH_AudioStream_Usage usage, int32_t *maxVolumeLevel)](#oh_audiovolumemanager_getmaxvolumebyusage) | - | 获取指定用途类型音频流的最大音量等级。 |
| [OH_AudioCommon_Result OH_AudioVolumeManager_GetMinVolumeByUsage(OH_AudioVolumeManager *volumeManager, OH_AudioStream_Usage usage, int32_t *minVolumeLevel)](#oh_audiovolumemanager_getminvolumebyusage) | - | 获取指定用途类型音频流的最小音量等级。 |
| [OH_AudioCommon_Result OH_AudioVolumeManager_GetVolumeByUsage(OH_AudioVolumeManager *volumeManager, OH_AudioStream_Usage usage, int32_t *volumeLevel)](#oh_audiovolumemanager_getvolumebyusage) | - | 获取指定用途类型音频流的系统音量等级。 |
| [OH_AudioCommon_Result OH_AudioVolumeManager_IsMuteByUsage(OH_AudioVolumeManager *volumeManager, OH_AudioStream_Usage usage, bool *muted)](#oh_audiovolumemanager_ismutebyusage) | - | 检查指定用途类型的音频流是否处于静音状态。 |
| [OH_AudioCommon_Result OH_AudioVolumeManager_RegisterStreamVolumeChangeCallback(OH_AudioVolumeManager *volumeManager, OH_AudioStream_Usage usage, OH_AudioVolumeManager_OnStreamVolumeChangeCallback callback, void *userData)](#oh_audiovolumemanager_registerstreamvolumechangecallback) | - | 注册音频流音量变化回调函数。 <br>多次注册同一个OH_AudioStream_Usage的变化回调时，系统会保存所有不同的回调函数，在其音量变化时遍历触发。 同一个回调函数，也只能用于注册一个OH_AudioStream_Usage的变化回调。 <br>若不再需要监听音频流音量变化，可调用[OH_AudioVolumeManager_UnregisterStreamVolumeChangeCallback](capi-native-audio-volume-manager-h.md#oh_audiovolumemanager_unregisterstreamvolumechangecallback)取消注册。 |
| [OH_AudioCommon_Result OH_AudioVolumeManager_UnregisterStreamVolumeChangeCallback(OH_AudioVolumeManager *volumeManager, OH_AudioVolumeManager_OnStreamVolumeChangeCallback callback)](#oh_audiovolumemanager_unregisterstreamvolumechangecallback) | - | 取消注册音频流音量变化回调函数。 |
| [OH_AudioCommon_Result OH_AudioVolumeManager_GetRingerMode(OH_AudioVolumeManager *volumeManager, OH_AudioRingerMode *ringerMode)](#oh_audiovolumemanager_getringermode) | - | 获取系统当前的铃声模式。 |
| [OH_AudioCommon_Result OH_AudioVolumeManager_RegisterRingerModeChangeCallback(OH_AudioVolumeManager *volumeManager, OH_AudioVolumeManager_OnRingerModeChangeCallback callback, void *userData)](#oh_audiovolumemanager_registerringermodechangecallback) | - | 注册铃声模式变化回调函数。 <br>多次注册时，系统会保存所有不同的回调函数，在铃声模式变化时遍历触发。 <br>若不再需要监听铃声模式变化，可调用[OH_AudioVolumeManager_UnregisterRingerModeChangeCallback](capi-native-audio-volume-manager-h.md#oh_audiovolumemanager_unregisterringermodechangecallback)取消注册。 |
| [OH_AudioCommon_Result OH_AudioVolumeManager_UnregisterRingerModeChangeCallback(OH_AudioVolumeManager *volumeManager, OH_AudioVolumeManager_OnRingerModeChangeCallback callback)](#oh_audiovolumemanager_unregisterringermodechangecallback) | - | 取消注册铃声模式变化回调函数。 |

### 变量

| 名称 | 描述 |
| -- | -- |
| void (*OH_AudioVolumeManager_OnStreamVolumeChangeCallback)( void *userData, OH_AudioStream_Usage usage, int32_t volumeLevel, bool updateUi ) | 音量变化回调函数的原型定义，用于传递给[OH_AudioVolumeManager_RegisterStreamVolumeChangeCallback](capi-native-audio-volume-manager-h.md#oh_audiovolumemanager_registerstreamvolumechangecallback)。<br>**起始版本：** 20<br>**系统能力：** SystemCapability.Multimedia.Audio.Core |
| void (*OH_AudioVolumeManager_OnRingerModeChangeCallback)( void *userData, OH_AudioRingerMode ringerMode ) | 铃声模式变化回调函数的原型定义，用于传递给[OH_AudioVolumeManager_RegisterRingerModeChangeCallback](capi-native-audio-volume-manager-h.md#oh_audiovolumemanager_registerringermodechangecallback)。<br>**起始版本：** 20<br>**系统能力：** SystemCapability.Multimedia.Audio.Core |

## 函数说明

### OH_AudioVolumeManager_OnStreamVolumeChangeCallback()

```c
typedef void (*OH_AudioVolumeManager_OnStreamVolumeChangeCallback)(void *userData, OH_AudioStream_Usage usage, int32_t volumeLevel, bool updateUi)
```

**描述：**

音量变化回调函数的原型定义，用于传递给[OH_AudioVolumeManager_RegisterStreamVolumeChangeCallback](capi-native-audio-volume-manager-h.md#oh_audiovolumemanager_registerstreamvolumechangecallback)。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| void *userData | 指向开发者在[OH_AudioVolumeManager_RegisterStreamVolumeChangeCallback](capi-native-audio-volume-manager-h.md#oh_audiovolumemanager_registerstreamvolumechangecallback)接口传入的userData数据。 |
| [OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage) usage | 对应音量被调整的流的用途类型。 |
| int32_t volumeLevel | 变化后的音量等级。 |
| bool updateUi | 是否在UI界面显示音量变化。true表示显示，false表示不显示。 |

### OH_AudioVolumeManager_OnRingerModeChangeCallback()

```c
typedef void (*OH_AudioVolumeManager_OnRingerModeChangeCallback)(void *userData, OH_AudioRingerMode ringerMode)
```

**描述：**

铃声模式变化回调函数的原型定义，用于传递给[OH_AudioVolumeManager_RegisterRingerModeChangeCallback](capi-native-audio-volume-manager-h.md#oh_audiovolumemanager_registerringermodechangecallback)。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| void *userData | 指向开发者在[OH_AudioVolumeManager_RegisterRingerModeChangeCallback](capi-native-audio-volume-manager-h.md#oh_audiovolumemanager_registerringermodechangecallback)接口传入的userData数据。 |
| [OH_AudioRingerMode](capi-native-audio-common-h.md#oh_audioringermode) ringerMode | 变化后的铃声模式。 |

### OH_AudioManager_GetAudioVolumeManager()

```c
OH_AudioCommon_Result OH_AudioManager_GetAudioVolumeManager(OH_AudioVolumeManager **volumeManager)
```

**描述：**

获取音量管理器实例，该实例为单例，用于调用系统音量和铃声模式查询和监听功能接口。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioVolumeManager](capi-ohaudio-oh-audiovolumemanager.md) **volumeManager | [out] 指向OH_AudioVolumeManager指针的地址，用于接收获取的音量管理器实例。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 函数执行成功。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) 参数volumeManager为空指针。</li> </ul> |

### OH_AudioVolumeManager_GetMaxVolumeByUsage()

```c
OH_AudioCommon_Result OH_AudioVolumeManager_GetMaxVolumeByUsage(OH_AudioVolumeManager *volumeManager, OH_AudioStream_Usage usage, int32_t *maxVolumeLevel)
```

**描述：**

获取指定用途类型音频流的最大音量等级。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioVolumeManager](capi-ohaudio-oh-audiovolumemanager.md) *volumeManager | [in] 指向通过[OH_AudioManager_GetAudioVolumeManager](capi-native-audio-volume-manager-h.md#oh_audiomanager_getaudiovolumemanager)获取的音量管理器实例。 |
| [OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage) usage | [in] 用于映射特定音量类型的音频流用途类型。 |
| int32_t *maxVolumeLevel | [out] 用于接收返回的最大音量等级。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 函数执行成功。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result)参数volumeManager或maxVolumeLevel为空指针，或usage是无效值。</li> <li>[AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) 系统处理错误。</li> </ul> |

### OH_AudioVolumeManager_GetMinVolumeByUsage()

```c
OH_AudioCommon_Result OH_AudioVolumeManager_GetMinVolumeByUsage(OH_AudioVolumeManager *volumeManager, OH_AudioStream_Usage usage, int32_t *minVolumeLevel)
```

**描述：**

获取指定用途类型音频流的最小音量等级。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioVolumeManager](capi-ohaudio-oh-audiovolumemanager.md) *volumeManager | [in] 指向通过[OH_AudioManager_GetAudioVolumeManager](capi-native-audio-volume-manager-h.md#oh_audiomanager_getaudiovolumemanager)获取的音量管理器实例。 |
| [OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage) usage | [in] 用于映射特定音量类型的音频流用途类型。 |
| int32_t *minVolumeLevel | [out] 用于接收返回的最小音量等级。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 函数执行成功。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result)参数volumeManager或minVolumeLevel为空指针，或usage是无效值。</li> <li>[AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) 系统处理错误。</li> </ul> |

### OH_AudioVolumeManager_GetVolumeByUsage()

```c
OH_AudioCommon_Result OH_AudioVolumeManager_GetVolumeByUsage(OH_AudioVolumeManager *volumeManager, OH_AudioStream_Usage usage, int32_t *volumeLevel)
```

**描述：**

获取指定用途类型音频流的系统音量等级。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioVolumeManager](capi-ohaudio-oh-audiovolumemanager.md) *volumeManager | [in] 指向通过[OH_AudioManager_GetAudioVolumeManager](capi-native-audio-volume-manager-h.md#oh_audiomanager_getaudiovolumemanager)获取的音量管理器实例。 |
| [OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage) usage | [in] 用于映射特定音量类型的音频流用途类型。 |
| int32_t *volumeLevel | [out] 用于接收返回的系统音量等级。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 函数执行成功。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result)参数volumeManager或volumeLevel为空指针，或usage是无效值。</li> <li>[AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) 系统处理错误。</li> </ul> |

### OH_AudioVolumeManager_IsMuteByUsage()

```c
OH_AudioCommon_Result OH_AudioVolumeManager_IsMuteByUsage(OH_AudioVolumeManager *volumeManager, OH_AudioStream_Usage usage, bool *muted)
```

**描述：**

检查指定用途类型的音频流是否处于静音状态。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioVolumeManager](capi-ohaudio-oh-audiovolumemanager.md) *volumeManager | [in] 指向通过[OH_AudioManager_GetAudioVolumeManager](capi-native-audio-volume-manager-h.md#oh_audiomanager_getaudiovolumemanager)获取的音量管理器实例。 |
| [OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage) usage | [in] 用于映射特定音量类型的音频流用途类型。 |
| bool *muted | [out] 用于接收返回的音频流是否静音。true表示静音，false表示未静音。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 函数执行成功。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) 参数volumeManager或muted为空指针，或usage是无效值。</li> <li>[AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) 系统处理错误。</li> </ul> |

### OH_AudioVolumeManager_RegisterStreamVolumeChangeCallback()

```c
OH_AudioCommon_Result OH_AudioVolumeManager_RegisterStreamVolumeChangeCallback(OH_AudioVolumeManager *volumeManager, OH_AudioStream_Usage usage, OH_AudioVolumeManager_OnStreamVolumeChangeCallback callback, void *userData)
```

**描述：**

注册音频流音量变化回调函数。 <br>多次注册同一个OH_AudioStream_Usage的变化回调时，系统会保存所有不同的回调函数，在其音量变化时遍历触发。 同一个回调函数，也只能用于注册一个OH_AudioStream_Usage的变化回调。 <br>若不再需要监听音频流音量变化，可调用[OH_AudioVolumeManager_UnregisterStreamVolumeChangeCallback](capi-native-audio-volume-manager-h.md#oh_audiovolumemanager_unregisterstreamvolumechangecallback)取消注册。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioVolumeManager](capi-ohaudio-oh-audiovolumemanager.md) *volumeManager | [in] 指向通过[OH_AudioManager_GetAudioVolumeManager](capi-native-audio-volume-manager-h.md#oh_audiomanager_getaudiovolumemanager)获取的音量管理器实例。 |
| [OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage) usage | [in] 用于映射特定音量类型的音频流用途类型。 |
| [OH_AudioVolumeManager_OnStreamVolumeChangeCallback](capi-native-audio-volume-manager-h.md#oh_audiovolumemanager_onstreamvolumechangecallback) callback | [in] 监听的音频流音量发生变化时，将调用此回调函数。 |
| void *userData | [in] 用户自定义数据指针，回调函数触发时会携带。若无需传递数据，可传入空指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 函数执行成功。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result)参数volumeManager、usage或callback为空指针，或usage是无效值。</li> <li>[AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) 系统处理错误。</li> </ul> |

### OH_AudioVolumeManager_UnregisterStreamVolumeChangeCallback()

```c
OH_AudioCommon_Result OH_AudioVolumeManager_UnregisterStreamVolumeChangeCallback(OH_AudioVolumeManager *volumeManager, OH_AudioVolumeManager_OnStreamVolumeChangeCallback callback)
```

**描述：**

取消注册音频流音量变化回调函数。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioVolumeManager](capi-ohaudio-oh-audiovolumemanager.md) *volumeManager | [in] 指向通过[OH_AudioManager_GetAudioVolumeManager](capi-native-audio-volume-manager-h.md#oh_audiomanager_getaudiovolumemanager)获取的音量管理器实例。 |
| [OH_AudioVolumeManager_OnStreamVolumeChangeCallback](capi-native-audio-volume-manager-h.md#oh_audiovolumemanager_onstreamvolumechangecallback) callback | [in] 需要取消注册的回调函数， 该函数应与[OH_AudioVolumeManager_RegisterStreamVolumeChangeCallback](capi-native-audio-volume-manager-h.md#oh_audiovolumemanager_registerstreamvolumechangecallback)注册时的回调函数一致。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 函数执行成功。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) 参数volumeManager或callback为空指针。</li> <li>[AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) 系统处理错误。</li> </ul> |

### OH_AudioVolumeManager_GetRingerMode()

```c
OH_AudioCommon_Result OH_AudioVolumeManager_GetRingerMode(OH_AudioVolumeManager *volumeManager, OH_AudioRingerMode *ringerMode)
```

**描述：**

获取系统当前的铃声模式。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioVolumeManager](capi-ohaudio-oh-audiovolumemanager.md) *volumeManager | [in] 指向通过[OH_AudioManager_GetAudioVolumeManager](capi-native-audio-volume-manager-h.md#oh_audiomanager_getaudiovolumemanager)获取的音量管理器实例。 |
| [OH_AudioRingerMode](capi-native-audio-common-h.md#oh_audioringermode) *ringerMode | [out] 用于接收返回的铃声模式。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 函数执行成功。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) 参数volumeManager或ringerMode为空指针。</li> <li>[AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) 系统处理错误。</li> </ul> |

### OH_AudioVolumeManager_RegisterRingerModeChangeCallback()

```c
OH_AudioCommon_Result OH_AudioVolumeManager_RegisterRingerModeChangeCallback(OH_AudioVolumeManager *volumeManager, OH_AudioVolumeManager_OnRingerModeChangeCallback callback, void *userData)
```

**描述：**

注册铃声模式变化回调函数。 <br>多次注册时，系统会保存所有不同的回调函数，在铃声模式变化时遍历触发。 <br>若不再需要监听铃声模式变化，可调用[OH_AudioVolumeManager_UnregisterRingerModeChangeCallback](capi-native-audio-volume-manager-h.md#oh_audiovolumemanager_unregisterringermodechangecallback)取消注册。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioVolumeManager](capi-ohaudio-oh-audiovolumemanager.md) *volumeManager | [in] 指向通过[OH_AudioManager_GetAudioVolumeManager](capi-native-audio-volume-manager-h.md#oh_audiomanager_getaudiovolumemanager)获取的音量管理器实例。 |
| [OH_AudioVolumeManager_OnRingerModeChangeCallback](capi-native-audio-volume-manager-h.md#oh_audiovolumemanager_onringermodechangecallback) callback | [in] 当监听到铃声模式发生变化时，将调用此回调函数。 |
| void *userData | [in] 用户自定义数据指针，回调函数触发时会携带。若无需传递数据，可传入空指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 函数执行成功。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) 参数volumeManager或callback为空指针。</li> <li>[AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) 系统处理错误。</li> </ul> |

### OH_AudioVolumeManager_UnregisterRingerModeChangeCallback()

```c
OH_AudioCommon_Result OH_AudioVolumeManager_UnregisterRingerModeChangeCallback(OH_AudioVolumeManager *volumeManager, OH_AudioVolumeManager_OnRingerModeChangeCallback callback)
```

**描述：**

取消注册铃声模式变化回调函数。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioVolumeManager](capi-ohaudio-oh-audiovolumemanager.md) *volumeManager | [in] 指向通过[OH_AudioManager_GetAudioVolumeManager](capi-native-audio-volume-manager-h.md#oh_audiomanager_getaudiovolumemanager)获取的音量管理器实例。 |
| [OH_AudioVolumeManager_OnRingerModeChangeCallback](capi-native-audio-volume-manager-h.md#oh_audiovolumemanager_onringermodechangecallback) callback | [in] 需要取消注册的回调函数，该函数应与[OH_AudioVolumeManager_RegisterRingerModeChangeCallback](capi-native-audio-volume-manager-h.md#oh_audiovolumemanager_registerringermodechangecallback) 注册时的回调函数一致。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 函数执行成功。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) 参数volumeManager或callback为空指针。</li> <li>[AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) 系统处理错误。</li> </ul> |


