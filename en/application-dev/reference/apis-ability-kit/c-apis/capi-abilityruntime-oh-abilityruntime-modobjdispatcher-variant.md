# OH_AbilityRuntime_ModObjDispatcher_Variant

```c
typedef struct OH_AbilityRuntime_ModObjDispatcher_Variant {...} OH_AbilityRuntime_ModObjDispatcher_Variant
```

## Overview

Defines a variant struct that uses a union with a type tag to distinguish the actual data type, for safely passing values of multiple types during parameter passing and return value receiving. The value of a variant is determined by the vt field, which specifies the actual stored data type and the valid member of the union. When a variant holds heap-allocated resources (such as strings and container handles), call [OH_AbilityRuntime_ModObjDispatcher_VariantClear](capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_variantclear). Simple types (boolean, integer, and floating-point) do not hold heap resources and do not need to be released by calling OH_AbilityRuntime_ModObjDispatcher_VariantClear.<br>
> **NOTE**
>
> Do not call OH_AbilityRuntime_ModObjDispatcher_VariantClear on a shallow copy of the variant.
> If Variant v2 = v1 is executed, only one of them can be cleared.

<!--Device-typedef struct OH_AbilityRuntime_ModObjDispatcher_Variant {...} OH_AbilityRuntime_ModObjDispatcher_Variant--><!--Device-typedef struct OH_AbilityRuntime_ModObjDispatcher_Variant {...} OH_AbilityRuntime_ModObjDispatcher_Variant-End-->

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Related module**: [AbilityRuntime](capi-ability-kit-abilityruntime.md)

**Header file**: [modular_object_dispatcher.h](capi-modular-object-dispatcher-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [OH_AbilityRuntime_ModObjDispatcher_ValueType](capi-modular-object-dispatcher-h.md#oh_abilityruntime_modobjdispatcher_valuetype) vt | Type tag of the variant, which determines the valid member in the union.<br>**Since**: 26.0.0<br><!--Device-OH_AbilityRuntime_ModObjDispatcher_ValueType vt--><!--Device-OH_AbilityRuntime_ModObjDispatcher_ValueType vt-End--> |
| uint64_t reserved1 | Reserved field 1. Reserved space for future versions. The caller should initialize it to 0 and should not read or modify it.<br>**Since**: 26.0.0<br><!--Device-uint64_t reserved1--><!--Device-uint64_t reserved1-End--> |
| uint64_t reserved2 | Reserved field 2. Reserved space for future versions. The caller should initialize it to 0 and should not read or modify it.<br>**Since**: 26.0.0<br><!--Device-uint64_t reserved2--><!--Device-uint64_t reserved2-End--> |
| uint64_t reserved3 | Reserved field 3 for future use.<br>**Since**: 26.0.0<br><!--Device-uint64_t reserved3--><!--Device-uint64_t reserved3-End--> |
| u.pvoidVal | Void pointer.<br>**Since**: 26.0.0<br><!--Device-u.pvoidVal--><!--Device-u.pvoidVal-End--> |
| u.boolVal | Boolean value.<br>**Since**: 26.0.0<br><!--Device-u.boolVal--><!--Device-u.boolVal-End--> |
| u.i8Val | 8-bit signed integer.<br>**Since**: 26.0.0<br><!--Device-u.i8Val--><!--Device-u.i8Val-End--> |
| u.i16Val | 16-bit signed integer.<br>**Since**: 26.0.0<br><!--Device-u.i16Val--><!--Device-u.i16Val-End--> |
| u.i32Val | 32-bit signed integer.<br>**Since**: 26.0.0<br><!--Device-u.i32Val--><!--Device-u.i32Val-End--> |
| u.i64Val | 64-bit signed integer.<br>**Since**: 26.0.0<br><!--Device-u.i64Val--><!--Device-u.i64Val-End--> |
| u.u8Val | 8-bit unsigned integer.<br>**Since**: 26.0.0<br><!--Device-u.u8Val--><!--Device-u.u8Val-End--> |
| u.u16Val | 16-bit unsigned integer.<br>**Since**: 26.0.0<br><!--Device-u.u16Val--><!--Device-u.u16Val-End--> |
| u.u32Val | 32-bit unsigned integer.<br>**Since**: 26.0.0<br><!--Device-u.u32Val--><!--Device-u.u32Val-End--> |
| u.u64Val | 64-bit unsigned integer.<br>**Since**: 26.0.0<br><!--Device-u.u64Val--><!--Device-u.u64Val-End--> |
| u.f32Val | 32-bit floating-point number (single precision).<br>**Since**: 26.0.0<br><!--Device-u.f32Val--><!--Device-u.f32Val-End--> |
| u.f64Val | 64-bit floating-point number (double precision).<br>**Since**: 26.0.0<br><!--Device-u.f64Val--><!--Device-u.f64Val-End--> |
| u.enumVal | Enum value.<br>**Since**: 26.0.0<br><!--Device-u.enumVal--><!--Device-u.enumVal-End--> |
| u.bstrVal | UTF-8 string handle, pointing to a heap-allocated string.<br>**Since**: 26.0.0<br><!--Device-u.bstrVal--><!--Device-u.bstrVal-End--> |
| u.parrayVal | Array handle.<br>**Since**: 26.0.0<br><!--Device-u.parrayVal--><!--Device-u.parrayVal-End--> |
| u.pvectorVal | Vector handle.<br>**Since**: 26.0.0<br><!--Device-u.pvectorVal--><!--Device-u.pvectorVal-End--> |
| u.psetVal | Set handle.<br>**Since**: 26.0.0<br><!--Device-u.psetVal--><!--Device-u.psetVal-End--> |
| u.pmapVal | Map handle.<br>**Since**: 26.0.0<br><!--Device-u.pmapVal--><!--Device-u.pmapVal-End--> |
| u.pstructVal | Struct handle.<br>**Since**: 26.0.0<br><!--Device-u.pstructVal--><!--Device-u.pstructVal-End--> |
| u.premoteProxyVal | Ipc remote proxy handle.<br>**Since**: 26.0.0<br><!--Device-u.premoteProxyVal--><!--Device-u.premoteProxyVal-End--> |
| u.premoteStubVal | Ipc remote stub handle.<br>**Since**: 26.0.0<br><!--Device-u.premoteStubVal--><!--Device-u.premoteStubVal-End--> |


