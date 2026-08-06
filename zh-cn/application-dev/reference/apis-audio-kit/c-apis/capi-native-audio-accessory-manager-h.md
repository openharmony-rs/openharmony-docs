# native_audio_accessory_manager.h

## 概述

Declare audio accessory manager related interfaces.

**库：** libohaudio.so

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 26.0.0

**相关模块：** [AudioAccessoryManager](capi-audioaccessorymanager.md)

## 汇总

### 函数

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [typedef bool (\*OH_AudioAccessory_SetNoiseReductionCallback)(OH_AudioAccessory *accessory, OH_AudioNoiseReductionMode mode)](#oh_audioaccessory_setnoisereductioncallback) | OH_AudioAccessory_SetNoiseReductionCallback | 配件降噪模式切换回调。<b>When Called:</b>当系统请求更改噪音时附件上的还原模式。此回调可以在任何时候调用连接附件后。 |
| [OH_AudioCommon_Result OH_AudioManager_GetAccessoryManager(OH_AudioAccessoryManager **outManager)](#oh_audiomanager_getaccessorymanager) | - | 获取音频配件管理器实例。 |
| [OH_AudioCommon_Result OH_AudioAccessoryManager_CreateInput(OH_AudioAccessoryManager *manager, const OH_AudioAccessoryInfo *info, const OH_AudioAccessoryCapabilities *capabilities, OH_AudioAccessory_OpenInputStreamCallback openInputStream, OH_AudioAccessory **outOwnedAccessory)](#oh_audioaccessorymanager_createinput) | - | 创建输入音频配件实例并注册其能力。该函数只创建音频附件实例。它不会创造任何输入流。框架会对附件名称、制造商、modelNumber和macAddress字段。调用方可以释放这些缓冲区在此函数返回后。该框架还执行streamProperties数组的深拷贝的能力。调用者可以在此函数返回后释放此数组。成功后，框架会分配一个[OH_AudioAccessory](capi-ohaudio-oh-audioaccessory.md)句柄，通过辅助指针返回。输入流是由框架懒创建的，当应用程序实际上是从这个附件开始录制的。当时，框架创建一个新的[OH_AudioAccessoryInputStream](capi-ohaudio-oh-audioaccessoryinputstream.md)句柄并调用开流。回调接收新创建的流句柄和请求的流信息，并且是调用者必须注册的位置所需的流回调。流句柄由框架管理，不能由调用者。流一直有效，直到框架调用该流的{@链接OH_AudioAccessoryInputStream_ReleaseCallback}。之后release回调返回，则流句柄无效，不能被再次使用。在一个辅助句柄的生命周期内，输入流可以多次创建和释放。 |
| [OH_AudioCommon_Result OH_AudioAccessoryManager_SetAssociatedMacAddresses(OH_AudioAccessoryManager *manager, OH_AudioAccessory *accessory, const char **macAddresses, uint32_t count)](#oh_audioaccessorymanager_setassociatedmacaddresses) | - | 设置音频附件的关联MAC地址列表。此接口替换现有的关联MAC地址列表链接到附件实例。它设计用于多发射机场景（例如，1对2、1对4系统），其中连接的组发射器可能会动态更改。在创建附件后调用此选项以报告与主MAC关联的所有当前活动的发送器。如果更换变送器或断开变送器，请使用更新列表以覆盖先前的状态。在活动期间安全呼叫录制会话。 |
| [OH_AudioCommon_Result OH_AudioAccessoryManager_RegisterNoiseReductionCapability(OH_AudioAccessoryManager *manager, OH_AudioAccessory *accessory, const OH_AudioAccessoryNoiseReductionCapability *capability, OH_AudioAccessory_SetNoiseReductionCallback onNoiseReduction)](#oh_audioaccessorymanager_registernoisereductioncapability) | - | 注册音频配件降噪能力。框架对支持的Modes数组和其他能力结构中的字段。调用方可以释放该能力结构，并在此函数返回后返回支持的Modes数组。 |
| [OH_AudioCommon_Result OH_AudioAccessoryManager_SetNoiseReductionMode(OH_AudioAccessoryManager *manager, OH_AudioAccessory *accessory, OH_AudioNoiseReductionMode mode)](#oh_audioaccessorymanager_setnoisereductionmode) | - | 设置音频附件的降噪模式。该功能允许附件服务主动同步当前降噪模式为框架。它通常用于通过其他手段(例如，硬件按钮或)，确保框架与附件保持同步更新实际状态。 |
| [OH_AudioCommon_Result OH_AudioAccessoryManager_Connected(OH_AudioAccessoryManager *manager, OH_AudioAccessory *accessory)](#oh_audioaccessorymanager_connected) | - | 将音频配件连接到音频框架。在调用此函数之前，必须注册所有必需的能力。<b>Recommendation:</b>建议第三方音频配件优先考虑与智慧生活APP的集成。这确保了一致的设备发现和连接的用户体验，允许附件服务，避免直接进行权限管理。 |
| [OH_AudioCommon_Result OH_AudioAccessoryManager_Disconnected(OH_AudioAccessoryManager *manager, OH_AudioAccessory *accessory)](#oh_audioaccessorymanager_disconnected) | - | 断开音频附件与音频框架的连接。 |
| [OH_AudioCommon_Result OH_AudioAccessoryManager_Destroy(OH_AudioAccessoryManager *manager, OH_AudioAccessory *accessory)](#oh_audioaccessorymanager_destroy) | - | 销毁音频附件实例。销毁前必须断开附件。 |

## 函数说明

### OH_AudioAccessory_SetNoiseReductionCallback()

```c
typedef bool (*OH_AudioAccessory_SetNoiseReductionCallback)(OH_AudioAccessory *accessory, OH_AudioNoiseReductionMode mode)
```

**描述**

配件降噪模式切换回调。<b>When Called:</b>当系统请求更改噪音时附件上的还原模式。此回调可以在任何时候调用连接附件后。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| (OH_AudioAccessory \*accessory | 音频配件。 |
| OH_AudioNoiseReductionMode mode | 要在附件上设置的降噪模式。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| bool | <ul><br> <li>`true`如果请求的模式处理成功</li><br> <li>`false`否则。</li><br> </ul> |

### OH_AudioManager_GetAccessoryManager()

```c
OH_AudioCommon_Result OH_AudioManager_GetAccessoryManager(OH_AudioAccessoryManager **outManager)
```

**描述**

获取音频配件管理器实例。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioAccessoryManager](capi-ohaudio-oh-audioaccessorymanager.md) **outManager | 【out】返回指向管理器句柄的指针。注意句柄由系统管理，不能释放被调用者调用，否则可能会出现异常。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AudioCommon_Result | <ul><br> <li>如果执行成功，则返回</li><br> <li>{@link AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM}如果管理器为空。</li><br> </ul> |

### OH_AudioAccessoryManager_CreateInput()

```c
OH_AudioCommon_Result OH_AudioAccessoryManager_CreateInput(OH_AudioAccessoryManager *manager, const OH_AudioAccessoryInfo *info, const OH_AudioAccessoryCapabilities *capabilities, OH_AudioAccessory_OpenInputStreamCallback openInputStream, OH_AudioAccessory **outOwnedAccessory)
```

**描述**

创建输入音频配件实例并注册其能力。该函数只创建音频附件实例。它不会创造任何输入流。框架会对附件名称、制造商、modelNumber和macAddress字段。调用方可以释放这些缓冲区在此函数返回后。该框架还执行streamProperties数组的深拷贝的能力。调用者可以在此函数返回后释放此数组。成功后，框架会分配一个[OH_AudioAccessory](capi-ohaudio-oh-audioaccessory.md)句柄，通过辅助指针返回。输入流是由框架懒创建的，当应用程序实际上是从这个附件开始录制的。当时，框架创建一个新的[OH_AudioAccessoryInputStream](capi-ohaudio-oh-audioaccessoryinputstream.md)句柄并调用开流。回调接收新创建的流句柄和请求的流信息，并且是调用者必须注册的位置所需的流回调。流句柄由框架管理，不能由调用者。流一直有效，直到框架调用该流的{@链接OH_AudioAccessoryInputStream_ReleaseCallback}。之后release回调返回，则流句柄无效，不能被再次使用。在一个辅助句柄的生命周期内，输入流可以多次创建和释放。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioAccessoryManager](capi-ohaudio-oh-audioaccessorymanager.md) *manager | 【in】音频附件管理器指针。 |
| [const OH_AudioAccessoryInfo](capi-ohaudio-oh-audioaccessoryinfo.md) *info | 【in】附件基本信息指针。不能为空。 |
| [const OH_AudioAccessoryCapabilities](capi-ohaudio-oh-audioaccessorycapabilities.md) *capabilities | 【in】指向附件功能的指针。不能为空。 |
| [OH_AudioAccessory_OpenInputStreamCallback](capi-native-audio-accessory-input-stream-manager-h.md#oh_audioaccessory_openinputstreamcallback) openInputStream | 【in】当框架打开输入流时调用的回调。不能为空。只有当框架创建时，才会调用回调此附件的流，而不是在调用此函数时。 |
| [OH_AudioAccessory](capi-ohaudio-oh-audioaccessory.md) **outOwnedAccessory | 【out】返回创建的辅助句柄。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AudioCommon_Result | <ul><br> <li>如果执行成功，则返回</li><br> <li>如果任何参数为null，则{@link AudioCOMMON_RESULT_ERROR_INVALID_PARAM}。</li><br> 如果管理器未初始化，则为<li>{@link AudioCOMMON_RESULT_ERROR_ILAL_STATE}。</li><br> </ul> |

### OH_AudioAccessoryManager_SetAssociatedMacAddresses()

```c
OH_AudioCommon_Result OH_AudioAccessoryManager_SetAssociatedMacAddresses(OH_AudioAccessoryManager *manager, OH_AudioAccessory *accessory, const char **macAddresses, uint32_t count)
```

**描述**

设置音频附件的关联MAC地址列表。此接口替换现有的关联MAC地址列表链接到附件实例。它设计用于多发射机场景（例如，1对2、1对4系统），其中连接的组发射器可能会动态更改。在创建附件后调用此选项以报告与主MAC关联的所有当前活动的发送器。如果更换变送器或断开变送器，请使用更新列表以覆盖先前的状态。在活动期间安全呼叫录制会话。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioAccessoryManager](capi-ohaudio-oh-audioaccessorymanager.md) *manager | 音频配件管理器指针。 |
| [OH_AudioAccessory](capi-ohaudio-oh-audioaccessory.md) *accessory | 指向附件句柄的指针。 |
| const char **macAddresses | 要关联的MAC地址数组。<b>Can be null if count is 0</b>，表示所有关联的MAC地址。应清除（例如，当所有辅助变送器断开时）。如果不为null，框架将对这些字符串执行深拷贝。 |
| uint32_t count | 数组中的MAC地址数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AudioCommon_Result | <ul><br> <li>如果执行成功，则返回</li><br> 如果参数无效，则<li>{@link AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM}。</li><br> <li>{@link AudioCOMMON_RESULT_ERROR_ILA_STATE}如果未创建配件。</li><br> </ul> |

### OH_AudioAccessoryManager_RegisterNoiseReductionCapability()

```c
OH_AudioCommon_Result OH_AudioAccessoryManager_RegisterNoiseReductionCapability(OH_AudioAccessoryManager *manager, OH_AudioAccessory *accessory, const OH_AudioAccessoryNoiseReductionCapability *capability, OH_AudioAccessory_SetNoiseReductionCallback onNoiseReduction)
```

**描述**

注册音频配件降噪能力。框架对支持的Modes数组和其他能力结构中的字段。调用方可以释放该能力结构，并在此函数返回后返回支持的Modes数组。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioAccessoryManager](capi-ohaudio-oh-audioaccessorymanager.md) *manager | 音频配件管理器指针。 |
| [OH_AudioAccessory](capi-ohaudio-oh-audioaccessory.md) *accessory | CreateInput创建的辅助句柄指针。 |
| [const OH_AudioAccessoryNoiseReductionCapability](capi-ohaudio-oh-audioaccessorynoisereductioncapability.md) *capability | 降噪能力指针。不能为空。 |
| [OH_AudioAccessory_SetNoiseReductionCallback](capi-native-audio-accessory-manager-h.md#oh_audioaccessory_setnoisereductioncallback) onNoiseReduction | 框架时调用的回调请求更改降噪模式。如果附件，则可能为空不支持动态模式切换。如果提供，则回调必须成功时返回`true`，失败时返回`false`。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AudioCommon_Result | <ul><br> <li>如果执行成功，则返回</li><br> 如果参数无效，则<li>{@link AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM}。</li><br> <li>{@link AudioCOMMON_RESULT_ERROR_ILA_STATE}如果未创建配件。</li><br> </ul> |

### OH_AudioAccessoryManager_SetNoiseReductionMode()

```c
OH_AudioCommon_Result OH_AudioAccessoryManager_SetNoiseReductionMode(OH_AudioAccessoryManager *manager, OH_AudioAccessory *accessory, OH_AudioNoiseReductionMode mode)
```

**描述**

设置音频附件的降噪模式。该功能允许附件服务主动同步当前降噪模式为框架。它通常用于通过其他手段(例如，硬件按钮或)，确保框架与附件保持同步更新实际状态。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioAccessoryManager](capi-ohaudio-oh-audioaccessorymanager.md) *manager | 音频配件管理器指针。 |
| [OH_AudioAccessory](capi-ohaudio-oh-audioaccessory.md) *accessory | 指向附件句柄的指针。 |
| OH_AudioNoiseReductionMode mode | 要设置的降噪模式。一定是模式之一通过RegisterNoiseReduceCapability注册。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AudioCommon_Result | <ul><br> <li>如果执行成功，则返回</li><br> 如果参数无效，则<li>{@link AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM}。</li><br> <li>{@link AudioCOMMON_RESULT_ERROR_ILAL_STATE}如果未连接配件。</li><br> <li>{@link AUDIOCOMMON_RESULT_ERROR_UNSUPPORTED}如果该模式不受支持。</li><br> </ul> |

### OH_AudioAccessoryManager_Connected()

```c
OH_AudioCommon_Result OH_AudioAccessoryManager_Connected(OH_AudioAccessoryManager *manager, OH_AudioAccessory *accessory)
```

**描述**

将音频配件连接到音频框架。在调用此函数之前，必须注册所有必需的能力。<b>Recommendation:</b>建议第三方音频配件优先考虑与智慧生活APP的集成。这确保了一致的设备发现和连接的用户体验，允许附件服务，避免直接进行权限管理。

**需要权限：** ohos.permission.MANAGE_AUDIO_ACCESSORY

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioAccessoryManager](capi-ohaudio-oh-audioaccessorymanager.md) *manager | 音频配件管理器指针。 |
| [OH_AudioAccessory](capi-ohaudio-oh-audioaccessory.md) *accessory | 指向要连接的附件句柄的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AudioCommon_Result | <ul><br> <li>如果执行成功，则返回</li><br> <li>{@link AudioCommon_RESULT_ERROR_PERATION_DENIED}如果调用者没有<br> 需要权限。</li><br> <li>{@link AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM}如果附件为空。</li><br> <li>{@link AudioCOMMON_RESULT_ERROR_ILAL_STATE}如果功能未注册或<br> 配件已连接。</li><br> <li>{@link AUDIOCOMMON_RESULT_ERROR_SYSTEM}如果音频服务器进程已死。</li><br> </ul> |

### OH_AudioAccessoryManager_Disconnected()

```c
OH_AudioCommon_Result OH_AudioAccessoryManager_Disconnected(OH_AudioAccessoryManager *manager, OH_AudioAccessory *accessory)
```

**描述**

断开音频附件与音频框架的连接。

**需要权限：** ohos.permission.MANAGE_AUDIO_ACCESSORY

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioAccessoryManager](capi-ohaudio-oh-audioaccessorymanager.md) *manager | 音频配件管理器指针。 |
| [OH_AudioAccessory](capi-ohaudio-oh-audioaccessory.md) *accessory | 指针类型，指向要断开连接的附件句柄。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AudioCommon_Result | <ul><br> <li>如果执行成功，则返回</li><br> <li>{@link AudioCommon_RESULT_ERROR_PERATION_DENIED}如果调用者没有<br> 需要权限。</li><br> <li>{@link AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM}如果附件为空。</li><br> <li>{@link AudioCOMMON_RESULT_ERROR_ILAL_STATE}如果未连接配件。</li><br> <li>{@link AUDIOCOMMON_RESULT_ERROR_SYSTEM}如果音频服务器进程已死。</li><br> </ul> |

### OH_AudioAccessoryManager_Destroy()

```c
OH_AudioCommon_Result OH_AudioAccessoryManager_Destroy(OH_AudioAccessoryManager *manager, OH_AudioAccessory *accessory)
```

**描述**

销毁音频附件实例。销毁前必须断开附件。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioAccessoryManager](capi-ohaudio-oh-audioaccessorymanager.md) *manager | 【in】音频附件管理器指针。 |
| [OH_AudioAccessory](capi-ohaudio-oh-audioaccessory.md) *accessory | 【in】指向要销毁的辅助句柄的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AudioCommon_Result | <ul><br> <li>如果执行成功，则返回</li><br> <li>{@link AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM}如果附件为空。</li><br> 如果配件仍处于连接状态，则显示<li>{@link AudioCOMMON_RESULT_ERROR_ILAL_STATE}。</li><br> </ul> |


