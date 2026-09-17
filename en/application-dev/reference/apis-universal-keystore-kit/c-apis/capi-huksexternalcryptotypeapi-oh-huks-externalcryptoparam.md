# OH_Huks_ExternalCryptoParam

```c
typedef struct OH_Huks_ExternalCryptoParam {...} OH_Huks_ExternalCryptoParam
```

## Overview

Defines a single parameter in a parameter set.

**Since**: 22

**Related module**: [HuksExternalCryptoTypeApi](capi-huksexternalcryptotypeapi.md)

**Header file**: [native_huks_external_crypto_type.h](capi-native-huks-external-crypto-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t tag | Tag value.<br>**Since**: 22 |
| union | Tag Content.<br>**Since**: 22 |
| bool boolParam | Parameter of the Boolean type.<br>**Since**: 22 |
| int32_t int32Param | Parameter of the int32_t type.<br>**Since**: 22 |
| uint32_t uint32Param | Parameter of the uint32_t type.<br>**Since**: 22 |
| uint64_t uint64Param | Parameter of the uint64_t type.<br>**Since**: 22 |
| struct OH_Huks_Blob blob;
 } | Parameter of the struct OH_Huks_Blob type.<br>**Since**: 22 |


