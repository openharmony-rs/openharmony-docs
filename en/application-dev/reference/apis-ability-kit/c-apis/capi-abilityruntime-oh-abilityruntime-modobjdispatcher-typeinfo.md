# OH_AbilityRuntime_ModObjDispatcher_TypeInfo

```c
struct OH_AbilityRuntime_ModObjDispatcher_TypeInfo {...}
```

## Overview

Defines the parameter type descriptor for modular object dispatcher.<br> Describes the type of a parameter or return value using a tagged union. for array types, use u.arrayType.pElementType and u.arrayType.size; for vector/set types, use u.pElementType; for struct/proxy/stub/enum types, use u.idlType.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Related module**: [AbilityRuntime](capi-abilityruntime.md)

**Header file**: [modular_object_dispatcher.h](capi-modular-object-dispatcher-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| OH_AbilityRuntime_ModObjDispatcher_ValueType vt | Type tag that determines which union member is valid.<br>**Since**: 26.0.0 |
| u.mapType.keyType | Key type of the map. Only basic types are supported. Container types (ARRAY, VECTOR, SET, MAP) and complex types (STRUCT, IPC_REMOTE_PROXY, IPC_REMOTE_STUB) are not supported.<br>**Since**: 26.0.0 |
| u.mapType->pValueType | Pointer to the value type descriptor. Must be released by [OH_AbilityRuntime_ModObjDispatcher_TypeInfoClear](capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_typeinfoclear).<br>**Since**: 26.0.0 |
| u.arrayType->pElementType | Pointer to the element type descriptor. Must be released by [OH_AbilityRuntime_ModObjDispatcher_TypeInfoClear](capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_typeinfoclear).<br>**Since**: 26.0.0 |
| u.arrayType.size | Fixed array size.<br>**Since**: 26.0.0 |
| u->pElementType | Pointer to the element type descriptor. Used when vt is [OH_ABILITY_RUNTIME_MOD_OBJ_DISPATCHER_VT_VECTOR](capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_valuetype) or [OH_ABILITY_RUNTIME_MOD_OBJ_DISPATCHER_VT_SET](capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_valuetype). Must be released by [OH_AbilityRuntime_ModObjDispatcher_TypeInfoClear](capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_typeinfoclear).<br>**Since**: 26.0.0 |
| u.idlType | IDL type name string (heap-allocated). Used when vt is [OH_ABILITY_RUNTIME_MOD_OBJ_DISPATCHER_VT_STRUCT](capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_valuetype), [OH_ABILITY_RUNTIME_MOD_OBJ_DISPATCHER_VT_IPC_REMOTE_PROXY](capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_valuetype), [OH_ABILITY_RUNTIME_MOD_OBJ_DISPATCHER_VT_IPC_REMOTE_STUB](capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_valuetype), or [OH_ABILITY_RUNTIME_MOD_OBJ_DISPATCHER_VT_ENUM](capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_valuetype). Must be released by [OH_AbilityRuntime_ModObjDispatcher_TypeInfoClear](capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_typeinfoclear).<br>**Since**: 26.0.0 |


