# OH_Huks_KeyMaterialEcc

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=2e095fa5ecc4620fd41ae7343a0724b558fdb05d translatedAt=2026-11-03T06:26:59.389Z pushedAt=2026-11-03T12:08:25.630Z nl=1 -->

```c
struct OH_Huks_KeyMaterialEcc {...}
```

## Overview

Defines the struct for an ECC key.

**Since**: 9

**Related module:** [HuksTypeApi](capi-hukstypeapi.md)

**Header file**: [native_huks_type.h](capi-native-huks-type-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| enum [OH_Huks_KeyAlg](capi-native-huks-type-h.md#oh_huks_keyalg) keyAlg | Algorithm of the key.|
| uint32_t keySize | Key length, in bits. |
| uint32_t xSize | Length of the x value, in bytes. |
| uint32_t ySize | Length of the y value, in bytes. |
| uint32_t zSize | Length of the z value, in bytes. |


