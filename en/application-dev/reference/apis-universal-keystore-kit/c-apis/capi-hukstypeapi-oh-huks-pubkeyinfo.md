# OH_Huks_PubKeyInfo

```c
typedef struct OH_Huks_PubKeyInfo {...} OH_Huks_PubKeyInfo
```

## Overview

Defines the struct of a public key.

<!--Device-struct OH_Huks_PubKeyInfo {...}--><!--Device-struct OH_Huks_PubKeyInfo {...}-End-->

**System capability**: SystemCapability.Security.Huks.Core

**Since**: 9

**Related module**: [HuksTypeApi](capi-universal-keystore-kit-hukstypeapi.md)

**Header file**: [native_huks_type.h](capi-native-huks-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| enum [OH_Huks_KeyAlg](capi-native-huks-type-h.md#oh_huks_keyalg) keyAlg | Algorithm of the public key.<br><!--Device-enum OH_Huks_KeyAlg keyAlg--><!--Device-enum OH_Huks_KeyAlg keyAlg-End--> |
| uint32_t keySize | Length of the public key.<br><!--Device-uint32_t keySize--><!--Device-uint32_t keySize-End--> |
| uint32_t nOrXSize | Length of **n** or **X**.<br><!--Device-uint32_t nOrXSize--><!--Device-uint32_t nOrXSize-End--> |
| uint32_t eOrYSize | Length of **e** or **Y**.<br><!--Device-uint32_t eOrYSize--><!--Device-uint32_t eOrYSize-End--> |
| uint32_t placeHolder | Placeholder size, intended for memory alignment or reserving space for future algorithmic extensions.<br><!--Device-uint32_t placeHolder--><!--Device-uint32_t placeHolder-End--> |


