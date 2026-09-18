# __TEE_OperationHandle

```c
typedef struct __TEE_OperationHandle {...} TEE_OperationHandleVar
```

## Overview

Defines the cryptographic operation handle.

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
| uint32_t keySize | Key length |
| uint32_t keySize2 | Key length |
| uint32_t requiredKeyUsage | Required key usage |
| uint32_t handleState | Handle state |
| void *keyValue | Key |
| void *keyValue2 | Key |
| void *crypto_ctxt |  |
| void *hmac_rest_ctext |  |
| void *IV | iv |
| void *publicKey | Public key |
| uint32_t publicKeyLen | Length of the public key |
| void *privateKey | Private key |
| uint32_t privateKeyLen | Length of the private key |
| uint32_t IVLen | Length of the IV |
| [TEE_DH_OtherInfo](capi-teetrusted-tee-dh-otherinfo.md) *dh_otherinfo | TEE_DH_OtherInfo |
| uint32_t dh_hash_mode | TEE_DH_HASH_Mode |
| uint32_t dh_derive_func | TEE_DH_DerivFuncMode |
| uint32_t dh_op_mode;
 void *dh_prime;
 uint32_t dh_prime_size | TEE_DH_OpMode_t |
| pthread_mutex_t operation_lock | Operation lock |
| void *hal_info | HAL information |


