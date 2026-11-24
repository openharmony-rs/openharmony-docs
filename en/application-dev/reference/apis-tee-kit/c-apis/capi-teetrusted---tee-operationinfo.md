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
| uint32_t algorithm | Algorithm ID<br><!--Device-uint32_t algorithm--><!--Device-uint32_t algorithm-End--> |
| [](capi-tee-crypto-api-h.md#) | #\_\_TEE_CRYPTO_ALGORITHM_ID<br><!--Device---><!--Device--End--> |
| uint32_t operationClass | Operation type<br><!--Device-uint32_t operationClass--><!--Device-uint32_t operationClass-End--> |
| [](capi-tee-crypto-api-h.md#) | #\_\_TEE_Operation_Constants<br><!--Device---><!--Device--End--> |
| uint32_t mode | Operation mode<br><!--Device-uint32_t mode--><!--Device-uint32_t mode-End--> |
| [](capi-tee-crypto-api-h.md#) | #\_\_TEE_OperationMode<br><!--Device---><!--Device--End--> |
| uint32_t digestLength | Digest length<br><!--Device-uint32_t digestLength--><!--Device-uint32_t digestLength-End--> |
| uint32_t maxKeySize | Maximum key length<br><!--Device-uint32_t maxKeySize--><!--Device-uint32_t maxKeySize-End--> |
| uint32_t keySize | Key length<br><!--Device-uint32_t keySize--><!--Device-uint32_t keySize-End--> |
| uint32_t requiredKeyUsage | Required key usage<br><!--Device-uint32_t requiredKeyUsage--><!--Device-uint32_t requiredKeyUsage-End--> |
| uint32_t handleState | Handle state<br><!--Device-uint32_t handleState--><!--Device-uint32_t handleState-End--> |
| void *keyValue | Key<br><!--Device-void *keyValue--><!--Device-void *keyValue-End--> |


