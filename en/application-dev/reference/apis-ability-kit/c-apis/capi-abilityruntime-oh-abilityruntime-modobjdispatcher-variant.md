# OH_AbilityRuntime_ModObjDispatcher_Variant

```c
typedef struct OH_AbilityRuntime_ModObjDispatcher_Variant {...} OH_AbilityRuntime_ModObjDispatcher_Variant
```

## Overview

Defines a variant structure using union + type tag for ABI compatibility.

**Since**: 26.0.0

**Related module**: [AbilityRuntime](capi-abilityruntime.md)

**Header file**: [modular_object_dispatcher.h](capi-modular-object-dispatcher-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| OH_AbilityRuntime_ModObjDispatcher_ValueType vt | Variant type.<br>**Since**: 26.0.0 |
| uint64_t reserved1 | Reserved field 1 for future use.<br>**Since**: 26.0.0 |
| uint64_t reserved2 | Reserved field 2 for future use.<br>**Since**: 26.0.0 |
| uint64_t reserved3 | Reserved field 3 for future use.<br>**Since**: 26.0.0 |
| union | Variant value data.<br>**Since**: 26.0.0 |
| void *pvoidVal | Empty value.<br>**Since**: 26.0.0 |
| bool boolVal | Boolean value.<br>**Since**: 26.0.0 |
| int8_t i8Val | 8-bit signed integer.<br>**Since**: 26.0.0 |
| int16_t i16Val | 16-bit signed integer.<br>**Since**: 26.0.0 |
| int32_t i32Val | 32-bit signed integer.<br>**Since**: 26.0.0 |
| int64_t i64Val | 64-bit signed integer.<br>**Since**: 26.0.0 |
| uint8_t u8Val | 8-bit unsigned integer.<br>**Since**: 26.0.0 |
| uint16_t u16Val | 16-bit unsigned integer.<br>**Since**: 26.0.0 |
| uint32_t u32Val | 32-bit unsigned integer.<br>**Since**: 26.0.0 |
| uint64_t u64Val | 64-bit unsigned integer.<br>**Since**: 26.0.0 |
| float f32Val | 32-bit floating point.<br>**Since**: 26.0.0 |
| double f64Val | 64-bit floating point.<br>**Since**: 26.0.0 |
| int32_t enumVal | Enum value.<br>**Since**: 26.0.0 |
| char* bstrVal | String value (UTF-8) pointer.<br>**Since**: 26.0.0 |
| [OH_AbilityRuntime_ModObjDispatcher_ArrayHandle](capi-abilityruntime-oh-abilityruntime-modularobjectdispatcher-array8h.md) parrayVal | Array handle.<br>**Since**: 26.0.0 |
| [OH_AbilityRuntime_ModObjDispatcher_VectorHandle](capi-abilityruntime-oh-abilityruntime-modularobjectdispatcher-vector8h.md) pvectorVal | Vector handle.<br>**Since**: 26.0.0 |
| [OH_AbilityRuntime_ModObjDispatcher_SetHandle](capi-abilityruntime-oh-abilityruntime-modularobjectdispatcher-set8h.md) psetVal | Set handle.<br>**Since**: 26.0.0 |
| [OH_AbilityRuntime_ModObjDispatcher_MapHandle](capi-abilityruntime-oh-abilityruntime-modularobjectdispatcher-map8h.md) pmapVal | Map handle.<br>**Since**: 26.0.0 |
| [OH_AbilityRuntime_ModObjDispatcher_StructHandle](capi-abilityruntime-oh-abilityruntime-modularobjectdispatcher-struct8h.md) pstructVal | Struct handle.<br>**Since**: 26.0.0 |
| OHIPCRemoteProxy *premoteProxyVal | Ipc remote proxy handle.<br>**Since**: 26.0.0 |
| OHIPCRemoteStub *premoteStubVal;
 } u | Ipc remote stub handle.<br>**Since**: 26.0.0 |


