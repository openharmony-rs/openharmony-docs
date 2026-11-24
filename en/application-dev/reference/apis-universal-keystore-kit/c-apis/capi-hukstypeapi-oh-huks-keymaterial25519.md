# OH_Huks_KeyMaterial25519

```c
typedef struct OH_Huks_KeyMaterial25519 {...} OH_Huks_KeyMaterial25519
```

## Overview

Defines a struct of a 25519 key.

<!--Device-struct OH_Huks_KeyMaterial25519 {...}--><!--Device-struct OH_Huks_KeyMaterial25519 {...}-End-->

**System capability**: SystemCapability.Security.Huks.Core

**Since**: 9

**Related module**: [HuksTypeApi](capi-universal-keystore-kit-hukstypeapi.md)

**Header file**: [native_huks_type.h](capi-native-huks-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| enum [OH_Huks_KeyAlg](capi-native-huks-type-h.md#oh_huks_keyalg) keyAlg | Algorithm of the key.<br><!--Device-enum OH_Huks_KeyAlg keyAlg--><!--Device-enum OH_Huks_KeyAlg keyAlg-End--> |
| uint32_t keySize | Length of the 25519 key.<br><!--Device-uint32_t keySize--><!--Device-uint32_t keySize-End--> |
| uint32_t pubKeySize | Length of the public key.<br><!--Device-uint32_t pubKeySize--><!--Device-uint32_t pubKeySize-End--> |
| uint32_t priKeySize | Length of the private key.<br><!--Device-uint32_t priKeySize--><!--Device-uint32_t priKeySize-End--> |
| uint32_t reserved | Reserved field.<br><!--Device-uint32_t reserved--><!--Device-uint32_t reserved-End--> |


