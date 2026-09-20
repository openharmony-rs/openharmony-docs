# modular_object_extension_context.h

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @yzkp-->
<!--Designer: @yzkp-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=b64fba1a3bfa56ac6a22a458a141c3f45d9c160b translatedAt=2026-09-03T08:48:55.967Z pushedAt=2026-09-05T10:47:30.106Z -->

## Overview

Declares the context APIs of ModularObjectExtensionAbility, including starting a UIAbility, destroying the ModularObjectExtensionAbility itself, and creating and destroying IPC objects.

**File to include:** <AbilityKit/ability_runtime/modular_object_extension_context.h>

**Library:** libability_runtime.so

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 26.0.0

**Related module:** [AbilityRuntime](capi-abilityruntime.md)

## Summary

### Structs

| Name | typedef Keyword | Description |
| -- | -- | -- |
| [OH_AbilityRuntime_ModularObjectExtensionContext*](capi-abilityruntime-oh-abilityruntime-modularobjectextensioncontext8h.md) | OH_AbilityRuntime_ModObjExtensionContextHandle | Represents the handle to the ModularObjectExtensionAbility context. |

### Functions

| Name | Description |
| -- | -- |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjExtensionContext_GetBaseContext(OH_AbilityRuntime_ModObjExtensionContextHandle modObjExtensionContext, AbilityRuntime_ContextHandle* baseContext)](#oh_abilityruntime_modobjextensioncontext_getbasecontext) | Obtains the base context from the ModularObjectExtensionAbility context. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjExtensionContext_StartSelfUIAbility(OH_AbilityRuntime_ModObjExtensionContextHandle context, const AbilityBase_Want *want)](#oh_abilityruntime_modobjextensioncontext_startselfuiability) | Starts the UIAbility of the current application. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjExtensionContext_StartSelfUIAbilityWithStartOptions(OH_AbilityRuntime_ModObjExtensionContextHandle context, const AbilityBase_Want *want, const AbilityRuntime_StartOptions *options)](#oh_abilityruntime_modobjextensioncontext_startselfuiabilitywithstartoptions) | Starts the UIAbility of the current application with StartOptions. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjExtensionContext_TerminateSelf(OH_AbilityRuntime_ModObjExtensionContextHandle context)](#oh_abilityruntime_modobjextensioncontext_terminateself) | Destroys the ModularObjectExtensionAbility itself. |
| [OHIPCRemoteStub* OH_AbilityRuntime_ModObjExtensionContext_CreateIPCRemoteStub(OH_AbilityRuntime_ModObjExtensionContextHandle context, const char *descriptor, OH_OnRemoteRequestCallback requestCallback, OH_OnRemoteDestroyCallback destroyCallback, void *userData)](#oh_abilityruntime_modobjextensioncontext_createipcremotestub) | Creates an OHIPCRemoteStub object. The callback functions run on the thread specified by the ExtensionAbility. requestCallback and destroyCallback are executed in sequence on the thread determined by the [OH_AbilityRuntime_ThreadMode](capi-modular-object-extension-manager-h.md#oh_abilityruntime_threadmode) of the ExtensionAbility. After [OH_AbilityRuntime_ModObjExtensionContext_DestroyIPCRemoteStub](capi-modular-object-extension-context-h.md#oh_abilityruntime_modobjextensioncontext_destroyipcremotestub) is called, no new requestCallback is invoked, and destroyCallback is invoked only after the ongoing requestCallback is complete. The caller must call [OH_AbilityRuntime_ModObjExtensionContext_DestroyIPCRemoteStub](capi-modular-object-extension-context-h.md#oh_abilityruntime_modobjextensioncontext_destroyipcremotestub) to destroy the returned object to avoid memory leaks. |
| [void OH_AbilityRuntime_ModObjExtensionContext_DestroyIPCRemoteStub(OH_AbilityRuntime_ModObjExtensionContextHandle context, OHIPCRemoteStub *stub)](#oh_abilityruntime_modobjextensioncontext_destroyipcremotestub) | Destroys the OHIPCRemoteStub object. |

## Function Description

### OH_AbilityRuntime_ModObjExtensionContext_GetBaseContext()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjExtensionContext_GetBaseContext(OH_AbilityRuntime_ModObjExtensionContextHandle modObjExtensionContext, AbilityRuntime_ContextHandle* baseContext)
```

**Description**

Obtains the base context from the ModularObjectExtensionAbility context.

**Since:** 26.0.0

**Parameters**

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjExtensionContextHandle](capi-abilityruntime-oh-abilityruntime-modularobjectextensioncontext8h.md) modObjExtensionContext | Pointer to the ModularObjectExtensionAbility context. |
| AbilityRuntime_ContextHandle* baseContext | Pointer to [AbilityRuntime_ContextHandle](capi-abilityruntime-abilityruntime-context8h.md), used to receive the result. |

**Return**

| Type | Description |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | Result code.<br>         Returns [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the API call is successful.<br>         Returns [ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if parameter verification fails. |

### OH_AbilityRuntime_ModObjExtensionContext_StartSelfUIAbility()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjExtensionContext_StartSelfUIAbility(OH_AbilityRuntime_ModObjExtensionContextHandle context, const AbilityBase_Want *want)
```

**Description**

Starts the UIAbility of the current app.

**Required permissions:** ohos.permission.NDK_START_SELF_UI_ABILITY

**Since:** 26.0.0

**Parameters**

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjExtensionContextHandle](capi-abilityruntime-oh-abilityruntime-modularobjectextensioncontext8h.md) context | Pointer to the ModularObjectExtensionAbility context. |
| const [AbilityBase_Want](capi-abilitybase-want.md) *want | Want information required for starting the UIAbility of the current application. For details, see [AbilityBase_Want](capi-abilitybase-want.md). |

**Return**

| Type | Description |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | Result code.<br>         [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode): API call succeeded.<br>         [ABILITY_RUNTIME_ERROR_CODE_PERMISSION_DENIED](capi-ability-runtime-common-h.md#abilityruntime_errorcode): the caller does not have the required permission.<br>         [ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode): invalid input parameter.<br>         [ABILITY_RUNTIME_ERROR_CODE_NOT_SUPPORTED](capi-ability-runtime-common-h.md#abilityruntime_errorcode): the device does not support starting the UIAbility of the current application.<br>         [ABILITY_RUNTIME_ERROR_CODE_NO_SUCH_ABILITY](capi-ability-runtime-common-h.md#abilityruntime_errorcode): the target ability does not exist.<br>         [ABILITY_RUNTIME_ERROR_CODE_INCORRECT_ABILITY_TYPE](capi-ability-runtime-common-h.md#abilityruntime_errorcode): incorrect ability type.<br>         [ABILITY_RUNTIME_ERROR_CODE_CROWDTEST_EXPIRED](capi-ability-runtime-common-h.md#abilityruntime_errorcode): the crowdtest application has expired.<br>         [ABILITY_RUNTIME_ERROR_CODE_WUKONG_MODE](capi-ability-runtime-common-h.md#abilityruntime_errorcode): the ability cannot be started in Wukong mode.<br>         [ABILITY_RUNTIME_ERROR_CODE_CONTROLLED](capi-ability-runtime-common-h.md#abilityruntime_errorcode): the application is controlled.<br>         [ABILITY_RUNTIME_ERROR_CODE_EDM_CONTROLLED](capi-ability-runtime-common-h.md#abilityruntime_errorcode): the application is controlled by EDM.<br>         [ABILITY_RUNTIME_ERROR_CODE_CROSS_APP](capi-ability-runtime-common-h.md#abilityruntime_errorcode): the caller attempts to start a different application.<br>         [ABILITY_RUNTIME_ERROR_CODE_INTERNAL](capi-ability-runtime-common-h.md#abilityruntime_errorcode): internal error.<br>         [ABILITY_RUNTIME_ERROR_CODE_NOT_TOP_ABILITY](capi-ability-runtime-common-h.md#abilityruntime_errorcode): the caller process is not in the foreground.<br>                 [ABILITY_RUNTIME_ERROR_CODE_MULTI_APP_NOT_SUPPORTED](capi-ability-runtime-common-h.md#abilityruntime_errorcode): application clone and multi-instance are not supported.<br>         [ABILITY_RUNTIME_ERROR_CODE_INVALID_APP_INSTANCE_KEY](capi-ability-runtime-common-h.md#abilityruntime_errorcode): invalid application instance key.<br>         [ABILITY_RUNTIME_ERROR_CODE_UPPER_LIMIT_REACHED](capi-ability-runtime-common-h.md#abilityruntime_errorcode): the number of application instances has reached the upper limit.<br>         [ABILITY_RUNTIME_ERROR_MULTI_INSTANCE_NOT_SUPPORTED](capi-ability-runtime-common-h.md#abilityruntime_errorcode): application multi-instance is not supported.<br>         [ABILITY_RUNTIME_ERROR_CODE_APP_INSTANCE_KEY_NOT_SUPPORTED](capi-ability-runtime-common-h.md#abilityruntime_errorcode): setting APP_INSTANCE_KEY is not allowed. |

### OH_AbilityRuntime_ModObjExtensionContext_StartSelfUIAbilityWithStartOptions()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjExtensionContext_StartSelfUIAbilityWithStartOptions(OH_AbilityRuntime_ModObjExtensionContextHandle context, const AbilityBase_Want *want, const AbilityRuntime_StartOptions *options)
```

**Description**

Starts the UIAbility of the current app with StartOptions.

**Required permissions:** ohos.permission.NDK_START_SELF_UI_ABILITY

**Since:** 26.0.0

**Parameters**

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjExtensionContextHandle](capi-abilityruntime-oh-abilityruntime-modularobjectextensioncontext8h.md) context | Pointer to the ModularObjectExtensionAbility context. |
| const [AbilityBase_Want](capi-abilitybase-want.md) *want | Want information required for starting the UIAbility of the current application. For details, see [AbilityBase_Want](capi-abilitybase-want.md). |
| const [AbilityRuntime_StartOptions](capi-abilityruntime-startoptions.md) *options | StartOptions information required for starting the UIAbility of the current application. For details, see [AbilityRuntime_StartOptions](capi-abilityruntime-startoptions.md). |

**Return**

| Type | Description |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | Result code.<br>         [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) API call succeeded.<br>         [ABILITY_RUNTIME_ERROR_CODE_PERMISSION_DENIED](capi-ability-runtime-common-h.md#abilityruntime_errorcode) The caller does not have the required permission.<br>         [ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) Invalid input parameter.<br>         [ABILITY_RUNTIME_ERROR_CODE_NOT_SUPPORTED](capi-ability-runtime-common-h.md#abilityruntime_errorcode) The device does not support starting the UIAbility of the current application.<br>         [ABILITY_RUNTIME_ERROR_CODE_NO_SUCH_ABILITY](capi-ability-runtime-common-h.md#abilityruntime_errorcode) The target ability does not exist.<br>         [ABILITY_RUNTIME_ERROR_CODE_INCORRECT_ABILITY_TYPE](capi-ability-runtime-common-h.md#abilityruntime_errorcode) Incorrect ability type.<br>         [ABILITY_RUNTIME_ERROR_CODE_CROWDTEST_EXPIRED](capi-ability-runtime-common-h.md#abilityruntime_errorcode) The crowdtest application has expired.<br>         [ABILITY_RUNTIME_ERROR_CODE_WUKONG_MODE](capi-ability-runtime-common-h.md#abilityruntime_errorcode) The ability cannot be started in Wukong mode.<br>         [ABILITY_RUNTIME_ERROR_CODE_CONTROLLED](capi-ability-runtime-common-h.md#abilityruntime_errorcode) The application is controlled.<br>         [ABILITY_RUNTIME_ERROR_CODE_EDM_CONTROLLED](capi-ability-runtime-common-h.md#abilityruntime_errorcode) The application is controlled by EDM.<br>         [ABILITY_RUNTIME_ERROR_CODE_CROSS_APP](capi-ability-runtime-common-h.md#abilityruntime_errorcode) The caller attempts to start a different application.<br>         [ABILITY_RUNTIME_ERROR_CODE_INTERNAL](capi-ability-runtime-common-h.md#abilityruntime_errorcode) Internal error.<br>         [ABILITY_RUNTIME_ERROR_CODE_NOT_TOP_ABILITY](capi-ability-runtime-common-h.md#abilityruntime_errorcode) The caller process is not in the foreground.<br>         [ABILITY_RUNTIME_ERROR_VISIBILITY_SETTING_DISABLED](capi-ability-runtime-common-h.md#abilityruntime_errorcode) Visibility setting is disabled.<br>         [ABILITY_RUNTIME_ERROR_CODE_MULTI_APP_NOT_SUPPORTED](capi-ability-runtime-common-h.md#abilityruntime_errorcode) App clone and multi-instance are not supported.<br>         [ABILITY_RUNTIME_ERROR_CODE_INVALID_APP_INSTANCE_KEY](capi-ability-runtime-common-h.md#abilityruntime_errorcode) Invalid application instance key.<br>         [ABILITY_RUNTIME_ERROR_CODE_UPPER_LIMIT_REACHED](capi-ability-runtime-common-h.md#abilityruntime_errorcode) The number of application instances has reached the upper limit.<br>         [ABILITY_RUNTIME_ERROR_MULTI_INSTANCE_NOT_SUPPORTED](capi-ability-runtime-common-h.md#abilityruntime_errorcode) Application multi-instance is not supported.<br>         [ABILITY_RUNTIME_ERROR_CODE_APP_INSTANCE_KEY_NOT_SUPPORTED](capi-ability-runtime-common-h.md#abilityruntime_errorcode) Setting APP_INSTANCE_KEY is not allowed. |

### OH_AbilityRuntime_ModObjExtensionContext_TerminateSelf()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjExtensionContext_TerminateSelf(OH_AbilityRuntime_ModObjExtensionContextHandle context)
```

**Description**

Destroys the ModularObjectExtensionAbility itself.

**Since:** 26.0.0

**Parameters**

| Parameter item | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjExtensionContextHandle](capi-abilityruntime-oh-abilityruntime-modularobjectextensioncontext8h.md) context | Pointer to the ModularObjectExtensionAbility context. |

**Return**

| Type | Description |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | Result code.<br>         Returns [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the API call is successful.<br>         Returns [ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the input parameter is invalid.<br>         Returns [ABILITY_RUNTIME_ERROR_CODE_WUKONG_MODE](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the ability cannot be destroyed in Wukong mode.<br>         Returns [ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the context does not exist.<br>         Returns [ABILITY_RUNTIME_ERROR_CODE_INTERNAL](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if an internal error occurs. |

### OH_AbilityRuntime_ModObjExtensionContext_CreateIPCRemoteStub()

```c
OHIPCRemoteStub* OH_AbilityRuntime_ModObjExtensionContext_CreateIPCRemoteStub(OH_AbilityRuntime_ModObjExtensionContextHandle context, const char *descriptor, OH_OnRemoteRequestCallback requestCallback, OH_OnRemoteDestroyCallback destroyCallback, void *userData)
```

**Description**

Creates an OHIPCRemoteStub object. The callbacks run on the thread specified by the ExtensionAbility. requestCallback and destroyCallback are executed in sequence on the thread determined by the [OH_AbilityRuntime_ThreadMode](capi-modular-object-extension-manager-h.md#oh_abilityruntime_threadmode) of the ExtensionAbility. After [OH_AbilityRuntime_ModObjExtensionContext_DestroyIPCRemoteStub](capi-modular-object-extension-context-h.md#oh_abilityruntime_modobjextensioncontext_destroyipcremotestub) is called, no new requestCallback will be invoked, and destroyCallback is invoked only after the ongoing requestCallback completes. The caller must call [OH_AbilityRuntime_ModObjExtensionContext_DestroyIPCRemoteStub](capi-modular-object-extension-context-h.md#oh_abilityruntime_modobjextensioncontext_destroyipcremotestub) to destroy the returned object to avoid memory leaks.

**Since:** 26.0.0

**Parameters**

| Parameter item | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjExtensionContextHandle](capi-abilityruntime-oh-abilityruntime-modularobjectextensioncontext8h.md) context | Pointer to the ModularObjectExtensionAbility context. |
| const char *descriptor | Pointer to the descriptor of the OHIPCRemoteStub object to create. It cannot be NULL. The string is copied internally during creation, and the caller can release the descriptor after this function returns. |
| OH_OnRemoteRequestCallback requestCallback | Callback function for processing data requests. It cannot be NULL. |
| OH_OnRemoteDestroyCallback destroyCallback | Callback function invoked when the object is destroyed. It can be NULL. |
| void *userData | Pointer to the user data. It can be NULL and must remain valid until the object is destroyed. |

**Return**

| Type | Description |
| -- | -- |
| OHIPCRemoteStub* | Pointer to the created OHIPCRemoteStub object if the operation is successful; NULL otherwise. |

### OH_AbilityRuntime_ModObjExtensionContext_DestroyIPCRemoteStub()

```c
void OH_AbilityRuntime_ModObjExtensionContext_DestroyIPCRemoteStub(OH_AbilityRuntime_ModObjExtensionContextHandle context, OHIPCRemoteStub *stub)
```

**Description**

Destroys the OHIPCRemoteStub object.

**Since:** 26.0.0

**Parameters**

| Parameter item | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjExtensionContextHandle](capi-abilityruntime-oh-abilityruntime-modularobjectextensioncontext8h.md) context | Pointer to the ModularObjectExtensionAbility context. |
| OHIPCRemoteStub *stub | Pointer to the OHIPCRemoteStub object to destroy. |


