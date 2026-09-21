# OH_Huks_Param

```c
typedef struct OH_Huks_Param {...} OH_Huks_Param
```

## Overview

Defines the types of the parameters in a parameter set.

**System capability**: SystemCapability.Security.Huks.Core

**Since**: 9

**Related module**: [HuksTypeApi](capi-hukstypeapi.md)

**Header file**: [native_huks_type.h](capi-native-huks-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t tag;

 union | Tag value. |
| bool boolParam | Parameter of the Boolean type. |
| int32_t int32Param | Parameter of the int32_t type. |
| uint32_t uint32Param | Parameter of the uint32_t type. |
| uint64_t uint64Param | Parameter of the uint64_t type. |
| struct [OH_Huks_Blob](capi-hukstypeapi-oh-huks-blob.md) blob;
 } | Parameter of the struct OH_Huks_Blob type. |


