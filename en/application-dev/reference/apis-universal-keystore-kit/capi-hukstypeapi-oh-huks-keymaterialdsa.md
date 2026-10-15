# OH_Huks_KeyMaterialDsa

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=1e1412148ed572eddb6ce9ee7817f465f66a8cee translatedAt=2026-10-12T08:38:22.080Z pushedAt=2026-10-13T06:55:17.697Z -->

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
| uint32_t keySize | Length of the key, in bits. |
| uint32_t xSize | Length of the x value, in bytes. |
| uint32_t ySize | Length of the y value, in bytes. |
| uint32_t pSize | Length of the p value, in bytes. |
| uint32_t qSize | Length of the q value, in bytes. |
| uint32_t gSize | Length of the g value, in bytes. |


