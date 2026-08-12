# native_audio_accessory_manager.h
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @hao-liangfei; @zhanganxiang-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

## 概述

声明音频配件管理相关的接口。可用于管理音频配件的创建、连接、断开和销毁等功能。

**引用文件：** <ohaudio/native_audio_accessory_manager.h>

**库：** libohaudio.so

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 26.0.0

**相关模块：** [OHAudio](capi-ohaudio.md)

## 汇总

### 函数指针

| 名称 | 描述 |
| -- | -- |
| [OH_AudioAccessory_SetNoiseReductionCallback](#oh_audioaccessory_setnoisereductioncallback) | 音频配件降噪模式发生变更时触发的回调。 |

### 函数

| 名称 | 描述 |
| -- | -- |
| [OH_AudioManager_GetAccessoryManager](#oh_audiomanager_getaccessorymanager) | 获取音频配件管理器实例。 |
| [OH_AudioAccessoryManager_CreateInput](#oh_audioaccessorymanager_createinput) | 创建音频配件实例并注册其能力。 |
| [OH_AudioAccessoryManager_SetAssociatedMacAddresses](#oh_audioaccessorymanager_setassociatedmacaddresses) | 设置与主音频配件组合使用的副配件MAC地址列表。 |
| [OH_AudioAccessoryManager_RegisterNoiseReductionCapability](#oh_audioaccessorymanager_registernoisereductioncapability) | 注册音频配件的降噪能力。 |
| [OH_AudioAccessoryManager_SetNoiseReductionMode](#oh_audioaccessorymanager_setnoisereductionmode) | 同步音频配件当前降噪模式。 |
| [OH_AudioAccessoryManager_Connected](#oh_audioaccessorymanager_connected) | 将音频配件连接到音频系统。 |
| [OH_AudioAccessoryManager_Disconnected](#oh_audioaccessorymanager_disconnected) | 将音频配件从音频系统断开连接。 |
| [OH_AudioAccessoryManager_Destroy](#oh_audioaccessorymanager_destroy) | 销毁音频配件实例。 |

## 函数指针说明

### OH_AudioAccessory_SetNoiseReductionCallback

```c
typedef bool (*OH_AudioAccessory_SetNoiseReductionCallback)(OH_AudioAccessory *accessory, OH_AudioNoiseReductionMode mode)
```

**描述**

当配件的降噪模式发生变更时触发，此回调可以在配件连接后的任意时间触发。

**起始版本：** 26.0.0

**参数**

| 名称 | 描述 |
| -- | -- |
| OH_AudioAccessory *accessory | 音频配件。 |
| [OH_AudioNoiseReductionMode](capi-native-audio-common-h.md#oh_audionoisereductionmode) mode | 配件当前的降噪模式。 |

**返回值**

返回 **true** 表示请求的模式处理成功；返回 **false** 表示处理失败。

## 函数说明

### OH_AudioManager_GetAccessoryManager()

```c
OH_AudioCommon_Result OH_AudioManager_GetAccessoryManager(OH_AudioAccessoryManager **outManager)
```

**描述**

获取音频配件管理器实例。返回的句柄由系统管理，调用方不得释放。

**起始版本：** 26.0.0

**返回值**

[OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result)：**AUDIOCOMMON_RESULT_SUCCESS** 表示执行成功；**AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM** 表示 **outManager** 为空。

### OH_AudioAccessoryManager_CreateInput()

```c
OH_AudioCommon_Result OH_AudioAccessoryManager_CreateInput(OH_AudioAccessoryManager *manager, const OH_AudioAccessoryInfo *info, const OH_AudioAccessoryCapabilities *capabilities, OH_AudioAccessory_OpenInputStreamCallback openInputStream, OH_AudioAccessory **outOwnedAccessory)
```

**描述**

创建音频配件实例并注册其能力。此函数仅用于创建音频配件实例，不会创建任何输入流。当应用请求从该音频配件采集音频时，系统会触发 **openInputStream** 回调函数。在一个音频配件的生命周期内，输入流可能被创建和释放多次。

**起始版本：** 26.0.0

**返回值**

[OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result)：**AUDIOCOMMON_RESULT_SUCCESS** 表示执行成功；**AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM** 表示参数无效，包括 **info**、**capabilities**、**openInputStream**、**outOwnedAccessory** 为空，信息未全部填写，或 **outOwnedAccessory** 已通过该接口创建；**AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE** 表示 **manager** 未通过 [OH_AudioManager_GetAccessoryManager](#oh_audiomanager_getaccessorymanager) 初始化。

### OH_AudioAccessoryManager_SetAssociatedMacAddresses()

```c
OH_AudioCommon_Result OH_AudioAccessoryManager_SetAssociatedMacAddresses(OH_AudioAccessoryManager *manager, OH_AudioAccessory *accessory, const char **macAddresses, uint32_t count)
```

**描述**

设置与主音频配件组合使用的副配件MAC地址列表。此函数适用于多配件组合场景（如二合一、四合一），支持在配件创建后初始化副配件列表，并在副配件替换或断开连接时覆盖旧的MAC列表。录音期间可安全调用。**count** 为0时，**macAddresses** 可为空，表示清除副配件MAC列表。同一数组中的重复地址会被忽略。

**起始版本：** 26.0.0

**返回值**

[OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result)：**AUDIOCOMMON_RESULT_SUCCESS** 表示执行成功；**AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM** 表示参数无效，包括 **manager** 为空、**manager** 未初始化、**accessory** 为空，或 **macAddresses** 传入的个数与 **count** 不一致；**AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE** 表示 **accessory** 未通过 [OH_AudioAccessoryManager_CreateInput](#oh_audioaccessorymanager_createinput) 创建。

### OH_AudioAccessoryManager_RegisterNoiseReductionCapability()

```c
OH_AudioCommon_Result OH_AudioAccessoryManager_RegisterNoiseReductionCapability(OH_AudioAccessoryManager *manager, OH_AudioAccessory *accessory, const OH_AudioAccessoryNoiseReductionCapability *capability, OH_AudioAccessory_SetNoiseReductionCallback onNoiseReduction)
```

**描述**

注册音频配件的降噪能力。如果配件不支持动态模式切换，回调可以为空。

**起始版本：** 26.0.0

**返回值**

[OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result)：**AUDIOCOMMON_RESULT_SUCCESS** 表示执行成功；**AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM** 表示参数无效，包括 **manager** 为空、**manager** 未初始化、**accessory** 为空、**capability** 为空，或 **supportedModes** 为空或 **supportedModeCount** 为0；**AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE** 表示 **accessory** 未通过 [OH_AudioAccessoryManager_CreateInput](#oh_audioaccessorymanager_createinput) 创建。

### OH_AudioAccessoryManager_SetNoiseReductionMode()

```c
OH_AudioCommon_Result OH_AudioAccessoryManager_SetNoiseReductionMode(OH_AudioAccessoryManager *manager, OH_AudioAccessory *accessory, OH_AudioNoiseReductionMode mode)
```

**描述**

由配件关联的服务或应用调用，将配件当前降噪模式更新到系统。通常在通过硬件按钮或配套应用更改降噪模式时使用，以确保系统侧的降噪模式与配件实际降噪模式保持一致。

**起始版本：** 26.0.0

**返回值**

[OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result)：**AUDIOCOMMON_RESULT_SUCCESS** 表示执行成功；**AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM** 表示 **accessory** 为空；**AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE** 表示 **accessory** 未创建或未连接；**AUDIOCOMMON_RESULT_ERROR_UNSUPPORTED** 表示设置的降噪模式未通过 [OH_AudioAccessoryManager_RegisterNoiseReductionCapability](#oh_audioaccessorymanager_registernoisereductioncapability) 注册。

### OH_AudioAccessoryManager_Connected()

```c
OH_AudioCommon_Result OH_AudioAccessoryManager_Connected(OH_AudioAccessoryManager *manager, OH_AudioAccessory *accessory)
```

**描述**

将音频配件连接到音频系统。调用此函数前，必须通过 [OH_AudioManager_GetAccessoryManager](#oh_audiomanager_getaccessorymanager) 获取音频配件管理器实例，并通过 [OH_AudioAccessoryManager_CreateInput](#oh_audioaccessorymanager_createinput) 创建 **accessory** 实例。

建议音频配件管理程序优先接入智慧生活应用，为用户提供设备发现与连接体验的一致性；若以独立音频配件管理应用方式接入，需要申请ACL权限 **ohos.permission.MANAGE_AUDIO_ACCESSORY**。

**所需权限：** ohos.permission.MANAGE_AUDIO_ACCESSORY

**起始版本：** 26.0.0

**返回值**

[OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result)：**AUDIOCOMMON_RESULT_SUCCESS** 表示执行成功；**AUDIOCOMMON_RESULT_ERROR_PERMISSION_DENIED** 表示调用方没有 **ohos.permission.MANAGE_AUDIO_ACCESSORY** 权限；**AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM** 表示参数无效，包括 **manager** 为空、**manager** 未初始化，或 **accessory** 为空；**AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE** 表示 **accessory** 未创建或已连接；**AUDIOCOMMON_RESULT_ERROR_SYSTEM** 表示音频服务进程死亡。

### OH_AudioAccessoryManager_Disconnected()

```c
OH_AudioCommon_Result OH_AudioAccessoryManager_Disconnected(OH_AudioAccessoryManager *manager, OH_AudioAccessory *accessory)
```

**描述**

将音频配件从音频系统断开连接。

**所需权限：** ohos.permission.MANAGE_AUDIO_ACCESSORY

**起始版本：** 26.0.0

**返回值**

[OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result)：**AUDIOCOMMON_RESULT_SUCCESS** 表示执行成功；**AUDIOCOMMON_RESULT_ERROR_PERMISSION_DENIED** 表示调用方没有 **ohos.permission.MANAGE_AUDIO_ACCESSORY** 权限；**AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM** 表示 **accessory** 为空；**AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE** 表示 **accessory** 未连接；**AUDIOCOMMON_RESULT_ERROR_SYSTEM** 表示音频服务进程死亡。

### OH_AudioAccessoryManager_Destroy()

```c
OH_AudioCommon_Result OH_AudioAccessoryManager_Destroy(OH_AudioAccessoryManager *manager, OH_AudioAccessory *accessory)
```

**描述**

销毁音频配件实例。销毁前必须先断开配件连接。

**起始版本：** 26.0.0

**返回值**

[OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result)：**AUDIOCOMMON_RESULT_SUCCESS** 表示执行成功；**AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM** 表示参数无效，包括 **manager** 为空、**manager** 未初始化，或 **accessory** 为空；**AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE** 表示 **accessory** 未断开连接。
