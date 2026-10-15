# native_audio_resource_manager.h

## 概述

本文件提供音频资源管理功能的接口。 <br>音频播放或录制都需要持续对音频数据进行处理，消耗系统CPU资源。 当处理性能不足时，会出现杂音或卡顿问题，因此系统提供资源管理接口帮助应用开发者优化音频处理线程的性能。 <br>音频资源管理主要通过音频工作组实现。音频工作组是一组音频数据处理线程集合， 开发者通过接口将应用内音频数据处理相关线程添加到音频工作组，合理设置数据处理的预期完成时间，系统会平衡功耗和性能， 按照工作组内线程负载分配不同CPU资源，保障数据按时处理完成。 <br>音频工作组必须配合音频播放业务使用，支持的音频场景包括音乐、视频、听书、导航和语音通话。 没有音频流播放时，系统不会对线程性能进行优化。 <br>音频工作组的使用数量也存在约束，每个应用进程最多创建2个工作组，且进程内所有工作组总共最多添加4个处理线程。

**库：** libohaudio.so

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 20

**相关模块：** [OHAudio](capi-ohaudio.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_AudioResourceManager](capi-ohaudio-oh-audioresourcemanager.md) | OH_AudioResourceManager | 声明音频资源管理结构体，该结构体用于调用音频资源管理和线程调度优化功能接口。 |
| [OH_AudioWorkgroup](capi-ohaudio-oh-audioworkgroup.md) | OH_AudioWorkgroup | 声明音频工作组结构体，该结构体表示一组用于协同处理音频数据任务的线程， 系统会以工作组为单元管理其使用的CPU资源。 |

### 函数

