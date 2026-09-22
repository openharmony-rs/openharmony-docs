# modular_object_extension_ability.h

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @yzkp-->
<!--Designer: @yzkp-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=b64fba1a3bfa56ac6a22a458a141c3f45d9c160b translatedAt=2026-09-03T08:46:22.566Z pushedAt=2026-09-05T10:47:30.108Z -->

## Overview

Declares the interfaces of a ModularObjectExtensionAbility instance, including the capabilities of registering lifecycle callback functions and obtaining the context. It is applicable to scenarios where the lifecycle of ModularObjectExtensionAbility is processed.

**File to include:** <AbilityKit/ability_runtime/modular_object_extension_ability.h>

**Library:** libability_runtime.so

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 26.0.0

**Related module:** [AbilityRuntime](capi-abilityruntime.md)

## Summary

### Structs

| Name | typedef Keyword | Description |
| -- | -- | -- |
| [OH_AbilityRuntime_ModularObjectExtensionInstance](capi-abilityruntime-oh-abilityruntime-modularobjectextensioninstance.md) | OH_AbilityRuntime_ModObjExtensionInstance | Represents a ModularObjectExtensionAbility instance. |
| [OH_AbilityRuntime_ModObjExtensionInstance*](capi-abilityruntime-oh-abilityruntime-modobjextensioninstance8h.md) | OH_AbilityRuntime_ModObjExtensionInstanceHandle | Defines a pointer to OH_AbilityRuntime_ModObjExtensionInstance. |

### Functions

