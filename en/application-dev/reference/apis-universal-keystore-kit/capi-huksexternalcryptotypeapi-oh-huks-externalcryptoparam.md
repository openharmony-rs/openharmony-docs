# OH_Huks_ExternalCryptoParam

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

```c
typedef struct {...} OH_Huks_ExternalCryptoParam
```

## Overview

Defines a single parameter in a parameter set.

**Since**: 22

**Related modules**: [HuksExternalCryptoTypeApi](capi-huksexternalcryptotypeapi.md)

**Header file**: [native_huks_external_crypto_type.h](capi-native-huks-external-crypto-type-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t tag | Tag value.|
| union {<br>  bool boolParam; <br>  int32_t int32Param; <br> uint32_t uint32Param; <br>    uint64_t uint64Param; <br>    [struct OH_Huks_Blob](capi-hukstypeapi-oh-huks-blob.md) blob; <br> } | Tag content.<br>**boolParam**: Boolean-type parameter.<br>**int32Param**: int32_t-type parameter.<br>**uint32Param**: uint32_t-type parameter.<br>**uint64Param**: uint64_t-type parameter.<br>**blob**: OH_Huks_Blob-type parameter. |