| 名称 | 描述 |
| -- | -- |
| [OH_AudioCommon_Result OH_AudioManager_GetAudioResourceManager(OH_AudioResourceManager **resourceManager)](#oh_audiomanager_getaudioresourcemanager) | 获取音频资源管理器实例，该实例为单例，用于调用音频资源管理功能接口。 |
| [OH_AudioCommon_Result OH_AudioResourceManager_CreateWorkgroup(OH_AudioResourceManager *resourceManager, const char *name, OH_AudioWorkgroup **group)](#oh_audioresourcemanager_createworkgroup) | 创建音频工作组。 <br>每个应用进程最多创建2个音频工作组，不再使用的音频工作组， 及时通过[OH_AudioResourceManager_ReleaseWorkgroup](capi-native-audio-resource-manager-h.md#oh_audioresourcemanager_releaseworkgroup)接口释放。 |
| [OH_AudioCommon_Result OH_AudioResourceManager_ReleaseWorkgroup(OH_AudioResourceManager *resourceManager, OH_AudioWorkgroup *group)](#oh_audioresourcemanager_releaseworkgroup) | 释放音频工作组。 |
| [OH_AudioCommon_Result OH_AudioWorkgroup_AddCurrentThread(OH_AudioWorkgroup *group, int32_t *tokenId)](#oh_audioworkgroup_addcurrentthread) | 添加当前线程到音频工作组。 <br>添加完成后，系统会为此线程分配一个标识符，可在[OH_AudioWorkgroup_RemoveThread](capi-native-audio-resource-manager-h.md#oh_audioworkgroup_removethread)接口通过此标识符移除线程。 <br>添加到工作组的线程将参与工作组的统一调度，系统会根据工作组的任务时间要求动态调整线程的CPU资源分配。 <br>进程内所有工作组总共最多添加4个处理线程。 |
| [OH_AudioCommon_Result OH_AudioWorkgroup_RemoveThread(OH_AudioWorkgroup *group, int32_t tokenId)](#oh_audioworkgroup_removethread) | 从音频工作组移除指定线程。 |
| [OH_AudioCommon_Result OH_AudioWorkgroup_Start(OH_AudioWorkgroup *group, uint64_t startTime, uint64_t deadlineTime)](#oh_audioworkgroup_start) | 通知系统音频工作组开始执行任务。此接口应在每个周期的音频数据处理前调用， 处理完成后需要调用[OH_AudioWorkgroup_Stop](capi-native-audio-resource-manager-h.md#oh_audioworkgroup_stop)。 <br>系统会基于任务启动时间和预期完成时间，对音频工作组内的所有线程进行优先级调整和CPU资源分配。 <br>请合理设置启动和预期完成时间，如果时间间隔过短，系统无法确保音频任务能够及时完成。 |
| [OH_AudioCommon_Result OH_AudioWorkgroup_Stop(OH_AudioWorkgroup *group)](#oh_audioworkgroup_stop) | 通知系统音频工作组任务执行完成。此接口应在每个周期的音频数据处理完成后调用。 |

## 函数说明

### OH_AudioManager_GetAudioResourceManager()

```c
OH_AudioCommon_Result OH_AudioManager_GetAudioResourceManager(OH_AudioResourceManager **resourceManager)
```

**描述：**

获取音频资源管理器实例，该实例为单例，用于调用音频资源管理功能接口。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioResourceManager](capi-ohaudio-oh-audioresourcemanager.md) **resourceManager | [out] 用于接收获取的音频资源管理器实例。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 函数执行成功。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) 参数resourceManager为空指针。</li> </ul> |

### OH_AudioResourceManager_CreateWorkgroup()

```c
OH_AudioCommon_Result OH_AudioResourceManager_CreateWorkgroup(OH_AudioResourceManager *resourceManager, const char *name, OH_AudioWorkgroup **group)
```

**描述：**

创建音频工作组。 <br>每个应用进程最多创建2个音频工作组，不再使用的音频工作组， 及时通过[OH_AudioResourceManager_ReleaseWorkgroup](capi-native-audio-resource-manager-h.md#oh_audioresourcemanager_releaseworkgroup)接口释放。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioResourceManager](capi-ohaudio-oh-audioresourcemanager.md) *resourceManager | [in] 指向[OH_AudioManager_GetAudioResourceManager](capi-native-audio-resource-manager-h.md#oh_audiomanager_getaudioresourcemanager)创建的 音频资源管理器实例OH_AudioResourceManager。 |
| const char *name | [in] 创建的音频工作组名称。 |
| [OH_AudioWorkgroup](capi-ohaudio-oh-audioworkgroup.md) **group | [out] 用于接收创建的音频工作组实例。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 函数执行成功。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) 1. 参数resourceManager为空指针；2. 参数name为空指针；3. 参数group为空指针。</li> <li>[AUDIOCOMMON_RESULT_ERROR_NO_MEMORY](capi-native-audio-common-h.md#oh_audiocommon_result) 系统资源不足。</li> <li>[AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) 系统处理错误。</li> </ul> |

### OH_AudioResourceManager_ReleaseWorkgroup()

```c
OH_AudioCommon_Result OH_AudioResourceManager_ReleaseWorkgroup(OH_AudioResourceManager *resourceManager, OH_AudioWorkgroup *group)
```

**描述：**

释放音频工作组。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioResourceManager](capi-ohaudio-oh-audioresourcemanager.md) *resourceManager | [in] 指向[OH_AudioManager_GetAudioResourceManager](capi-native-audio-resource-manager-h.md#oh_audiomanager_getaudioresourcemanager)创建的音频资源管理器实例。 |
| [OH_AudioWorkgroup](capi-ohaudio-oh-audioworkgroup.md) *group | [in] 指向[OH_AudioResourceManager_CreateWorkgroup](capi-native-audio-resource-manager-h.md#oh_audioresourcemanager_createworkgroup)创建的音频工作组实例。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 函数执行成功。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) 1. 参数resourceManager为空指针；2. 参数group为空指针。</li> <li>[AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) 系统处理错误。</li> </ul> |

### OH_AudioWorkgroup_AddCurrentThread()

```c
OH_AudioCommon_Result OH_AudioWorkgroup_AddCurrentThread(OH_AudioWorkgroup *group, int32_t *tokenId)
```

**描述：**

添加当前线程到音频工作组。 <br>添加完成后，系统会为此线程分配一个标识符，可在[OH_AudioWorkgroup_RemoveThread](capi-native-audio-resource-manager-h.md#oh_audioworkgroup_removethread)接口通过此标识符移除线程。 <br>添加到工作组的线程将参与工作组的统一调度，系统会根据工作组的任务时间要求动态调整线程的CPU资源分配。 <br>进程内所有工作组总共最多添加4个处理线程。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioWorkgroup](capi-ohaudio-oh-audioworkgroup.md) *group | [in] 指向[OH_AudioResourceManager_CreateWorkgroup](capi-native-audio-resource-manager-h.md#oh_audioresourcemanager_createworkgroup)创建的音频工作组实例。 |
| int32_t *tokenId | [out] 用于接收系统为添加到音频工作组的线程分配的标识符。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 函数执行成功。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) 1. 参数group为空指针；2. 参数tokenId为空指针。</li> <li>[AUDIOCOMMON_RESULT_ERROR_NO_MEMORY](capi-native-audio-common-h.md#oh_audiocommon_result) 系统资源不足。</li> <li>[AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) 系统处理错误。</li> </ul> |

### OH_AudioWorkgroup_RemoveThread()

```c
OH_AudioCommon_Result OH_AudioWorkgroup_RemoveThread(OH_AudioWorkgroup *group, int32_t tokenId)
```

**描述：**

从音频工作组移除指定线程。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioWorkgroup](capi-ohaudio-oh-audioworkgroup.md) *group | [in] 指向[OH_AudioResourceManager_CreateWorkgroup](capi-native-audio-resource-manager-h.md#oh_audioresourcemanager_createworkgroup)创建的音频工作组实例。 |
| int32_t tokenId | [in] 待移除线程的标识符，标识符是从[OH_AudioWorkgroup_AddCurrentThread](capi-native-audio-resource-manager-h.md#oh_audioworkgroup_addcurrentthread)接口获取的。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 函数执行成功。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) 1. 参数group为空指针；2. 参数tokenId无效。</li> <li>[AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) 系统处理错误。</li> </ul> |

### OH_AudioWorkgroup_Start()

```c
OH_AudioCommon_Result OH_AudioWorkgroup_Start(OH_AudioWorkgroup *group, uint64_t startTime, uint64_t deadlineTime)
```

**描述：**

通知系统音频工作组开始执行任务。此接口应在每个周期的音频数据处理前调用， 处理完成后需要调用[OH_AudioWorkgroup_Stop](capi-native-audio-resource-manager-h.md#oh_audioworkgroup_stop)。 <br>系统会基于任务启动时间和预期完成时间，对音频工作组内的所有线程进行优先级调整和CPU资源分配。 <br>请合理设置启动和预期完成时间，如果时间间隔过短，系统无法确保音频任务能够及时完成。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioWorkgroup](capi-ohaudio-oh-audioworkgroup.md) *group | [in] 指向[OH_AudioResourceManager_CreateWorkgroup](capi-native-audio-resource-manager-h.md#oh_audioresourcemanager_createworkgroup)创建的音频工作组实例。 |
| uint64_t startTime | [in] 当前音频任务的启动时间点，使用UTC时间戳，单位为ms。 |
| uint64_t deadlineTime | [in] 当前音频任务的预期完成时间，使用UTC时间戳，单位为ms。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 函数执行成功。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) 1. 参数group为空指针；2. 参数startTime无效；3. 参数deadlineTime无效。</li> <li>[AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) 系统处理错误。</li> </ul> |

### OH_AudioWorkgroup_Stop()

```c
OH_AudioCommon_Result OH_AudioWorkgroup_Stop(OH_AudioWorkgroup *group)
```

**描述：**

通知系统音频工作组任务执行完成。此接口应在每个周期的音频数据处理完成后调用。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioWorkgroup](capi-ohaudio-oh-audioworkgroup.md) *group | [in] 指向[OH_AudioResourceManager_CreateWorkgroup](capi-native-audio-resource-manager-h.md#oh_audioresourcemanager_createworkgroup)创建的音频工作组实例。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 函数执行成功。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) 参数group为空指针。</li> <li>[AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) 系统处理错误。</li> </ul> |


