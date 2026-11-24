# TEE_OperationInfoMultiple

```c
typedef struct TEE_OperationInfoMultiple {...} TEE_OperationInfoMultiple
```

## Overview

Defines information about an operation.

<!--Device-typedef struct TEE_OperationInfoMultiple {...} TEE_OperationInfoMultiple--><!--Device-typedef struct TEE_OperationInfoMultiple {...} TEE_OperationInfoMultiple-End-->

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Related module**: [TeeTrusted](capi-tee-kit-teetrusted.md)

**Header file**: [tee_crypto_api.h](capi-tee-crypto-api-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t algorithm | Algorithm ID<br><!--Device-uint32_t algorithm--><!--Device-uint32_t algorithm-End--> |
| uint32_t operationClass | Operation type<br><!--Device-uint32_t operationClass--><!--Device-uint32_t operationClass-End--> |
| uint32_t mode | Operation mode<br><!--Device-uint32_t mode--><!--Device-uint32_t mode-End--> |
| uint32_t digestLength | Digest length<br><!--Device-uint32_t digestLength--><!--Device-uint32_t digestLength-End--> |
| uint32_t maxKeySize | Maximum key length<br><!--Device-uint32_t maxKeySize--><!--Device-uint32_t maxKeySize-End--> |
| uint32_t handleState | Handle state<br><!--Device-uint32_t handleState--><!--Device-uint32_t handleState-End--> |
| uint32_t operationState | Operation state<br><!--Device-uint32_t operationState--><!--Device-uint32_t operationState-End--> |
| uint32_t numberOfKeys | Number of keys<br><!--Device-uint32_t numberOfKeys--><!--Device-uint32_t numberOfKeys-End--> |
| [TEE_OperationInfoKey](capi-teetrusted-tee-operationinfokey.md) keyInformation[] | Key information<br><!--Device-TEE_OperationInfoKey keyInformation[]--><!--Device-TEE_OperationInfoKey keyInformation[]-End--> |


