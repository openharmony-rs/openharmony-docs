# tee_crypto_api.h

## Overview

Provides APIs for cryptographic operations.<br> You can use these APIs to implement encryption and decryption.

**Library**: NA

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Related module**: [TeeTrusted](capi-teetrusted.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [TEE_DH_OtherInfo](capi-teetrusted-tee-dh-otherinfo.md) | TEE_DH_OtherInfo | Defines a struct for TEE_DH_OtherInfo. |
| [\_\_TEE_OperationInfo](capi-teetrusted---tee-operationinfo.md) | TEE_OperationInfo | Defines the operation information. |
| [TEE_OperationInfoKey](capi-teetrusted-tee-operationinfokey.md) | TEE_OperationInfoKey | Defines the key information stored in the <b>OperationInfo</b>. |
| [TEE_OperationInfoMultiple](capi-teetrusted-tee-operationinfomultiple.md) | TEE_OperationInfoMultiple | Defines information about an operation. |
| [\_\_TEE_OperationHandle](capi-teetrusted---tee-operationhandle.md) | TEE_OperationHandleVar | Defines the cryptographic operation handle. |
| [crypto_uint2uint](capi-teetrusted-crypto-uint2uint.md) | crypto_uint2uint | Defines the data used for conversion of integers. |
| [peration_src_dest](capi-teetrusted-peration-src-dest.md) | - | Defines a structure to hold the input and output data. |
| [peration_ae_init](capi-teetrusted-peration-ae-init.md) | - | Defines the AE initialization data. |
| [\_\_TEE_ObjectHandle](capi-teetrusted---tee-objecthandle.md) | TEE_ObjectHandleVar | Defines the <b>\_\_TEE_ObjectHandle</b> struct. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [\_\_TEE_Operation_Constants](#\_\_tee_operation_constants) | - | Enumerates the cryptographic operation handles. |
| [\_\_tee_crypto_algorithm_id](#\_\_tee_crypto_algorithm_id) | - | Enumerates the cryptographic algorithms. |
| [TEE_ECC_CURVE](#tee_ecc_curve) | TEE_ECC_CURVE | Enumerates the Elliptic-Curve Cryptography (ECC) curves supported. |
| [TEE_DH_HASH_Mode](#tee_dh_hash_mode) | TEE_DH_HASH_Mode | Enumerates the Mask Generation Function (MGF1) modes. |
| [TEE_DH_OpMode_t](#tee_dh_opmode_t) | TEE_DH_OpMode_t | Enumerates the Diffie-Hellman operation modes. |
| [TEE_DH_DerivFuncMode](#tee_dh_derivfuncmode) | TEE_DH_DerivFuncMode | Defines an enum for TEE_DH_DerivFuncMode. |
| [\_\_TEE_DK_ObjectAttribute](#\_\_tee_dk_objectattribute) | - | Enumerates the object attributes for cryptographic operations. |
| [\_\_TEE_OperationMode](#\_\_tee_operationmode) | - | Enumerates the cryptographic operation modes. |
| [tee_operation_state](#tee_operation_state) | - | Enumerates the cryptographic operation states. |

### Macro

| Name | Description |
| -- | -- |
| NULL ((void *)0) | Definition of <b>NULL</b>.<br>**Since**: 20 |
| TEE_MAX_KEY_SIZE_IN_BITS      (1024 * 8) | Defines the maximum key length, in bits.<br>**Since**: 20 |
| SW_RSA_KEYLEN                 1024 | Defines the length of the SW_RSA key, in bytes.<br>**Since**: 20 |
| TEE_DH_MAX_SIZE_OF_OTHER_INFO 64 | Defines the maximum length of other Diffie-Hellman (DH) information, in bytes.<br>**Since**: 20 |
| TEE_PARAM_COUNT_MAX 9 | Defines the maximum parameter count.<br>**Since**: 20 |
| TEE_OPTIONAL_ELEMENT_NONE 0x00000000 | No element is available.<br>**Since**: 20 |
| RSA_PUBKEY_MAXSIZE sizeof(CRYS_RSAUserPubKey_t) | Defines the maximum length of an RSA public key.<br>**Since**: 20 |
| RSA_PRIVKEY_MAXSIZE sizeof(CRYS_RSAUserPrivKey_t) | Defines the maximum length of an RES private key.<br>**Since**: 20 |

### Function

| Name | Description |
| -- | -- |
| [TEE_Result TEE_AllocateOperation(TEE_OperationHandle *operation, uint32_t algorithm, uint32_t mode, uint32_t maxKeySize)](#tee_allocateoperation) | Allocates an operation handle. |
| [void TEE_FreeOperation(TEE_OperationHandle operation)](#tee_freeoperation) | Releases an operation handle. |
| [void TEE_GetOperationInfo(const TEE_OperationHandle operation, TEE_OperationInfo *operationInfo)](#tee_getoperationinfo) | Obtains operation information. |
| [void TEE_ResetOperation(TEE_OperationHandle operation)](#tee_resetoperation) | Resets an operation handle. |
| [TEE_Result TEE_SetOperationKey(TEE_OperationHandle operation, const TEE_ObjectHandle key)](#tee_setoperationkey) | Sets the key for an operation. |
| [TEE_Result TEE_SetOperationKey2(TEE_OperationHandle operation, const TEE_ObjectHandle key1, const TEE_ObjectHandle key2)](#tee_setoperationkey2) | Sets two keys for an operation. |
| [void TEE_CopyOperation(TEE_OperationHandle dstOperation, const TEE_OperationHandle srcOperation)](#tee_copyoperation) | Copies an operation handle. |
| [void TEE_CipherInit(TEE_OperationHandle operation, const void *IV, size_t IVLen)](#tee_cipherinit) | Initializes the context to start a cipher operation. |
| [TEE_Result TEE_CipherUpdate(TEE_OperationHandle operation, const void *srcData, size_t srcLen, void *destData, size_t *destLen)](#tee_cipherupdate) | Updates the data for a cipher operation. |
| [TEE_Result TEE_CipherDoFinal(TEE_OperationHandle operation, const void *srcData, size_t srcLen, void *destData, size_t *destLen)](#tee_cipherdofinal) | Finalizes a cipher operation. |
| [void TEE_DigestUpdate(TEE_OperationHandle operation, const void *chunk, size_t chunkSize)](#tee_digestupdate) | Updates the digest. |
| [TEE_Result TEE_DigestDoFinal(TEE_OperationHandle operation, const void *chunk, size_t chunkLen, void *hash, size_t *hashLen)](#tee_digestdofinal) | Finalizes the message digest operation. |
| [void TEE_MACInit(TEE_OperationHandle operation, void *IV, size_t IVLen)](#tee_macinit) | Initializes a MAC operation. |
| [void TEE_MACUpdate(TEE_OperationHandle operation, const void *chunk, size_t chunkSize)](#tee_macupdate) | Updates the MAC. |
| [TEE_Result TEE_MACComputeFinal(TEE_OperationHandle operation, const void *message, size_t messageLen, void *mac, size_t *macLen)](#tee_maccomputefinal) | MAC Finalizes the MAC operation with a last chunk of message and computes the MAC. |
| [TEE_Result TEE_MACCompareFinal(TEE_OperationHandle operation, const void *message, size_t messageLen, const void *mac, const size_t macLen)](#tee_maccomparefinal) | Finalizes the MAC operation and compares the MAC with the one passed in. |
| [void TEE_DeriveKey(TEE_OperationHandle operation, const TEE_Attribute *params, uint32_t paramCount, TEE_ObjectHandle derivedKey)](#tee_derivekey) | Derives a key. |
| [void TEE_GenerateRandom(void *randomBuffer, size_t randomBufferLen)](#tee_generaterandom) | Generates random data. |
| [TEE_Result TEE_AEInit(TEE_OperationHandle operation, void *nonce, size_t nonceLen, uint32_t tagLen, size_t AADLen, size_t payloadLen)](#tee_aeinit) | Initializes an AE operation. |
| [void TEE_AEUpdateAAD(TEE_OperationHandle operation, const void *AADdata, size_t AADdataLen)](#tee_aeupdateaad) | Updates the AAD in an AE operation. |
| [TEE_Result TEE_AEUpdate(TEE_OperationHandle operation, void *srcData, size_t srcLen, void *destData, size_t *destLen)](#tee_aeupdate) | Updates data for an AE operation. |
| [TEE_Result TEE_AEEncryptFinal(TEE_OperationHandle operation, void *srcData, size_t srcLen, void *destData, size_t *destLen, void *tag, size_t *tagLen)](#tee_aeencryptfinal) | Finalizes the AE encryption operation. |
| [TEE_Result TEE_AEDecryptFinal(TEE_OperationHandle operation, void *srcData, size_t srcLen, void *destData, size_t *destLen, void *tag, size_t tagLen)](#tee_aedecryptfinal) | Finalizes an AE decryption operation. |
| [TEE_Result TEE_AsymmetricEncrypt(TEE_OperationHandle operation, const TEE_Attribute *params, uint32_t paramCount, void *srcData, size_t srcLen, void *destData, size_t *destLen)](#tee_asymmetricencrypt) | Performs asymmetric encryption. |
| [TEE_Result TEE_AsymmetricDecrypt(TEE_OperationHandle operation, const TEE_Attribute *params, uint32_t paramCount, void *srcData, size_t srcLen, void *destData, size_t *destLen)](#tee_asymmetricdecrypt) | Performs asymmetric decryption. |
| [TEE_Result TEE_AsymmetricSignDigest(TEE_OperationHandle operation, const TEE_Attribute *params, uint32_t paramCount, void *digest, size_t digestLen, void *signature, size_t *signatureLen)](#tee_asymmetricsigndigest) | Signs a message digest in an asymmetric operation. |
| [TEE_Result TEE_AsymmetricVerifyDigest(TEE_OperationHandle operation, const TEE_Attribute *params, uint32_t paramCount, void *digest, size_t digestLen, void *signature, size_t signatureLen)](#tee_asymmetricverifydigest) | Verifies a message digest signature in an asymmetric operation. |
| [TEE_Result TEE_GetOperationInfoMultiple(TEE_OperationHandle operation, TEE_OperationInfoMultiple *operationInfoMultiple, const size_t *operationSize)](#tee_getoperationinfomultiple) | Obtains information about the operation involving multiple keys. |
| [TEE_Result TEE_IsAlgorithmSupported(uint32_t algId, uint32_t element)](#tee_isalgorithmsupported) | Checks whether the algorithm is supported. |

### Variable

| Name | Description |
| -- | -- |
| uint32_t TEE_OperationMode | Defines the mode for cryptographic operations.<br>**Since**: 20 |

## Enum type description

### __TEE_Operation_Constants

```c
enum __TEE_Operation_Constants
```

**Description**

Enumerates the cryptographic operation handles.

**Since**: 20

| Enum item | Description |
| -- | -- |
| TEE_OPERATION_CIPHER               = 0x1 | Cipher |
| TEE_OPERATION_MAC                  = 3 | MAC |
| TEE_OPERATION_AE                   = 4 | AE |
| TEE_OPERATION_DIGEST               = 5 | Digest |
| TEE_OPERATION_ASYMMETRIC_CIPHER    = 6 | Asymmetric Cipher |
| TEE_OPERATION_ASYMMETRIC_SIGNATURE = 7 | Asymmetric Signature |
| TEE_OPERATION_KEY_DERIVATION       = 8 | Key Derivation |
| TEE_OPERATION_KDF_KEY_DERIVATION   = 9 | KDF Key Derivation |

### __tee_crypto_algorithm_id

```c
enum __tee_crypto_algorithm_id
```

**Description**

Enumerates the cryptographic algorithms.

**Since**: 20

| Enum item | Description |
| -- | -- |
| TEE_ALG_INVALID                      = 0x0 | Invalid algorithm |
| TEE_ALG_AES_ECB_NOPAD                = 0x10000010 | AES_ECB_NOPAD |
| TEE_ALG_AES_CBC_NOPAD                = 0x10000110 | AES_CBC_NOPAD |
| TEE_ALG_AES_CTR                      = 0x10000210 | AES_CTR |
| TEE_ALG_AES_CTS                      = 0x10000310 | AES_CTS |
| TEE_ALG_AES_XTS                      = 0x10000410 | AES_XTS |
| TEE_ALG_AES_CBC_MAC_NOPAD            = 0x30000110 | AES_CBC_MAC_NOPAD |
| TEE_ALG_AES_CBC_MAC_PKCS5            = 0x30000510 | AES_CBC_MAC_PKCS5 |
| TEE_ALG_AES_CMAC                     = 0x30000610 | AES_CMAC |
| TEE_ALG_AES_GMAC                     = 0x30000810 | AES_GMAC |
| TEE_ALG_AES_CCM                      = 0x40000710 | AES_CCM |
| TEE_ALG_AES_GCM                      = 0x40000810 | AES_GCM |
| TEE_ALG_DES_ECB_NOPAD                = 0x10000011 | DES_ECB_NOPAD |
| TEE_ALG_DES_CBC_NOPAD                = 0x10000111 | DES_CBC_NOPAD |
| TEE_ALG_DES_CBC_MAC_NOPAD            = 0x30000111 | DES_CBC_MAC_NOPAD |
| TEE_ALG_DES_CBC_MAC_PKCS5            = 0x30000511 | DES_CBC_MAC_PKCS5 |
| TEE_ALG_DES3_ECB_NOPAD               = 0x10000013 | DES3_ECB_NOPAD |
| TEE_ALG_DES3_CBC_NOPAD               = 0x10000113 | DES3_CBC_NOPAD |
| TEE_ALG_DES3_CBC_MAC_NOPAD           = 0x30000113 | DES3_CBC_MAC_NOPAD |
| TEE_ALG_DES3_CBC_MAC_PKCS5           = 0x30000513 | DES3_CBC_MAC_PKCS5 |
| TEE_ALG_RSASSA_PKCS1_V1_5_MD5        = 0x70001830 | RSASSA_PKCS1_V1_5_MD5 |
| TEE_ALG_RSASSA_PKCS1_V1_5_SHA1       = 0x70002830 | RSASSA_PKCS1_V1_5_SHA1 |
| TEE_ALG_RSASSA_PKCS1_V1_5_SHA224     = 0x70003830 | RSASSA_PKCS1_V1_5_SHA224 |
| TEE_ALG_RSASSA_PKCS1_V1_5_SHA256     = 0x70004830 | RSASSA_PKCS1_V1_5_SHA256 |
| TEE_ALG_RSASSA_PKCS1_V1_5_SHA384     = 0x70005830 | RSASSA_PKCS1_V1_5_SHA384 |
| TEE_ALG_RSASSA_PKCS1_V1_5_SHA512     = 0x70006830 | RSASSA_PKCS1_V1_5_SHA512 |
| TEE_ALG_RSASSA_PKCS1_V1_5_SM3        = 0xF0007830 | RSASSA_PKCS1_V1_5_SM3 |
| TEE_ALG_RSASSA_PKCS1_V1_5_MD5_SHA1   = 0xF0008830 | RSASSA_PKCS1_V1_5_MD5_SHA1 |
| TEE_ALG_RSASSA_PKCS1_PSS_MGF1_MD5    = 0x70111930 | RSASSA_PKCS1_PSS_MGF1_MD5 |
| TEE_ALG_RSASSA_PKCS1_PSS_MGF1_SHA1   = 0x70212930 | RSASSA_PKCS1_PSS_MGF1_SHA1 |
| TEE_ALG_RSASSA_PKCS1_PSS_MGF1_SHA224 = 0x70313930 | RSASSA_PKCS1_PSS_MGF1_SHA224 |
| TEE_ALG_RSASSA_PKCS1_PSS_MGF1_SHA256 = 0x70414930 | RSASSA_PKCS1_PSS_MGF1_SHA256 |
| TEE_ALG_RSASSA_PKCS1_PSS_MGF1_SHA384 = 0x70515930 | RSASSA_PKCS1_PSS_MGF1_SHA384 |
| TEE_ALG_RSASSA_PKCS1_PSS_MGF1_SHA512 = 0x70616930 | RSASSA_PKCS1_PSS_MGF1_SHA512 |
| TEE_ALG_RSAES_PKCS1_V1_5             = 0x60000130 | RSAES_PKCS1_V1_5 |
| TEE_ALG_RSAES_PKCS1_OAEP_MGF1_SHA1   = 0x60210230 | RSAES_PKCS1_OAEP_MGF1_SHA1 |
| TEE_ALG_RSAES_PKCS1_OAEP_MGF1_SHA224 = 0x60211230 | RSAES_PKCS1_OAEP_MGF1_SHA224 |
| TEE_ALG_RSAES_PKCS1_OAEP_MGF1_SHA256 = 0x60212230 | RSAES_PKCS1_OAEP_MGF1_SHA256 |
| TEE_ALG_RSAES_PKCS1_OAEP_MGF1_SHA384 = 0x60213230 | RSAES_PKCS1_OAEP_MGF1_SHA384 |
| TEE_ALG_RSAES_PKCS1_OAEP_MGF1_SHA512 = 0x60214230 | RSAES_PKCS1_OAEP_MGF1_SHA512 |
| TEE_ALG_RSA_NOPAD                    = 0x60000030 | RSA_NOPAD |
| TEE_ALG_DSA_SHA1                     = 0x70002131 | DSA_SHA1 |
| TEE_ALG_DSA_SHA224                   = 0x70003131 | DSA_SHA224 |
| TEE_ALG_DSA_SHA256                   = 0x70004131 | DSA_SHA256 |
| TEE_ALG_DH_DERIVE_SHARED_SECRET      = 0x80000032 | DH_DERIVE_SHARED_SECRET |
| TEE_ALG_MD5                          = 0x50000001 | MD5 |
| TEE_ALG_SHA1                         = 0x50000002 | SHA1 |
| TEE_ALG_SHA224                       = 0x50000003 | SHA224 |
| TEE_ALG_SHA256                       = 0x50000004 | SHA256 |
| TEE_ALG_SHA384                       = 0x50000005 | SHA384 |
| TEE_ALG_SHA512                       = 0x50000006 | SHA512 |
| TEE_ALG_HMAC_MD5                     = 0x30000001 | HMAC_MD5 |
| TEE_ALG_HMAC_SHA1                    = 0x30000002 | HMAC_SHA1 |
| TEE_ALG_HMAC_SHA224                  = 0x30000003 | HMAC_SHA224 |
| TEE_ALG_HMAC_SHA256                  = 0x30000004 | HMAC_SHA256 |
| TEE_ALG_HMAC_SHA384                  = 0x30000005 | HMAC_SHA384 |
| TEE_ALG_HMAC_SHA512                  = 0x30000006 | HMAC_SHA512 |
| TEE_ALG_HMAC_SM3                     = 0x30000007 | HMAC_SM3 |
| TEE_ALG_AES_ECB_PKCS5                = 0x10000020 | AES_ECB_PKCS5 |
| TEE_ALG_AES_CBC_PKCS5                = 0x10000220 | AES_CBC_PKCS5 |
| TEE_ALG_AES_CBC_ISO_PADDING          = 0x10000330 | AES_CBC_ISO_PADDING |
| TEE_ALG_ECDSA_SHA1                   = 0x70001042 | ECDSA_SHA1 |
| TEE_ALG_ECDSA_SHA224                 = 0x70002042 | ECDSA_SHA224 |
| TEE_ALG_ECDSA_SHA256                 = 0x70003042 | ECDSA_SHA256 |
| TEE_ALG_ECDSA_SHA384                 = 0x70004042 | ECDSA_SHA384 |
| TEE_ALG_ECDSA_SHA512                 = 0x70005042 | ECDSA_SHA512 |
| TEE_ALG_ED25519                      = 0x70005043 | ED25519 |
| TEE_ALG_ECDH_DERIVE_SHARED_SECRET    = 0x80000042 | ECDH_DERIVE_SHARED_SECRET |
| TEE_ALG_X25519                       = 0x80000044 | X25519 |
| TEE_ALG_ECC                          = 0x80000001 | ECC |
| TEE_ALG_ECDSA_P192                   = 0x70001042 | ECDSA_P192 |
| TEE_ALG_ECDSA_P224                   = 0x70002042 | ECDSA_P224 |
| TEE_ALG_ECDSA_P256                   = 0x70003042 | ECDSA_P256 |
| TEE_ALG_ECDSA_P384                   = 0x70004042 | ECDSA_P384 |
| TEE_ALG_ECDSA_P521                   = 0x70005042 | ECDSA_P521 |
| TEE_ALG_ECDH_P192                    = 0x80001042 | ECDH_P192 |
| TEE_ALG_ECDH_P224                    = 0x80002042 | ECDH_P224 |
| TEE_ALG_ECDH_P256                    = 0x80003042 | ECDH_P256 |
| TEE_ALG_ECDH_P384                    = 0x80004042 | ECDH_P384 |
| TEE_ALG_ECDH_P521                    = 0x80005042 | ECDH_P521 |
| TEE_ALG_SIP_HASH                     = 0xF0000002 | SIP_HASH |
| TEE_ALG_SM2_DSA_SM3                  = 0x70006045 | SM2_DSA_SM3 |
| TEE_ALG_SM2_PKE                      = 0x80000045 | SM2_PKE |
| TEE_ALG_SM3                          = 0x50000007 | SM3 |
| TEE_ALG_SM4_ECB_NOPAD                = 0x10000014 | SM4_ECB_NOPAD |
| TEE_ALG_SM4_ECB_PKCS7                = 0x10000024 | SM4_ECB_PKCS7 |
| TEE_ALG_SM4_CBC_NOPAD                = 0x10000114 | SM4_CBC_NOPAD |
| TEE_ALG_SM4_CBC_PKCS7                = 0xF0000003 | SM4_CBC_PKCS7 |
| TEE_ALG_SM4_CTR                      = 0x10000214 | SM4_CTR |
| TEE_ALG_SM4_CFB128                   = 0xF0000000 | SM4_CFB128 |
| TEE_ALG_SM4_XTS                      = 0x10000414 | SM4_XTS |
| TEE_ALG_SM4_OFB                      = 0x10000514 | SM4_OFB |
| TEE_ALG_AES_OFB                      = 0x10000510 | AES_OFB |
| TEE_ALG_AES_CFB128                   = 0xF0000610 | AES_CFB128 |
| TEE_ALG_SM4_GCM                      = 0xF0000005 | SM4_GCM |
| TEE_ALG_PBKDF2_HMAC_SHA1_DERIVE_KEY  = 0x800020C2 | PBKDF2_HMAC_SHA1_DERIVE_KEY |
| TEE_ALG_PBKDF2_HMAC_SHA256_DERIVE_KEY = 0x800040C2 | PBKDF2_HMAC_SHA256_DERIVE_KEY |
| TEE_ALG_PBKDF2_HMAC_SHA384_DERIVE_KEY = 0x800050C2 | PBKDF2_HMAC_SHA384_DERIVE_KEY |
| TEE_ALG_PBKDF2_HMAC_SHA512_DERIVE_KEY = 0x800060C2 | PBKDF2_HMAC_SHA512_DERIVE_KEY |
| TEE_ALG_HKDF                         = 0x80000047 | HKDF |
| TEE_ALG_PRF                          = 0xF0000006 | PRF |

### TEE_ECC_CURVE

```c
enum TEE_ECC_CURVE
```

**Description**

Enumerates the Elliptic-Curve Cryptography (ECC) curves supported.

**Since**: 20

| Enum item | Description |
| -- | -- |
| TEE_ECC_CURVE_NIST_P192 = 0x00000001 | CURVE_NIST_P192 |
| TEE_ECC_CURVE_NIST_P224 = 0x00000002 | CURVE_NIST_P224 |
| TEE_ECC_CURVE_NIST_P256 = 0x00000003 | CURVE_NIST_P256 |
| TEE_ECC_CURVE_NIST_P384 = 0x00000004 | CURVE_NIST_P384 |
| TEE_ECC_CURVE_NIST_P521 = 0x00000005 | CURVE_NIST_P521 |
| TEE_ECC_CURVE_SM2       = 0x00000300 | CURVE_SM2 256 bits |
| TEE_ECC_CURVE_25519     = 0x00000200 | CURVE_25519 256 bits |

### TEE_DH_HASH_Mode

```c
enum TEE_DH_HASH_Mode
```

**Description**

Enumerates the Mask Generation Function (MGF1) modes.

**Since**: 20

| Enum item | Description |
| -- | -- |
| TEE_DH_HASH_SHA1_mode   = 0 | SHA1 mode for DH hashing. |
| TEE_DH_HASH_SHA224_mode = 1 | SHA224 mode for DH hashing. |
| TEE_DH_HASH_SHA256_mode = 2 | SHA256 mode for DH hashing. |
| TEE_DH_HASH_SHA384_mode = 3 | SHA384 mode for DH hashing. |
| TEE_DH_HASH_SHA512_mode = 4 | SHA512 mode for DH hashing. |
| TEE_DH_HASH_NumOfModes | Total number of DH hashing modes. |

### TEE_DH_OpMode_t

```c
enum TEE_DH_OpMode_t
```

**Description**

Enumerates the Diffie-Hellman operation modes.

**Since**: 20

| Enum item | Description |
| -- | -- |
| TEE_DH_PKCS3_mode = 0 | PKCS3 |
| TEE_DH_ANSI_X942_mode = 1 | X942 algorithm. |
| TEE_DH_NumOfModes | Number of modes. |

### TEE_DH_DerivFuncMode

```c
enum TEE_DH_DerivFuncMode
```

**Description**

Defines an enum for TEE_DH_DerivFuncMode.

**Since**: 20

| Enum item | Description |
| -- | -- |
| TEE_DH_ASN1_DerivMode = 0 | ASN1_DerivMode |
| TEE_DH_ConcatDerivMode = 1 | ConcatDerivMode |
| TEE_DH_X963_DerivMode = TEE_DH_ConcatDerivMode | X963_DerivMode |
| TEE_DH_OMADRM_DerivMode = 2 | OMADRM_DerivMode |
| TEE_DH_ISO18033_KDF1_DerivMode = 3 | ISO18033_KDF1_DerivMode |
| TEE_DH_ISO18033_KDF2_DerivMode = 4 | ISO18033_KDF2_DerivMode |
| TEE_DH_DerivFunc_NumOfModes | Number of modes. |

### __TEE_DK_ObjectAttribute

```c
enum __TEE_DK_ObjectAttribute
```

**Description**

Enumerates the object attributes for cryptographic operations.

**Since**: 20

| Enum item | Description |
| -- | -- |
| TEE_DK_SECRECT = 0 | Pointer to the shared secret value. |
| TEE_DK_OTHER | Pointer to a struct that contains other data. |
| TEE_DK_HASH_MODE | Enumerator ID of the hash function to be used. |
| TEE_DK_DERIVATION_MODE | Enumerator ID of the derivation function mode. |

### __TEE_OperationMode

```c
enum __TEE_OperationMode
```

**Description**

Enumerates the cryptographic operation modes.

**Since**: 20

| Enum item | Description |
| -- | -- |
| TEE_MODE_ENCRYPT = 0x0 | Encryption |
| TEE_MODE_DECRYPT | Decryption |
| TEE_MODE_SIGN | Signing |
| TEE_MODE_VERIFY | Signature verification |
| TEE_MODE_MAC | MAC |
| TEE_MODE_DIGEST | Digest |
| TEE_MODE_DERIVE | Key derivation |

### tee_operation_state

```c
enum tee_operation_state
```

**Description**

Enumerates the cryptographic operation states.

**Since**: 20

| Enum item | Description |
| -- | -- |
| TEE_OPERATION_STATE_INITIAL = 0x00000000 | Initial |
| TEE_OPERATION_STATE_ACTIVE  = 0x00000001 | Active |


## Function description

### TEE_AllocateOperation()

```c
TEE_Result TEE_AllocateOperation(TEE_OperationHandle *operation, uint32_t algorithm, uint32_t mode, uint32_t maxKeySize)
```

**Description**

Allocates an operation handle.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_OperationHandle *operation | Indicates the pointer to the operation handle. |
| uint32_t algorithm | Indicates the cipher algorithm. |
| uint32_t mode | Indicates the operation mode. |
| uint32_t maxKeySize | Indicates the maximum length of the key. |

**Returns**:

| Type | Description |
| -- | -- |
| TEE_Result | Returns <b>TEE_SUCCESS</b> if the operation handle is allocated.          Returns <b>TEE_ERROR_OUT_OF_MEMORY</b> if there is no enough memory for this operation.          Returns <b>TEE_ERROR_NOT_SUPPORTED</b> if the specified algorithm is not supported.          Returns <b>TEE_ERROR_GENERIC</b> if the operation fails due to other errors. |

### TEE_FreeOperation()

```c
void TEE_FreeOperation(TEE_OperationHandle operation)
```

**Description**

Releases an operation handle.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_OperationHandle operation | Indicates the operation handle to release. |

### TEE_GetOperationInfo()

```c
void TEE_GetOperationInfo(const TEE_OperationHandle operation, TEE_OperationInfo *operationInfo)
```

**Description**

Obtains operation information.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| const TEE_OperationHandle operation | Indicates the operation handle. |
| [TEE_OperationInfo](capi-teetrusted---tee-operationinfo.md) *operationInfo | Indicates the pointer to the operation information. |

### TEE_ResetOperation()

```c
void TEE_ResetOperation(TEE_OperationHandle operation)
```

**Description**

Resets an operation handle.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_OperationHandle operation | Indicates the operation handle to reset. |

### TEE_SetOperationKey()

```c
TEE_Result TEE_SetOperationKey(TEE_OperationHandle operation, const TEE_ObjectHandle key)
```

**Description**

Sets the key for an operation.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_OperationHandle operation | Indicates the operation handle. |
| const TEE_ObjectHandle key | Indicates the key. |

**Returns**:

| Type | Description |
| -- | -- |
| TEE_Result | Returns <b>TEE_SUCCESS</b> if the operation is successful.          Returns <b>TEE_ERROR_BAD_PARAMETERS</b> if the operation fails due to invalid parameters.          Returns <b>TEE_ERROR_OUT_OF_MEMORY</b> if there is no enough memory for this operation. |

### TEE_SetOperationKey2()

```c
TEE_Result TEE_SetOperationKey2(TEE_OperationHandle operation, const TEE_ObjectHandle key1, const TEE_ObjectHandle key2)
```

**Description**

Sets two keys for an operation.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_OperationHandle operation | Indicates the operation handle. |
| const TEE_ObjectHandle key1 | Indicates key 1. |
| const TEE_ObjectHandle key2 | Indicates key 2. |

**Returns**:

| Type | Description |
| -- | -- |
| TEE_Result | Returns <b>TEE_SUCCESS</b> if the operation is successful.          Returns <b>TEE_ERROR_BAD_PARAMETERS</b> if the operation fails due to invalid parameters. |

### TEE_CopyOperation()

```c
void TEE_CopyOperation(TEE_OperationHandle dstOperation, const TEE_OperationHandle srcOperation)
```

**Description**

Copies an operation handle.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_OperationHandle dstOperation | Indicates the destination operation handle. |
| const TEE_OperationHandle srcOperation | Indicates the source operation handle. |

### TEE_CipherInit()

```c
void TEE_CipherInit(TEE_OperationHandle operation, const void *IV, size_t IVLen)
```

**Description**

Initializes the context to start a cipher operation.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_OperationHandle operation | Indicates the operation handle. |
| const void *IV | Indicates the pointer to the buffer storing the operation IV. If this parameter is not used, set it to <b>NULL</b>. |
| size_t IVLen | Indicates the length of the IV buffer. |

### TEE_CipherUpdate()

```c
TEE_Result TEE_CipherUpdate(TEE_OperationHandle operation, const void *srcData, size_t srcLen, void *destData, size_t *destLen)
```

**Description**

Updates the data for a cipher operation.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_OperationHandle operation | Indicates the operation handle. |
| const void *srcData | Indicates the pointer to the source data. |
| size_t srcLen | Indicates the length of the source data. |
| void *destData | Indicates the pointer to the destination data. |
| size_t *destLen | Indicates the pointer to the destination data length. |

**Returns**:

| Type | Description |
| -- | -- |
| TEE_Result | Returns <b>TEE_SUCCESS</b> if the operation is successful.          Returns <b>TEE_ERROR_BAD_PARAMETERS</b> if the operation fails due to invalid parameters.          Returns <b>TEE_ERROR_GENERIC</b> if the operation fails due to other errors. |

### TEE_CipherDoFinal()

```c
TEE_Result TEE_CipherDoFinal(TEE_OperationHandle operation, const void *srcData, size_t srcLen, void *destData, size_t *destLen)
```

**Description**

Finalizes a cipher operation.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_OperationHandle operation | Indicates the operation handle. |
| const void *srcData | Indicates the pointer to the source data. |
| size_t srcLen | Indicates the length of the source data. |
| void *destData | Indicates the pointer to the destination data. |
| size_t *destLen | Indicates the pointer to the destination data length. |

**Returns**:

| Type | Description |
| -- | -- |
| TEE_Result | Returns <b>TEE_SUCCESS</b> if the operation is successful.          Returns <b>TEE_ERROR_BAD_PARAMETERS</b> if the operation fails due to invalid parameters.          Returns <b>TEE_ERROR_GENERIC</b> if the operation fails due to other errors. |

### TEE_DigestUpdate()

```c
void TEE_DigestUpdate(TEE_OperationHandle operation, const void *chunk, size_t chunkSize)
```

**Description**

Updates the digest.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_OperationHandle operation | Indicates the operation handle. |
| const void *chunk | Indicates the pointer to the chunk of data to be hashed. |
| size_t chunkSize | Indicates the length of the chunk. |

### TEE_DigestDoFinal()

```c
TEE_Result TEE_DigestDoFinal(TEE_OperationHandle operation, const void *chunk, size_t chunkLen, void *hash, size_t *hashLen)
```

**Description**

Finalizes the message digest operation.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_OperationHandle operation | Indicates the operation handle. |
| const void *chunk | Indicates the pointer to the chunk of data to be hashed. |
| size_t chunkLen | Indicates the length of the chunk. |
| void *hash | Indicates the pointer to the buffer storing the message hash. |
| size_t *hashLen |  |

**Returns**:

| Type | Description |
| -- | -- |
| TEE_Result | Returns <b>TEE_SUCCESS</b> if the operation is successful.          Returns <b>TEE_ERROR_SHORT_BUFFER</b> if the operationInfo buffer is not large enough to  hold the information obtained. |

### TEE_MACInit()

```c
void TEE_MACInit(TEE_OperationHandle operation, void *IV, size_t IVLen)
```

**Description**

Initializes a MAC operation.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_OperationHandle operation | Indicates the operation handle. |
| void *IV | Indicates the pointer to the buffer storing the operation IV. If this parameter is not used, set it to <b>NULL</b>. |
| size_t IVLen | Indicates the length of the IV buffer. |

### TEE_MACUpdate()

```c
void TEE_MACUpdate(TEE_OperationHandle operation, const void *chunk, size_t chunkSize)
```

**Description**

Updates the MAC.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_OperationHandle operation | Indicates the operation handle. |
| const void *chunk | Indicates the pointer to the chunk of MAC data. |
| size_t chunkSize | Indicates the size of the chunk. |

### TEE_MACComputeFinal()

```c
TEE_Result TEE_MACComputeFinal(TEE_OperationHandle operation, const void *message, size_t messageLen, void *mac, size_t *macLen)
```

**Description**

MAC Finalizes the MAC operation with a last chunk of message and computes the MAC.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_OperationHandle operation | Indicates the operation handle. |
| const void *message | Indicates the pointer to the buffer containing the last message chunk to MAC. |
| size_t messageLen | Indicates the length of the message buffer. |
| void *mac | Indicates the pointer to the buffer storing the computed MAC. |
| size_t *macLen | Indicates the pointer to the MAC buffer length. |

**Returns**:

| Type | Description |
| -- | -- |
| TEE_Result | Returns <b>TEE_SUCCESS</b> if the operation is successful.          Returns <b>TEE_ERROR_GENERIC</b> if the operation fails due to other errors. |

### TEE_MACCompareFinal()

```c
TEE_Result TEE_MACCompareFinal(TEE_OperationHandle operation, const void *message, size_t messageLen, const void *mac, const size_t macLen)
```

**Description**

Finalizes the MAC operation and compares the MAC with the one passed in.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_OperationHandle operation | Indicates the operation handle. |
| const void *message | Indicates the pointer to the buffer containing the last message chunk to MAC. |
| size_t messageLen | Indicates the length of the buffer. |
| const void *mac | Indicates the pointer to the buffer storing the computed MAC. |
| const size_t macLen | Indicates the MAC buffer length. |

**Returns**:

| Type | Description |
| -- | -- |
| TEE_Result | Returns <b>TEE_SUCCESS</b> if the operation is successful.          Returns <b>TEE_ERROR_GENERIC</b> if the operation fails due to other errors.          Returns <b>TEE_ERROR_MAC_INVALID</b> if the computed MAC is not the same as that passed in. |

### TEE_DeriveKey()

```c
void TEE_DeriveKey(TEE_OperationHandle operation, const TEE_Attribute *params, uint32_t paramCount, TEE_ObjectHandle derivedKey)
```

**Description**

Derives a key.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_OperationHandle operation | Indicates the operation handle. |
| const TEE_Attribute *params | Indicates the pointer to the parameters for this operation. |
| uint32_t paramCount | Indicates the number of parameters. |
| TEE_ObjectHandle derivedKey | Indicates the derived key. |

### TEE_GenerateRandom()

```c
void TEE_GenerateRandom(void *randomBuffer, size_t randomBufferLen)
```

**Description**

Generates random data.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| void *randomBuffer | Indicates the pointer to the buffer storing the random data generated. |
| size_t randomBufferLen | Indicates the length of the buffer storing the random data. |

### TEE_AEInit()

```c
TEE_Result TEE_AEInit(TEE_OperationHandle operation, void *nonce, size_t nonceLen, uint32_t tagLen, size_t AADLen, size_t payloadLen)
```

**Description**

Initializes an AE operation.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_OperationHandle operation | Indicates the operation handle. |
| void *nonce | Indicates the pointer to the buffer for storing the nonce. |
| size_t nonceLen | Indicates the length of the nonce. |
| uint32_t tagLen | Indicates the length of the tag. |
| size_t AADLen | Indicates the length of the AAD. |
| size_t payloadLen | Indicates the length of the payload. |

**Returns**:

| Type | Description |
| -- | -- |
| TEE_Result | Returns <b>TEE_SUCCESS</b> if the operation is successful.          Returns <b>TEE_ERROR_GENERIC</b> if the operation fails due to other errors. |

### TEE_AEUpdateAAD()

```c
void TEE_AEUpdateAAD(TEE_OperationHandle operation, const void *AADdata, size_t AADdataLen)
```

**Description**

Updates the AAD in an AE operation.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_OperationHandle operation | Indicates the operation handle. |
| const void *AADdata | Indicates the pointer to the new AAD. |
| size_t AADdataLen | Indicates the length of the new AAD. |

### TEE_AEUpdate()

```c
TEE_Result TEE_AEUpdate(TEE_OperationHandle operation, void *srcData, size_t srcLen, void *destData, size_t *destLen)
```

**Description**

Updates data for an AE operation.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_OperationHandle operation | Indicates the operation handle. |
| void *srcData | Indicates the pointer to the source data. |
| size_t srcLen | Indicates the length of the source data. |
| void *destData | Indicates the pointer to the destination data. |
| size_t *destLen | Indicates the pointer to the destination data length. |

**Returns**:

| Type | Description |
| -- | -- |
| TEE_Result | Returns <b>TEE_SUCCESS</b> if the operation is successful.          Returns <b>TEE_ERROR_GENERIC</b> if the operation fails due to other errors. |

### TEE_AEEncryptFinal()

```c
TEE_Result TEE_AEEncryptFinal(TEE_OperationHandle operation, void *srcData, size_t srcLen, void *destData, size_t *destLen, void *tag, size_t *tagLen)
```

**Description**

Finalizes the AE encryption operation.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_OperationHandle operation | Indicates the operation handle. |
| void *srcData | Indicates the pointer to the source data. |
| size_t srcLen | Indicates the length of the source data. |
| void *destData | Indicates the pointer to the destination data. |
| size_t *destLen | Indicates the pointer to the destination data length. |
| void *tag | Indicates the pointer to the buffer storing the computed tag. |
| size_t *tagLen | Indicates the pointer to the tag buffer length. |

**Returns**:

| Type | Description |
| -- | -- |
| TEE_Result | Returns <b>TEE_SUCCESS</b> if the operation is successful.          Returns <b>TEE_ERROR_GENERIC</b> if the operation fails due to other errors. |

### TEE_AEDecryptFinal()

```c
TEE_Result TEE_AEDecryptFinal(TEE_OperationHandle operation, void *srcData, size_t srcLen, void *destData, size_t *destLen, void *tag, size_t tagLen)
```

**Description**

Finalizes an AE decryption operation.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_OperationHandle operation | Indicates the operation handle. |
| void *srcData | Indicates the pointer to the source data. |
| size_t srcLen | Indicates the length of the source data. |
| void *destData | Indicates the pointer to the destination data. |
| size_t *destLen | Indicates the pointer to the destination data length. |
| void *tag | Indicates the pointer to the buffer storing the computed tag. |
| size_t tagLen | Indicates the tag buffer length. |

**Returns**:

| Type | Description |
| -- | -- |
| TEE_Result | Returns <b>TEE_SUCCESS</b> if the operation is successful.          Returns <b>TEE_ERROR_MAC_INVALID</b> if the computed tag does not match the provided tag. |

### TEE_AsymmetricEncrypt()

```c
TEE_Result TEE_AsymmetricEncrypt(TEE_OperationHandle operation, const TEE_Attribute *params, uint32_t paramCount, void *srcData, size_t srcLen, void *destData, size_t *destLen)
```

**Description**

Performs asymmetric encryption.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_OperationHandle operation | Indicates the operation handle. |
| const TEE_Attribute *params | Indicates the pointer to the parameters for this operation. |
| uint32_t paramCount | Indicates the number of parameters. |
| void *srcData | Indicates the pointer to the source data. |
| size_t srcLen | Indicates the length of the source data. |
| void *destData | Indicates the pointer to the destination data. |
| size_t *destLen | Indicates the pointer to the destination data length. |

**Returns**:

| Type | Description |
| -- | -- |
| TEE_Result | Returns <b>TEE_SUCCESS</b> if the operation is successful.          Returns <b>TEE_ERROR_BAD_PARAMETERS</b> if the operation fails due to invalid parameters.          Returns <b>TEE_ERROR_GENERIC</b> if the operation fails due to other errors. |

### TEE_AsymmetricDecrypt()

```c
TEE_Result TEE_AsymmetricDecrypt(TEE_OperationHandle operation, const TEE_Attribute *params, uint32_t paramCount, void *srcData, size_t srcLen, void *destData, size_t *destLen)
```

**Description**

Performs asymmetric decryption.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_OperationHandle operation | Indicates the operation handle. |
| const TEE_Attribute *params | Indicates the pointer to the parameters for this operation. |
| uint32_t paramCount | Indicates the number of parameters. |
| void *srcData | Indicates the pointer to the source data. |
| size_t srcLen | Indicates the length of the source data. |
| void *destData | Indicates the pointer to the destination data. |
| size_t *destLen | Indicates the pointer to the destination data length. |

**Returns**:

| Type | Description |
| -- | -- |
| TEE_Result | Returns <b>TEE_SUCCESS</b> if the operation is successful.          Returns <b>TEE_ERROR_BAD_PARAMETERS</b> if the operation fails due to invalid parameters.          Returns <b>TEE_ERROR_GENERIC</b> if the operation fails due to other errors. |

### TEE_AsymmetricSignDigest()

```c
TEE_Result TEE_AsymmetricSignDigest(TEE_OperationHandle operation, const TEE_Attribute *params, uint32_t paramCount, void *digest, size_t digestLen, void *signature, size_t *signatureLen)
```

**Description**

Signs a message digest in an asymmetric operation.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_OperationHandle operation | Indicates the operation handle. |
| const TEE_Attribute *params | Indicates the pointer to the parameters for this operation. |
| uint32_t paramCount | Indicates the number of parameters. |
| void *digest | Indicates the pointer to the message digest. |
| size_t digestLen | Indicates the digest length. |
| void *signature | Indicates the pointer to the signature. |
| size_t *signatureLen | Indicates the pointer to the signature length. |

**Returns**:

| Type | Description |
| -- | -- |
| TEE_Result | Returns <b>TEE_SUCCESS</b> if the operation is successful.          Returns <b>TEE_ERROR_BAD_PARAMETERS</b> if the operation fails due to invalid parameters.          Returns <b>TEE_ERROR_GENERIC</b> if the operation fails due to other errors. |

### TEE_AsymmetricVerifyDigest()

```c
TEE_Result TEE_AsymmetricVerifyDigest(TEE_OperationHandle operation, const TEE_Attribute *params, uint32_t paramCount, void *digest, size_t digestLen, void *signature, size_t signatureLen)
```

**Description**

Verifies a message digest signature in an asymmetric operation.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_OperationHandle operation | Indicates the operation handle. |
| const TEE_Attribute *params | Indicates the pointer to the parameters for this operation. |
| uint32_t paramCount | Indicates the number of parameters. |
| void *digest | Indicates the pointer to the message digest. |
| size_t digestLen | Indicates the digest length. |
| void *signature | Indicates the pointer to the signature. |
| size_t signatureLen | Indicates the signature length. |

**Returns**:

| Type | Description |
| -- | -- |
| TEE_Result | Returns <b>TEE_SUCCESS</b> if the operation is successful.          Returns <b>TEE_ERROR_BAD_PARAMETERS</b> if the operation fails due to invalid parameters.          Returns <b>TEE_ERROR_GENERIC</b> if the operation fails due to other errors. |

### TEE_GetOperationInfoMultiple()

```c
TEE_Result TEE_GetOperationInfoMultiple(TEE_OperationHandle operation, TEE_OperationInfoMultiple *operationInfoMultiple, const size_t *operationSize)
```

**Description**

Obtains information about the operation involving multiple keys.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| TEE_OperationHandle operation | Indicates the operation handle. |
| [TEE_OperationInfoMultiple](capi-teetrusted-tee-operationinfomultiple.md) *operationInfoMultiple | Indicates the pointer to the operation information obtained. |
| const size_t *operationSize | [IN/OUT] Indicates the pointer to the operation information size. |

**Returns**:

| Type | Description |
| -- | -- |
| TEE_Result | Returns <b>TEE_SUCCESS</b> if the operation is successful.          Returns <b>TEE_ERROR_BAD_PARAMETERS</b> if the operation fails due to invalid parameters.          Returns <b>TEE_ERROR_SHORT_BUFFER</b> if the operationInfo buffer is not large enough to  hold the information obtained. |

### TEE_IsAlgorithmSupported()

```c
TEE_Result TEE_IsAlgorithmSupported(uint32_t algId, uint32_t element)
```

**Description**

Checks whether the algorithm is supported.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint32_t algId | Indicates the algorithm to check. |
| uint32_t element | Indicates the cryptographic element. |

**Returns**:

| Type | Description |
| -- | -- |
| TEE_Result | Returns <b>TEE_SUCCESS</b> if the algorithm is supported.          Returns <b>TEE_ERROR_NOT_SUPPORTED</b> otherwise. |


