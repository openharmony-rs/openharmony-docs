# TEE_OperationInfoKey

```c
typedef struct TEE_OperationInfoKey {...} TEE_OperationInfoKey
```

## Overview

Defines the key information stored in the <b>OperationInfo</b>.

<!--Device-typedef struct TEE_OperationInfoKey {...} TEE_OperationInfoKey--><!--Device-typedef struct TEE_OperationInfoKey {...} TEE_OperationInfoKey-End-->

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Related module**: [TeeTrusted](capi-tee-kit-teetrusted.md)

**Header file**: [tee_crypto_api.h](capi-tee-crypto-api-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t keySize | Key length |
| uint32_t requiredKeyUsage | Required key usage |


