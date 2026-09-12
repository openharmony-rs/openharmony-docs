# connect_options.h

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @yzkp-->
<!--Designer: @yzkp-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=b64fba1a3bfa56ac6a22a458a141c3f45d9c160b translatedAt=2026-09-03T08:42:31.066Z pushedAt=2026-09-05T10:47:30.104Z -->

## Overview

Declares the connection options of an ExtensionAbility, including the callbacks for connection success, disconnection, and connection failure.

**Reference file:** <AbilityKit/ability_runtime/connect_options.h>

**Library:** libability_runtime.so

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 26.0.0

**Related module:** [AbilityRuntime](capi-abilityruntime.md)

## Summary

### Structs

| Name | typedef Keyword | Description |
| -- | -- | -- |
| [OH_AbilityRuntime_ConnectOptions](capi-abilityruntime-oh-abilityruntime-connectoptions.md) | OH_AbilityRuntime_ConnectOptions | Defines the OH_AbilityRuntime_ConnectOptions struct type. |

### Functions

| Name | typedef Keyword | Description |
| -- | -- | -- |
| [typedef void (\*OH_AbilityRuntime_ConnectOptions_OnConnectCallback)(OH_AbilityRuntime_ConnectOptions *connectOptions, AbilityBase_Element *element, OHIPCRemoteProxy *proxy)](#oh_abilityruntime_connectoptions_onconnectcallback) | OH_AbilityRuntime_ConnectOptions_OnConnectCallback | Defines a pointer to the callback function triggered when the connection succeeds. |
| [typedef void (\*OH_AbilityRuntime_ConnectOptions_OnDisconnectCallback)(OH_AbilityRuntime_ConnectOptions *connectOptions, AbilityBase_Element *element)](#oh_abilityruntime_connectoptions_ondisconnectcallback) | OH_AbilityRuntime_ConnectOptions_OnDisconnectCallback | Defines a pointer to the callback function triggered when the connection is disconnected. |
| [typedef void (\*OH_AbilityRuntime_ConnectOptions_OnFailedCallback)(OH_AbilityRuntime_ConnectOptions *connectOptions, AbilityRuntime_ErrorCode code)](#oh_abilityruntime_connectoptions_onfailedcallback) | OH_AbilityRuntime_ConnectOptions_OnFailedCallback | Defines a pointer to the callback function triggered when the connection fails. |
| [OH_AbilityRuntime_ConnectOptions* OH_AbilityRuntime_CreateConnectOptions()](#oh_abilityruntime_createconnectoptions) | - | Creates a ConnectOptions object. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_DestroyConnectOptions(OH_AbilityRuntime_ConnectOptions *connectOptions)](#oh_abilityruntime_destroyconnectoptions) | - | Destroys the specified ConnectOptions object. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ConnectOptions_SetOnConnectCallback(OH_AbilityRuntime_ConnectOptions *connectOptions, OH_AbilityRuntime_ConnectOptions_OnConnectCallback onConnectCallback)](#oh_abilityruntime_connectoptions_setonconnectcallback) | - | Sets the connection success callback [OH_AbilityRuntime_ConnectOptions_OnConnectCallback](capi-connect-options-h.md#oh_abilityruntime_connectoptions_onconnectcallback) in [OH_AbilityRuntime_ConnectOptions](capi-abilityruntime-oh-abilityruntime-connectoptions.md). |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ConnectOptions_SetOnDisconnectCallback(OH_AbilityRuntime_ConnectOptions *connectOptions, OH_AbilityRuntime_ConnectOptions_OnDisconnectCallback onDisconnectCallback)](#oh_abilityruntime_connectoptions_setondisconnectcallback) | - | Sets the disconnect callback [OH_AbilityRuntime_ConnectOptions_OnDisconnectCallback](capi-connect-options-h.md#oh_abilityruntime_connectoptions_ondisconnectcallback) in [OH_AbilityRuntime_ConnectOptions](capi-abilityruntime-oh-abilityruntime-connectoptions.md). |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ConnectOptions_SetOnFailedCallback(OH_AbilityRuntime_ConnectOptions *connectOptions, OH_AbilityRuntime_ConnectOptions_OnFailedCallback onFailedCallback)](#oh_abilityruntime_connectoptions_setonfailedcallback) | - | Sets the connection failure callback [OH_AbilityRuntime_ConnectOptions_OnFailedCallback](capi-connect-options-h.md#oh_abilityruntime_connectoptions_onfailedcallback) in [OH_AbilityRuntime_ConnectOptions](capi-abilityruntime-oh-abilityruntime-connectoptions.md). |

## Function Description

### OH_AbilityRuntime_ConnectOptions_OnConnectCallback()

```c
typedef void (*OH_AbilityRuntime_ConnectOptions_OnConnectCallback)(OH_AbilityRuntime_ConnectOptions *connectOptions, AbilityBase_Element *element, OHIPCRemoteProxy *proxy)
```

**Description**

Triggered when the connection succeeds.

**Since:** 26.0.0

**Parameters**

| Parameter item | Description |
| -- | -- |
| OH_AbilityRuntime_ConnectOptions \*connectOptions | Pointer to the [OH_AbilityRuntime_ConnectOptions](capi-abilityruntime-oh-abilityruntime-connectoptions.md) instance. |
| [AbilityBase_Element](capi-abilitybase-element.md) \*element | Name of the ExtensionAbility component. |
| [OHIPCRemoteProxy](../apis-ipc-kit/capi-ohipcparcel-ohipcremoteproxy.md) \*proxy | Remote object instance. |

### OH_AbilityRuntime_ConnectOptions_OnDisconnectCallback()

```c
typedef void (*OH_AbilityRuntime_ConnectOptions_OnDisconnectCallback)(OH_AbilityRuntime_ConnectOptions *connectOptions, AbilityBase_Element *element)
```

**Description**

Triggered when a connection is disconnected.

**Since:** 26.0.0

**Parameters**

| Parameter item | Description |
| -- | -- |
| OH_AbilityRuntime_ConnectOptions \*connectOptions | Pointer to the [OH_AbilityRuntime_ConnectOptions](capi-abilityruntime-oh-abilityruntime-connectoptions.md) instance. |
| [AbilityBase_Element](capi-abilitybase-element.md) \*element | Indicates the component name of the ExtensionAbility. |

### OH_AbilityRuntime_ConnectOptions_OnFailedCallback()

```c
typedef void (*OH_AbilityRuntime_ConnectOptions_OnFailedCallback)(OH_AbilityRuntime_ConnectOptions *connectOptions, AbilityRuntime_ErrorCode code)
```

**Description**

Called when the connection fails.

**Since:** 26.0.0

**Parameters**

| Parameter item | Description |
| -- | -- |
| OH_AbilityRuntime_ConnectOptions \*connectOptions | Pointer to the [OH_AbilityRuntime_ConnectOptions](capi-abilityruntime-oh-abilityruntime-connectoptions.md) instance. |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) code | Error code that indicates the failure. |

### OH_AbilityRuntime_CreateConnectOptions()

```c
OH_AbilityRuntime_ConnectOptions* OH_AbilityRuntime_CreateConnectOptions()
```

**Description**

Creates a ConnectOptions object.

**Since:** 26.0.0

**Returns:**

| Type | Description |
| -- | -- |
| [OH_AbilityRuntime_ConnectOptions*](capi-abilityruntime-oh-abilityruntime-connectoptions.md) | Returns the newly created OH_AbilityRuntime_ConnectOptions object.<br> The caller must call [OH_AbilityRuntime_DestroyConnectOptions](capi-connect-options-h.md#oh_abilityruntime_destroyconnectoptions) to destroy the returned object to avoid memory leaks. |

### OH_AbilityRuntime_DestroyConnectOptions()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_DestroyConnectOptions(OH_AbilityRuntime_ConnectOptions *connectOptions)
```

**Description**

Destroys the specified ConnectOptions object.

**Since:** 26.0.0

**Parameters**

| Parameter item | Description |
| -- | -- |
| [OH_AbilityRuntime_ConnectOptions](capi-abilityruntime-oh-abilityruntime-connectoptions.md) *connectOptions | Pointer to the [OH_AbilityRuntime_ConnectOptions](capi-abilityruntime-oh-abilityruntime-connectoptions.md) instance to be destroyed. |

**Returns:**

| Type | Description |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | Returns specific error code.<br>         [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode): success.<br>         [ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode): invalid connectOptions. |

### OH_AbilityRuntime_ConnectOptions_SetOnConnectCallback()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ConnectOptions_SetOnConnectCallback(OH_AbilityRuntime_ConnectOptions *connectOptions, OH_AbilityRuntime_ConnectOptions_OnConnectCallback onConnectCallback)
```

**Description**

Sets the connection success callback [OH_AbilityRuntime_ConnectOptions_OnConnectCallback](capi-connect-options-h.md#oh_abilityruntime_connectoptions_onconnectcallback) in [OH_AbilityRuntime_ConnectOptions](capi-abilityruntime-oh-abilityruntime-connectoptions.md).

**Since:** 26.0.0

**Parameters**

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ConnectOptions](capi-abilityruntime-oh-abilityruntime-connectoptions.md) *connectOptions | Pointer to the target [OH_AbilityRuntime_ConnectOptions](capi-abilityruntime-oh-abilityruntime-connectoptions.md) instance. |
| [OH_AbilityRuntime_ConnectOptions_OnConnectCallback](capi-connect-options-h.md#oh_abilityruntime_connectoptions_onconnectcallback) onConnectCallback | Indicates the target [OH_AbilityRuntime_ConnectOptions_OnConnectCallback](capi-connect-options-h.md#oh_abilityruntime_connectoptions_onconnectcallback) callback function. |

**Returns:**

| Type | Description |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | Returns the specific error code.<br>         [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) API call success.<br>         [ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) parameter validation failure. |

### OH_AbilityRuntime_ConnectOptions_SetOnDisconnectCallback()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ConnectOptions_SetOnDisconnectCallback(OH_AbilityRuntime_ConnectOptions *connectOptions, OH_AbilityRuntime_ConnectOptions_OnDisconnectCallback onDisconnectCallback)
```

**Description**

Sets the disconnect callback [OH_AbilityRuntime_ConnectOptions_OnDisconnectCallback](capi-connect-options-h.md#oh_abilityruntime_connectoptions_ondisconnectcallback) in [OH_AbilityRuntime_ConnectOptions](capi-abilityruntime-oh-abilityruntime-connectoptions.md).

**Since:** 26.0.0

**Parameters**

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ConnectOptions](capi-abilityruntime-oh-abilityruntime-connectoptions.md) *connectOptions | Pointer to the target [OH_AbilityRuntime_ConnectOptions](capi-abilityruntime-oh-abilityruntime-connectoptions.md) instance. |
| [OH_AbilityRuntime_ConnectOptions_OnDisconnectCallback](capi-connect-options-h.md#oh_abilityruntime_connectoptions_ondisconnectcallback) onDisconnectCallback | Indicates the target [OH_AbilityRuntime_ConnectOptions_OnDisconnectCallback](capi-connect-options-h.md#oh_abilityruntime_connectoptions_ondisconnectcallback) callback function. |

**Returns:**

| Type | Description |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | Returns a specific error code.<br>         [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) API call success.<br>         [ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) parameter validation failure. |

### OH_AbilityRuntime_ConnectOptions_SetOnFailedCallback()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ConnectOptions_SetOnFailedCallback(OH_AbilityRuntime_ConnectOptions *connectOptions, OH_AbilityRuntime_ConnectOptions_OnFailedCallback onFailedCallback)
```

**Description**

Sets the connection failure callback [OH_AbilityRuntime_ConnectOptions_OnFailedCallback](capi-connect-options-h.md#oh_abilityruntime_connectoptions_onfailedcallback) in [OH_AbilityRuntime_ConnectOptions](capi-abilityruntime-oh-abilityruntime-connectoptions.md).

**Since:** 26.0.0

**Parameters**

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ConnectOptions](capi-abilityruntime-oh-abilityruntime-connectoptions.md) *connectOptions | Pointer to the target [OH_AbilityRuntime_ConnectOptions](capi-abilityruntime-oh-abilityruntime-connectoptions.md) instance. |
| [OH_AbilityRuntime_ConnectOptions_OnFailedCallback](capi-connect-options-h.md#oh_abilityruntime_connectoptions_onfailedcallback) onFailedCallback | Indicates the target [OH_AbilityRuntime_ConnectOptions_OnFailedCallback](capi-connect-options-h.md#oh_abilityruntime_connectoptions_onfailedcallback) callback function. |

**Returns:**

| Type | Description |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | Returns a specific error code.<br>         [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) API call succeeded.<br>         [ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) Parameter validation failed. |


