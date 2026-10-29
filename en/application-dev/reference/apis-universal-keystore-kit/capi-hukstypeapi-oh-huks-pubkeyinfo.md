# OH_Huks_PubKeyInfo

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=cd5375bfd4eb9f0c52b88e433ebccd662d60f877 translatedAt=2026-10-12T08:38:54.750Z pushedAt=2026-10-13T06:55:17.700Z -->

```c
struct OH_Huks_PubKeyInfo {...}
```

## Overview

Defines the struct of a public key.

**Since**: 9

**Related module**: [HuksTypeApi](capi-hukstypeapi.md)

**Header file**: [native_huks_type.h](capi-native-huks-type-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| enum [OH_Huks_KeyAlg](capi-native-huks-type-h.md#oh_huks_keyalg) keyAlg | Algorithm of the public key.|
| uint32_t keySize | Length of the public key, in bits. |
| uint32_t nOrXSize | Length of the n or X value, in bytes. |
| uint32_t eOrYSize | Length of the e or Y value, in bytes. |
| uint32_t placeHolder | Size of the placeholder, in bytes. |
