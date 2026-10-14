# OH_Huks_KeyMaterial25519

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=644b82cc8188e2ec88f46c00e089b5401f6d2d07 translatedAt=2026-10-12T08:37:33.186Z pushedAt=2026-10-13T06:55:17.692Z -->

```c
struct OH_Huks_KeyMaterial25519 {...}
```

## Overview

Defines a struct of a 25519 key.

**Since**: 9

**Related module**: [HuksTypeApi](capi-hukstypeapi.md)

**Header file**: [native_huks_type.h](capi-native-huks-type-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| enum [OH_Huks_KeyAlg](capi-native-huks-type-h.md#oh_huks_keyalg) keyAlg | Algorithm of the key.|
| uint32_t keySize | Length of the 25519 key, in bits. |
| uint32_t pubKeySize | Length of the public key, in bytes. |
| uint32_t priKeySize | Length of the private key, in bytes. |
| uint32_t reserved | The reserved field. You are advised to set the value to **0**.|