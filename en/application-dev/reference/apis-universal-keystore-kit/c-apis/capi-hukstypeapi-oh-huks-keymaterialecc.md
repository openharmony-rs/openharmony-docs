# OH_Huks_KeyMaterialEcc

```c
typedef struct OH_Huks_KeyMaterialEcc {...} OH_Huks_KeyMaterialEcc
```

## Overview

Defines the struct for an ECC key.

**Since**: 9

**Related module**: [HuksTypeApi](capi-hukstypeapi.md)

**Header file**: [native_huks_type.h](capi-native-huks-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| enum [OH_Huks_KeyAlg](capi-native-huks-type-h.md#oh_huks_keyalg) keyAlg | Algorithm of the key. |
| uint32_t keySize | Length of the key. |
| uint32_t xSize | Length of **x**. |
| uint32_t ySize | Length of **y**. |
| uint32_t zSize | Length of **z**, which corresponds to the size of the private key d. |


