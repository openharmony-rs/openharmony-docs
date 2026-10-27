# OH_AbilityRuntime_ModObjDispatcher_TypeInfo

```c
struct OH_AbilityRuntime_ModObjDispatcher_TypeInfo {...}
```

## Overview

Defines the type information of a parameter or return value. Uses the tagged union u to describe the type information, and uses the vt field to determine which member of the union is valid. - For the map (MAP) type, use u.mapType.keyType to describe the key type and u.mapType.pValueType to describe the value type. - For the array (ARRAY) type, use u.arrayType.pElementType to describe the element type and u.arrayType.size to describe the fixed size of the array. - For the vector (VECTOR) or set (SET) type, use u.pElementType to describe the element type. - For the struct (STRUCT), remote communication object (IPC_REMOTE_PROXY, IPC_REMOTE_STUB), and enum (ENUM) types, use u.idlType to describe the IDL type name. After use, call [OH_AbilityRuntime_ModObjDispatcher_TypeInfoClear](capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_typeinfoclear) to release the heap resources held internally.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Related module**: [AbilityRuntime](capi-abilityruntime.md)

**Header file**: [modular_object_dispatcher.h](capi-modular-object-dispatcher-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| OH_AbilityRuntime_ModObjDispatcher_ValueType vt | Type tag that determines which union member is valid.<br>**Since**: 26.0.0 |
| u.mapType.keyType | key type of the map. Only basic types (BOOL, signed integer, unsigned integer, floating-point number, STRING, and ENUM) are supported. Container types (ARRAY, VECTOR, SET, and MAP) and complex types (STRUCT, IPC_REMOTE_PROXY, and IPC_REMOTE_STUB) are not supported.<br>**Since**: 26.0.0 |
| u.mapType->pValueType | Pointer to the value type descriptor. Must be released by [OH_AbilityRuntime_ModObjDispatcher_TypeInfoClear](capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_typeinfoclear).<br>**Since**: 26.0.0 |
| u.arrayType->pElementType | Pointer to the element type descriptor. Must be released by [OH_AbilityRuntime_ModObjDispatcher_TypeInfoClear](capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_typeinfoclear).<br>**Since**: 26.0.0 |
| u.arrayType.size | Fixed array size.<br>**Since**: 26.0.0 |
| u->pElementType | Pointer to the element type descriptor. Used when vt is [OH_ABILITY_RUNTIME_MOD_OBJ_DISPATCHER_VT_VECTOR](capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_valuetype) or [OH_ABILITY_RUNTIME_MOD_OBJ_DISPATCHER_VT_SET](capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_valuetype). Must be released by [OH_AbilityRuntime_ModObjDispatcher_TypeInfoClear](capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_typeinfoclear).<br>**Since**: 26.0.0 |
| u.idlType | IDL type name string (heap-allocated). Used when vt is [OH_ABILITY_RUNTIME_MOD_OBJ_DISPATCHER_VT_STRUCT](capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_valuetype), [OH_ABILITY_RUNTIME_MOD_OBJ_DISPATCHER_VT_IPC_REMOTE_PROXY](capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_valuetype), [OH_ABILITY_RUNTIME_MOD_OBJ_DISPATCHER_VT_IPC_REMOTE_STUB](capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_valuetype), or [OH_ABILITY_RUNTIME_MOD_OBJ_DISPATCHER_VT_ENUM](capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_valuetype). Must be released by [OH_AbilityRuntime_ModObjDispatcher_TypeInfoClear](capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_typeinfoclear).<br>**Since**: 26.0.0 |


