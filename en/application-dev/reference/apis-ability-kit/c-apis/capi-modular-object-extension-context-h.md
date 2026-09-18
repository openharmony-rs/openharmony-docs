# modular_object_extension_context.h

## Overview

Declares the modular object extension context.

**Library**: libability_runtime.so

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 13

**Related module**: [AbilityRuntime](capi-abilityruntime.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AbilityRuntime_ModularObjectExtensionContext*](capi-abilityruntime-oh-abilityruntime-modularobjectextensioncontext8h.md) | OH_AbilityRuntime_ModObjExtensionContextHandle | Defines a pointer type to OH_AbilityRuntime_ModObjExtensionContextHandle. |

### Function

| Name | Description |
| -- | -- |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjExtensionContext_GetBaseContext(OH_AbilityRuntime_ModObjExtensionContextHandle modObjExtensionContext, AbilityRuntime_ContextHandle* baseContext)](#oh_abilityruntime_modobjextensioncontext_getbasecontext) | Gets the base context from the modular object extension context. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjExtensionContext_StartSelfUIAbility(OH_AbilityRuntime_ModObjExtensionContextHandle context, const AbilityBase_Want *want)](#oh_abilityruntime_modobjextensioncontext_startselfuiability) | Starts the self UIAbility. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjExtensionContext_StartSelfUIAbilityWithStartOptions(OH_AbilityRuntime_ModObjExtensionContextHandle context, const AbilityBase_Want *want, const AbilityRuntime_StartOptions *options)](#oh_abilityruntime_modobjextensioncontext_startselfuiabilitywithstartoptions) | Starts the self UIAbility with start options. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjExtensionContext_TerminateSelf(OH_AbilityRuntime_ModObjExtensionContextHandle context)](#oh_abilityruntime_modobjextensioncontext_terminateself) | Destroys the modular object extension. |
| [OHIPCRemoteStub* OH_AbilityRuntime_ModObjExtensionContext_CreateIPCRemoteStub(OH_AbilityRuntime_ModObjExtensionContextHandle context, const char *descriptor, OH_OnRemoteRequestCallback requestCallback, OH_OnRemoteDestroyCallback destroyCallback, void *userData)](#oh_abilityruntime_modobjextensioncontext_createipcremotestub) | Creates an <b>OHIPCRemoteStub</b> object with callbacks running on the extension's designated thread. The requestCallback and destroyCallback are invoked serially on the thread determined by the extension's {@link OH_AbilityRuntime_ThreadMode}. After calling [OH_AbilityRuntime_ModObjExtensionContext_DestroyIPCRemoteStub](capi-modular-object-extension-context-h.md#oh_abilityruntime_modobjextensioncontext_destroyipcremotestub), no new requestCallback<br>invocations will occur, and any in-flight requestCallback will complete before destroyCallback is invoked.<br>The caller is responsible for destroying the returned object by calling<br>[OH_AbilityRuntime_ModObjExtensionContext_DestroyIPCRemoteStub](capi-modular-object-extension-context-h.md#oh_abilityruntime_modobjextensioncontext_destroyipcremotestub) to avoid memory leaks. |
| [void OH_AbilityRuntime_ModObjExtensionContext_DestroyIPCRemoteStub(OH_AbilityRuntime_ModObjExtensionContextHandle context, OHIPCRemoteStub *stub)](#oh_abilityruntime_modobjextensioncontext_destroyipcremotestub) | Destroys an <b>OHIPCRemoteStub</b> object. |

## Function description

### OH_AbilityRuntime_ModObjExtensionContext_GetBaseContext()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjExtensionContext_GetBaseContext(OH_AbilityRuntime_ModObjExtensionContextHandle modObjExtensionContext, AbilityRuntime_ContextHandle* baseContext)
```

**Description**

Gets the base context from the modular object extension context.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjExtensionContextHandle](capi-abilityruntime-oh-abilityruntime-modularobjectextensioncontext8h.md) modObjExtensionContext | Represents a pointer to a modular object extension ability context. |
| AbilityRuntime_ContextHandle* baseContext | Represents a pointer to a {@link AbilityRuntime_ContextHandle} base extension ability context. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | Returns a specific error code.          {@link ABILITY_RUNTIME_ERROR_CODE_NO_ERROR} success.<br>        {@link ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID} parameter check failed. |

### OH_AbilityRuntime_ModObjExtensionContext_StartSelfUIAbility()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjExtensionContext_StartSelfUIAbility(OH_AbilityRuntime_ModObjExtensionContextHandle context, const AbilityBase_Want *want)
```

**Description**

Starts the self UIAbility.

**Required permission**: ohos.permission.NDK_START_SELF_UI_ABILITY

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjExtensionContextHandle](capi-abilityruntime-oh-abilityruntime-modularobjectextensioncontext8h.md) context | Represents a pointer to a modular object extension ability context. |
| const AbilityBase_Want *want | The arguments passed to start the self UIAbility. For details, see {@link AbilityBase_Want}. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | Returns a specific error code.           {@link ABILITY_RUNTIME_ERROR_CODE_NO_ERROR} if the call is successful.<br>         {@link ABILITY_RUNTIME_ERROR_CODE_PERMISSION_DENIED} if the caller has no correct permission.<br>         {@link ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID} if the arguments provided is invalid.<br>         {@link ABILITY_RUNTIME_ERROR_CODE_NOT_SUPPORTED} if the device does not support starting self UIAbility.<br>         {@link ABILITY_RUNTIME_ERROR_CODE_NO_SUCH_ABILITY} if the target ability does not exist.<br>         {@link ABILITY_RUNTIME_ERROR_CODE_INCORRECT_ABILITY_TYPE} if the ability type is incorrect.<br>         {@link ABILITY_RUNTIME_ERROR_CODE_CROWDTEST_EXPIRED} if the crowdtesting application expires.<br>         {@link ABILITY_RUNTIME_ERROR_CODE_WUKONG_MODE} if the ability cannot be started in Wukong mode.<br>         {@link ABILITY_RUNTIME_ERROR_CODE_CONTROLLED} if the app is controlled.<br>         {@link ABILITY_RUNTIME_ERROR_CODE_EDM_CONTROLLED} if the app is controlled by EDM.<br>         {@link ABILITY_RUNTIME_ERROR_CODE_CROSS_APP} if the caller tries to start a different application.<br>         {@link ABILITY_RUNTIME_ERROR_CODE_INTERNAL} if an internal error occurs.<br>         {@link ABILITY_RUNTIME_ERROR_CODE_NOT_TOP_ABILITY} if the caller is not top ability.<br>         {@link ABILITY_RUNTIME_ERROR_CODE_MULTI_APP_NOT_SUPPORTED} if the app clone or multi-instance is<br>            not supported.<br>         {@link ABILITY_RUNTIME_ERROR_CODE_INVALID_APP_INSTANCE_KEY} if the app instance key is invalid.<br>         {@link ABILITY_RUNTIME_ERROR_CODE_UPPER_LIMIT_REACHED} if the number of app instances has reached<br>            the limit.<br>         {@link ABILITY_RUNTIME_ERROR_MULTI_INSTANCE_NOT_SUPPORTED} if multi-instance is not supported.<br>         {@link ABILITY_RUNTIME_ERROR_CODE_APP_INSTANCE_KEY_NOT_SUPPORTED} if the APP_INSTANCE_KEY cannot            be specified. |

### OH_AbilityRuntime_ModObjExtensionContext_StartSelfUIAbilityWithStartOptions()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjExtensionContext_StartSelfUIAbilityWithStartOptions(OH_AbilityRuntime_ModObjExtensionContextHandle context, const AbilityBase_Want *want, const AbilityRuntime_StartOptions *options)
```

**Description**

Starts the self UIAbility with start options.

**Required permission**: ohos.permission.NDK_START_SELF_UI_ABILITY

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjExtensionContextHandle](capi-abilityruntime-oh-abilityruntime-modularobjectextensioncontext8h.md) context | Represents a pointer to a modular object extension ability context. |
| const AbilityBase_Want *want | The arguments passed to start the self UIAbility. For details, see {@link AbilityBase_Want}. |
| const AbilityRuntime_StartOptions *options | The start options passed to start the self UIAbility. For details, see {@link AbilityRuntime_StartOptions}. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | Returns a specific error code.           {@link ABILITY_RUNTIME_ERROR_CODE_NO_ERROR} if the call is successful.<br>         {@link ABILITY_RUNTIME_ERROR_CODE_PERMISSION_DENIED} if the caller has no correct permission.<br>         {@link ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID} if the arguments provided are invalid.<br>         {@link ABILITY_RUNTIME_ERROR_CODE_NOT_SUPPORTED} if the device does not support starting self UIAbility.<br>         {@link ABILITY_RUNTIME_ERROR_CODE_NO_SUCH_ABILITY} if the target ability does not exist.<br>         {@link ABILITY_RUNTIME_ERROR_CODE_INCORRECT_ABILITY_TYPE} if the ability type is incorrect.<br>         {@link ABILITY_RUNTIME_ERROR_CODE_CROWDTEST_EXPIRED} if the crowdtesting application expires.<br>         {@link ABILITY_RUNTIME_ERROR_CODE_WUKONG_MODE} if the ability cannot be started in Wukong mode.<br>         {@link ABILITY_RUNTIME_ERROR_CODE_CONTROLLED} if the app is controlled.<br>         {@link ABILITY_RUNTIME_ERROR_CODE_EDM_CONTROLLED} if the app is controlled by EDM.<br>         {@link ABILITY_RUNTIME_ERROR_CODE_CROSS_APP} if the caller tries to start a different application.<br>         {@link ABILITY_RUNTIME_ERROR_CODE_INTERNAL} if an internal error occurs.<br>         {@link ABILITY_RUNTIME_ERROR_CODE_NOT_TOP_ABILITY} if the caller is not a foreground process.<br>         {@link ABILITY_RUNTIME_ERROR_VISIBILITY_SETTING_DISABLED} if setting visibility is disabled.<br>         {@link ABILITY_RUNTIME_ERROR_CODE_MULTI_APP_NOT_SUPPORTED} if the app clone or multi-instance is<br>            not supported.<br>         {@link ABILITY_RUNTIME_ERROR_CODE_INVALID_APP_INSTANCE_KEY} if the app instance key is invalid.<br>         {@link ABILITY_RUNTIME_ERROR_CODE_UPPER_LIMIT_REACHED} if the number of app instances has reached<br>            the limit.<br>         {@link ABILITY_RUNTIME_ERROR_MULTI_INSTANCE_NOT_SUPPORTED} if multi-instance is not supported.<br>         {@link ABILITY_RUNTIME_ERROR_CODE_APP_INSTANCE_KEY_NOT_SUPPORTED} if the APP_INSTANCE_KEY cannot            be specified. |

### OH_AbilityRuntime_ModObjExtensionContext_TerminateSelf()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjExtensionContext_TerminateSelf(OH_AbilityRuntime_ModObjExtensionContextHandle context)
```

**Description**

Destroys the modular object extension.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjExtensionContextHandle](capi-abilityruntime-oh-abilityruntime-modularobjectextensioncontext8h.md) context | Represents a pointer to a modular object extension ability context. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>       <li>{@link ABILITY_RUNTIME_ERROR_CODE_NO_ERROR} if the call is successful.</li><br>     <li>{@link ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID} if the arguments provided are invalid.</li><br>     <li>{@link ABILITY_RUNTIME_ERROR_CODE_WUKONG_MODE} if the ability cannot be terminated in Wukong mode.</li><br>     <li>{@link ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST} if the context does not exist.</li><br>     <li>{@link ABILITY_RUNTIME_ERROR_CODE_INTERNAL} if an internal error occurs.</li>       </ul> |

### OH_AbilityRuntime_ModObjExtensionContext_CreateIPCRemoteStub()

```c
OHIPCRemoteStub* OH_AbilityRuntime_ModObjExtensionContext_CreateIPCRemoteStub(OH_AbilityRuntime_ModObjExtensionContextHandle context, const char *descriptor, OH_OnRemoteRequestCallback requestCallback, OH_OnRemoteDestroyCallback destroyCallback, void *userData)
```

**Description**

Creates an <b>OHIPCRemoteStub</b> object with callbacks running on the extension's designated thread. The requestCallback and destroyCallback are invoked serially on the thread determined by the extension's {@link OH_AbilityRuntime_ThreadMode}. After calling [OH_AbilityRuntime_ModObjExtensionContext_DestroyIPCRemoteStub](capi-modular-object-extension-context-h.md#oh_abilityruntime_modobjextensioncontext_destroyipcremotestub), no new requestCallback<br>invocations will occur, and any in-flight requestCallback will complete before destroyCallback is invoked.<br>The caller is responsible for destroying the returned object by calling<br>[OH_AbilityRuntime_ModObjExtensionContext_DestroyIPCRemoteStub](capi-modular-object-extension-context-h.md#oh_abilityruntime_modobjextensioncontext_destroyipcremotestub) to avoid memory leaks.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjExtensionContextHandle](capi-abilityruntime-oh-abilityruntime-modularobjectextensioncontext8h.md) context | Represents a pointer to a modular object extension ability context. |
| const char *descriptor | Pointer to the descriptor of the <b>OHIPCRemoteStub</b> object to create. It cannot be NULL. The string is copied internally during creation, so the caller may release the descriptor after this function returns. |
| OH_OnRemoteRequestCallback requestCallback | Callback used to process the data request. It cannot be NULL. |
| OH_OnRemoteDestroyCallback destroyCallback | Callback to be invoked when the object is destroyed. It can be NULL. |
| void *userData | Pointer to the user data. It can be NULL. Must remain valid before the object is destroyed. |

**Returns**:

| Type | Description |
| -- | -- |
| OHIPCRemoteStub* | Returns the pointer to the <b>OHIPCRemoteStub</b> object created if the operation is successful;  returns NULL otherwise. |

### OH_AbilityRuntime_ModObjExtensionContext_DestroyIPCRemoteStub()

```c
void OH_AbilityRuntime_ModObjExtensionContext_DestroyIPCRemoteStub(OH_AbilityRuntime_ModObjExtensionContextHandle context, OHIPCRemoteStub *stub)
```

**Description**

Destroys an <b>OHIPCRemoteStub</b> object.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjExtensionContextHandle](capi-abilityruntime-oh-abilityruntime-modularobjectextensioncontext8h.md) context | Represents a pointer to a modular object extension ability context. |
| OHIPCRemoteStub *stub | Pointer to the <b>OHIPCRemoteStub</b> object to destroy. |


