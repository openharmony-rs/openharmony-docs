# OH_Huks_KeyMaterialDh

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=2b1d4a689ab1802cb3fa270f284f5341d5d21f59 translatedAt=2026-10-12T08:37:34.735Z pushedAt=2026-10-13T06:55:17.695Z -->

```c
struct OH_Huks_KeyMaterialDh {...}
```

## Overview

Defines the struct for a DH key.

**Since**: 9

**Related module**: [HuksTypeApi](capi-hukstypeapi.md)

**Header file**: [native_huks_type.h](capi-native-huks-type-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| enum [OH_Huks_KeyAlg](capi-native-huks-type-h.md#oh_huks_keyalg) keyAlg | Algorithm of the key.|
| uint32_t keySize | Length of the DH key, in bits. |
| uint32_t pubKeySize | Length of the public key, in bytes. |
| uint32_t priKeySize | Length of the private key, in bytes. |
| uint32_t reserved | Reserved field.|


