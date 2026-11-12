# OH_Huks_ExternalCryptoParamSet

```c
typedef struct OH_Huks_ExternalCryptoParamSet {...} OH_Huks_ExternalCryptoParamSet
```

## Overview

Defines an external cryptographic parameter set.

<!--Device-struct OH_Huks_ExternalCryptoParamSet {...}--><!--Device-struct OH_Huks_ExternalCryptoParamSet {...}-End-->

**System capability**: SystemCapability.Security.Huks.CryptoExtension

**Since**: 22

**Related module**: [HuksExternalCryptoTypeApi](capi-universal-keystore-kit-huksexternalcryptotypeapi.md)

**Header file**: [native_huks_external_crypto_type.h](capi-native-huks-external-crypto-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t paramSetSize | Memory size of the parameter set.<br>**Since**: 22 |
| uint32_t paramsCnt | Number of parameters in the parameter set.<br>**Since**: 22 |
| [OH_Huks_ExternalCryptoParam](capi-huksexternalcryptotypeapi-oh-huks-externalcryptoparam.md) params[] | Parameter array.<br>**Since**: 22 |


