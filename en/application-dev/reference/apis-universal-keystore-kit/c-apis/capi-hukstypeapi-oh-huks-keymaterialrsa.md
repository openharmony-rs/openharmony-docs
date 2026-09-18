# OH_Huks_KeyMaterialRsa

```c
typedef struct OH_Huks_KeyMaterialRsa {...} OH_Huks_KeyMaterialRsa
```

## Overview

Defines the struct for an RSA key.

**Since**: 9

**Related module**: [HuksTypeApi](capi-hukstypeapi.md)

**Header file**: [native_huks_type.h](capi-native-huks-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| enum [OH_Huks_KeyAlg](capi-native-huks-type-h.md#oh_huks_keyalg) keyAlg | Algorithm of the key. |
| uint32_t keySize | Length of the key. |
| uint32_t nSize | Length of **n**. |
| uint32_t eSize | Length of **e**. |
| uint32_t dSize | Length of **d**. |


