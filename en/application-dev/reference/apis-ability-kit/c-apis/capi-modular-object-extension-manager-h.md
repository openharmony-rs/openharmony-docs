# modular_object_extension_manager.h

## Overview

Declares the modular object extension manager.

**Library**: libability_runtime.so

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 13

**Related module**: [AbilityRuntime](capi-abilityruntime.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AbilityRuntime_ModularObjectExtensionInfo*](capi-abilityruntime-oh-abilityruntime-modularobjectextensioninfo8h.md) | OH_AbilityRuntime_ModObjExtensionInfoHandle | Defines the pointer to OH_AbilityRuntime_ModularObjectExtensionInfo. |
| [OH_AbilityRuntime_AllModularObjectExtensionInfos*](capi-abilityruntime-oh-abilityruntime-allmodularobjectextensioninfos8h.md) | OH_AbilityRuntime_AllModObjExtensionInfosHandle | Defines the pointer to OH_AbilityRuntime_AllModularObjectExtensionInfos. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AbilityRuntime_LaunchMode](#oh_abilityruntime_launchmode) | OH_AbilityRuntime_LaunchMode | The launch mode of a modular object extension. |
| [OH_AbilityRuntime_ProcessMode](#oh_abilityruntime_processmode) | OH_AbilityRuntime_ProcessMode | The process mode of a modular object extension. |
| [OH_AbilityRuntime_ThreadMode](#oh_abilityruntime_threadmode) | OH_AbilityRuntime_ThreadMode | The thread mode of a modular object extension. |

### Function

| Name | Description |
| -- | -- |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetModularObjectExtensionInfoLaunchMode(OH_AbilityRuntime_ModObjExtensionInfoHandle extensionInfo, OH_AbilityRuntime_LaunchMode *launchMode)](#oh_abilityruntime_getmodularobjectextensioninfolaunchmode) | Gets the launch mode from modular object extension info. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetModularObjectExtensionInfoProcessMode(OH_AbilityRuntime_ModObjExtensionInfoHandle extensionInfo, OH_AbilityRuntime_ProcessMode *processMode)](#oh_abilityruntime_getmodularobjectextensioninfoprocessmode) | Gets the process mode from modular object extension info. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetModularObjectExtensionInfoThreadMode(OH_AbilityRuntime_ModObjExtensionInfoHandle extensionInfo, OH_AbilityRuntime_ThreadMode *threadMode)](#oh_abilityruntime_getmodularobjectextensioninfothreadmode) | Gets the thread mode from modular object extension info. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetModularObjectExtensionInfoElementName(OH_AbilityRuntime_ModObjExtensionInfoHandle extensionInfo, AbilityBase_Element *element)](#oh_abilityruntime_getmodularobjectextensioninfoelementname) | Gets elementName from modular object extension info. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetModularObjectExtensionInfoDisableState(OH_AbilityRuntime_ModObjExtensionInfoHandle extensionInfo, bool *isDisabled)](#oh_abilityruntime_getmodularobjectextensioninfodisablestate) | Gets the disable state of modular object extension. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_AcquireSelfModularObjectExtensionInfos(OH_AbilityRuntime_AllModObjExtensionInfosHandle *outOwnedAllExtensionInfos)](#oh_abilityruntime_acquireselfmodularobjectextensioninfos) | Acquires all modular object extension infos within the self application. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ReleaseAllExtensionInfos(OH_AbilityRuntime_AllModObjExtensionInfosHandle *allExtensionInfos)](#oh_abilityruntime_releaseallextensioninfos) | Releases the specified all modular object extension infos. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetCountFromAllModObjExtensionInfos(OH_AbilityRuntime_AllModObjExtensionInfosHandle allExtensionInfos, size_t *count)](#oh_abilityruntime_getcountfromallmodobjextensioninfos) | Gets the exact count of modular object extension infos present in the collection. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetModObjExtensionInfoByIndex(OH_AbilityRuntime_AllModObjExtensionInfosHandle allExtensionInfos, size_t index, OH_AbilityRuntime_ModObjExtensionInfoHandle *extensionInfo)](#oh_abilityruntime_getmodobjextensioninfobyindex) | Retrieves a specific modular object extension info handle from the collection by its index. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ConnectModularObjectExtensionAbility(AbilityBase_Want *want, OH_AbilityRuntime_ConnectOptions *connectOptions, int64_t *connectionId)](#oh_abilityruntime_connectmodularobjectextensionability) | Connect to a modular object extension ability. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_DisconnectModularObjectExtensionAbility(int64_t connectionId)](#oh_abilityruntime_disconnectmodularobjectextensionability) | Disconnect the modular object extension ability. |

## Enum type description

### OH_AbilityRuntime_LaunchMode

```c
enum OH_AbilityRuntime_LaunchMode
```

**Description**

The launch mode of a modular object extension.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

| Enum item | Description |
| -- | -- |
| OH_ABILITY_RUNTIME_LAUNCH_MODE_IN_PROCESS = 0 | All extensions under the same bundle share a single process.<br>**Since**: 26.0.0 |
| OH_ABILITY_RUNTIME_LAUNCH_MODE_CROSS_PROCESS = 1 | Allow modular object extension abilities to be started across processes.<br>**Since**: 26.0.0 |

### OH_AbilityRuntime_ProcessMode

```c
enum OH_AbilityRuntime_ProcessMode
```

**Description**

The process mode of a modular object extension.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

| Enum item | Description |
| -- | -- |
| OH_ABILITY_RUNTIME_PROCESS_MODE_BUNDLE = 0 | All modular object extensions under the same bundle share a single process.<br>**Since**: 26.0.0 |
| OH_ABILITY_RUNTIME_PROCESS_MODE_TYPE = 1 | Modular object extensions with the same name share a single process.<br>**Since**: 26.0.0 |
| OH_ABILITY_RUNTIME_PROCESS_MODE_INSTANCE = 2 | Each modular object extension instance is a process.<br>**Since**: 26.0.0 |

### OH_AbilityRuntime_ThreadMode

```c
enum OH_AbilityRuntime_ThreadMode
```

**Description**

The thread mode of a modular object extension.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

| Enum item | Description |
| -- | -- |
| OH_ABILITY_RUNTIME_THREAD_MODE_BUNDLE = 0 | All modular object extensions under the same bundle share a single thread.<br>**Since**: 26.0.0 |
| OH_ABILITY_RUNTIME_THREAD_MODE_TYPE = 1 | Modular object extensions with the same name share a single thread.<br>**Since**: 26.0.0 |
| OH_ABILITY_RUNTIME_THREAD_MODE_INSTANCE = 2 | Each modular object extension instance is a thread.<br>**Since**: 26.0.0 |


## Function description

### OH_AbilityRuntime_GetModularObjectExtensionInfoLaunchMode()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetModularObjectExtensionInfoLaunchMode(OH_AbilityRuntime_ModObjExtensionInfoHandle extensionInfo, OH_AbilityRuntime_LaunchMode *launchMode)
```

**Description**

Gets the launch mode from modular object extension info.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjExtensionInfoHandle](capi-abilityruntime-oh-abilityruntime-modularobjectextensioninfo8h.md) extensionInfo | The modular object extension info from which to get the launch mode. |
| [OH_AbilityRuntime_LaunchMode](capi-modular-object-extension-manager-h.md#oh_abilityruntime_launchmode) *launchMode | The launch mode obtained from the extension info. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | Returns a specific error code.           [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the operation is successful.           [ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the arguments provided are invalid. |

### OH_AbilityRuntime_GetModularObjectExtensionInfoProcessMode()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetModularObjectExtensionInfoProcessMode(OH_AbilityRuntime_ModObjExtensionInfoHandle extensionInfo, OH_AbilityRuntime_ProcessMode *processMode)
```

**Description**

Gets the process mode from modular object extension info.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjExtensionInfoHandle](capi-abilityruntime-oh-abilityruntime-modularobjectextensioninfo8h.md) extensionInfo | The modular object extension info to get the process mode from. |
| [OH_AbilityRuntime_ProcessMode](capi-modular-object-extension-manager-h.md#oh_abilityruntime_processmode) *processMode | The process mode obtained from the extension info. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | Returns a specific error code.           [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the operation is successful.           [ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the arguments provided are invalid. |

### OH_AbilityRuntime_GetModularObjectExtensionInfoThreadMode()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetModularObjectExtensionInfoThreadMode(OH_AbilityRuntime_ModObjExtensionInfoHandle extensionInfo, OH_AbilityRuntime_ThreadMode *threadMode)
```

**Description**

Gets the thread mode from modular object extension info.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjExtensionInfoHandle](capi-abilityruntime-oh-abilityruntime-modularobjectextensioninfo8h.md) extensionInfo | The modular object extension info to get the thread mode from. |
| [OH_AbilityRuntime_ThreadMode](capi-modular-object-extension-manager-h.md#oh_abilityruntime_threadmode) *threadMode | The thread mode obtained from the extension info. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | Returns a specific error code.           [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the operation is successful.           [ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the arguments provided are invalid. |

### OH_AbilityRuntime_GetModularObjectExtensionInfoElementName()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetModularObjectExtensionInfoElementName(OH_AbilityRuntime_ModObjExtensionInfoHandle extensionInfo, AbilityBase_Element *element)
```

**Description**

Gets elementName from modular object extension info.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjExtensionInfoHandle](capi-abilityruntime-oh-abilityruntime-modularobjectextensioninfo8h.md) extensionInfo | The modular object extension info to get the element name from. |
| AbilityBase_Element *element | The element name obtained from the extension info. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | Returns a specific error code.           [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the operation is successful.           [ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the arguments provided are invalid. |

### OH_AbilityRuntime_GetModularObjectExtensionInfoDisableState()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetModularObjectExtensionInfoDisableState(OH_AbilityRuntime_ModObjExtensionInfoHandle extensionInfo, bool *isDisabled)
```

**Description**

Gets the disable state of modular object extension.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjExtensionInfoHandle](capi-abilityruntime-oh-abilityruntime-modularobjectextensioninfo8h.md) extensionInfo | The modular object extension info. |
| bool *isDisabled | Whether the extension is disabled. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | Returns a specific error code.           [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the operation is successful.           [ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the arguments provided are invalid. |

### OH_AbilityRuntime_AcquireSelfModularObjectExtensionInfos()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_AcquireSelfModularObjectExtensionInfos(OH_AbilityRuntime_AllModObjExtensionInfosHandle *outOwnedAllExtensionInfos)
```

**Description**

Acquires all modular object extension infos within the self application.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_AllModObjExtensionInfosHandle](capi-abilityruntime-oh-abilityruntime-allmodularobjectextensioninfos8h.md) *outOwnedAllExtensionInfos | Information about all extensions within the self application. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | Returns a specific error code.           [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the operation is successful.           [ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the arguments provided are invalid.           [ABILITY_RUNTIME_ERROR_CODE_NOT_SUPPORTED](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the device does not support. |

### OH_AbilityRuntime_ReleaseAllExtensionInfos()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ReleaseAllExtensionInfos(OH_AbilityRuntime_AllModObjExtensionInfosHandle *allExtensionInfos)
```

**Description**

Releases the specified all modular object extension infos.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_AllModObjExtensionInfosHandle](capi-abilityruntime-oh-abilityruntime-allmodularobjectextensioninfos8h.md) *allExtensionInfos | The all modular object extension infos to be released. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | Returns a specific error code.           [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the operation is successful.           [ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the arguments provided are invalid. |

**Reference**:

[OH_AbilityRuntime_AcquireSelfModularObjectExtensionInfos](capi-modular-object-extension-manager-h.md#oh_abilityruntime_acquireselfmodularobjectextensioninfos)


### OH_AbilityRuntime_GetCountFromAllModObjExtensionInfos()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetCountFromAllModObjExtensionInfos(OH_AbilityRuntime_AllModObjExtensionInfosHandle allExtensionInfos, size_t *count)
```

**Description**

Gets the exact count of modular object extension infos present in the collection.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_AllModObjExtensionInfosHandle](capi-abilityruntime-oh-abilityruntime-allmodularobjectextensioninfos8h.md) allExtensionInfos | The handle representing the collection of all modular object extension infos. |
| size_t *count | Return value to receive the count of extensions in the collection. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | Returns a specific error code.           [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the operation is successful.           [ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the arguments provided are invalid. |

### OH_AbilityRuntime_GetModObjExtensionInfoByIndex()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetModObjExtensionInfoByIndex(OH_AbilityRuntime_AllModObjExtensionInfosHandle allExtensionInfos, size_t index, OH_AbilityRuntime_ModObjExtensionInfoHandle *extensionInfo)
```

**Description**

Retrieves a specific modular object extension info handle from the collection by its index.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_AllModObjExtensionInfosHandle](capi-abilityruntime-oh-abilityruntime-allmodularobjectextensioninfos8h.md) allExtensionInfos | Information about all extensions within the self application. |
| size_t index | The index of the extension to retrieve. Must be strictly less than the count. |
| [OH_AbilityRuntime_ModObjExtensionInfoHandle](capi-abilityruntime-oh-abilityruntime-modularobjectextensioninfo8h.md) *extensionInfo | The retrieved single modular object extension info handle for the specified index. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | Returns a specific error code.           [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the operation is successful.           [ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the arguments provided are invalid. |

### OH_AbilityRuntime_ConnectModularObjectExtensionAbility()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ConnectModularObjectExtensionAbility(AbilityBase_Want *want, OH_AbilityRuntime_ConnectOptions *connectOptions, int64_t *connectionId)
```

**Description**

Connect to a modular object extension ability.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| AbilityBase_Want *want | Indicates the modular object extension ability to connect. For details, see {@link AbilityBase_Want}. |
| OH_AbilityRuntime_ConnectOptions *connectOptions | Indicates the connection options. |
| int64_t *connectionId | Indicates the connection id that is a output param. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>       <li>[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the call is successful.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the arguments provided are invalid.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_NOT_SUPPORTED](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the device does not support connecting modular       object extension ability.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_NO_SUCH_ABILITY](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the target ability does not exist.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_INCORRECT_ABILITY_TYPE](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the ability type is incorrect.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_VISIBILITY_VERIFICATION_FAILED](capi-ability-runtime-common-h.md#abilityruntime_errorcode) - Cannot start an invisible       component.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_STATIC_CFG_PERMISSION](capi-ability-runtime-common-h.md#abilityruntime_errorcode) The specified process does not have       the permission.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_CROSS_USER_OPERATION](capi-ability-runtime-common-h.md#abilityruntime_errorcode) Cross-user operations are not allowed.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_CROWDTEST_EXPIRED](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the crowdtesting application expires.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_INTERNAL](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if an internal error occurs.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_NOT_TOP_ABILITY](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the caller is not a foreground process.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_UPPER_LIMIT_REACHED](capi-ability-runtime-common-h.md#abilityruntime_errorcode) The number of instances with the same       ability name is more than twenty.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_NO_RUNNING_ABILITIES_WITH_UI](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the target application does not have       running abilities with UI.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_UPPER_RATE_LIMIT](capi-ability-runtime-common-h.md#abilityruntime_errorcode) The API call frequency is too high and       exceeds 20 times per second.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_UPPER_CONNECTION_NUMBER_LIMIT](capi-ability-runtime-common-h.md#abilityruntime_errorcode) The number of connections to       the same ability name from the same pid exceeds five.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_CROSS_APP_IN_PROCESS](capi-ability-runtime-common-h.md#abilityruntime_errorcode) Caller and target are not in the       same application for [OH_ABILITY_RUNTIME_LAUNCH_MODE_IN_PROCESS](capi-modular-object-extension-manager-h.md#oh_abilityruntime_launchmode) mode.</li>       </ul> |

### OH_AbilityRuntime_DisconnectModularObjectExtensionAbility()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_DisconnectModularObjectExtensionAbility(int64_t connectionId)
```

**Description**

Disconnect the modular object extension ability.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| int64_t connectionId | Indicates the connection ID. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | Returns a specific error code.           [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the call is successful.           [ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the arguments provided are invalid.           [ABILITY_RUNTIME_ERROR_CODE_INTERNAL](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if an internal error occurs. |


