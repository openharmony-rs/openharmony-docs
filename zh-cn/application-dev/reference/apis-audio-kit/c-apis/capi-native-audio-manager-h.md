# native_audio_manager.h

## 概述

本文件提供音频基础管理功能的接口。 <br>当前支持音频场景信息的查询以及音频场景变化的监听。

**库：** libohaudio.so

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 12

**相关模块：** [OHAudio](capi-ohaudio.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_AudioManager](capi-ohaudio-oh-audiomanager.md) | OH_AudioManager | 声明音频管理结构体，该结构体用于调用音频基础管理功能接口，如查询系统音频场景。 |

### 函数

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [typedef void (\*OH_AudioManager_OnAudioSceneChangeCallback)(void *userData, OH_AudioScene scene)](#oh_audiomanager_onaudioscenechangecallback) | OH_AudioManager_OnAudioSceneChangeCallback | 音频场景变化回调函数的原型定义，用于[OH_AudioManager_RegisterAudioSceneChangeCallback](capi-native-audio-manager-h.md#oh_audiomanager_registeraudioscenechangecallback)接口。 |
| [OH_AudioCommon_Result OH_GetAudioManager(OH_AudioManager **audioManager)](#oh_getaudiomanager) | - | 获取音频基础管理器实例，该实例为单例，用于调用音频基础管理功能接口。 |
| [OH_AudioCommon_Result OH_GetAudioScene(OH_AudioManager* manager, OH_AudioScene *scene)](#oh_getaudioscene) | - | 获取音频场景。 <br>音频场景主要用于表示音频通话相关的系统状态，调用者可通过音频场景识别系统是否处于语音通话或通话响铃状态。 |
| [OH_AudioCommon_Result OH_AudioManager_RegisterAudioSceneChangeCallback(OH_AudioManager *manager, OH_AudioManager_OnAudioSceneChangeCallback callback, void *userData)](#oh_audiomanager_registeraudioscenechangecallback) | - | 注册音频场景变化回调函数。 <br>音频场景主要用于表示音频通话相关的系统状态，调用者可通过此接口监听系统是否进入或退出通话状态。 <br>若不再需要监听音频场景变化，可调用[OH_AudioManager_UnregisterAudioSceneChangeCallback](capi-native-audio-manager-h.md#oh_audiomanager_unregisteraudioscenechangecallback)取消注册。 |
| [OH_AudioCommon_Result OH_AudioManager_UnregisterAudioSceneChangeCallback(OH_AudioManager *manager, OH_AudioManager_OnAudioSceneChangeCallback callback)](#oh_audiomanager_unregisteraudioscenechangecallback) | - | 取消注册音频场景变化回调函数。 |

### 变量

| 名称 | 描述 |
| -- | -- |
| void (*OH_AudioManager_OnAudioSceneChangeCallback) ( void *userData, OH_AudioScene scene ) | 音频场景变化回调函数的原型定义，用于[OH_AudioManager_RegisterAudioSceneChangeCallback](capi-native-audio-manager-h.md#oh_audiomanager_registeraudioscenechangecallback)接口。<br>**起始版本：** 20<br>**系统能力：** SystemCapability.Multimedia.Audio.Core |

## 函数说明

### OH_AudioManager_OnAudioSceneChangeCallback()

```c
typedef void (*OH_AudioManager_OnAudioSceneChangeCallback)(void *userData, OH_AudioScene scene)
```

**描述：**

音频场景变化回调函数的原型定义，用于[OH_AudioManager_RegisterAudioSceneChangeCallback](capi-native-audio-manager-h.md#oh_audiomanager_registeraudioscenechangecallback)接口。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| void *userData | 指向开发者在[OH_AudioManager_RegisterAudioSceneChangeCallback](capi-native-audio-manager-h.md#oh_audiomanager_registeraudioscenechangecallback)接口传入的userData数据。 |
| [OH_AudioScene](capi-native-audio-common-h.md#oh_audioscene) scene | 变化后的音频场景。 |

### OH_GetAudioManager()

```c
OH_AudioCommon_Result OH_GetAudioManager(OH_AudioManager **audioManager)
```

**描述：**

获取音频基础管理器实例，该实例为单例，用于调用音频基础管理功能接口。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioManager](capi-ohaudio-oh-audiomanager.md) **audioManager | [out] 指向OH_AudioManager指针的地址，用于接收获取的音频管理器实例。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 函数执行成功。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) 参数audioManager为空指针。</li> </ul> |

### OH_GetAudioScene()

```c
OH_AudioCommon_Result OH_GetAudioScene(OH_AudioManager* manager, OH_AudioScene *scene)
```

**描述：**

获取音频场景。 <br>音频场景主要用于表示音频通话相关的系统状态，调用者可通过音频场景识别系统是否处于语音通话或通话响铃状态。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| audioManager | the [OH_AudioManager](capi-ohaudio-oh-audiomanager.md) handle received from [OH_GetAudioManager](capi-native-audio-manager-h.md#oh_getaudiomanager). |
| [OH_AudioScene](capi-native-audio-common-h.md#oh_audioscene) *scene | [out] 用于接收获取的音频场景。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 函数执行成功。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) <br>1. 参数manager为空指针；<br>2. 参数scene为空指针。</li> </ul> |

### OH_AudioManager_RegisterAudioSceneChangeCallback()

```c
OH_AudioCommon_Result OH_AudioManager_RegisterAudioSceneChangeCallback(OH_AudioManager *manager, OH_AudioManager_OnAudioSceneChangeCallback callback, void *userData)
```

**描述：**

注册音频场景变化回调函数。 <br>音频场景主要用于表示音频通话相关的系统状态，调用者可通过此接口监听系统是否进入或退出通话状态。 <br>若不再需要监听音频场景变化，可调用[OH_AudioManager_UnregisterAudioSceneChangeCallback](capi-native-audio-manager-h.md#oh_audiomanager_unregisteraudioscenechangecallback)取消注册。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioManager](capi-ohaudio-oh-audiomanager.md) *manager | [in] 指向通过[OH_GetAudioManager](capi-native-audio-manager-h.md#oh_getaudiomanager)获取的音频管理器实例。 |
| [OH_AudioManager_OnAudioSceneChangeCallback](capi-native-audio-manager-h.md#oh_audiomanager_onaudioscenechangecallback) callback | [in] 当音频场景变化时，将触发此回调函数。 |
| void *userData | [in] 用户自定义数据指针，回调函数触发时会携带。若无需传递数据，可传入空指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 函数执行成功。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) <br>1. 参数manager为空指针；<br>2. 参数callback为空指针。</li> <li>[AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) 系统错误，主要为系统服务异常。</li> </ul> |

### OH_AudioManager_UnregisterAudioSceneChangeCallback()

```c
OH_AudioCommon_Result OH_AudioManager_UnregisterAudioSceneChangeCallback(OH_AudioManager *manager, OH_AudioManager_OnAudioSceneChangeCallback callback)
```

**描述：**

取消注册音频场景变化回调函数。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioManager](capi-ohaudio-oh-audiomanager.md) *manager | [in] 指向通过[OH_GetAudioManager](capi-native-audio-manager-h.md#oh_getaudiomanager)获取的音频管理器实例。 |
| [OH_AudioManager_OnAudioSceneChangeCallback](capi-native-audio-manager-h.md#oh_audiomanager_onaudioscenechangecallback) callback | [in] 指向[OH_AudioManager_RegisterAudioSceneChangeCallback](capi-native-audio-manager-h.md#oh_audiomanager_registeraudioscenechangecallback)传入的回调函数，用于取消注册。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 函数执行成功。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) <br>1. 参数manager为空指针；<br>2. 参数callback为空指针。</li> <li>[AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) 系统错误，主要为系统服务异常。</li> </ul> |


