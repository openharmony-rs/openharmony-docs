# OH_Huks_KeyMaterialRsa

```c
typedef struct OH_Huks_KeyMaterialRsa {...} OH_Huks_KeyMaterialRsa
```

## Overview

Defines the struct for an RSA key.

<!--Device-struct OH_Huks_KeyMaterialRsa {...}--><!--Device-struct OH_Huks_KeyMaterialRsa {...}-End-->

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
| uint32_t nSize | Length of **n**.<br><!--Device-uint32_t nSize--><!--Device-uint32_t nSize-End--> |
| uint32_t eSize | Length of **e**.<br><!--Device-uint32_t eSize--><!--Device-uint32_t eSize-End--> |
| uint32_t dSize | Length of **d**.<br><!--Device-uint32_t dSize--><!--Device-uint32_t dSize-End--> |


