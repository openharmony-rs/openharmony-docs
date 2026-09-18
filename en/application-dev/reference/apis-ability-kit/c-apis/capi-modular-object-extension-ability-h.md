# modular_object_extension_ability.h

## Overview

Declares the modular object extension ability.

**Library**: libability_runtime.so

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 13

**Related module**: [AbilityRuntime](capi-abilityruntime.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AbilityRuntime_ModularObjectExtensionInstance](capi-abilityruntime-oh-abilityruntime-modularobjectextensioninstance.md) | OH_AbilityRuntime_ModObjExtensionInstance | Defines the struct for OH_AbilityRuntime_ModObjExtensionInstance. |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef void (\*OH_AbilityRuntime_ModObjExtensionAbility_OnCreateFunc)(OH_AbilityRuntime_ModObjExtensionInstanceHandle instance, AbilityBase_Want *want)](#oh_abilityruntime_modobjextensionability_oncreatefunc) | OH_AbilityRuntime_ModObjExtensionAbility_OnCreateFunc | Callback invoked when a modular object extension is started for initialization. |
| [typedef void (\*OH_AbilityRuntime_ModObjExtensionAbility_OnDestroyFunc)(OH_AbilityRuntime_ModObjExtensionInstanceHandle instance)](#oh_abilityruntime_modobjextensionability_ondestroyfunc) | OH_AbilityRuntime_ModObjExtensionAbility_OnDestroyFunc | Callback invoked before a modular object extension is destroyed. |
| [typedef OHIPCRemoteStub* (\*OH_AbilityRuntime_ModObjExtensionAbility_OnConnectFunc)(OH_AbilityRuntime_ModObjExtensionInstanceHandle instance, AbilityBase_Want *want)](#oh_abilityruntime_modobjextensionability_onconnectfunc) | OH_AbilityRuntime_ModObjExtensionAbility_OnConnectFunc | Callback invoked when a modular object extension is connected to an ability. |
| [typedef void (\*OH_AbilityRuntime_ModObjExtensionAbility_OnDisconnectFunc)(OH_AbilityRuntime_ModObjExtensionInstanceHandle instance)](#oh_abilityruntime_modobjextensionability_ondisconnectfunc) | OH_AbilityRuntime_ModObjExtensionAbility_OnDisconnectFunc | Callback invoked when all abilities connected to a modular object extension are disconnected. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjExtensionAbility_RegisterOnCreateFunc(OH_AbilityRuntime_ModObjExtensionInstanceHandle instance, OH_AbilityRuntime_ModObjExtensionAbility_OnCreateFunc onCreateFunc)](#oh_abilityruntime_modobjextensionability_registeroncreatefunc) | - | Registers the function [OH_AbilityRuntime_ModObjExtensionAbility_OnCreateFunc](capi-modular-object-extension-ability-h.md#oh_abilityruntime_modobjextensionability_oncreatefunc) with [OH_AbilityRuntime_ModObjExtensionInstance](capi-abilityruntime-oh-abilityruntime-modularobjectextensioninstance.md). |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjExtensionAbility_RegisterOnDestroyFunc(OH_AbilityRuntime_ModObjExtensionInstanceHandle instance, OH_AbilityRuntime_ModObjExtensionAbility_OnDestroyFunc onDestroyFunc)](#oh_abilityruntime_modobjextensionability_registerondestroyfunc) | - | Registers the function [OH_AbilityRuntime_ModObjExtensionAbility_OnDestroyFunc](capi-modular-object-extension-ability-h.md#oh_abilityruntime_modobjextensionability_ondestroyfunc) with [OH_AbilityRuntime_ModObjExtensionInstance](capi-abilityruntime-oh-abilityruntime-modularobjectextensioninstance.md). |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjExtensionAbility_RegisterOnConnectFunc(OH_AbilityRuntime_ModObjExtensionInstanceHandle instance, OH_AbilityRuntime_ModObjExtensionAbility_OnConnectFunc onConnectFunc)](#oh_abilityruntime_modobjextensionability_registeronconnectfunc) | - | Registers the function [OH_AbilityRuntime_ModObjExtensionAbility_OnConnectFunc](capi-modular-object-extension-ability-h.md#oh_abilityruntime_modobjextensionability_onconnectfunc) with [OH_AbilityRuntime_ModObjExtensionInstance](capi-abilityruntime-oh-abilityruntime-modularobjectextensioninstance.md). |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjExtensionAbility_RegisterOnDisconnectFunc(OH_AbilityRuntime_ModObjExtensionInstanceHandle instance, OH_AbilityRuntime_ModObjExtensionAbility_OnDisconnectFunc onDisconnectFunc)](#oh_abilityruntime_modobjextensionability_registerondisconnectfunc) | - | Registers the function [OH_AbilityRuntime_ModObjExtensionAbility_OnDisconnectFunc](capi-modular-object-extension-ability-h.md#oh_abilityruntime_modobjextensionability_ondisconnectfunc) with [OH_AbilityRuntime_ModObjExtensionInstance](capi-abilityruntime-oh-abilityruntime-modularobjectextensioninstance.md). |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjExtensionAbility_GetContextFromInstance(OH_AbilityRuntime_ModObjExtensionInstanceHandle instance, OH_AbilityRuntime_ModObjExtensionContextHandle* context)](#oh_abilityruntime_modobjextensionability_getcontextfrominstance) | - | Gets the extension context from the modular object extension instance. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjExtensionAbility_GetInstanceFromBase(AbilityRuntime_ExtensionInstanceHandle baseExtensionInstance, OH_AbilityRuntime_ModObjExtensionInstanceHandle* modObjExtensionInstance)](#oh_abilityruntime_modobjextensionability_getinstancefrombase) | - | Gets the modular object extension instance from a base extension instance. |

### Variable

| Name | Description |
| -- | -- |
| OH_AbilityRuntime_ModObjExtensionInstance* OH_AbilityRuntime_ModObjExtensionInstanceHandle | Defines the pointer to OH_AbilityRuntime_ModObjExtensionInstance.<br>**Since**: 26.0.0 |
| void (*OH_AbilityRuntime_ModObjExtensionAbility_OnCreateFunc)( OH_AbilityRuntime_ModObjExtensionInstanceHandle instance, AbilityBase_Want *want) | Callback invoked when a modular object extension is started for initialization.<br>**Since**: 26.0.0 |
| void (*OH_AbilityRuntime_ModObjExtensionAbility_OnDestroyFunc)( OH_AbilityRuntime_ModObjExtensionInstanceHandle instance) | Callback invoked before a modular object extension is destroyed.<br>**Since**: 26.0.0 |
| OHIPCRemoteStub* (*OH_AbilityRuntime_ModObjExtensionAbility_OnConnectFunc)( OH_AbilityRuntime_ModObjExtensionInstanceHandle instance, AbilityBase_Want *want) | Callback invoked when a modular object extension is connected to an ability.<br>**Since**: 26.0.0 |
| void (*OH_AbilityRuntime_ModObjExtensionAbility_OnDisconnectFunc)( OH_AbilityRuntime_ModObjExtensionInstanceHandle instance) | Callback invoked when all abilities connected to a modular object extension are disconnected.<br>**Since**: 26.0.0 |

## Function description

### OH_AbilityRuntime_ModObjExtensionAbility_OnCreateFunc()

```c
typedef void (*OH_AbilityRuntime_ModObjExtensionAbility_OnCreateFunc)(OH_AbilityRuntime_ModObjExtensionInstanceHandle instance, AbilityBase_Want *want)
```

**Description**

Callback invoked when a modular object extension is started for initialization.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AbilityRuntime_ModObjExtensionInstanceHandle instance | Points to an [OH_AbilityRuntime_ModObjExtensionInstance](capi-abilityruntime-oh-abilityruntime-modularobjectextensioninstance.md) instance. |
| AbilityBase_Want \*want | Indicates the want of created modular object extension. For details, see {@link AbilityBase_Want}. |

### OH_AbilityRuntime_ModObjExtensionAbility_OnDestroyFunc()

```c
typedef void (*OH_AbilityRuntime_ModObjExtensionAbility_OnDestroyFunc)(OH_AbilityRuntime_ModObjExtensionInstanceHandle instance)
```

**Description**

Callback invoked before a modular object extension is destroyed.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AbilityRuntime_ModObjExtensionInstanceHandle instance | Points to an [OH_AbilityRuntime_ModObjExtensionInstance](capi-abilityruntime-oh-abilityruntime-modularobjectextensioninstance.md) instance. |

### OH_AbilityRuntime_ModObjExtensionAbility_OnConnectFunc()

```c
typedef OHIPCRemoteStub* (*OH_AbilityRuntime_ModObjExtensionAbility_OnConnectFunc)(OH_AbilityRuntime_ModObjExtensionInstanceHandle instance, AbilityBase_Want *want)
```

**Description**

Callback invoked when a modular object extension is connected to an ability.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AbilityRuntime_ModObjExtensionInstanceHandle instance | Points to an [OH_AbilityRuntime_ModObjExtensionInstance](capi-abilityruntime-oh-abilityruntime-modularobjectextensioninstance.md) instance. |
| AbilityBase_Want \*want | Indicates the want of created modular object extension. |

### OH_AbilityRuntime_ModObjExtensionAbility_OnDisconnectFunc()

```c
typedef void (*OH_AbilityRuntime_ModObjExtensionAbility_OnDisconnectFunc)(OH_AbilityRuntime_ModObjExtensionInstanceHandle instance)
```

**Description**

Callback invoked when all abilities connected to a modular object extension are disconnected.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AbilityRuntime_ModObjExtensionInstanceHandle instance | Points to an [OH_AbilityRuntime_ModObjExtensionInstance](capi-abilityruntime-oh-abilityruntime-modularobjectextensioninstance.md) instance. |

### OH_AbilityRuntime_ModObjExtensionAbility_RegisterOnCreateFunc()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjExtensionAbility_RegisterOnCreateFunc(OH_AbilityRuntime_ModObjExtensionInstanceHandle instance, OH_AbilityRuntime_ModObjExtensionAbility_OnCreateFunc onCreateFunc)
```

**Description**

Registers the function [OH_AbilityRuntime_ModObjExtensionAbility_OnCreateFunc](capi-modular-object-extension-ability-h.md#oh_abilityruntime_modobjextensionability_oncreatefunc) with [OH_AbilityRuntime_ModObjExtensionInstance](capi-abilityruntime-oh-abilityruntime-modularobjectextensioninstance.md).

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AbilityRuntime_ModObjExtensionInstanceHandle instance | Points to an [OH_AbilityRuntime_ModObjExtensionInstance](capi-abilityruntime-oh-abilityruntime-modularobjectextensioninstance.md) instance. |
| [OH_AbilityRuntime_ModObjExtensionAbility_OnCreateFunc](capi-modular-object-extension-ability-h.md#oh_abilityruntime_modobjextensionability_oncreatefunc) onCreateFunc | Represents the onCreate callback function. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | Returns a specific error code.          {@link ABILITY_RUNTIME_ERROR_CODE_NO_ERROR} success.<br>        {@link ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID} parameter check failed. |

### OH_AbilityRuntime_ModObjExtensionAbility_RegisterOnDestroyFunc()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjExtensionAbility_RegisterOnDestroyFunc(OH_AbilityRuntime_ModObjExtensionInstanceHandle instance, OH_AbilityRuntime_ModObjExtensionAbility_OnDestroyFunc onDestroyFunc)
```

**Description**

Registers the function [OH_AbilityRuntime_ModObjExtensionAbility_OnDestroyFunc](capi-modular-object-extension-ability-h.md#oh_abilityruntime_modobjextensionability_ondestroyfunc) with [OH_AbilityRuntime_ModObjExtensionInstance](capi-abilityruntime-oh-abilityruntime-modularobjectextensioninstance.md).

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AbilityRuntime_ModObjExtensionInstanceHandle instance | Points to an [OH_AbilityRuntime_ModObjExtensionInstance](capi-abilityruntime-oh-abilityruntime-modularobjectextensioninstance.md) instance. |
| [OH_AbilityRuntime_ModObjExtensionAbility_OnDestroyFunc](capi-modular-object-extension-ability-h.md#oh_abilityruntime_modobjextensionability_ondestroyfunc) onDestroyFunc | Represents the onDestroy callback function. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | Returns a specific error code.          {@link ABILITY_RUNTIME_ERROR_CODE_NO_ERROR} success.<br>        {@link ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID} parameter check failed. |

### OH_AbilityRuntime_ModObjExtensionAbility_RegisterOnConnectFunc()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjExtensionAbility_RegisterOnConnectFunc(OH_AbilityRuntime_ModObjExtensionInstanceHandle instance, OH_AbilityRuntime_ModObjExtensionAbility_OnConnectFunc onConnectFunc)
```

**Description**

Registers the function [OH_AbilityRuntime_ModObjExtensionAbility_OnConnectFunc](capi-modular-object-extension-ability-h.md#oh_abilityruntime_modobjextensionability_onconnectfunc) with [OH_AbilityRuntime_ModObjExtensionInstance](capi-abilityruntime-oh-abilityruntime-modularobjectextensioninstance.md).

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AbilityRuntime_ModObjExtensionInstanceHandle instance | Points to an [OH_AbilityRuntime_ModObjExtensionInstance](capi-abilityruntime-oh-abilityruntime-modularobjectextensioninstance.md) instance. |
| [OH_AbilityRuntime_ModObjExtensionAbility_OnConnectFunc](capi-modular-object-extension-ability-h.md#oh_abilityruntime_modobjextensionability_onconnectfunc) onConnectFunc | Represents the onConnect callback function. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | Returns a specific error code.          {@link ABILITY_RUNTIME_ERROR_CODE_NO_ERROR} success.<br>        {@link ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID} parameter check failed. |

### OH_AbilityRuntime_ModObjExtensionAbility_RegisterOnDisconnectFunc()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjExtensionAbility_RegisterOnDisconnectFunc(OH_AbilityRuntime_ModObjExtensionInstanceHandle instance, OH_AbilityRuntime_ModObjExtensionAbility_OnDisconnectFunc onDisconnectFunc)
```

**Description**

Registers the function [OH_AbilityRuntime_ModObjExtensionAbility_OnDisconnectFunc](capi-modular-object-extension-ability-h.md#oh_abilityruntime_modobjextensionability_ondisconnectfunc) with [OH_AbilityRuntime_ModObjExtensionInstance](capi-abilityruntime-oh-abilityruntime-modularobjectextensioninstance.md).

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AbilityRuntime_ModObjExtensionInstanceHandle instance | Points to an [OH_AbilityRuntime_ModObjExtensionInstance](capi-abilityruntime-oh-abilityruntime-modularobjectextensioninstance.md) instance. |
| [OH_AbilityRuntime_ModObjExtensionAbility_OnDisconnectFunc](capi-modular-object-extension-ability-h.md#oh_abilityruntime_modobjextensionability_ondisconnectfunc) onDisconnectFunc | Represents the onDisconnect callback function. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | Returns a specific error code.          {@link ABILITY_RUNTIME_ERROR_CODE_NO_ERROR} success.<br>        {@link ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID} parameter check failed. |

### OH_AbilityRuntime_ModObjExtensionAbility_GetContextFromInstance()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjExtensionAbility_GetContextFromInstance(OH_AbilityRuntime_ModObjExtensionInstanceHandle instance, OH_AbilityRuntime_ModObjExtensionContextHandle* context)
```

**Description**

Gets the extension context from the modular object extension instance.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AbilityRuntime_ModObjExtensionInstanceHandle instance | Points to an [OH_AbilityRuntime_ModObjExtensionInstance](capi-abilityruntime-oh-abilityruntime-modularobjectextensioninstance.md) instance. |
| OH_AbilityRuntime_ModObjExtensionContextHandle* context | Represents a pointer to the modular object extension ability context. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | Returns a specific error code.          {@link ABILITY_RUNTIME_ERROR_CODE_NO_ERROR} success.<br>        {@link ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID} parameter check failed. |

### OH_AbilityRuntime_ModObjExtensionAbility_GetInstanceFromBase()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ModObjExtensionAbility_GetInstanceFromBase(AbilityRuntime_ExtensionInstanceHandle baseExtensionInstance, OH_AbilityRuntime_ModObjExtensionInstanceHandle* modObjExtensionInstance)
```

**Description**

Gets the modular object extension instance from a base extension instance.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| AbilityRuntime_ExtensionInstanceHandle baseExtensionInstance | Represents a pointer to a {@link<br>AbilityRuntime_ExtensionInstance} base extension instance. |
| OH_AbilityRuntime_ModObjExtensionInstanceHandle* modObjExtensionInstance | Represents a pointer to an {@link<br>OH_AbilityRuntime_ModObjExtensionInstanceHandle} instance that is an output parameter. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | Returns a specific error code.          {@link ABILITY_RUNTIME_ERROR_CODE_NO_ERROR} success.<br>        {@link ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID} parameter check failed.<br>        {@link ABILITY_RUNTIME_ERROR_CODE_INCORRECT_ABILITY_TYPE} if the ability instance is not          a modular object extension. |


