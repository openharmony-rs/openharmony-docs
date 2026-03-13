# OH_Huks_ExternalCryptoParamSet

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

```c
typedef struct OH_Huks_ExternalCryptoParamSet {...} OH_Huks_ExternalCryptoParamSet
```

## Overview

Defines an external cryptographic parameter set.

**Since**: 22

**Related modules**: [HuksExternalCryptoTypeApi](capi-huksexternalcryptotypeapi.md)

**Header file**: [native_huks_external_crypto_type.h](capi-native-huks-external-crypto-type-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t paramSetSize | Size of the parameter set, in bytes.<br>**Since**: 22|
| uint32_t paramsCnt | Number of parameters in the parameter set.<br>**Since**: 22|
| [OH_Huks_ExternalCryptoParam](capi-huksexternalcryptotypeapi-oh-huks-externalcryptoparam.md) params[] | Parameter array. The size is determined by **paramSetSize** and **paramsCnt**.<br>**Since**: 22|
