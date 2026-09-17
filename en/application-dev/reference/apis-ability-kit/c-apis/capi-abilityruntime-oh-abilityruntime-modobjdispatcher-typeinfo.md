# OH_AbilityRuntime_ModObjDispatcher_TypeInfo

```c
typedef struct OH_AbilityRuntime_ModObjDispatcher_TypeInfo {...} OH_AbilityRuntime_ModObjDispatcher_TypeInfo
```

## Overview

Defines the parameter type descriptor for modular object dispatcher.<br> Describes the type of a parameter or return value using a tagged union. for array types, use u.arrayType.pElementType and u.arrayType.size; for vector/set types, use u.pElementType; for struct/proxy/stub/enum types, use u.idlType.

**Since**: 26.0.0

**Related module**: [AbilityRuntime](capi-abilityruntime.md)

**Header file**: [modular_object_dispatcher.h](capi-modular-object-dispatcher-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| OH_AbilityRuntime_ModObjDispatcher_ValueType vt | Type tag that determines which union member is valid.<br>**Since**: 26.0.0 |
| union | Union of type-specific metadata. The valid member is determined by {@link vt}.<br>**Since**: 26.0.0 |
| struct | Map type metadata. Used when vt is {@link OH_ABILITY_RUNTIME_MOD_OBJ_DISPATCHER_VT_MAP}.<br>**Since**: 26.0.0 |
| OH_AbilityRuntime_ModObjDispatcher_ValueType keyType | Key type of the map. Only basic types are supported. Container types (ARRAY, VECTOR, SET, MAP) and complex types (STRUCT, IPC_REMOTE_PROXY, IPC_REMOTE_STUB) are not supported.<br>**Since**: 26.0.0 |
| OH_AbilityRuntime_ModObjDispatcher_TypeInfo *pValueType;
 } mapType | Pointer to the value type descriptor. Must be released by [OH_AbilityRuntime_ModObjDispatcher_TypeInfoClear](capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_typeinfoclear).<br>**Since**: 26.0.0 |
| struct | Array type metadata. Used when vt is {@link OH_ABILITY_RUNTIME_MOD_OBJ_DISPATCHER_VT_ARRAY}.<br>**Since**: 26.0.0 |
| struct [OH_AbilityRuntime_ModObjDispatcher_TypeInfo](capi-abilityruntime-oh-abilityruntime-modobjdispatcher-typeinfo.md) *pElementType | Pointer to the element type descriptor. Must be released by [OH_AbilityRuntime_ModObjDispatcher_TypeInfoClear](capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_typeinfoclear).<br>**Since**: 26.0.0 |
| uint32_t size;
 } arrayType | Fixed array size.<br>**Since**: 26.0.0 |
| [OH_AbilityRuntime_ModObjDispatcher_TypeInfo](capi-abilityruntime-oh-abilityruntime-modobjdispatcher-typeinfo.md) *pElementType | Pointer to the element type descriptor. Used when vt is {@link OH_ABILITY_RUNTIME_MOD_OBJ_DISPATCHER_VT_VECTOR}<br> or {@link OH_ABILITY_RUNTIME_MOD_OBJ_DISPATCHER_VT_SET}. Must be released by [OH_AbilityRuntime_ModObjDispatcher_TypeInfoClear](capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_typeinfoclear).<br>**Since**: 26.0.0 |
| char* idlType;
 } u | IDL type name string (heap-allocated). Used when vt is {@link OH_ABILITY_RUNTIME_MOD_OBJ_DISPATCHER_VT_STRUCT},<br> {@link OH_ABILITY_RUNTIME_MOD_OBJ_DISPATCHER_VT_IPC_REMOTE_PROXY},<br> {@link OH_ABILITY_RUNTIME_MOD_OBJ_DISPATCHER_VT_IPC_REMOTE_STUB},<br> or {@link OH_ABILITY_RUNTIME_MOD_OBJ_DISPATCHER_VT_ENUM}. Must be released by [OH_AbilityRuntime_ModObjDispatcher_TypeInfoClear](capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_typeinfoclear).<br>**Since**: 26.0.0 |


