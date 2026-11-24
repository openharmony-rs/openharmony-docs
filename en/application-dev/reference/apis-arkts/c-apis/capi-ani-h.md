# ani.h

## Overview

Defines native api of ArkTS 1.2 native module.

**Library**: libani.z.so

**System capability**: SystemCapability.ArkCompiler.ANI

**Since**: 23

**Related module**: [](capi-arkts-.md)

## Summary

### Structs

| Name | typedef keyword | Description |
| -- | -- | -- |
| [\_\_ani_ref](capi----ani-ref.md) | - | Defines native api of ArkTS 1.2 native module. |
| [\_\_ani_object](capi----ani-object.md) | - |  |
| [\_\_ani_fn_object](capi----ani-fn-object.md) | - |  |
| [\_\_ani_enum_item](capi----ani-enum-item.md) | - |  |
| [\_\_ani_error](capi----ani-error.md) | - |  |
| [\_\_ani_tuple_value](capi----ani-tuple-value.md) | - |  |
| [\_\_ani_arraybuffer](capi----ani-arraybuffer.md) | - |  |
| [\_\_ani_string](capi----ani-string.md) | - |  |
| [\_\_ani_type](capi----ani-type.md) | - |  |
| [\_\_ani_class](capi----ani-class.md) | - |  |
| [\_\_ani_module](capi----ani-module.md) | - |  |
| [\_\_ani_namespace](capi----ani-namespace.md) | - |  |
| [\_\_ani_enum](capi----ani-enum.md) | - |  |
| [\_\_ani_array](capi----ani-array.md) | - |  |
| [\_\_ani_fixedarray](capi----ani-fixedarray.md) | - |  |
| [\_\_ani_valuearray](capi----ani-valuearray.md) | - |  |
| [\_\_ani_valuearray_boolean](capi----ani-valuearray-boolean.md) | - |  |
| [\_\_ani_valuearray_char](capi----ani-valuearray-char.md) | - |  |
| [\_\_ani_valuearray_byte](capi----ani-valuearray-byte.md) | - |  |
| [\_\_ani_valuearray_short](capi----ani-valuearray-short.md) | - |  |
| [\_\_ani_valuearray_int](capi----ani-valuearray-int.md) | - |  |
| [\_\_ani_valuearray_long](capi----ani-valuearray-long.md) | - |  |
| [\_\_ani_valuearray_float](capi----ani-valuearray-float.md) | - |  |
| [\_\_ani_valuearray_double](capi----ani-valuearray-double.md) | - |  |
| [ani_value](capi--ani-value.md) | ani_value |  |
| [ani_native_function](capi--ani-native-function.md) | ani_native_function |  |
| [ani_option](capi--ani-option.md) | ani_option |  |
| [ani_options](capi--ani-options.md) | ani_options |  |
| [\_\_ani_vm_api](capi----ani-vm-api.md) | - |  |
| [\_\_ani_interaction_api](capi----ani-interaction-api.md) | - |  |
| [\_\_ani_vm](capi----ani-vm.md) | - |  |
| [\_\_ani_env](capi----ani-env.md) | - |  |

### Enums

