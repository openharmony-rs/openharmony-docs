# OH_AbilityRuntime_ModObjDispatcher_Variant

```c
typedef struct OH_AbilityRuntime_ModObjDispatcher_Variant {...} OH_AbilityRuntime_ModObjDispatcher_Variant
```

## Overview

Defines a variant structure using union + type tag for ABI compatibility.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

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
| u->pvoidVal | Empty value.<br>**Since**: 26.0.0 |
| u.boolVal | Boolean value.<br>**Since**: 26.0.0 |
| u.i8Val | 8-bit signed integer.<br>**Since**: 26.0.0 |
| u.i16Val | 16-bit signed integer.<br>**Since**: 26.0.0 |
| u.i32Val | 32-bit signed integer.<br>**Since**: 26.0.0 |
| u.i64Val | 64-bit signed integer.<br>**Since**: 26.0.0 |
| u.u8Val | 8-bit unsigned integer.<br>**Since**: 26.0.0 |
| u.u16Val | 16-bit unsigned integer.<br>**Since**: 26.0.0 |
| u.u32Val | 32-bit unsigned integer.<br>**Since**: 26.0.0 |
| u.u64Val | 64-bit unsigned integer.<br>**Since**: 26.0.0 |
| u.f32Val | 32-bit floating point.<br>**Since**: 26.0.0 |
| u.f64Val | 64-bit floating point.<br>**Since**: 26.0.0 |
| u.enumVal | Enum value.<br>**Since**: 26.0.0 |
| u.bstrVal | String value (UTF-8) pointer.<br>**Since**: 26.0.0 |
| u.parrayVal | Array handle.<br>**Since**: 26.0.0 |
| u.pvectorVal | Vector handle.<br>**Since**: 26.0.0 |
| u.psetVal | Set handle.<br>**Since**: 26.0.0 |
| u.pmapVal | Map handle.<br>**Since**: 26.0.0 |
| u.pstructVal | Struct handle.<br>**Since**: 26.0.0 |
| u->premoteProxyVal | Ipc remote proxy handle.<br>**Since**: 26.0.0 |
| u->premoteStubVal | Ipc remote stub handle.<br>**Since**: 26.0.0 |


