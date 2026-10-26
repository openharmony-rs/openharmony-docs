# OH_AbilityRuntime_ModObjDispatcher_Variant

```c
typedef struct OH_AbilityRuntime_ModObjDispatcher_Variant {...} OH_AbilityRuntime_ModObjDispatcher_Variant
```

## Overview

Defines a variant struct that uses a union with a type tag to distinguish the actual data type, for safely passing values of multiple types during parameter passing and return value receiving. The value of a variant is determined by the vt field, which specifies the actual stored data type and the valid member of the union. When a variant holds heap-allocated resources (such as strings and container handles), call [OH_AbilityRuntime_ModObjDispatcher_VariantClear](capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_variantclear). Simple types (boolean, integer, and floating-point) do not hold heap resources and do not need to be released by calling OH_AbilityRuntime_ModObjDispatcher_VariantClear.<br> > **NOTE**<br>> > Do not call OH_AbilityRuntime_ModObjDispatcher_VariantClear on a shallow copy of the variant. > If Variant v2 = v1 is executed, only one of them can be cleared.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Related module**: [AbilityRuntime](capi-abilityruntime.md)

**Header file**: [modular_object_dispatcher.h](capi-modular-object-dispatcher-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| OH_AbilityRuntime_ModObjDispatcher_ValueType vt | Type tag of the variant, which determines the valid member in the union.<br>**Since**: 26.0.0 |
| uint64_t reserved1 | Reserved field 1. Reserved space for future versions. The caller should initialize it to 0 and should not read or modify it.<br>**Since**: 26.0.0 |
| uint64_t reserved2 | Reserved field 2. Reserved space for future versions. The caller should initialize it to 0 and should not read or modify it.<br>**Since**: 26.0.0 |
| uint64_t reserved3 | Reserved field 3 for future use.<br>**Since**: 26.0.0 |
| u->pvoidVal | Void pointer.<br>**Since**: 26.0.0 |
| u.boolVal | Boolean value.<br>**Since**: 26.0.0 |
| u.i8Val | 8-bit signed integer.<br>**Since**: 26.0.0 |
| u.i16Val | 16-bit signed integer.<br>**Since**: 26.0.0 |
| u.i32Val | 32-bit signed integer.<br>**Since**: 26.0.0 |
| u.i64Val | 64-bit signed integer.<br>**Since**: 26.0.0 |
| u.u8Val | 8-bit unsigned integer.<br>**Since**: 26.0.0 |
| u.u16Val | 16-bit unsigned integer.<br>**Since**: 26.0.0 |
| u.u32Val | 32-bit unsigned integer.<br>**Since**: 26.0.0 |
| u.u64Val | 64-bit unsigned integer.<br>**Since**: 26.0.0 |
| u.f32Val | 32-bit floating-point number (single precision).<br>**Since**: 26.0.0 |
| u.f64Val | 64-bit floating-point number (double precision).<br>**Since**: 26.0.0 |
| u.enumVal | Enum value.<br>**Since**: 26.0.0 |
| u.bstrVal | UTF-8 string handle, pointing to a heap-allocated string.<br>**Since**: 26.0.0 |
| u.parrayVal | Array handle.<br>**Since**: 26.0.0 |
| u.pvectorVal | Vector handle.<br>**Since**: 26.0.0 |
| u.psetVal | Set handle.<br>**Since**: 26.0.0 |
| u.pmapVal | Map handle.<br>**Since**: 26.0.0 |
| u.pstructVal | Struct handle.<br>**Since**: 26.0.0 |
| u->premoteProxyVal | Ipc remote proxy handle.<br>**Since**: 26.0.0 |
| u->premoteStubVal | Ipc remote stub handle.<br>**Since**: 26.0.0 |


