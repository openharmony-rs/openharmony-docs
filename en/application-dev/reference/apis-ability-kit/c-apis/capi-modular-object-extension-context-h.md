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
| [OHIPCRemoteStub* OH_AbilityRuntime_ModObjExtensionContext_CreateIPCRemoteStub(OH_AbilityRuntime_ModObjExtensionContextHandle context, const char *descriptor, OH_OnRemoteRequestCallback requestCallback, OH_OnRemoteDestroyCallback destroyCallback, void *userData)](#oh_abilityruntime_modobjextensioncontext_createipcremotestub) | Creates an <b>OHIPCRemoteStub</b> object with callbacks running on the extension's designated thread. The requestCallback and destroyCallback are invoked serially on the thread determined by the extension's [OH_AbilityRuntime_ThreadMode](capi-modular-object-extension-manager-h.md#oh_abilityruntime_threadmode). After calling [OH_AbilityRuntime_ModObjExtensionContext_DestroyIPCRemoteStub](capi-modular-object-extension-context-h.md#oh_abilityruntime_modobjextensioncontext_destroyipcremotestub), no new requestCallback invocations will occur, and any in-flight requestCallback will complete before destroyCallback is invoked.<br> The caller is responsible for destroying the returned object by calling [OH_AbilityRuntime_ModObjExtensionContext_DestroyIPCRemoteStub](capi-modular-object-extension-context-h.md#oh_abilityruntime_modobjextensioncontext_destroyipcremotestub) to avoid memory leaks. |
| [void OH_AbilityRuntime_ModObjExtensionContext_DestroyIPCRemoteStub(OH_AbilityRuntime_ModObjExtensionContextHandle context, OHIPCRemoteStub *stub)](#oh_abilityruntime_modobjextensioncontext_destroyipcremotestub) | Destroys an <b>OHIPCRemoteStub</b> object. |

## Function description

### OH_AbilityRuntime_ModObjExtensionContext_GetBaseContext()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjExtensionContext_GetBaseContext(OH_AbilityRuntime_ModObjExtensionContextHandle modObjExtensionContext, AbilityRuntime_ContextHandle* baseContext)
```

**Description**

Gets the base context from the modular object extension context.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjExtensionContextHandle](capi-abilityruntime-oh-abilityruntime-modularobjectextensioncontext8h.md) modObjExtensionContext | Represents a pointer to a modular object extension ability context. |
| AbilityRuntime_ContextHandle* baseContext | Represents a pointer to a {@link AbilityRuntime_ContextHandle} base extension ability context. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | Returns a specific error code.          [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) success.          [ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) parameter check failed. |

### OH_AbilityRuntime_ModObjExtensionContext_StartSelfUIAbility()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjExtensionContext_StartSelfUIAbility(OH_AbilityRuntime_ModObjExtensionContextHandle context, const AbilityBase_Want *want)
```

**Description**

Starts the self UIAbility.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

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
| AbilityRuntime_ErrorCode | Returns a specific error code.           [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the call is successful.           [ABILITY_RUNTIME_ERROR_CODE_PERMISSION_DENIED](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the caller has no correct permission.           [ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the arguments provided is invalid.           [ABILITY_RUNTIME_ERROR_CODE_NOT_SUPPORTED](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the device does not support starting self UIAbility.           [ABILITY_RUNTIME_ERROR_CODE_NO_SUCH_ABILITY](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the target ability does not exist.           [ABILITY_RUNTIME_ERROR_CODE_INCORRECT_ABILITY_TYPE](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the ability type is incorrect.           [ABILITY_RUNTIME_ERROR_CODE_CROWDTEST_EXPIRED](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the crowdtesting application expires.           [ABILITY_RUNTIME_ERROR_CODE_WUKONG_MODE](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the ability cannot be started in Wukong mode.           [ABILITY_RUNTIME_ERROR_CODE_CONTROLLED](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the app is controlled.           [ABILITY_RUNTIME_ERROR_CODE_EDM_CONTROLLED](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the app is controlled by EDM.           [ABILITY_RUNTIME_ERROR_CODE_CROSS_APP](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the caller tries to start a different application.           [ABILITY_RUNTIME_ERROR_CODE_INTERNAL](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if an internal error occurs.           [ABILITY_RUNTIME_ERROR_CODE_NOT_TOP_ABILITY](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the caller is not top ability.           [ABILITY_RUNTIME_ERROR_CODE_MULTI_APP_NOT_SUPPORTED](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the app clone or multi-instance is            not supported.           [ABILITY_RUNTIME_ERROR_CODE_INVALID_APP_INSTANCE_KEY](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the app instance key is invalid.           [ABILITY_RUNTIME_ERROR_CODE_UPPER_LIMIT_REACHED](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the number of app instances has reached            the limit.           [ABILITY_RUNTIME_ERROR_MULTI_INSTANCE_NOT_SUPPORTED](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if multi-instance is not supported.           [ABILITY_RUNTIME_ERROR_CODE_APP_INSTANCE_KEY_NOT_SUPPORTED](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the APP_INSTANCE_KEY cannot            be specified. |

### OH_AbilityRuntime_ModObjExtensionContext_StartSelfUIAbilityWithStartOptions()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjExtensionContext_StartSelfUIAbilityWithStartOptions(OH_AbilityRuntime_ModObjExtensionContextHandle context, const AbilityBase_Want *want, const AbilityRuntime_StartOptions *options)
```

**Description**

Starts the self UIAbility with start options.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

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
| AbilityRuntime_ErrorCode | Returns a specific error code.           [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the call is successful.           [ABILITY_RUNTIME_ERROR_CODE_PERMISSION_DENIED](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the caller has no correct permission.           [ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the arguments provided are invalid.           [ABILITY_RUNTIME_ERROR_CODE_NOT_SUPPORTED](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the device does not support starting self UIAbility.           [ABILITY_RUNTIME_ERROR_CODE_NO_SUCH_ABILITY](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the target ability does not exist.           [ABILITY_RUNTIME_ERROR_CODE_INCORRECT_ABILITY_TYPE](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the ability type is incorrect.           [ABILITY_RUNTIME_ERROR_CODE_CROWDTEST_EXPIRED](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the crowdtesting application expires.           [ABILITY_RUNTIME_ERROR_CODE_WUKONG_MODE](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the ability cannot be started in Wukong mode.           [ABILITY_RUNTIME_ERROR_CODE_CONTROLLED](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the app is controlled.           [ABILITY_RUNTIME_ERROR_CODE_EDM_CONTROLLED](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the app is controlled by EDM.           [ABILITY_RUNTIME_ERROR_CODE_CROSS_APP](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the caller tries to start a different application.           [ABILITY_RUNTIME_ERROR_CODE_INTERNAL](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if an internal error occurs.           [ABILITY_RUNTIME_ERROR_CODE_NOT_TOP_ABILITY](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the caller is not a foreground process.           [ABILITY_RUNTIME_ERROR_VISIBILITY_SETTING_DISABLED](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if setting visibility is disabled.           [ABILITY_RUNTIME_ERROR_CODE_MULTI_APP_NOT_SUPPORTED](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the app clone or multi-instance is            not supported.           [ABILITY_RUNTIME_ERROR_CODE_INVALID_APP_INSTANCE_KEY](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the app instance key is invalid.           [ABILITY_RUNTIME_ERROR_CODE_UPPER_LIMIT_REACHED](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the number of app instances has reached            the limit.           [ABILITY_RUNTIME_ERROR_MULTI_INSTANCE_NOT_SUPPORTED](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if multi-instance is not supported.           [ABILITY_RUNTIME_ERROR_CODE_APP_INSTANCE_KEY_NOT_SUPPORTED](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the APP_INSTANCE_KEY cannot            be specified. |

### OH_AbilityRuntime_ModObjExtensionContext_TerminateSelf()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjExtensionContext_TerminateSelf(OH_AbilityRuntime_ModObjExtensionContextHandle context)
```

**Description**

Destroys the modular object extension.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjExtensionContextHandle](capi-abilityruntime-oh-abilityruntime-modularobjectextensioncontext8h.md) context | Represents a pointer to a modular object extension ability context. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>       <li>[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the call is successful.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the arguments provided are invalid.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_WUKONG_MODE](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the ability cannot be terminated in Wukong mode.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the context does not exist.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_INTERNAL](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if an internal error occurs.</li>       </ul> |

### OH_AbilityRuntime_ModObjExtensionContext_CreateIPCRemoteStub()

```c
OHIPCRemoteStub* OH_AbilityRuntime_ModObjExtensionContext_CreateIPCRemoteStub(OH_AbilityRuntime_ModObjExtensionContextHandle context, const char *descriptor, OH_OnRemoteRequestCallback requestCallback, OH_OnRemoteDestroyCallback destroyCallback, void *userData)
```

**Description**

Creates an <b>OHIPCRemoteStub</b> object with callbacks running on the extension's designated thread. The requestCallback and destroyCallback are invoked serially on the thread determined by the extension's [OH_AbilityRuntime_ThreadMode](capi-modular-object-extension-manager-h.md#oh_abilityruntime_threadmode). After calling [OH_AbilityRuntime_ModObjExtensionContext_DestroyIPCRemoteStub](capi-modular-object-extension-context-h.md#oh_abilityruntime_modobjextensioncontext_destroyipcremotestub), no new requestCallback invocations will occur, and any in-flight requestCallback will complete before destroyCallback is invoked.<br> The caller is responsible for destroying the returned object by calling [OH_AbilityRuntime_ModObjExtensionContext_DestroyIPCRemoteStub](capi-modular-object-extension-context-h.md#oh_abilityruntime_modobjextensioncontext_destroyipcremotestub) to avoid memory leaks.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

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

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjExtensionContextHandle](capi-abilityruntime-oh-abilityruntime-modularobjectextensioncontext8h.md) context | Represents a pointer to a modular object extension ability context. |
| OHIPCRemoteStub *stub | Pointer to the <b>OHIPCRemoteStub</b> object to destroy. |


