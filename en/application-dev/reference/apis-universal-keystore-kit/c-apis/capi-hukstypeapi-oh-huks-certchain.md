# OH_Huks_CertChain

```c
typedef struct OH_Huks_CertChain {...} OH_Huks_CertChain
```

## Overview

Defines the struct of a certificate chain.

**Since**: 9

**Related module**: [HuksTypeApi](capi-hukstypeapi.md)

**Header file**: [native_huks_type.h](capi-native-huks-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| struct [OH_Huks_Blob](capi-hukstypeapi-oh-huks-blob.md) *certs | Pointer to the certificate data. |
| uint32_t certsCount | Number of certificates. |


