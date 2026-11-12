# __TEE_OperationInfo

```c
typedef struct __TEE_OperationInfo {...} TEE_OperationInfo
```

## Overview

Defines the operation information.

<!--Device-typedef struct __TEE_OperationInfo {...} TEE_OperationInfo--><!--Device-typedef struct __TEE_OperationInfo {...} TEE_OperationInfo-End-->

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Related module**: [TeeTrusted](capi-tee-kit-teetrusted.md)

**Header file**: [tee_crypto_api.h](capi-tee-crypto-api-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t algorithm | Algorithm ID |
| [](capi-tee-crypto-api-h.md#) | #\_\_TEE_CRYPTO_ALGORITHM_ID |
| uint32_t operationClass | Operation type |
| [](capi-tee-crypto-api-h.md#) | #\_\_TEE_Operation_Constants |
| uint32_t mode | Operation mode |
| [](capi-tee-crypto-api-h.md#) | #\_\_TEE_OperationMode |
| uint32_t digestLength | Digest length |
| uint32_t maxKeySize | Maximum key length |
| uint32_t keySize | Key length |
| uint32_t requiredKeyUsage | Required key usage |
| uint32_t handleState | Handle state |
| void *keyValue | Key |


