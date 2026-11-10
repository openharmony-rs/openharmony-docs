# OH_Huks_KeyMaterialDsa

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=1e1412148ed572eddb6ce9ee7817f465f66a8cee translatedAt=2026-11-03T06:26:25.246Z pushedAt=2026-11-03T12:08:25.629Z nl=1 -->

```c
struct OH_Huks_KeyMaterialDsa {...}
```

## Overview

Defines the struct for a DSA key.

**Since**: 9

**Related module**: [HuksTypeApi](capi-hukstypeapi.md)

**Header file**: [native_huks_type.h](capi-native-huks-type-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| enum [OH_Huks_KeyAlg](capi-native-huks-type-h.md#oh_huks_keyalg) keyAlg | Algorithm of the key.|
| uint32_t keySize | Key length, in bits. |
| uint32_t xSize | x value length, in bytes. |
| uint32_t ySize | y value length, in bytes. |
| uint32_t pSize | p value length, in bytes. |
| uint32_t qSize | q value length, in bytes. |
| uint32_t gSize | g value length, in bytes. |


