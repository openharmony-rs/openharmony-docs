# native_audio_accessory_manager.h
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @caixuejiang; @hao-liangfei; @zhanganxiang-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

## 概述

声明音频配件管理器相关接口。可用于创建输入音频配件、上报关联MAC地址、注册降噪能力、连接或断开配件，以及销毁配件句柄。

**引用文件：** <ohaudio/native_audio_accessory_manager.h>

**库：** libohaudio.so

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 26.0.0

**相关模块：** [OHAudio](capi-ohaudio.md)

## 汇总

### 函数指针

| 名称 | 描述 |
| -- | -- |
| [OH_AudioAccessory_SetNoiseReductionCallback](#oh_audioaccessory_setnoisereductioncallback) | 系统请求变更降噪模式时触发的回调。 |

### 函数

| 名称 | 描述 |
| -- | -- |
| [OH_AudioManager_GetAccessoryManager](#oh_audiomanager_getaccessorymanager) | 获取音频配件管理器实例。 |
| [OH_AudioAccessoryManager_CreateInput](#oh_audioaccessorymanager_createinput) | 创建输入音频配件实例并注册其能力。 |
| [OH_AudioAccessoryManager_SetAssociatedMacAddresses](#oh_audioaccessorymanager_setassociatedmacaddresses) | 设置音频配件的关联MAC地址列表。 |
| [OH_AudioAccessoryManager_RegisterNoiseReductionCapability](#oh_audioaccessorymanager_registernoisereductioncapability) | 注册音频配件的降噪能力。 |
| [OH_AudioAccessoryManager_SetNoiseReductionMode](#oh_audioaccessorymanager_setnoisereductionmode) | 同步音频配件当前降噪模式。 |
| [OH_AudioAccessoryManager_Connected](#oh_audioaccessorymanager_connected) | 将音频配件连接到音频框架。 |
| [OH_AudioAccessoryManager_Disconnected](#oh_audioaccessorymanager_disconnected) | 将音频配件从音频框架断开连接。 |
| [OH_AudioAccessoryManager_Destroy](#oh_audioaccessorymanager_destroy) | 销毁音频配件实例。 |

## 函数指针说明

### OH_AudioAccessory_SetNoiseReductionCallback

```c
typedef bool (*OH_AudioAccessory_SetNoiseReductionCallback)(OH_AudioAccessory *accessory, OH_AudioNoiseReductionMode mode)
```

**描述**

配件连接后，当系统请求更改配件降噪模式时触发。

**起始版本：** 26.0.0

**参数**

| 名称 | 描述 |
| -- | -- |
| [OH_AudioAccessory](capi-native-audio-accessory-common-h.md) *accessory | 音频配件。 |
| [OH_AudioNoiseReductionMode](capi-native-audio-common-h.md#oh_audionoisereductionmode) mode | 要设置的降噪模式。 |

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

创建输入音频配件实例。输入流会在应用实际从该配件录音时由框架延迟创建。调用方必须在打开输入流回调中注册必需的流回调。

框架会对 **accessoryName**、**manufacturer**、**modelNumber**、**macAddress** 和 **streamProperties** 进行深拷贝，调用方可在函数返回后释放这些缓冲区。

**起始版本：** 26.0.0

**返回值**

[OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result)：**AUDIOCOMMON_RESULT_SUCCESS** 表示执行成功；**AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM** 表示任意参数为空；**AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE** 表示管理器未初始化。

### OH_AudioAccessoryManager_SetAssociatedMacAddresses()

```c
OH_AudioCommon_Result OH_AudioAccessoryManager_SetAssociatedMacAddresses(OH_AudioAccessoryManager *manager, OH_AudioAccessory *accessory, const char **macAddresses, uint32_t count)
```

**描述**

替换音频配件的关联MAC地址列表，用于1对2、1对4等多发射器场景。**count** 为0时，**macAddresses** 可为空，表示清除所有关联地址。同一数组中的重复地址会被忽略。

**起始版本：** 26.0.0

**返回值**

[OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result)：**AUDIOCOMMON_RESULT_SUCCESS** 表示执行成功；**AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM** 表示参数无效；**AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE** 表示配件未创建。

### OH_AudioAccessoryManager_RegisterNoiseReductionCapability()

```c
OH_AudioCommon_Result OH_AudioAccessoryManager_RegisterNoiseReductionCapability(OH_AudioAccessoryManager *manager, OH_AudioAccessory *accessory, const OH_AudioAccessoryNoiseReductionCapability *capability, OH_AudioAccessory_SetNoiseReductionCallback onNoiseReduction)
```

**描述**

注册音频配件的降噪能力。如果配件不支持动态模式切换，回调可以为空。

**起始版本：** 26.0.0

**返回值**

[OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result)：**AUDIOCOMMON_RESULT_SUCCESS** 表示执行成功；**AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM** 表示参数无效；**AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE** 表示配件未创建。

### OH_AudioAccessoryManager_SetNoiseReductionMode()

```c
OH_AudioCommon_Result OH_AudioAccessoryManager_SetNoiseReductionMode(OH_AudioAccessoryManager *manager, OH_AudioAccessory *accessory, OH_AudioNoiseReductionMode mode)
```

**描述**

将配件当前降噪模式同步给框架，通常用于通过硬件按键或配套应用更改模式后的状态同步。

**起始版本：** 26.0.0

**返回值**

[OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result)：**AUDIOCOMMON_RESULT_SUCCESS** 表示执行成功；**AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM** 表示参数无效；**AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE** 表示配件未连接；**AUDIOCOMMON_RESULT_ERROR_UNSUPPORTED** 表示不支持该模式。

### OH_AudioAccessoryManager_Connected()

```c
OH_AudioCommon_Result OH_AudioAccessoryManager_Connected(OH_AudioAccessoryManager *manager, OH_AudioAccessory *accessory)
```

**描述**

将音频配件连接到音频框架。调用此函数前，必须注册所有必需能力。

**所需权限：** ohos.permission.MANAGE_AUDIO_ACCESSORY

**起始版本：** 26.0.0

**返回值**

[OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result)：**AUDIOCOMMON_RESULT_SUCCESS** 表示执行成功；**AUDIOCOMMON_RESULT_ERROR_PERMISSION_DENIED** 表示调用方没有所需权限；**AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM** 表示 **accessory** 为空；**AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE** 表示能力未注册或配件已连接；**AUDIOCOMMON_RESULT_ERROR_SYSTEM** 表示音频服务进程死亡。

### OH_AudioAccessoryManager_Disconnected()

```c
OH_AudioCommon_Result OH_AudioAccessoryManager_Disconnected(OH_AudioAccessoryManager *manager, OH_AudioAccessory *accessory)
```

**描述**

将音频配件从音频框架断开连接。

**所需权限：** ohos.permission.MANAGE_AUDIO_ACCESSORY

**起始版本：** 26.0.0

**返回值**

[OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result)：**AUDIOCOMMON_RESULT_SUCCESS** 表示执行成功；**AUDIOCOMMON_RESULT_ERROR_PERMISSION_DENIED** 表示调用方没有所需权限；**AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM** 表示 **accessory** 为空；**AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE** 表示配件未连接；**AUDIOCOMMON_RESULT_ERROR_SYSTEM** 表示音频服务进程死亡。

### OH_AudioAccessoryManager_Destroy()

```c
OH_AudioCommon_Result OH_AudioAccessoryManager_Destroy(OH_AudioAccessoryManager *manager, OH_AudioAccessory *accessory)
```

**描述**

销毁音频配件实例。销毁前必须先断开配件连接。销毁成功后，配件句柄失效。

**起始版本：** 26.0.0

**返回值**

[OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result)：**AUDIOCOMMON_RESULT_SUCCESS** 表示执行成功；**AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM** 表示 **accessory** 为空；**AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE** 表示配件仍处于连接状态。

