# OH_Huks_PubKeyInfo

```c
typedef struct OH_Huks_PubKeyInfo {...} OH_Huks_PubKeyInfo
```

## Overview

Defines the struct of a public key.

**Since**: 9

**Related module**: [HuksTypeApi](capi-hukstypeapi.md)

**Header file**: [native_huks_type.h](capi-native-huks-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| enum [OH_Huks_KeyAlg](capi-native-huks-type-h.md#oh_huks_keyalg) keyAlg | Algorithm of the public key. |
| uint32_t keySize | Length of the public key. |
| uint32_t nOrXSize | Length of **n** or **X**. |
| uint32_t eOrYSize | Length of **e** or **Y**. |
| uint32_t placeHolder | Placeholder size, intended for memory alignment or reserving space for future algorithmic extensions. |