| Name | typedef keyword | Description |
| -- | -- | -- |
| [](#) | - | Defines native api of ArkTS 1.2 native module. |
| [](#) | - | Defines native api of ArkTS 1.2 native module. |
| [ani_status](#ani_status) | ani_status | Defines native api of ArkTS 1.2 native module. |

### Variables

| Name | Description |
| -- | -- |
| typedef uint8_t ani_boolean | Defines native api of ArkTS 1.2 native module.<br>**Since**: 23<br>**System capability**: SystemCapability.ArkCompiler.ANI<br><!--Device-typedef uint8_t ani_boolean--><!--Device-typedef uint8_t ani_boolean-End--> |
| typedef uint16_t ani_char | Defines native api of ArkTS 1.2 native module.<br>**Since**: 23<br>**System capability**: SystemCapability.ArkCompiler.ANI<br><!--Device-typedef uint16_t ani_char--><!--Device-typedef uint16_t ani_char-End--> |
| typedef int8_t ani_byte | Defines native api of ArkTS 1.2 native module.<br>**Since**: 23<br>**System capability**: SystemCapability.ArkCompiler.ANI<br><!--Device-typedef int8_t ani_byte--><!--Device-typedef int8_t ani_byte-End--> |
| typedef int16_t ani_short | Defines native api of ArkTS 1.2 native module.<br>**Since**: 23<br>**System capability**: SystemCapability.ArkCompiler.ANI<br><!--Device-typedef int16_t ani_short--><!--Device-typedef int16_t ani_short-End--> |
| typedef int32_t ani_int | Defines native api of ArkTS 1.2 native module.<br>**Since**: 23<br>**System capability**: SystemCapability.ArkCompiler.ANI<br><!--Device-typedef int32_t ani_int--><!--Device-typedef int32_t ani_int-End--> |
| typedef float ani_float | Defines native api of ArkTS 1.2 native module.<br>**Since**: 23<br>**System capability**: SystemCapability.ArkCompiler.ANI<br><!--Device-typedef float ani_float--><!--Device-typedef float ani_float-End--> |
| typedef double ani_double | Defines native api of ArkTS 1.2 native module.<br>**Since**: 23<br>**System capability**: SystemCapability.ArkCompiler.ANI<br><!--Device-typedef double ani_double--><!--Device-typedef double ani_double-End--> |

## Enum type description

### 

```c
enum 
```

**Description**

Defines native api of ArkTS 1.2 native module.

<!--Device---><!--Device--End-->

**System capability**: SystemCapability.ArkCompiler.ANI

**Since**: 23

| Enum item | Description |
| -- | -- |

### 

```c
enum 
```

**Description**

Defines native api of ArkTS 1.2 native module.

<!--Device---><!--Device--End-->

**System capability**: SystemCapability.ArkCompiler.ANI

**Since**: 23

| Enum item | Description |
| -- | -- |

### ani_status

```c
enum ani_status
```

**Description**

Defines native api of ArkTS 1.2 native module.

<!--Device-enum ani_status--><!--Device-enum ani_status-End-->

**System capability**: SystemCapability.ArkCompiler.ANI

**Since**: 23

| Enum item | Description |
| -- | -- |
| ANI_OK | <!--Device-ANI_OK--><!--Device-ANI_OK-End--> |
| ANI_ERROR | <!--Device-ANI_ERROR--><!--Device-ANI_ERROR-End--> |
| ANI_INVALID_ARGS | <!--Device-ANI_INVALID_ARGS--><!--Device-ANI_INVALID_ARGS-End--> |
| ANI_INVALID_TYPE | <!--Device-ANI_INVALID_TYPE--><!--Device-ANI_INVALID_TYPE-End--> |
| ANI_INVALID_DESCRIPTOR | <!--Device-ANI_INVALID_DESCRIPTOR--><!--Device-ANI_INVALID_DESCRIPTOR-End--> |
| ANI_INCORRECT_REF | <!--Device-ANI_INCORRECT_REF--><!--Device-ANI_INCORRECT_REF-End--> |
| ANI_PENDING_ERROR | <!--Device-ANI_PENDING_ERROR--><!--Device-ANI_PENDING_ERROR-End--> |
| ANI_NOT_FOUND | <!--Device-ANI_NOT_FOUND--><!--Device-ANI_NOT_FOUND-End--> |
| ANI_ALREADY_BINDED | <!--Device-ANI_ALREADY_BINDED--><!--Device-ANI_ALREADY_BINDED-End--> |
| ANI_OUT_OF_REF | <!--Device-ANI_OUT_OF_REF--><!--Device-ANI_OUT_OF_REF-End--> |
| ANI_OUT_OF_MEMORY | <!--Device-ANI_OUT_OF_MEMORY--><!--Device-ANI_OUT_OF_MEMORY-End--> |
| ANI_OUT_OF_RANGE | <!--Device-ANI_OUT_OF_RANGE--><!--Device-ANI_OUT_OF_RANGE-End--> |
| ANI_BUFFER_TO_SMALL | <!--Device-ANI_BUFFER_TO_SMALL--><!--Device-ANI_BUFFER_TO_SMALL-End--> |
| ANI_INVALID_VERSION | <!--Device-ANI_INVALID_VERSION--><!--Device-ANI_INVALID_VERSION-End--> |
| ANI_AMBIGUOUS | <!--Device-ANI_AMBIGUOUS--><!--Device-ANI_AMBIGUOUS-End--> |


