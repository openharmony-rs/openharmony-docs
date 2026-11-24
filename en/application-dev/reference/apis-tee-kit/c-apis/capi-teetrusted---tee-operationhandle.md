# __TEE_OperationHandle

```c
typedef struct __TEE_OperationHandle {...} TEE_OperationHandleVar
```

## Overview

Defines the cryptographic operation handle.

<!--Device-typedef struct __TEE_OperationHandle {...} TEE_OperationHandleVar--><!--Device-typedef struct __TEE_OperationHandle {...} TEE_OperationHandleVar-End-->

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
| uint32_t keySize | Key length<br><!--Device-uint32_t keySize--><!--Device-uint32_t keySize-End--> |
| uint32_t keySize2 | Key length<br><!--Device-uint32_t keySize2--><!--Device-uint32_t keySize2-End--> |
| uint32_t requiredKeyUsage | Required key usage<br><!--Device-uint32_t requiredKeyUsage--><!--Device-uint32_t requiredKeyUsage-End--> |
| uint32_t handleState | Handle state<br><!--Device-uint32_t handleState--><!--Device-uint32_t handleState-End--> |
| void *keyValue | Key<br><!--Device-void *keyValue--><!--Device-void *keyValue-End--> |
| void *keyValue2 | Key<br><!--Device-void *keyValue2--><!--Device-void *keyValue2-End--> |
| void *crypto_ctxt | <!--Device-void *crypto_ctxt--><!--Device-void *crypto_ctxt-End--> |
| void *hmac_rest_ctext | <!--Device-void *hmac_rest_ctext--><!--Device-void *hmac_rest_ctext-End--> |
| void *IV | iv<br><!--Device-void *IV--><!--Device-void *IV-End--> |
| void *publicKey | Public key<br><!--Device-void *publicKey--><!--Device-void *publicKey-End--> |
| uint32_t publicKeyLen | Length of the public key<br><!--Device-uint32_t publicKeyLen--><!--Device-uint32_t publicKeyLen-End--> |
| void *privateKey | Private key<br><!--Device-void *privateKey--><!--Device-void *privateKey-End--> |
| uint32_t privateKeyLen | Length of the private key<br><!--Device-uint32_t privateKeyLen--><!--Device-uint32_t privateKeyLen-End--> |
| uint32_t IVLen | Length of the IV<br><!--Device-uint32_t IVLen--><!--Device-uint32_t IVLen-End--> |
| [TEE_DH_OtherInfo](capi-teetrusted-tee-dh-otherinfo.md) *dh_otherinfo | TEE_DH_OtherInfo<br><!--Device-TEE_DH_OtherInfo *dh_otherinfo--><!--Device-TEE_DH_OtherInfo *dh_otherinfo-End--> |
| uint32_t dh_hash_mode | TEE_DH_HASH_Mode<br><!--Device-uint32_t dh_hash_mode--><!--Device-uint32_t dh_hash_mode-End--> |
| uint32_t dh_derive_func | TEE_DH_DerivFuncMode<br><!--Device-uint32_t dh_derive_func--><!--Device-uint32_t dh_derive_func-End--> |
| uint32_t dh_op_mode;
 void *dh_prime;
 uint32_t dh_prime_size | TEE_DH_OpMode_t<br><!--Device-uint32_t dh_op_mode; void *dh_prime; uint32_t dh_prime_size--><!--Device-uint32_t dh_op_mode; void *dh_prime; uint32_t dh_prime_size-End--> |
| pthread_mutex_t operation_lock | Operation lock<br><!--Device-pthread_mutex_t operation_lock--><!--Device-pthread_mutex_t operation_lock-End--> |
| void *hal_info | HAL information<br><!--Device-void *hal_info--><!--Device-void *hal_info-End--> |
| void *dh_prime | <!--Device-void *dh_prime--><!--Device-void *dh_prime-End--> |