| Name | typedef Keyword | Description |
| -- | -- | -- |
| [typedef void (\*OH_AbilityRuntime_ModObjExtensionAbility_OnCreateFunc)(OH_AbilityRuntime_ModObjExtensionInstanceHandle instance, AbilityBase_Want *want)](#oh_abilityruntime_modobjextensionability_oncreatefunc) | OH_AbilityRuntime_ModObjExtensionAbility_OnCreateFunc | Defines a pointer to the callback function triggered when a ModularObjectExtensionAbility is created, used for initialization. |
| [typedef void (\*OH_AbilityRuntime_ModObjExtensionAbility_OnDestroyFunc)(OH_AbilityRuntime_ModObjExtensionInstanceHandle instance)](#oh_abilityruntime_modobjextensionability_ondestroyfunc) | OH_AbilityRuntime_ModObjExtensionAbility_OnDestroyFunc | Defines a pointer to the callback function triggered before a ModularObjectExtensionAbility is destroyed. |
| [typedef OHIPCRemoteStub* (\*OH_AbilityRuntime_ModObjExtensionAbility_OnConnectFunc)(OH_AbilityRuntime_ModObjExtensionInstanceHandle instance, AbilityBase_Want *want)](#oh_abilityruntime_modobjextensionability_onconnectfunc) | OH_AbilityRuntime_ModObjExtensionAbility_OnConnectFunc | Defines a pointer to the callback function triggered when a ModularObjectExtensionAbility is connected. |
| [typedef void (\*OH_AbilityRuntime_ModObjExtensionAbility_OnDisconnectFunc)(OH_AbilityRuntime_ModObjExtensionInstanceHandle instance)](#oh_abilityruntime_modobjextensionability_ondisconnectfunc) | OH_AbilityRuntime_ModObjExtensionAbility_OnDisconnectFunc | Defines a pointer to the callback function triggered when all connections to the current ModularObjectExtensionAbility are disconnected. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjExtensionAbility_RegisterOnCreateFunc(OH_AbilityRuntime_ModObjExtensionInstanceHandle instance, OH_AbilityRuntime_ModObjExtensionAbility_OnCreateFunc onCreateFunc)](#oh_abilityruntime_modobjextensionability_registeroncreatefunc) | - | Registers the [OH_AbilityRuntime_ModObjExtensionAbility_OnCreateFunc](capi-modular-object-extension-ability-h.md#oh_abilityruntime_modobjextensionability_oncreatefunc) callback function with the [OH_AbilityRuntime_ModObjExtensionInstance](capi-abilityruntime-oh-abilityruntime-modularobjectextensioninstance.md). |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjExtensionAbility_RegisterOnDestroyFunc(OH_AbilityRuntime_ModObjExtensionInstanceHandle instance, OH_AbilityRuntime_ModObjExtensionAbility_OnDestroyFunc onDestroyFunc)](#oh_abilityruntime_modobjextensionability_registerondestroyfunc) | - | Registers the [OH_AbilityRuntime_ModObjExtensionAbility_OnDestroyFunc](capi-modular-object-extension-ability-h.md#oh_abilityruntime_modobjextensionability_ondestroyfunc) callback function with the [OH_AbilityRuntime_ModObjExtensionInstance](capi-abilityruntime-oh-abilityruntime-modularobjectextensioninstance.md). |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjExtensionAbility_RegisterOnConnectFunc(OH_AbilityRuntime_ModObjExtensionInstanceHandle instance, OH_AbilityRuntime_ModObjExtensionAbility_OnConnectFunc onConnectFunc)](#oh_abilityruntime_modobjextensionability_registeronconnectfunc) | - | Registers the [OH_AbilityRuntime_ModObjExtensionAbility_OnConnectFunc](capi-modular-object-extension-ability-h.md#oh_abilityruntime_modobjextensionability_onconnectfunc) callback function with the [OH_AbilityRuntime_ModObjExtensionInstance](capi-abilityruntime-oh-abilityruntime-modularobjectextensioninstance.md). |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjExtensionAbility_RegisterOnDisconnectFunc(OH_AbilityRuntime_ModObjExtensionInstanceHandle instance, OH_AbilityRuntime_ModObjExtensionAbility_OnDisconnectFunc onDisconnectFunc)](#oh_abilityruntime_modobjextensionability_registerondisconnectfunc) | - | Registers the [OH_AbilityRuntime_ModObjExtensionAbility_OnDisconnectFunc](capi-modular-object-extension-ability-h.md#oh_abilityruntime_modobjextensionability_ondisconnectfunc) callback function with the [OH_AbilityRuntime_ModObjExtensionInstance](capi-abilityruntime-oh-abilityruntime-modularobjectextensioninstance.md). |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjExtensionAbility_GetContextFromInstance(OH_AbilityRuntime_ModObjExtensionInstanceHandle instance, OH_AbilityRuntime_ModObjExtensionContextHandle* context)](#oh_abilityruntime_modobjextensionability_getcontextfrominstance) | - | Obtains the ExtensionAbility context from a ModularObjectExtensionAbility instance. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjExtensionAbility_GetInstanceFromBase(AbilityRuntime_ExtensionInstanceHandle baseExtensionInstance, OH_AbilityRuntime_ModObjExtensionInstanceHandle* modObjExtensionInstance)](#oh_abilityruntime_modobjextensionability_getinstancefrombase) | - | Obtains a ModularObjectExtensionAbility instance from a base ExtensionAbility instance. |

## Function Description

### OH_AbilityRuntime_ModObjExtensionAbility_OnCreateFunc()

```c
typedef void (*OH_AbilityRuntime_ModObjExtensionAbility_OnCreateFunc)(OH_AbilityRuntime_ModObjExtensionInstanceHandle instance, AbilityBase_Want *want)
```

**Description**

Defines a pointer to the callback function invoked when a ModularObjectExtensionAbility is created, used for initialization.

**Since:** 26.0.0

**Parameters**

| Parameter | Description |
| -- | -- |
| OH_AbilityRuntime_ModObjExtensionInstanceHandle instance | Pointer to the [OH_AbilityRuntime_ModObjExtensionInstance](capi-abilityruntime-oh-abilityruntime-modularobjectextensioninstance.md) instance. |
| AbilityBase_Want \*want | Want information when the ModularObjectExtensionAbility is created. For details, see [AbilityBase_Want](capi-abilitybase-want.md). |

### OH_AbilityRuntime_ModObjExtensionAbility_OnDestroyFunc()

```c
typedef void (*OH_AbilityRuntime_ModObjExtensionAbility_OnDestroyFunc)(OH_AbilityRuntime_ModObjExtensionInstanceHandle instance)
```

**Description**

Called before the ModularObjectExtensionAbility instance is destroyed.

**Since:** 26.0.0

**Parameters**

| parameter item | Description |
| -- | -- |
| OH_AbilityRuntime_ModObjExtensionInstanceHandle instance | Pointer to the [OH_AbilityRuntime_ModObjExtensionInstance](capi-abilityruntime-oh-abilityruntime-modularobjectextensioninstance.md) instance. |

### OH_AbilityRuntime_ModObjExtensionAbility_OnConnectFunc()

```c
typedef OHIPCRemoteStub* (*OH_AbilityRuntime_ModObjExtensionAbility_OnConnectFunc)(OH_AbilityRuntime_ModObjExtensionInstanceHandle instance, AbilityBase_Want *want)
```

**Description**

Callback function invoked when the ModularObjectExtensionAbility is connected. It must return an OHIPCRemoteStub object to provide cross-process communication services.

**Since:** 26.0.0

**Parameters**

| Parameter item | Description |
| -- | -- |
| OH_AbilityRuntime_ModObjExtensionInstanceHandle instance | Pointer to the [OH_AbilityRuntime_ModObjExtensionInstance](capi-abilityruntime-oh-abilityruntime-modularobjectextensioninstance.md) instance. |
| AbilityBase_Want \*want | Want information when connecting to ModularObjectExtensionAbility. For details, see [AbilityBase_Want](capi-abilitybase-want.md). |

**Return**

| Type | Description |
| -- | -- |
| [OHIPCRemoteStub](../apis-ipc-kit/capi-ohipcparcel-ohipcremotestub.md)* | IPC remote stub object used for cross-process communication services. |

### OH_AbilityRuntime_ModObjExtensionAbility_OnDisconnectFunc()

```c
typedef void (*OH_AbilityRuntime_ModObjExtensionAbility_OnDisconnectFunc)(OH_AbilityRuntime_ModObjExtensionInstanceHandle instance)
```

**Description**

Callback function invoked when all client connections of the current ModularObjectExtensionAbility are disconnected.

**Since:** 26.0.0

**Parameters**

| Parameter item | Description |
| -- | -- |
| OH_AbilityRuntime_ModObjExtensionInstanceHandle instance | Pointer to the [OH_AbilityRuntime_ModObjExtensionInstance](capi-abilityruntime-oh-abilityruntime-modularobjectextensioninstance.md) instance. |

### OH_AbilityRuntime_ModObjExtensionAbility_RegisterOnCreateFunc()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjExtensionAbility_RegisterOnCreateFunc(OH_AbilityRuntime_ModObjExtensionInstanceHandle instance, OH_AbilityRuntime_ModObjExtensionAbility_OnCreateFunc onCreateFunc)
```

**Description**

Registers the [OH_AbilityRuntime_ModObjExtensionAbility_OnCreateFunc](capi-modular-object-extension-ability-h.md#oh_abilityruntime_modobjextensionability_oncreatefunc) callback function with the [OH_AbilityRuntime_ModObjExtensionInstance](capi-abilityruntime-oh-abilityruntime-modularobjectextensioninstance.md).

**Since:** 26.0.0

**Parameters**

| Parameter | Description |
| -- | -- |
| OH_AbilityRuntime_ModObjExtensionInstanceHandle instance | Pointer to the [OH_AbilityRuntime_ModObjExtensionInstance](capi-abilityruntime-oh-abilityruntime-modularobjectextensioninstance.md) instance. |
| [OH_AbilityRuntime_ModObjExtensionAbility_OnCreateFunc](capi-modular-object-extension-ability-h.md#oh_abilityruntime_modobjextensionability_oncreatefunc) onCreateFunc | Represents the OnCreate callback function to be registered. |

**Return**

| Type | Description |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | Result code.<br>         [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode): success.<br>         [ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode): parameter validation failed. Check whether the passed parameters are valid. |

### OH_AbilityRuntime_ModObjExtensionAbility_RegisterOnDestroyFunc()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjExtensionAbility_RegisterOnDestroyFunc(OH_AbilityRuntime_ModObjExtensionInstanceHandle instance, OH_AbilityRuntime_ModObjExtensionAbility_OnDestroyFunc onDestroyFunc)
```

**Description**

Registers the [OH_AbilityRuntime_ModObjExtensionAbility_OnDestroyFunc](capi-modular-object-extension-ability-h.md#oh_abilityruntime_modobjextensionability_ondestroyfunc) callback function with the [OH_AbilityRuntime_ModObjExtensionInstance](capi-abilityruntime-oh-abilityruntime-modularobjectextensioninstance.md).

**Since:** 26.0.0

**Parameters**

| Parameter item | Description |
| -- | -- |
| OH_AbilityRuntime_ModObjExtensionInstanceHandle instance | Pointer to the [OH_AbilityRuntime_ModObjExtensionInstance](capi-abilityruntime-oh-abilityruntime-modularobjectextensioninstance.md) instance. |
| [OH_AbilityRuntime_ModObjExtensionAbility_OnDestroyFunc](capi-modular-object-extension-ability-h.md#oh_abilityruntime_modobjextensionability_ondestroyfunc) onDestroyFunc | Callback function to be registered for OnDestroy. |

**Return**

| Type | Description |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | Result code.<br>         Returns [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the API call is successful.<br>         Returns [ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if parameter validation fails. Check whether the input parameters are valid. |

### OH_AbilityRuntime_ModObjExtensionAbility_RegisterOnConnectFunc()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjExtensionAbility_RegisterOnConnectFunc(OH_AbilityRuntime_ModObjExtensionInstanceHandle instance, OH_AbilityRuntime_ModObjExtensionAbility_OnConnectFunc onConnectFunc)
```

**Description**

Registers the [OH_AbilityRuntime_ModObjExtensionAbility_OnConnectFunc](capi-modular-object-extension-ability-h.md#oh_abilityruntime_modobjextensionability_onconnectfunc) callback function with the [OH_AbilityRuntime_ModObjExtensionInstance](capi-abilityruntime-oh-abilityruntime-modularobjectextensioninstance.md).

**Since:** 26.0.0

**Parameters**

| Parameter | Description |
| -- | -- |
| OH_AbilityRuntime_ModObjExtensionInstanceHandle instance | Pointer to the [OH_AbilityRuntime_ModObjExtensionInstance](capi-abilityruntime-oh-abilityruntime-modularobjectextensioninstance.md) instance. |
| [OH_AbilityRuntime_ModObjExtensionAbility_OnConnectFunc](capi-modular-object-extension-ability-h.md#oh_abilityruntime_modobjextensionability_onconnectfunc) onConnectFunc | OnConnect callback function to be registered. |

**Return**

| Type | Description |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | Result code.<br>         [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode): The API call is successful.<br>         [ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode): Parameter validation failed. Check whether the input parameters are valid. |

### OH_AbilityRuntime_ModObjExtensionAbility_RegisterOnDisconnectFunc()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjExtensionAbility_RegisterOnDisconnectFunc(OH_AbilityRuntime_ModObjExtensionInstanceHandle instance, OH_AbilityRuntime_ModObjExtensionAbility_OnDisconnectFunc onDisconnectFunc)
```

**Description**

Registers the [OH_AbilityRuntime_ModObjExtensionAbility_OnDisconnectFunc](capi-modular-object-extension-ability-h.md#oh_abilityruntime_modobjextensionability_ondisconnectfunc) callback function with the [OH_AbilityRuntime_ModObjExtensionInstance](capi-abilityruntime-oh-abilityruntime-modularobjectextensioninstance.md).

**Since:** 26.0.0

**Parameters**

| Parameter item | Description |
| -- | -- |
| OH_AbilityRuntime_ModObjExtensionInstanceHandle instance | Pointer to the [OH_AbilityRuntime_ModObjExtensionInstance](capi-abilityruntime-oh-abilityruntime-modularobjectextensioninstance.md) instance. |
| [OH_AbilityRuntime_ModObjExtensionAbility_OnDisconnectFunc](capi-modular-object-extension-ability-h.md#oh_abilityruntime_modobjextensionability_ondisconnectfunc) onDisconnectFunc | Indicates the OnDisconnect callback function to be registered. |

**Return**

| Type | Description |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | Result code.<br>         Returns [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the API call is successful.<br>         Returns [ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if parameter validation fails. Check whether the input parameters are valid. |

### OH_AbilityRuntime_ModObjExtensionAbility_GetContextFromInstance()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjExtensionAbility_GetContextFromInstance(OH_AbilityRuntime_ModObjExtensionInstanceHandle instance, OH_AbilityRuntime_ModObjExtensionContextHandle* context)
```

**Description**

Obtains the ExtensionAbility context from a ModularObjectExtensionAbility instance.

**Since:** 26.0.0

**Parameters**

| Parameter item | Description |
| -- | -- |
| OH_AbilityRuntime_ModObjExtensionInstanceHandle instance | Pointer to the [OH_AbilityRuntime_ModObjExtensionInstance](capi-abilityruntime-oh-abilityruntime-modularobjectextensioninstance.md) instance. |
| [OH_AbilityRuntime_ModObjExtensionContextHandle](capi-abilityruntime-oh-abilityruntime-modularobjectextensioncontext8h.md)* context | Pointer to OH_AbilityRuntime_ModObjExtensionContextHandle, used to receive the ExtensionAbility context, as an output parameter. |

**Return**

| Type | Description |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | Result code.<br>         Returns [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the API call is successful.<br>         Returns [ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if parameter validation fails. Check whether the input parameters are valid. |

### OH_AbilityRuntime_ModObjExtensionAbility_GetInstanceFromBase()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjExtensionAbility_GetInstanceFromBase(AbilityRuntime_ExtensionInstanceHandle baseExtensionInstance, OH_AbilityRuntime_ModObjExtensionInstanceHandle* modObjExtensionInstance)
```

**Description**

Obtains a ModularObjectExtensionAbility instance from a base ExtensionAbility instance. If the passed-in instance is not of the ModularObjectExtensionAbility type, the error code ABILITY_RUNTIME_ERROR_CODE_INCORRECT_ABILITY_TYPE is returned.

**Since:** 26.0.0

**Parameters**

| Parameter | Description |
| -- | -- |
| AbilityRuntime_ExtensionInstanceHandle baseExtensionInstance | Pointer to [AbilityRuntime_ExtensionInstance](capi-abilityruntime-extensioninstance.md). |
| [OH_AbilityRuntime_ModObjExtensionInstanceHandle](capi-abilityruntime-oh-abilityruntime-modobjextensioninstance8h.md)* modObjExtensionInstance | Pointer to OH_AbilityRuntime_ModObjExtensionInstance, used to receive the ModularObjectExtensionAbility instance as an output parameter. |

**Return**

| Type | Description |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | Returns a specific error code.<br>         [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) The API call is successful.<br>         [ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) Parameter validation fails. Check whether the input parameters are valid.<br>         [ABILITY_RUNTIME_ERROR_CODE_INCORRECT_ABILITY_TYPE](capi-ability-runtime-common-h.md#abilityruntime_errorcode) The ExtensionAbility instance is not of the ModularObjectExtensionAbility type. Ensure that the type of the ExtensionAbility instance passed in is correct. |


