# connect_options.h

## Overview

Declares the connection options for extension ability, including callbacks for connection success, disconnection, and connection failure.

**Library**: libability_runtime.so

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 13

**Related module**: [AbilityRuntime](capi-abilityruntime.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AbilityRuntime_ConnectOptions](capi-abilityruntime-oh-abilityruntime-connectoptions.md) | OH_AbilityRuntime_ConnectOptions | Defines the OH_AbilityRuntime_ConnectOptions structure type. |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef void (\*OH_AbilityRuntime_ConnectOptions_OnConnectCallback)(OH_AbilityRuntime_ConnectOptions *connectOptions, AbilityBase_Element *element, OHIPCRemoteProxy *proxy)](#oh_abilityruntime_connectoptions_onconnectcallback) | OH_AbilityRuntime_ConnectOptions_OnConnectCallback | The callback interface is invoked when the connection succeeds. |
| [typedef void (\*OH_AbilityRuntime_ConnectOptions_OnDisconnectCallback)(OH_AbilityRuntime_ConnectOptions *connectOptions, AbilityBase_Element *element)](#oh_abilityruntime_connectoptions_ondisconnectcallback) | OH_AbilityRuntime_ConnectOptions_OnDisconnectCallback | The callback interface is invoked when the disconnection occurs. |
| [typedef void (\*OH_AbilityRuntime_ConnectOptions_OnFailedCallback)(OH_AbilityRuntime_ConnectOptions *connectOptions, AbilityRuntime_ErrorCode code)](#oh_abilityruntime_connectoptions_onfailedcallback) | OH_AbilityRuntime_ConnectOptions_OnFailedCallback | The callback interface is invoked when the connection fails. |
| [OH_AbilityRuntime_ConnectOptions* OH_AbilityRuntime_CreateConnectOptions()](#oh_abilityruntime_createconnectoptions) | - | Creates a ConnectOptions object.<br> * |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_DestroyConnectOptions(OH_AbilityRuntime_ConnectOptions *connectOptions)](#oh_abilityruntime_destroyconnectoptions) | - | Destroys the specified ConnectOptions. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ConnectOptions_SetOnConnectCallback(OH_AbilityRuntime_ConnectOptions *connectOptions, OH_AbilityRuntime_ConnectOptions_OnConnectCallback onConnectCallback)](#oh_abilityruntime_connectoptions_setonconnectcallback) | - | Set the callback [OH_AbilityRuntime_ConnectOptions_OnConnectCallback](capi-connect-options-h.md#oh_abilityruntime_connectoptions_onconnectcallback) in [OH_AbilityRuntime_ConnectOptions](capi-abilityruntime-oh-abilityruntime-connectoptions.md). |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ConnectOptions_SetOnDisconnectCallback(OH_AbilityRuntime_ConnectOptions *connectOptions, OH_AbilityRuntime_ConnectOptions_OnDisconnectCallback onDisconnectCallback)](#oh_abilityruntime_connectoptions_setondisconnectcallback) | - | Set the callback [OH_AbilityRuntime_ConnectOptions_OnDisconnectCallback](capi-connect-options-h.md#oh_abilityruntime_connectoptions_ondisconnectcallback) in [OH_AbilityRuntime_ConnectOptions](capi-abilityruntime-oh-abilityruntime-connectoptions.md). |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ConnectOptions_SetOnFailedCallback(OH_AbilityRuntime_ConnectOptions *connectOptions, OH_AbilityRuntime_ConnectOptions_OnFailedCallback onFailedCallback)](#oh_abilityruntime_connectoptions_setonfailedcallback) | - | Set the callback [OH_AbilityRuntime_ConnectOptions_OnFailedCallback](capi-connect-options-h.md#oh_abilityruntime_connectoptions_onfailedcallback) in [OH_AbilityRuntime_ConnectOptions](capi-abilityruntime-oh-abilityruntime-connectoptions.md). |

### Variable

| Name | Description |
| -- | -- |
| void (*OH_AbilityRuntime_ConnectOptions_OnConnectCallback)( OH_AbilityRuntime_ConnectOptions *connectOptions, AbilityBase_Element *element, OHIPCRemoteProxy *proxy) | The callback interface is invoked when the connection succeeds.<br>**Since**: 26.0.0 |
| void (*OH_AbilityRuntime_ConnectOptions_OnDisconnectCallback)( OH_AbilityRuntime_ConnectOptions *connectOptions, AbilityBase_Element *element) | The callback interface is invoked when the disconnection occurs.<br>**Since**: 26.0.0 |
| void (*OH_AbilityRuntime_ConnectOptions_OnFailedCallback)( OH_AbilityRuntime_ConnectOptions *connectOptions, AbilityRuntime_ErrorCode code) | The callback interface is invoked when the connection fails.<br>**Since**: 26.0.0 |

## Function description

### OH_AbilityRuntime_ConnectOptions_OnConnectCallback()

```c
typedef void (*OH_AbilityRuntime_ConnectOptions_OnConnectCallback)(OH_AbilityRuntime_ConnectOptions *connectOptions, AbilityBase_Element *element, OHIPCRemoteProxy *proxy)
```

**Description**

The callback interface is invoked when the connection succeeds.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ConnectOptions](capi-abilityruntime-oh-abilityruntime-connectoptions.md) \*connectOptions | Represents a pointer to an {@link<br>OH_AbilityRuntime_ConnectOptions} instance. |
| AbilityBase_Element \*element | Represents the element name of the extension ability. |
| OHIPCRemoteProxy \*proxy | Represents the remote object instance. |

### OH_AbilityRuntime_ConnectOptions_OnDisconnectCallback()

```c
typedef void (*OH_AbilityRuntime_ConnectOptions_OnDisconnectCallback)(OH_AbilityRuntime_ConnectOptions *connectOptions, AbilityBase_Element *element)
```

**Description**

The callback interface is invoked when the disconnection occurs.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ConnectOptions](capi-abilityruntime-oh-abilityruntime-connectoptions.md) \*connectOptions | Represents a pointer to an [OH_AbilityRuntime_ConnectOptions](capi-abilityruntime-oh-abilityruntime-connectoptions.md) instance. |
| AbilityBase_Element \*element | Represents the element name of the extension ability. |

### OH_AbilityRuntime_ConnectOptions_OnFailedCallback()

```c
typedef void (*OH_AbilityRuntime_ConnectOptions_OnFailedCallback)(OH_AbilityRuntime_ConnectOptions *connectOptions, AbilityRuntime_ErrorCode code)
```

**Description**

The callback interface is invoked when the connection fails.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ConnectOptions](capi-abilityruntime-oh-abilityruntime-connectoptions.md) \*connectOptions | Represents a pointer to an [OH_AbilityRuntime_ConnectOptions](capi-abilityruntime-oh-abilityruntime-connectoptions.md) instance. |
| AbilityRuntime_ErrorCode code | Represents the error code of the failure. |

### OH_AbilityRuntime_CreateConnectOptions()

```c
OH_AbilityRuntime_ConnectOptions* OH_AbilityRuntime_CreateConnectOptions()
```

**Description**

Creates a ConnectOptions object.<br> *

**Since**: 26.0.0

**Returns**:

| Type | Description |
| -- | -- |
| [OH_AbilityRuntime_ConnectOptions*](capi-abilityruntime-oh-abilityruntime-connectoptions.md) | Returns a newly created OH_AbilityRuntime_ConnectOptions object.  The caller is responsible for destroying the returned object by calling  [OH_AbilityRuntime_DestroyConnectOptions](capi-connect-options-h.md#oh_abilityruntime_destroyconnectoptions) to avoid memory leaks. |

### OH_AbilityRuntime_DestroyConnectOptions()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_DestroyConnectOptions(OH_AbilityRuntime_ConnectOptions *connectOptions)
```

**Description**

Destroys the specified ConnectOptions.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ConnectOptions](capi-abilityruntime-oh-abilityruntime-connectoptions.md) *connectOptions | The ConnectOptions object to be destroyed. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | The error code.          {@link ABILITY_RUNTIME_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        {@link ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID} if the connectOptions is invalid. |

### OH_AbilityRuntime_ConnectOptions_SetOnConnectCallback()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ConnectOptions_SetOnConnectCallback(OH_AbilityRuntime_ConnectOptions *connectOptions, OH_AbilityRuntime_ConnectOptions_OnConnectCallback onConnectCallback)
```

**Description**

Set the callback [OH_AbilityRuntime_ConnectOptions_OnConnectCallback](capi-connect-options-h.md#oh_abilityruntime_connectoptions_onconnectcallback) in [OH_AbilityRuntime_ConnectOptions](capi-abilityruntime-oh-abilityruntime-connectoptions.md).

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ConnectOptions](capi-abilityruntime-oh-abilityruntime-connectoptions.md) *connectOptions | Pointer to an [OH_AbilityRuntime_ConnectOptions](capi-abilityruntime-oh-abilityruntime-connectoptions.md) instance to be set. |
| [OH_AbilityRuntime_ConnectOptions_OnConnectCallback](capi-connect-options-h.md#oh_abilityruntime_connectoptions_onconnectcallback) onConnectCallback | Represents [OH_AbilityRuntime_ConnectOptions_OnConnectCallback](capi-connect-options-h.md#oh_abilityruntime_connectoptions_onconnectcallback) instance which will be set in. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | Returns a specific error code.          {@link ABILITY_RUNTIME_ERROR_CODE_NO_ERROR} success.<br>        {@link ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID} parameter check failed. |

### OH_AbilityRuntime_ConnectOptions_SetOnDisconnectCallback()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ConnectOptions_SetOnDisconnectCallback(OH_AbilityRuntime_ConnectOptions *connectOptions, OH_AbilityRuntime_ConnectOptions_OnDisconnectCallback onDisconnectCallback)
```

**Description**

Set the callback [OH_AbilityRuntime_ConnectOptions_OnDisconnectCallback](capi-connect-options-h.md#oh_abilityruntime_connectoptions_ondisconnectcallback) in [OH_AbilityRuntime_ConnectOptions](capi-abilityruntime-oh-abilityruntime-connectoptions.md).

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ConnectOptions](capi-abilityruntime-oh-abilityruntime-connectoptions.md) *connectOptions | Pointer to an [OH_AbilityRuntime_ConnectOptions](capi-abilityruntime-oh-abilityruntime-connectoptions.md) instance to be set. |
| [OH_AbilityRuntime_ConnectOptions_OnDisconnectCallback](capi-connect-options-h.md#oh_abilityruntime_connectoptions_ondisconnectcallback) onDisconnectCallback | Represents [OH_AbilityRuntime_ConnectOptions_OnDisconnectCallback](capi-connect-options-h.md#oh_abilityruntime_connectoptions_ondisconnectcallback) instance which will be set in. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | Returns a specific error code.          {@link ABILITY_RUNTIME_ERROR_CODE_NO_ERROR} success.<br>        {@link ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID} parameter check failed. |

### OH_AbilityRuntime_ConnectOptions_SetOnFailedCallback()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ConnectOptions_SetOnFailedCallback(OH_AbilityRuntime_ConnectOptions *connectOptions, OH_AbilityRuntime_ConnectOptions_OnFailedCallback onFailedCallback)
```

**Description**

Set the callback [OH_AbilityRuntime_ConnectOptions_OnFailedCallback](capi-connect-options-h.md#oh_abilityruntime_connectoptions_onfailedcallback) in [OH_AbilityRuntime_ConnectOptions](capi-abilityruntime-oh-abilityruntime-connectoptions.md).

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ConnectOptions](capi-abilityruntime-oh-abilityruntime-connectoptions.md) *connectOptions | Pointer to an [OH_AbilityRuntime_ConnectOptions](capi-abilityruntime-oh-abilityruntime-connectoptions.md) instance to be set. |
| [OH_AbilityRuntime_ConnectOptions_OnFailedCallback](capi-connect-options-h.md#oh_abilityruntime_connectoptions_onfailedcallback) onFailedCallback | Represents [OH_AbilityRuntime_ConnectOptions_OnFailedCallback](capi-connect-options-h.md#oh_abilityruntime_connectoptions_onfailedcallback) instance which will be set in. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | Returns a specific error code.          {@link ABILITY_RUNTIME_ERROR_CODE_NO_ERROR} success.<br>        {@link ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID} parameter check failed. |


