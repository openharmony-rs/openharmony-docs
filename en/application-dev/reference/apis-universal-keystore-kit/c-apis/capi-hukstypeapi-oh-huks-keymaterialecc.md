# OH_Huks_KeyMaterialEcc

```c
typedef struct OH_Huks_KeyMaterialEcc {...} OH_Huks_KeyMaterialEcc
```

## Overview

Defines the struct for an ECC key.

<!--Device-struct OH_Huks_KeyMaterialEcc {...}--><!--Device-struct OH_Huks_KeyMaterialEcc {...}-End-->

**System capability**: SystemCapability.Security.Huks.Core

**Since**: 9

**Related module**: [HuksTypeApi](capi-universal-keystore-kit-hukstypeapi.md)

**Header file**: [native_huks_type.h](capi-native-huks-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| enum [OH_Huks_KeyAlg](capi-native-huks-type-h.md#oh_huks_keyalg) keyAlg | Algorithm of the key.<br><!--Device-enum OH_Huks_KeyAlg keyAlg--><!--Device-enum OH_Huks_KeyAlg keyAlg-End--> |
| uint32_t keySize | Length of the key.<br><!--Device-uint32_t keySize--><!--Device-uint32_t keySize-End--> |
| uint32_t xSize | Length of **x**.<br><!--Device-uint32_t xSize--><!--Device-uint32_t xSize-End--> |
| uint32_t ySize | Length of **y**.<br><!--Device-uint32_t ySize--><!--Device-uint32_t ySize-End--> |
| uint32_t zSize | Length of **z**, which corresponds to the size of the private key d.<br><!--Device-uint32_t zSize--><!--Device-uint32_t zSize-End--> |


