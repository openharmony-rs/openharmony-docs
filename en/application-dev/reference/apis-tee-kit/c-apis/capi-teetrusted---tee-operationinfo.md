# __TEE_OperationInfo

```c
typedef struct __TEE_OperationInfo {...} TEE_OperationInfo
```

## Overview

Defines the operation information.

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Related module**: [TeeTrusted](capi-teetrusted.md)

**Header file**: [tee_crypto_api.h](capi-tee-crypto-api-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t algorithm | Algorithm ID |
| [](capi-teetrusted-peration-src-dest.md) | #\_\_TEE_CRYPTO_ALGORITHM_ID |
| uint32_t operationClass | Operation type |
| [](capi-teetrusted-peration-src-dest.md) | #\_\_TEE_Operation_Constants |
| uint32_t mode | Operation mode |
| [](capi-teetrusted-peration-src-dest.md) | #\_\_TEE_OperationMode |
| uint32_t digestLength | Digest length |
| uint32_t maxKeySize | Maximum key length |
| uint32_t keySize | Key length |
| uint32_t requiredKeyUsage | Required key usage |
| uint32_t handleState | Handle state |
| void *keyValue | Key |


