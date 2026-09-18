# TEE_OperationInfoMultiple

```c
typedef struct TEE_OperationInfoMultiple {...} TEE_OperationInfoMultiple
```

## Overview

Defines information about an operation.

**Since**: 20

**Related module**: [TeeTrusted](capi-teetrusted.md)

**Header file**: [tee_crypto_api.h](capi-tee-crypto-api-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t algorithm | Algorithm ID |
| uint32_t operationClass | Operation type |
| uint32_t mode | Operation mode |
| uint32_t digestLength | Digest length |
| uint32_t maxKeySize | Maximum key length |
| uint32_t handleState | Handle state |
| uint32_t operationState | Operation state |
| uint32_t numberOfKeys | Number of keys |
| [TEE_OperationInfoKey](capi-teetrusted-tee-operationinfokey.md) keyInformation[] | Key information |


