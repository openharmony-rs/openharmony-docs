# modular_object_extension_context.h

## 概述

声明ModularObjectExtensionAbility的上下文接口，包括启动UIAbility、销毁ModularObjectExtensionAbility自身、创建和销毁IPC对象等功能。

**库：** libability_runtime.so

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**起始版本：** 26.0.0

**相关模块：** [AbilityRuntime](capi-abilityruntime.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_AbilityRuntime_ModularObjectExtensionContext*](capi-abilityruntime-oh-abilityruntime-modularobjectextensioncontext8h.md) | OH_AbilityRuntime_ModObjExtensionContextHandle | 表示ModularObjectExtensionAbility上下文的句柄。 |

### 函数

| 名称 | 描述 |
| -- | -- |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjExtensionContext_GetBaseContext(OH_AbilityRuntime_ModObjExtensionContextHandle modObjExtensionContext, AbilityRuntime_ContextHandle* baseContext)](#oh_abilityruntime_modobjextensioncontext_getbasecontext) | 从ModularObjectExtensionAbility上下文中获取基础上下文。 |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjExtensionContext_StartSelfUIAbility(OH_AbilityRuntime_ModObjExtensionContextHandle context, const AbilityBase_Want *want)](#oh_abilityruntime_modobjextensioncontext_startselfuiability) | 启动当前应用的UIAbility。 |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjExtensionContext_StartSelfUIAbilityWithStartOptions(OH_AbilityRuntime_ModObjExtensionContextHandle context, const AbilityBase_Want *want, const AbilityRuntime_StartOptions *options)](#oh_abilityruntime_modobjextensioncontext_startselfuiabilitywithstartoptions) | 通过StartOptions启动当前应用的UIAbility。 |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjExtensionContext_TerminateSelf(OH_AbilityRuntime_ModObjExtensionContextHandle context)](#oh_abilityruntime_modobjextensioncontext_terminateself) | 销毁ModularObjectExtensionAbility自身。 |
| [OHIPCRemoteStub* OH_AbilityRuntime_ModObjExtensionContext_CreateIPCRemoteStub(OH_AbilityRuntime_ModObjExtensionContextHandle context, const char *descriptor, OH_OnRemoteRequestCallback requestCallback, OH_OnRemoteDestroyCallback destroyCallback, void *userData)](#oh_abilityruntime_modobjextensioncontext_createipcremotestub) | 创建一个OHIPCRemoteStub对象，回调函数将在ExtensionAbility指定的线程上运行。requestCallback和destroyCallback将在由ExtensionAbility的{@link OH_AbilityRuntime_ThreadMode}决定的线程上按顺序执行。调用[OH_AbilityRuntime_ModObjExtensionContext_DestroyIPCRemoteStub](capi-modular-object-extension-context-h.md#oh_abilityruntime_modobjextensioncontext_destroyipcremotestub)后，不会再有新的requestCallback回调，且正在执行的requestCallback完成后才会回调destroyCallback。调用方需调用[OH_AbilityRuntime_ModObjExtensionContext_DestroyIPCRemoteStub](capi-modular-object-extension-context-h.md#oh_abilityruntime_modobjextensioncontext_destroyipcremotestub)销毁返回的对象，避免内存泄漏。 |
| [void OH_AbilityRuntime_ModObjExtensionContext_DestroyIPCRemoteStub(OH_AbilityRuntime_ModObjExtensionContextHandle context, OHIPCRemoteStub *stub)](#oh_abilityruntime_modobjextensioncontext_destroyipcremotestub) | 销毁OHIPCRemoteStub对象。 |

## 函数说明

### OH_AbilityRuntime_ModObjExtensionContext_GetBaseContext()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjExtensionContext_GetBaseContext(OH_AbilityRuntime_ModObjExtensionContextHandle modObjExtensionContext, AbilityRuntime_ContextHandle* baseContext)
```

**描述：**

从ModularObjectExtensionAbility上下文中获取基础上下文。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AbilityRuntime_ModObjExtensionContextHandle](capi-abilityruntime-oh-abilityruntime-modularobjectextensioncontext8h.md) modObjExtensionContext | 指向ModularObjectExtensionAbility上下文的指针。 |
| AbilityRuntime_ContextHandle* baseContext | 指向{@link AbilityRuntime_ContextHandle}的指针，用于接收结果。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| AbilityRuntime_ErrorCode | 返回特定的错误码。      <br>{@link ABILITY_RUNTIME_ERROR_CODE_NO_ERROR} 接口调用成功。      <br>{@link ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID} 参数校验失败。 |

### OH_AbilityRuntime_ModObjExtensionContext_StartSelfUIAbility()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjExtensionContext_StartSelfUIAbility(OH_AbilityRuntime_ModObjExtensionContextHandle context, const AbilityBase_Want *want)
```

**描述：**

启动当前应用的UIAbility。

**需要权限：** ohos.permission.NDK_START_SELF_UI_ABILITY

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AbilityRuntime_ModObjExtensionContextHandle](capi-abilityruntime-oh-abilityruntime-modularobjectextensioncontext8h.md) context | 指向ModularObjectExtensionAbility上下文的指针。 |
| const AbilityBase_Want *want | 启动当前应用UIAbility时需要的Want信息。详细内容参考{@link AbilityBase_Want}。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| AbilityRuntime_ErrorCode | 返回特定的错误码。      <br>{@link ABILITY_RUNTIME_ERROR_CODE_NO_ERROR} 接口调用成功。      <br>{@link ABILITY_RUNTIME_ERROR_CODE_PERMISSION_DENIED} 调用方无正确权限。      <br>{@link ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID} 传入参数无效。      <br>{@link ABILITY_RUNTIME_ERROR_CODE_NOT_SUPPORTED} 设备不支持启动当前应用的UIAbility。      <br>{@link ABILITY_RUNTIME_ERROR_CODE_NO_SUCH_ABILITY} 目标Ability不存在。      <br>{@link ABILITY_RUNTIME_ERROR_CODE_INCORRECT_ABILITY_TYPE} Ability类型不正确。      <br>{@link ABILITY_RUNTIME_ERROR_CODE_CROWDTEST_EXPIRED} 众测应用已过期。      <br>{@link ABILITY_RUNTIME_ERROR_CODE_WUKONG_MODE} 无法在Wukong模式下启动Ability。      <br>{@link ABILITY_RUNTIME_ERROR_CODE_CONTROLLED} 应用被管控。      <br>{@link ABILITY_RUNTIME_ERROR_CODE_EDM_CONTROLLED} 应用被EDM管控。      <br>{@link ABILITY_RUNTIME_ERROR_CODE_CROSS_APP} 调用方尝试启动不同应用。      <br>{@link ABILITY_RUNTIME_ERROR_CODE_INTERNAL} 内部错误。      <br>{@link ABILITY_RUNTIME_ERROR_CODE_NOT_TOP_ABILITY} 调用方进程不在前台。      <br>{@link ABILITY_RUNTIME_ERROR_CODE_MULTI_APP_NOT_SUPPORTED} 不支持应用分身和多实例。      <br>{@link ABILITY_RUNTIME_ERROR_CODE_INVALID_APP_INSTANCE_KEY} 应用实例Key无效。      <br>{@link ABILITY_RUNTIME_ERROR_CODE_UPPER_LIMIT_REACHED} 应用实例数量已达上限。      <br>{@link ABILITY_RUNTIME_ERROR_MULTI_INSTANCE_NOT_SUPPORTED} 不支持应用多实例。      <br>{@link ABILITY_RUNTIME_ERROR_CODE_APP_INSTANCE_KEY_NOT_SUPPORTED} 不允许设置APP_INSTANCE_KEY。 |

### OH_AbilityRuntime_ModObjExtensionContext_StartSelfUIAbilityWithStartOptions()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjExtensionContext_StartSelfUIAbilityWithStartOptions(OH_AbilityRuntime_ModObjExtensionContextHandle context, const AbilityBase_Want *want, const AbilityRuntime_StartOptions *options)
```

**描述：**

通过StartOptions启动当前应用的UIAbility。

**需要权限：** ohos.permission.NDK_START_SELF_UI_ABILITY

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AbilityRuntime_ModObjExtensionContextHandle](capi-abilityruntime-oh-abilityruntime-modularobjectextensioncontext8h.md) context | 指向ModularObjectExtensionAbility上下文的指针。 |
| const AbilityBase_Want *want | 启动当前应用UIAbility时需要的Want信息。详细内容参考{@link AbilityBase_Want}。 |
| const AbilityRuntime_StartOptions *options | 启动当前应用UIAbility时需要的StartOptions信息。详细内容参考{@link AbilityRuntime_StartOptions}。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| AbilityRuntime_ErrorCode | 返回特定的错误码。      <br>{@link ABILITY_RUNTIME_ERROR_CODE_NO_ERROR} 接口调用成功。      <br>{@link ABILITY_RUNTIME_ERROR_CODE_PERMISSION_DENIED} 调用方无正确权限。      <br>{@link ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID} 传入参数无效。      <br>{@link ABILITY_RUNTIME_ERROR_CODE_NOT_SUPPORTED} 设备不支持启动当前应用的UIAbility。      <br>{@link ABILITY_RUNTIME_ERROR_CODE_NO_SUCH_ABILITY} 目标Ability不存在。      <br>{@link ABILITY_RUNTIME_ERROR_CODE_INCORRECT_ABILITY_TYPE} Ability类型不正确。      <br>{@link ABILITY_RUNTIME_ERROR_CODE_CROWDTEST_EXPIRED} 众测应用已过期。      <br>{@link ABILITY_RUNTIME_ERROR_CODE_WUKONG_MODE} 无法在Wukong模式下启动Ability。      <br>{@link ABILITY_RUNTIME_ERROR_CODE_CONTROLLED} 应用被管控。      <br>{@link ABILITY_RUNTIME_ERROR_CODE_EDM_CONTROLLED} 应用被EDM管控。      <br>{@link ABILITY_RUNTIME_ERROR_CODE_CROSS_APP} 调用方尝试启动不同应用。      <br>{@link ABILITY_RUNTIME_ERROR_CODE_INTERNAL} 内部错误。      <br>{@link ABILITY_RUNTIME_ERROR_CODE_NOT_TOP_ABILITY} 调用方非前台进程。      <br>{@link ABILITY_RUNTIME_ERROR_VISIBILITY_SETTING_DISABLED} 可见性设置已禁用。      <br>{@link ABILITY_RUNTIME_ERROR_CODE_MULTI_APP_NOT_SUPPORTED} 不支持应用分身和多实例。      <br>{@link ABILITY_RUNTIME_ERROR_CODE_INVALID_APP_INSTANCE_KEY} 应用实例Key无效。      <br>{@link ABILITY_RUNTIME_ERROR_CODE_UPPER_LIMIT_REACHED} 应用实例数量已达上限。      <br>{@link ABILITY_RUNTIME_ERROR_MULTI_INSTANCE_NOT_SUPPORTED} 不支持应用多实例。      <br>{@link ABILITY_RUNTIME_ERROR_CODE_APP_INSTANCE_KEY_NOT_SUPPORTED} 不允许设置APP_INSTANCE_KEY。 |

### OH_AbilityRuntime_ModObjExtensionContext_TerminateSelf()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjExtensionContext_TerminateSelf(OH_AbilityRuntime_ModObjExtensionContextHandle context)
```

**描述：**

销毁ModularObjectExtensionAbility自身。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AbilityRuntime_ModObjExtensionContextHandle](capi-abilityruntime-oh-abilityruntime-modularobjectextensioncontext8h.md) context | 指向ModularObjectExtensionAbility上下文的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| AbilityRuntime_ErrorCode | 返回特定的错误码。      <br>{@link ABILITY_RUNTIME_ERROR_CODE_NO_ERROR} 接口调用成功。      <br>{@link ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID} 传入参数无效。      <br>{@link ABILITY_RUNTIME_ERROR_CODE_WUKONG_MODE} 无法在Wukong模式下销毁Ability。      <br>{@link ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST} 上下文不存在。      <br>{@link ABILITY_RUNTIME_ERROR_CODE_INTERNAL} 内部错误。 |

### OH_AbilityRuntime_ModObjExtensionContext_CreateIPCRemoteStub()

```c
OHIPCRemoteStub* OH_AbilityRuntime_ModObjExtensionContext_CreateIPCRemoteStub(OH_AbilityRuntime_ModObjExtensionContextHandle context, const char *descriptor, OH_OnRemoteRequestCallback requestCallback, OH_OnRemoteDestroyCallback destroyCallback, void *userData)
```

**描述：**

创建一个OHIPCRemoteStub对象，回调函数将在ExtensionAbility指定的线程上运行。requestCallback和destroyCallback将在由ExtensionAbility的{@link OH_AbilityRuntime_ThreadMode}决定的线程上按顺序执行。调用[OH_AbilityRuntime_ModObjExtensionContext_DestroyIPCRemoteStub](capi-modular-object-extension-context-h.md#oh_abilityruntime_modobjextensioncontext_destroyipcremotestub)后，不会再有新的requestCallback回调，且正在执行的requestCallback完成后才会回调destroyCallback。调用方需调用[OH_AbilityRuntime_ModObjExtensionContext_DestroyIPCRemoteStub](capi-modular-object-extension-context-h.md#oh_abilityruntime_modobjextensioncontext_destroyipcremotestub)销毁返回的对象，避免内存泄漏。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AbilityRuntime_ModObjExtensionContextHandle](capi-abilityruntime-oh-abilityruntime-modularobjectextensioncontext8h.md) context | 指向ModularObjectExtensionAbility上下文的指针。 |
| const char *descriptor | 指向待创建的OHIPCRemoteStub对象描述符的指针，不能为NULL。创建过程中会内部拷贝该字符串，调用方可在本函数返回后释放该描述符。 |
| OH_OnRemoteRequestCallback requestCallback | 处理数据请求的回调函数，不能为NULL。 |
| OH_OnRemoteDestroyCallback destroyCallback | 对象销毁时调用的回调函数，可以为NULL。 |
| void *userData | 指向用户数据的指针，可以为NULL，须在对象销毁前保持有效。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OHIPCRemoteStub* | 操作成功时返回创建的OHIPCRemoteStub对象指针；否则返回NULL。 |

### OH_AbilityRuntime_ModObjExtensionContext_DestroyIPCRemoteStub()

```c
void OH_AbilityRuntime_ModObjExtensionContext_DestroyIPCRemoteStub(OH_AbilityRuntime_ModObjExtensionContextHandle context, OHIPCRemoteStub *stub)
```

**描述：**

销毁OHIPCRemoteStub对象。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AbilityRuntime_ModObjExtensionContextHandle](capi-abilityruntime-oh-abilityruntime-modularobjectextensioncontext8h.md) context | 指向ModularObjectExtensionAbility上下文的指针。 |
| OHIPCRemoteStub *stub | 指向待销毁的OHIPCRemoteStub对象的指针。 |


