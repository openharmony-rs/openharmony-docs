# OH_Huks_KeyMaterialRsa

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=8206b4517f6911f415eabe97c00d211b77dc20ce translatedAt=2026-10-12T08:38:55.968Z pushedAt=2026-10-13T06:55:17.701Z -->

```c
struct OH_Huks_KeyMaterialRsa {...}
```

## Overview

Defines the struct for an RSA key.

**Since**: 9

**Related module:** [HuksTypeApi](capi-hukstypeapi.md)

**Header file**: [native_huks_type.h](capi-native-huks-type-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| enum [OH_Huks_KeyAlg](capi-native-huks-type-h.md#oh_huks_keyalg) keyAlg | Algorithm of the key.|
| uint32_t keySize | Length of the key, in bits. |
| uint32_t nSize | Length of n, in bytes. |
| uint32_t eSize | Length of e, in bytes. |
| uint32_t dSize | Length of d, in bytes. |


