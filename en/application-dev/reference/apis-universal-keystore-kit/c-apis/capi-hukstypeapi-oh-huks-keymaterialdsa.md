# OH_Huks_KeyMaterialDsa

```c
typedef struct OH_Huks_KeyMaterialDsa {...} OH_Huks_KeyMaterialDsa
```

## Overview

Defines the struct for a DSA key.

<!--Device-struct OH_Huks_KeyMaterialDsa {...}--><!--Device-struct OH_Huks_KeyMaterialDsa {...}-End-->

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
| uint32_t pSize | Length of **p**.<br><!--Device-uint32_t pSize--><!--Device-uint32_t pSize-End--> |
| uint32_t qSize | Length of **q**.<br><!--Device-uint32_t qSize--><!--Device-uint32_t qSize-End--> |
| uint32_t gSize | Length of **g**.<br><!--Device-uint32_t gSize--><!--Device-uint32_t gSize-End--> |


