# modular_object_extension_manager.h

## Overview

Declares the APIs for managing ModularObjectExtensionAbility, including querying ModularObjectExtensionAbility information, connecting to and disconnecting from it. Developers can use the APIs provided by this module to query the information of all registered ModularObjectExtensionAbility instances in the current app (including the startup mode, process mode, thread mode, component name, and disabled state), and establish or disconnect the communication connection with ModularObjectExtensionAbility as needed.<br> **File to include:** <AbilityKit/ability_runtime/modular_object_extension_manager.h>

**Library**: libability_runtime.so

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Related module**: [AbilityRuntime](capi-abilityruntime.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AbilityRuntime_ModObjExtensionInfoHandle](capi-abilityruntime-oh-abilityruntime-modobjextensioninfohandle.md) | OH_AbilityRuntime_ModObjExtensionInfoHandle | Represents the information handle of a single ModularObjectExtensionAbility. The handle points to the complete information of a ModularObjectExtensionAbility, including attributes such as the launch mode, process mode, thread mode, component name (AbilityBase_Element), and disabled state. |
| [OH_AbilityRuntime_AllModObjExtensionInfosHandle](capi-abilityruntime-oh-abilityruntime-allmodobjextensioninfoshandle.md) | OH_AbilityRuntime_AllModObjExtensionInfosHandle | Represents a handle to the collection of all ModularObjectExtensionAbility information in the current app. You can obtain this handle through [OH_AbilityRuntime_AcquireSelfModularObjectExtensionInfos](capi-modular-object-extension-manager-h.md#oh_abilityruntime_acquireselfmodularobjectextensioninfos). This handle points to a collection containing multiple [OH_AbilityRuntime_ModObjExtensionInfoHandle](capi-abilityruntime-oh-abilityruntime-modobjextensioninfohandle.md) objects. You can obtain the number of elements in the collection through [OH_AbilityRuntime_GetCountFromAllModObjExtensionInfos](capi-modular-object-extension-manager-h.md#oh_abilityruntime_getcountfromallmodobjextensioninfos), and obtain the information of a single ModularObjectExtensionAbility by index through [OH_AbilityRuntime_GetModObjExtensionInfoByIndex](capi-modular-object-extension-manager-h.md#oh_abilityruntime_getmodobjextensioninfobyindex). After use, release the collection through [OH_AbilityRuntime_ReleaseAllExtensionInfos](capi-modular-object-extension-manager-h.md#oh_abilityruntime_releaseallextensioninfos). |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AbilityRuntime_LaunchMode](#oh_abilityruntime_launchmode) | OH_AbilityRuntime_LaunchMode | Defines the launch mode of a ModularObjectExtensionAbility. |
| [OH_AbilityRuntime_ProcessMode](#oh_abilityruntime_processmode) | OH_AbilityRuntime_ProcessMode | Defines the process mode of a ModularObjectExtensionAbility. |
| [OH_AbilityRuntime_ThreadMode](#oh_abilityruntime_threadmode) | OH_AbilityRuntime_ThreadMode | Defines the thread mode of a ModularObjectExtensionAbility. |

### Function

| Name | Description |
| -- | -- |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetModularObjectExtensionInfoLaunchMode(OH_AbilityRuntime_ModObjExtensionInfoHandle extensionInfo, OH_AbilityRuntime_LaunchMode *launchMode)](#oh_abilityruntime_getmodularobjectextensioninfolaunchmode) | Obtains the startup mode from the specified ModularObjectExtensionAbility information. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetModularObjectExtensionInfoProcessMode(OH_AbilityRuntime_ModObjExtensionInfoHandle extensionInfo, OH_AbilityRuntime_ProcessMode *processMode)](#oh_abilityruntime_getmodularobjectextensioninfoprocessmode) | Obtains the process mode from the specified ModularObjectExtensionAbility information. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetModularObjectExtensionInfoThreadMode(OH_AbilityRuntime_ModObjExtensionInfoHandle extensionInfo, OH_AbilityRuntime_ThreadMode *threadMode)](#oh_abilityruntime_getmodularobjectextensioninfothreadmode) | Obtains the thread mode from the specified ModularObjectExtensionAbility information. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetModularObjectExtensionInfoElementName(OH_AbilityRuntime_ModObjExtensionInfoHandle extensionInfo, AbilityBase_Element *element)](#oh_abilityruntime_getmodularobjectextensioninfoelementname) | Gets the component name (AbilityBase_Element) from the specified ModularObjectExtensionAbility information. The bundleName, moduleName, and abilityName in element are non-owning pointers that point to the internal data of extensionInfo. Do not release them separately. They are available only while extensionInfo is valid. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetModularObjectExtensionInfoDisableState(OH_AbilityRuntime_ModObjExtensionInfoHandle extensionInfo, bool *isDisabled)](#oh_abilityruntime_getmodularobjectextensioninfodisablestate) | Obtains the disabled state from the specified ModularObjectExtensionAbility information. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_AcquireSelfModularObjectExtensionInfos(OH_AbilityRuntime_AllModObjExtensionInfosHandle *outOwnedAllExtensionInfos)](#oh_abilityruntime_acquireselfmodularobjectextensioninfos) | Gets the information about all registered ModularObjectExtensionAbility instances of the current application and returns a handle to the ModularObjectExtensionAbility information set. Use [OH_AbilityRuntime_GetCountFromAllModObjExtensionInfos](capi-modular-object-extension-manager-h.md#oh_abilityruntime_getcountfromallmodobjextensioninfos) to obtain the information count of the set, and use [OH_AbilityRuntime_GetModObjExtensionInfoByIndex](capi-modular-object-extension-manager-h.md#oh_abilityruntime_getmodobjextensioninfobyindex) to traverse each ModularObjectExtensionAbility information by index to obtain attributes such as the launch mode, process mode, and thread mode. After use, call [OH_AbilityRuntime_ReleaseAllExtensionInfos](capi-modular-object-extension-manager-h.md#oh_abilityruntime_releaseallextensioninfos) to release the handle to avoid memory leaks. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ReleaseAllExtensionInfos(OH_AbilityRuntime_AllModObjExtensionInfosHandle *allExtensionInfos)](#oh_abilityruntime_releaseallextensioninfos) | Releases the ModularObjectExtensionAbility information collection obtained by [OH_AbilityRuntime_AcquireSelfModularObjectExtensionInfos](capi-modular-object-extension-manager-h.md#oh_abilityruntime_acquireselfmodularobjectextensioninfos). When the ModularObjectExtensionAbility information collection is no longer needed, you must call this API to release the related resources to avoid memory leaks. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetCountFromAllModObjExtensionInfos(OH_AbilityRuntime_AllModObjExtensionInfosHandle allExtensionInfos, size_t *count)](#oh_abilityruntime_getcountfromallmodobjextensioninfos) | Obtains the number of ModularObjectExtensionAbility information items contained in the ModularObjectExtensionAbility information collection. The returned count can be used to determine the upper limit of the index when traversing the collection, and works with [OH_AbilityRuntime_GetModObjExtensionInfoByIndex](capi-modular-object-extension-manager-h.md#oh_abilityruntime_getmodobjextensioninfobyindex) to access each ModularObjectExtensionAbility information item in the collection. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetModObjExtensionInfoByIndex(OH_AbilityRuntime_AllModObjExtensionInfosHandle allExtensionInfos, size_t index, OH_AbilityRuntime_ModObjExtensionInfoHandle *extensionInfo)](#oh_abilityruntime_getmodobjextensioninfobyindex) | Obtains the specified ModularObjectExtensionAbility information from the ModularObjectExtensionAbility information collection by index. The valid index range is [0, count), where count can be obtained through [OH_AbilityRuntime_GetCountFromAllModObjExtensionInfos](capi-modular-object-extension-manager-h.md#oh_abilityruntime_getcountfromallmodobjextensioninfos). The obtained ModularObjectExtensionAbility information handle can be used to query the startup mode, process mode, thread mode, and other attributes of the ModularObjectExtensionAbility. The returned extensionInfo is a non-owning handle that points to the internal storage of the allExtensionInfos collection. Do not release it separately. It is available only while allExtensionInfos is valid. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ConnectModularObjectExtensionAbility(AbilityBase_Want *want, OH_AbilityRuntime_ConnectOptions *connectOptions, int64_t *connectionId)](#oh_abilityruntime_connectmodularobjectextensionability) | Connects to a ModularObjectExtensionAbility. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_DisconnectModularObjectExtensionAbility(int64_t connectionId)](#oh_abilityruntime_disconnectmodularobjectextensionability) | Disconnects from the ModularObjectExtensionAbility. |

## Enum type description

### OH_AbilityRuntime_LaunchMode

```c
enum OH_AbilityRuntime_LaunchMode
```

**Description**

Defines the launch mode of a ModularObjectExtensionAbility.

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

Defines the process mode of a ModularObjectExtensionAbility.

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

Defines the thread mode of a ModularObjectExtensionAbility.

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

Obtains the startup mode from the specified ModularObjectExtensionAbility information.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjExtensionInfoHandle](capi-abilityruntime-oh-abilityruntime-modobjextensioninfohandle.md) extensionInfo | The modular object extension info from which to get the launch mode. |
| [OH_AbilityRuntime_LaunchMode](capi-modular-object-extension-manager-h.md#oh_abilityruntime_launchmode) *launchMode | The launch mode obtained from the extension info. |

**Returns**:

| Type | Description |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | Returns a specific error code. [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the operation is successful. [ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the arguments provided are invalid. |

### OH_AbilityRuntime_GetModularObjectExtensionInfoProcessMode()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetModularObjectExtensionInfoProcessMode(OH_AbilityRuntime_ModObjExtensionInfoHandle extensionInfo, OH_AbilityRuntime_ProcessMode *processMode)
```

**Description**

Obtains the process mode from the specified ModularObjectExtensionAbility information.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjExtensionInfoHandle](capi-abilityruntime-oh-abilityruntime-modobjextensioninfohandle.md) extensionInfo | The modular object extension info to get the process mode from. |
| [OH_AbilityRuntime_ProcessMode](capi-modular-object-extension-manager-h.md#oh_abilityruntime_processmode) *processMode | The process mode obtained from the extension info. |

**Returns**:

| Type | Description |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | Returns a specific error code. [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the operation is successful. [ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the arguments provided are invalid. |

### OH_AbilityRuntime_GetModularObjectExtensionInfoThreadMode()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetModularObjectExtensionInfoThreadMode(OH_AbilityRuntime_ModObjExtensionInfoHandle extensionInfo, OH_AbilityRuntime_ThreadMode *threadMode)
```

**Description**

Obtains the thread mode from the specified ModularObjectExtensionAbility information.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjExtensionInfoHandle](capi-abilityruntime-oh-abilityruntime-modobjextensioninfohandle.md) extensionInfo | The modular object extension info to get the thread mode from. |
| [OH_AbilityRuntime_ThreadMode](capi-modular-object-extension-manager-h.md#oh_abilityruntime_threadmode) *threadMode | The thread mode obtained from the extension info. |

**Returns**:

| Type | Description |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | Returns a specific error code. [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the operation is successful. [ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the arguments provided are invalid. |

### OH_AbilityRuntime_GetModularObjectExtensionInfoElementName()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetModularObjectExtensionInfoElementName(OH_AbilityRuntime_ModObjExtensionInfoHandle extensionInfo, AbilityBase_Element *element)
```

**Description**

Gets the component name (AbilityBase_Element) from the specified ModularObjectExtensionAbility information. The bundleName, moduleName, and abilityName in element are non-owning pointers that point to the internal data of extensionInfo. Do not release them separately. They are available only while extensionInfo is valid.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjExtensionInfoHandle](capi-abilityruntime-oh-abilityruntime-modobjextensioninfohandle.md) extensionInfo | The modular object extension info to get the element name from. |
| [AbilityBase_Element](capi-abilitybase-abilitybase-element.md) *element | The element name obtained from the extension info. |

**Returns**:

| Type | Description |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | Returns a specific error code. [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the operation is successful. [ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the arguments provided are invalid. |

### OH_AbilityRuntime_GetModularObjectExtensionInfoDisableState()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetModularObjectExtensionInfoDisableState(OH_AbilityRuntime_ModObjExtensionInfoHandle extensionInfo, bool *isDisabled)
```

**Description**

Obtains the disabled state from the specified ModularObjectExtensionAbility information.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjExtensionInfoHandle](capi-abilityruntime-oh-abilityruntime-modobjextensioninfohandle.md) extensionInfo | The modular object extension info. |
| bool *isDisabled | Whether the extension is disabled. |

**Returns**:

| Type | Description |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | Returns a specific error code. [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the operation is successful. [ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the arguments provided are invalid. |

### OH_AbilityRuntime_AcquireSelfModularObjectExtensionInfos()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_AcquireSelfModularObjectExtensionInfos(OH_AbilityRuntime_AllModObjExtensionInfosHandle *outOwnedAllExtensionInfos)
```

**Description**

Gets the information about all registered ModularObjectExtensionAbility instances of the current application and returns a handle to the ModularObjectExtensionAbility information set. Use [OH_AbilityRuntime_GetCountFromAllModObjExtensionInfos](capi-modular-object-extension-manager-h.md#oh_abilityruntime_getcountfromallmodobjextensioninfos) to obtain the information count of the set, and use [OH_AbilityRuntime_GetModObjExtensionInfoByIndex](capi-modular-object-extension-manager-h.md#oh_abilityruntime_getmodobjextensioninfobyindex) to traverse each ModularObjectExtensionAbility information by index to obtain attributes such as the launch mode, process mode, and thread mode. After use, call [OH_AbilityRuntime_ReleaseAllExtensionInfos](capi-modular-object-extension-manager-h.md#oh_abilityruntime_releaseallextensioninfos) to release the handle to avoid memory leaks.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Resource release**: OH_AbilityRuntime_ReleaseAllExtensionInfos {outOwnedAllExtensionInfos}

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_AllModObjExtensionInfosHandle](capi-abilityruntime-oh-abilityruntime-allmodobjextensioninfoshandle.md) *outOwnedAllExtensionInfos | Information about all extensions within the self application. |

**Returns**:

| Type | Description |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | Returns a specific error code. [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the operation is successful. [ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the arguments provided are invalid. [ABILITY_RUNTIME_ERROR_CODE_NOT_SUPPORTED](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the device does not support. |

### OH_AbilityRuntime_ReleaseAllExtensionInfos()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ReleaseAllExtensionInfos(OH_AbilityRuntime_AllModObjExtensionInfosHandle *allExtensionInfos)
```

**Description**

Releases the ModularObjectExtensionAbility information collection obtained by [OH_AbilityRuntime_AcquireSelfModularObjectExtensionInfos](capi-modular-object-extension-manager-h.md#oh_abilityruntime_acquireselfmodularobjectextensioninfos). When the ModularObjectExtensionAbility information collection is no longer needed, you must call this API to release the related resources to avoid memory leaks.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_AllModObjExtensionInfosHandle](capi-abilityruntime-oh-abilityruntime-allmodobjextensioninfoshandle.md) *allExtensionInfos | The all modular object extension infos to be released. |

**Returns**:

| Type | Description |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | Returns a specific error code. [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the operation is successful. [ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the arguments provided are invalid. |

**Reference**:

[OH_AbilityRuntime_AcquireSelfModularObjectExtensionInfos](capi-modular-object-extension-manager-h.md#oh_abilityruntime_acquireselfmodularobjectextensioninfos)


### OH_AbilityRuntime_GetCountFromAllModObjExtensionInfos()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetCountFromAllModObjExtensionInfos(OH_AbilityRuntime_AllModObjExtensionInfosHandle allExtensionInfos, size_t *count)
```

**Description**

Obtains the number of ModularObjectExtensionAbility information items contained in the ModularObjectExtensionAbility information collection. The returned count can be used to determine the upper limit of the index when traversing the collection, and works with [OH_AbilityRuntime_GetModObjExtensionInfoByIndex](capi-modular-object-extension-manager-h.md#oh_abilityruntime_getmodobjextensioninfobyindex) to access each ModularObjectExtensionAbility information item in the collection.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_AllModObjExtensionInfosHandle](capi-abilityruntime-oh-abilityruntime-allmodobjextensioninfoshandle.md) allExtensionInfos | The handle representing the collection of all modular object extension infos. |
| size_t *count | Return value to receive the count of extensions in the collection. |

**Returns**:

| Type | Description |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | Returns a specific error code. [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the operation is successful. [ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the arguments provided are invalid. |

### OH_AbilityRuntime_GetModObjExtensionInfoByIndex()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetModObjExtensionInfoByIndex(OH_AbilityRuntime_AllModObjExtensionInfosHandle allExtensionInfos, size_t index, OH_AbilityRuntime_ModObjExtensionInfoHandle *extensionInfo)
```

**Description**

Obtains the specified ModularObjectExtensionAbility information from the ModularObjectExtensionAbility information collection by index. The valid index range is [0, count), where count can be obtained through [OH_AbilityRuntime_GetCountFromAllModObjExtensionInfos](capi-modular-object-extension-manager-h.md#oh_abilityruntime_getcountfromallmodobjextensioninfos). The obtained ModularObjectExtensionAbility information handle can be used to query the startup mode, process mode, thread mode, and other attributes of the ModularObjectExtensionAbility. The returned extensionInfo is a non-owning handle that points to the internal storage of the allExtensionInfos collection. Do not release it separately. It is available only while allExtensionInfos is valid.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_AllModObjExtensionInfosHandle](capi-abilityruntime-oh-abilityruntime-allmodobjextensioninfoshandle.md) allExtensionInfos | Information about all extensions within the self application. |
| size_t index | The index of the extension to retrieve. Must be strictly less than the count. |
| [OH_AbilityRuntime_ModObjExtensionInfoHandle](capi-abilityruntime-oh-abilityruntime-modobjextensioninfohandle.md) *extensionInfo | The retrieved single modular object extension info handle for the specified index. |

**Returns**:

| Type | Description |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | Returns a specific error code. [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the operation is successful. [ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the arguments provided are invalid. |

### OH_AbilityRuntime_ConnectModularObjectExtensionAbility()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ConnectModularObjectExtensionAbility(AbilityBase_Want *want, OH_AbilityRuntime_ConnectOptions *connectOptions, int64_t *connectionId)
```

**Description**

Connects to a ModularObjectExtensionAbility.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [AbilityBase_Want](capi-abilitybase-abilitybase-want.md) *want | Indicates the modular object extension ability to connect. For details, see [AbilityBase_Want](capi-abilitybase-abilitybase-want.md). |
| [OH_AbilityRuntime_ConnectOptions](capi-abilityruntime-oh-abilityruntime-connectoptions.md) *connectOptions | Indicates the connection options. |
| int64_t *connectionId | Indicates the connection id that is a output param. |

**Returns**:

| Type | Description |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | <ul> <li>[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the call is successful.</li> <li>[ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the arguments provided are invalid.</li> <li>[ABILITY_RUNTIME_ERROR_CODE_NOT_SUPPORTED](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the device does not support connecting modular object extension ability.</li> <li>[ABILITY_RUNTIME_ERROR_CODE_NO_SUCH_ABILITY](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the target ability does not exist.</li> <li>[ABILITY_RUNTIME_ERROR_CODE_INCORRECT_ABILITY_TYPE](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the ability type is incorrect.</li> <li>[ABILITY_RUNTIME_ERROR_CODE_VISIBILITY_VERIFICATION_FAILED](capi-ability-runtime-common-h.md#abilityruntime_errorcode) - Cannot start an invisible component.</li> <li>[ABILITY_RUNTIME_ERROR_CODE_STATIC_CFG_PERMISSION](capi-ability-runtime-common-h.md#abilityruntime_errorcode) The specified process does not have the permission.</li> <li>[ABILITY_RUNTIME_ERROR_CODE_CROSS_USER_OPERATION](capi-ability-runtime-common-h.md#abilityruntime_errorcode) Cross-user operations are not allowed.</li> <li>[ABILITY_RUNTIME_ERROR_CODE_CROWDTEST_EXPIRED](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the crowdtesting application expires.</li> <li>[ABILITY_RUNTIME_ERROR_CODE_INTERNAL](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if an internal error occurs.</li> <li>[ABILITY_RUNTIME_ERROR_CODE_NOT_TOP_ABILITY](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the caller is not a foreground process.</li> <li>[ABILITY_RUNTIME_ERROR_CODE_UPPER_LIMIT_REACHED](capi-ability-runtime-common-h.md#abilityruntime_errorcode) The number of instances with the same ability name is more than twenty.</li> <li>[ABILITY_RUNTIME_ERROR_CODE_NO_RUNNING_ABILITIES_WITH_UI](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the target application does not have running abilities with UI.</li> <li>[ABILITY_RUNTIME_ERROR_CODE_UPPER_RATE_LIMIT](capi-ability-runtime-common-h.md#abilityruntime_errorcode) The API call frequency is too high and exceeds 20 times per second.</li> <li>[ABILITY_RUNTIME_ERROR_CODE_UPPER_CONNECTION_NUMBER_LIMIT](capi-ability-runtime-common-h.md#abilityruntime_errorcode) The number of connections to the same ability name from the same pid exceeds five.</li> <li>[ABILITY_RUNTIME_ERROR_CODE_CROSS_APP_IN_PROCESS](capi-ability-runtime-common-h.md#abilityruntime_errorcode) Caller and target are not in the same application for [OH_ABILITY_RUNTIME_LAUNCH_MODE_IN_PROCESS](capi-modular-object-extension-manager-h.md#oh_abilityruntime_launchmode) mode.</li> </ul> |

### OH_AbilityRuntime_DisconnectModularObjectExtensionAbility()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_DisconnectModularObjectExtensionAbility(int64_t connectionId)
```

**Description**

Disconnects from the ModularObjectExtensionAbility.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| int64_t connectionId | Indicates the connection ID. |

**Returns**:

| Type | Description |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | Returns a specific error code. [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the call is successful. [ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the arguments provided are invalid. [ABILITY_RUNTIME_ERROR_CODE_INTERNAL](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if an internal error occurs. |


