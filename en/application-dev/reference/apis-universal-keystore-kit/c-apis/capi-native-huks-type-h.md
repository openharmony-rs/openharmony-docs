# native_huks_type.h

## Overview

Defines enums, structs, macros, and error codes in HUKS.

**File to Include**: <huks/native_huks_type.h>

**Library**: libhuks_ndk.z.so

**System capability**: SystemCapability.Security.Huks.Core

**Since**: 9

**Related module**: [HuksTypeApi](capi-universal-keystore-kit-hukstypeapi.md)

## Summary

### Structs

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_Huks_Result](capi-hukstypeapi-oh-huks-result.md) | OH_Huks_Result | Defines the returned data, including a status code and related description. |
| [OH_Huks_Blob](capi-hukstypeapi-oh-huks-blob.md) | OH_Huks_Blob | Defines the struct of a binary large object (BLOB). |
| [OH_Huks_Param](capi-hukstypeapi-oh-huks-param.md) | OH_Huks_Param | Defines the types of the parameters in a parameter set. |
| [OH_Huks_ParamSet](capi-hukstypeapi-oh-huks-paramset.md) | OH_Huks_ParamSet | Defines the struct of a parameter set. |
| [OH_Huks_CertChain](capi-hukstypeapi-oh-huks-certchain.md) | OH_Huks_CertChain | Defines the struct of a certificate chain. |
| [OH_Huks_KeyInfo](capi-hukstypeapi-oh-huks-keyinfo.md) | OH_Huks_KeyInfo | Defines the struct of key information. |
| [OH_Huks_PubKeyInfo](capi-hukstypeapi-oh-huks-pubkeyinfo.md) | OH_Huks_PubKeyInfo | Defines the struct of a public key. |
| [OH_Huks_KeyMaterialRsa](capi-hukstypeapi-oh-huks-keymaterialrsa.md) | OH_Huks_KeyMaterialRsa | Defines the struct for an RSA key. |
| [OH_Huks_KeyMaterialEcc](capi-hukstypeapi-oh-huks-keymaterialecc.md) | OH_Huks_KeyMaterialEcc | Defines the struct for an ECC key. |
| [OH_Huks_KeyMaterialDsa](capi-hukstypeapi-oh-huks-keymaterialdsa.md) | OH_Huks_KeyMaterialDsa | Defines the struct for a DSA key. |
| [OH_Huks_KeyMaterialDh](capi-hukstypeapi-oh-huks-keymaterialdh.md) | OH_Huks_KeyMaterialDh | Defines the struct for a DH key. |
| [OH_Huks_KeyMaterial25519](capi-hukstypeapi-oh-huks-keymaterial25519.md) | OH_Huks_KeyMaterial25519 | Defines a struct of a 25519 key. |
| [OH_Huks_KeyAliasSet](capi-hukstypeapi-oh-huks-keyaliasset.md) | OH_Huks_KeyAliasSet | Defines the struct of a key alias set. |

### Enums

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_Huks_KeyPurpose](#oh_huks_keypurpose) | OH_Huks_KeyPurpose | Enumerates the key purposes. Multiple purposes can be combined using bitwise OR (\\|). |
| [OH_Huks_KeyDigest](#oh_huks_keydigest) | OH_Huks_KeyDigest | Enumerates the digest algorithms. |
| [OH_Huks_KeyPadding](#oh_huks_keypadding) | OH_Huks_KeyPadding | Enumerates the padding algorithm types. |
| [OH_Huks_CipherMode](#oh_huks_ciphermode) | OH_Huks_CipherMode | Cipher mode. |
| [OH_Huks_KeySize](#oh_huks_keysize) | OH_Huks_KeySize | Enumerates the key sizes of different algorithms. |
| [OH_Huks_KeyAlg](#oh_huks_keyalg) | OH_Huks_KeyAlg | Enumerates the algorithms for keys. |
| [OH_Huks_AlgSuite](#oh_huks_algsuite) | OH_Huks_AlgSuite | Enumerates the algorithm suites that can be used for importing of a key in ciphertext. <br>Key material format for **OH_HUKS_UNWRAP_SUITE_X25519_AES_256_GCM_NOPADDING**: <br>\| x25519_plain_pubkey_length (4 Byte) \| x25519_plain_pubkey \| agreekey_aad_length (4 Byte) \| agreekey_aad <br>\| agreekey_nonce_length (4 Byte) \| agreekey_nonce \| agreekey_aead_tag_len(4 Byte) \| agreekey_aead_tag <br>\| kek_enc_data_length (4 Byte) \| kek_enc_data \| kek_aad_length (4 Byte) \| kek_aad <br>\| kek_nonce_length (4 Byte) \| kek_nonce \| kek_aead_tag_len (4 Byte) \| kek_aead_tag <br>\| key_material_size_len (4 Byte) \| key_material_size \| key_mat_enc_length (4 Byte) \| key_mat_enc_data<br> <br>Key material format for **OH_HUKS_UNWRAP_SUITE_ECDH_AES_256_GCM_NOPADDING**: <br>\| ECC_plain_pubkey_length (4 Byte) \| ECC_plain_pubkey \| agreekey_aad_length (4 Byte) \| agreekey_aad <br>\| agreekey_nonce_length (4 Byte) \| agreekey_nonce \| agreekey_aead_tag_len(4 Byte) \| agreekey_aead_tag <br>\| kek_enc_data_length (4 Byte) \| kek_enc_data \| kek_aad_length (4 Byte) \| kek_aad <br>\| kek_nonce_length (4 Byte) \| kek_nonce \| kek_aead_tag_len (4 Byte) \| kek_aead_tag <br>\| key_material_size_len (4 Byte) \| key_material_size \| key_mat_enc_length (4 Byte) \| key_mat_enc_data<br> <br>Key material format for **OH_HUKS_UNWRAP_SUITE_SM2_SM4_ECB_NOPADDING**: <br>\| kek_SM4_enc_length (4 Byte) \| EN_SM4_key \| importkey_enc_length (4 Byte) \| importkey_enc |
| [OH_Huks_KeyGenerateType](#oh_huks_keygeneratetype) | OH_Huks_KeyGenerateType | Enumerates the types of the key generated. |
| [OH_Huks_KeyFlag](#oh_huks_keyflag) | OH_Huks_KeyFlag | Enumerates the key generation types. |
| [OH_Huks_KeyStorageType](#oh_huks_keystoragetype) | OH_Huks_KeyStorageType | Enumerates the key storage types. |
| [OH_Huks_ImportKeyType](#oh_huks_importkeytype) | OH_Huks_ImportKeyType | Enumerates the types of the key to import. By default, a public key is imported. This field is not required when a symmetric key is imported. |
| [OH_Huks_RsaPssSaltLenType](#oh_huks_rsapsssaltlentype) | OH_Huks_RsaPssSaltLenType | Enumerates the length types of the salt value in PSS padding mode of the RSA algorithm. |
| [OH_Huks_ErrCode](#oh_huks_errcode) | OH_Huks_ErrCode | Enumerates error codes. |
| [OH_Huks_TagType](#oh_huks_tagtype) | OH_Huks_TagType | Enumerates parameter types. |
| [OH_Huks_UserAuthType](#oh_huks_userauthtype) | OH_Huks_UserAuthType | Enumerates the user authentication types in key access control. |
| [OH_Huks_AuthAccessType](#oh_huks_authaccesstype) | OH_Huks_AuthAccessType | Enumerates the rules for invalidating a key. |
| [OH_Huks_AuthStorageLevel](#oh_huks_authstoragelevel) | OH_Huks_AuthStorageLevel | Enumerates the security levels for storing the key generated or imported. |
| [OH_Huks_UserAuthMode](#oh_huks_userauthmode) | OH_Huks_UserAuthMode | Enumerates the user authentication modes in key access control. |
| [OH_Huks_ChallengeType](#oh_huks_challengetype) | OH_Huks_ChallengeType | Enumerates the types of the challenge generated when a key is used. |
| [OH_Huks_ChallengePosition](#oh_huks_challengeposition) | OH_Huks_ChallengePosition | Enumerates the positions of the 8-byte valid value in a custom challenge generated. |
| [OH_Huks_SecureSignType](#oh_huks_securesigntype) | OH_Huks_SecureSignType | Enumerates the signature types of the key generated or imported. |
| [OH_Huks_KeyClassType](#oh_huks_keyclasstype) | OH_Huks_KeyClassType | Key type. |
| [OH_Huks_KeyWrapType](#oh_huks_keywraptype) | OH_Huks_KeyWrapType | Enumerates the wrap type of the key generated or imported. |
| [OH_Huks_Tag](#oh_huks_tag) | OH_Huks_Tag | Enumerates the tags contained in a parameter set. <br>1 to 200: key parameter tag values. <br>301 to 500: tag values related to access control and authentication of key usage. <br>501 to 600: tag values related to key authentication. <br>601 to 1000: reserved values for other types of tag values. <br>1001 to 9999: extended tag values. <br>11000 to 12000: reserved values. <br>20001 to N: reserved tag values. |

### Macros

| Name | Description |
| -- | -- |
| OH_HUKS_AE_TAG_LEN 16 | Length of the AEAD authentication tag, in bytes.<br>**Since**: 9 |
| OH_HUKS_BITS_PER_BYTE 8 | Number of bits in each byte.<br>**Since**: 9 |
| OH_HUKS_MAX_KEY_SIZE 2048 | Maximum key size, in bytes.<br>**Since**: 9 |
| OH_HUKS_AE_NONCE_LEN 12 | Length of the AEAD one-time random number, in bytes.<br>**Since**: 9 |
| OH_HUKS_MAX_KEY_ALIAS_LEN 64 | Maximum length of a key alias, in bytes.<br>**Since**: 9 |
| OH_HUKS_MAX_PROCESS_NAME_LEN 50 | Maximum length of a process name, in bytes.<br>**Since**: 9 |
| OH_HUKS_MAX_RANDOM_LEN 1024 | Maximum length of a random number, in bytes.<br>**Since**: 9 |
| OH_HUKS_SIGNATURE_MIN_SIZE 64 | Minimum length of the signature result, in bytes.<br>**Since**: 9 |
| OH_HUKS_MAX_OUT_BLOB_SIZE (5 * 1024 * 1024) | Maximum size of the exported data, in bytes.<br>**Since**: 9 |
| OH_HUKS_WRAPPED_FORMAT_MAX_SIZE (1024 * 1024) | Maximum size of the key to be imported, in bytes.<br>**Since**: 9 |
| OH_HUKS_IMPORT_WRAPPED_KEY_TOTAL_BLOBS 10 | Maximum number of data blocks of the key to be imported, in bytes.<br>**Since**: 9 |
| TOKEN_CHALLENGE_LEN 32 | Byte length of the challenge value during access control.<br>**Since**: 9 |
| SHA256_SIGN_LEN 32 | Byte length of the SHA-256 signature.<br>**Since**: 9 |
| TOKEN_SIZE 32 | Byte length of the challenge value during access control.<br>**Since**: 9 |
| MAX_AUTH_TIMEOUT_SECOND 60 | Maximum user authentication timeout interval, in seconds.<br>**Since**: 9 |
| SECURE_SIGN_VERSION 0x01000001 | Version of the secure signature data.<br>**Since**: 9 |

## Enum type description

### OH_Huks_KeyPurpose

```c
enum OH_Huks_KeyPurpose
```

**Description**

Enumerates the key purposes. Multiple purposes can be combined using bitwise OR (\\|).

<!--Device-enum OH_Huks_KeyPurpose--><!--Device-enum OH_Huks_KeyPurpose-End-->

**System capability**: SystemCapability.Security.Huks.Core

**Since**: 9

| Enum item | Description |
| -- | -- |
| OH_HUKS_KEY_PURPOSE_ENCRYPT = 1 | Used to encrypt the plaintext.<br><!--Device-OH_HUKS_KEY_PURPOSE_ENCRYPT = 1--><!--Device-OH_HUKS_KEY_PURPOSE_ENCRYPT = 1-End--> |
| OH_HUKS_KEY_PURPOSE_DECRYPT = 2 | Used to decrypt the cipher text.<br><!--Device-OH_HUKS_KEY_PURPOSE_DECRYPT = 2--><!--Device-OH_HUKS_KEY_PURPOSE_DECRYPT = 2-End--> |
| OH_HUKS_KEY_PURPOSE_SIGN = 4 | Used for signing.<br><!--Device-OH_HUKS_KEY_PURPOSE_SIGN = 4--><!--Device-OH_HUKS_KEY_PURPOSE_SIGN = 4-End--> |
| OH_HUKS_KEY_PURPOSE_VERIFY = 8 | Used to verify the signature.<br><!--Device-OH_HUKS_KEY_PURPOSE_VERIFY = 8--><!--Device-OH_HUKS_KEY_PURPOSE_VERIFY = 8-End--> |
| OH_HUKS_KEY_PURPOSE_DERIVE = 16 | Used to derive a key.<br><!--Device-OH_HUKS_KEY_PURPOSE_DERIVE = 16--><!--Device-OH_HUKS_KEY_PURPOSE_DERIVE = 16-End--> |
| OH_HUKS_KEY_PURPOSE_WRAP = 32 | Used for exporting a key in ciphertext.<br><!--Device-OH_HUKS_KEY_PURPOSE_WRAP = 32--><!--Device-OH_HUKS_KEY_PURPOSE_WRAP = 32-End--> |
| OH_HUKS_KEY_PURPOSE_UNWRAP = 64 | Used for importing a key in ciphertext.<br><!--Device-OH_HUKS_KEY_PURPOSE_UNWRAP = 64--><!--Device-OH_HUKS_KEY_PURPOSE_UNWRAP = 64-End--> |
| OH_HUKS_KEY_PURPOSE_MAC = 128 | Used to generate a message authentication code (MAC).<br><!--Device-OH_HUKS_KEY_PURPOSE_MAC = 128--><!--Device-OH_HUKS_KEY_PURPOSE_MAC = 128-End--> |
| OH_HUKS_KEY_PURPOSE_AGREE = 256 | Used for key agreement.<br><!--Device-OH_HUKS_KEY_PURPOSE_AGREE = 256--><!--Device-OH_HUKS_KEY_PURPOSE_AGREE = 256-End--> |

### OH_Huks_KeyDigest

```c
enum OH_Huks_KeyDigest
```

**Description**

Enumerates the digest algorithms.

<!--Device-enum OH_Huks_KeyDigest--><!--Device-enum OH_Huks_KeyDigest-End-->

**System capability**: SystemCapability.Security.Huks.Core

**Since**: 9

| Enum item | Description |
| -- | -- |
| OH_HUKS_DIGEST_NONE = 0 | No digest algorithm.<br><!--Device-OH_HUKS_DIGEST_NONE = 0--><!--Device-OH_HUKS_DIGEST_NONE = 0-End--> |
| OH_HUKS_DIGEST_MD5 = 1 | MD5.<br><!--Device-OH_HUKS_DIGEST_MD5 = 1--><!--Device-OH_HUKS_DIGEST_MD5 = 1-End--> |
| OH_HUKS_DIGEST_SM3 = 2 | SM3.<br><!--Device-OH_HUKS_DIGEST_SM3 = 2--><!--Device-OH_HUKS_DIGEST_SM3 = 2-End--> |
| OH_HUKS_DIGEST_SHA1 = 10 | SHA-1.<br><!--Device-OH_HUKS_DIGEST_SHA1 = 10--><!--Device-OH_HUKS_DIGEST_SHA1 = 10-End--> |
| OH_HUKS_DIGEST_SHA224 = 11 | SHA-224.<br><!--Device-OH_HUKS_DIGEST_SHA224 = 11--><!--Device-OH_HUKS_DIGEST_SHA224 = 11-End--> |
| OH_HUKS_DIGEST_SHA256 = 12 | SHA-256.<br><!--Device-OH_HUKS_DIGEST_SHA256 = 12--><!--Device-OH_HUKS_DIGEST_SHA256 = 12-End--> |
| OH_HUKS_DIGEST_SHA384 = 13 | SHA-384.<br><!--Device-OH_HUKS_DIGEST_SHA384 = 13--><!--Device-OH_HUKS_DIGEST_SHA384 = 13-End--> |
| OH_HUKS_DIGEST_SHA512 = 14 | SHA-512.<br><!--Device-OH_HUKS_DIGEST_SHA512 = 14--><!--Device-OH_HUKS_DIGEST_SHA512 = 14-End--> |

### OH_Huks_KeyPadding

```c
enum OH_Huks_KeyPadding
```

**Description**

Enumerates the padding algorithm types.

<!--Device-enum OH_Huks_KeyPadding--><!--Device-enum OH_Huks_KeyPadding-End-->

**System capability**: SystemCapability.Security.Huks.Core

**Since**: 9

| Enum item | Description |
| -- | -- |
| OH_HUKS_PADDING_NONE = 0 | No padding algorithm.<br><!--Device-OH_HUKS_PADDING_NONE = 0--><!--Device-OH_HUKS_PADDING_NONE = 0-End--> |
| OH_HUKS_PADDING_OAEP = 1 | OAEP.<br><!--Device-OH_HUKS_PADDING_OAEP = 1--><!--Device-OH_HUKS_PADDING_OAEP = 1-End--> |
| OH_HUKS_PADDING_PSS = 2 | PSS.<br><!--Device-OH_HUKS_PADDING_PSS = 2--><!--Device-OH_HUKS_PADDING_PSS = 2-End--> |
| OH_HUKS_PADDING_PKCS1_V1_5 = 3 | PKCS1_V1_5.<br><!--Device-OH_HUKS_PADDING_PKCS1_V1_5 = 3--><!--Device-OH_HUKS_PADDING_PKCS1_V1_5 = 3-End--> |
| OH_HUKS_PADDING_PKCS5 = 4 | PKCS #5.<br><!--Device-OH_HUKS_PADDING_PKCS5 = 4--><!--Device-OH_HUKS_PADDING_PKCS5 = 4-End--> |
| OH_HUKS_PADDING_PKCS7 = 5 | PKCS #7.<br><!--Device-OH_HUKS_PADDING_PKCS7 = 5--><!--Device-OH_HUKS_PADDING_PKCS7 = 5-End--> |
| OH_HUKS_PADDING_ISO_IEC_9796_2 = 6 | ISO IEC 9796-2.<br>**Since**: 18<br><!--Device-OH_HUKS_PADDING_ISO_IEC_9796_2 = 6--><!--Device-OH_HUKS_PADDING_ISO_IEC_9796_2 = 6-End--> |
| OH_HUKS_PADDING_ISO_IEC_9797_1 = 7 | ISO IEC 9797-1.<br>**Since**: 18<br><!--Device-OH_HUKS_PADDING_ISO_IEC_9797_1 = 7--><!--Device-OH_HUKS_PADDING_ISO_IEC_9797_1 = 7-End--> |

### OH_Huks_CipherMode

```c
enum OH_Huks_CipherMode
```

**Description**

Cipher mode.

<!--Device-enum OH_Huks_CipherMode--><!--Device-enum OH_Huks_CipherMode-End-->

**System capability**: SystemCapability.Security.Huks.Core

**Since**: 9

| Enum item | Description |
| -- | -- |
| OH_HUKS_MODE_ECB = 1 | ECB.<br><!--Device-OH_HUKS_MODE_ECB = 1--><!--Device-OH_HUKS_MODE_ECB = 1-End--> |
| OH_HUKS_MODE_CBC = 2 | CBC.<br><!--Device-OH_HUKS_MODE_CBC = 2--><!--Device-OH_HUKS_MODE_CBC = 2-End--> |
| OH_HUKS_MODE_CTR = 3 | CTR.<br><!--Device-OH_HUKS_MODE_CTR = 3--><!--Device-OH_HUKS_MODE_CTR = 3-End--> |
| OH_HUKS_MODE_OFB = 4 | OFB.<br><!--Device-OH_HUKS_MODE_OFB = 4--><!--Device-OH_HUKS_MODE_OFB = 4-End--> |
| OH_HUKS_MODE_CFB = 5 | CFB.<br>**Since**: 12<br><!--Device-OH_HUKS_MODE_CFB = 5--><!--Device-OH_HUKS_MODE_CFB = 5-End--> |
| OH_HUKS_MODE_CCM = 31 | CCM.<br><!--Device-OH_HUKS_MODE_CCM = 31--><!--Device-OH_HUKS_MODE_CCM = 31-End--> |
| OH_HUKS_MODE_GCM = 32 | GCM.<br><!--Device-OH_HUKS_MODE_GCM = 32--><!--Device-OH_HUKS_MODE_GCM = 32-End--> |

### OH_Huks_KeySize

```c
enum OH_Huks_KeySize
```

**Description**

Enumerates the key sizes of different algorithms.

<!--Device-enum OH_Huks_KeySize--><!--Device-enum OH_Huks_KeySize-End-->

**System capability**: SystemCapability.Security.Huks.Core

**Since**: 9

| Enum item | Description |
| -- | -- |
| OH_HUKS_RSA_KEY_SIZE_512 = 512 | RSA key of 512 bits.<br><!--Device-OH_HUKS_RSA_KEY_SIZE_512 = 512--><!--Device-OH_HUKS_RSA_KEY_SIZE_512 = 512-End--> |
| OH_HUKS_RSA_KEY_SIZE_768 = 768 | RSA key of 768 bits.<br><!--Device-OH_HUKS_RSA_KEY_SIZE_768 = 768--><!--Device-OH_HUKS_RSA_KEY_SIZE_768 = 768-End--> |
| OH_HUKS_RSA_KEY_SIZE_1024 = 1024 | RSA key of 1024 bits.<br><!--Device-OH_HUKS_RSA_KEY_SIZE_1024 = 1024--><!--Device-OH_HUKS_RSA_KEY_SIZE_1024 = 1024-End--> |
| OH_HUKS_RSA_KEY_SIZE_2048 = 2048 | RSA key of 2048 bits.<br><!--Device-OH_HUKS_RSA_KEY_SIZE_2048 = 2048--><!--Device-OH_HUKS_RSA_KEY_SIZE_2048 = 2048-End--> |
| OH_HUKS_RSA_KEY_SIZE_3072 = 3072 | RSA key of 3072 bits.<br><!--Device-OH_HUKS_RSA_KEY_SIZE_3072 = 3072--><!--Device-OH_HUKS_RSA_KEY_SIZE_3072 = 3072-End--> |
| OH_HUKS_RSA_KEY_SIZE_4096 = 4096 | RSA key of 4096 bits.<br><!--Device-OH_HUKS_RSA_KEY_SIZE_4096 = 4096--><!--Device-OH_HUKS_RSA_KEY_SIZE_4096 = 4096-End--> |
| OH_HUKS_ECC_KEY_SIZE_224 = 224 | ECC key of 224 bits.<br><!--Device-OH_HUKS_ECC_KEY_SIZE_224 = 224--><!--Device-OH_HUKS_ECC_KEY_SIZE_224 = 224-End--> |
| OH_HUKS_ECC_KEY_SIZE_256 = 256 | ECC key of 256 bits.<br><!--Device-OH_HUKS_ECC_KEY_SIZE_256 = 256--><!--Device-OH_HUKS_ECC_KEY_SIZE_256 = 256-End--> |
| OH_HUKS_ECC_KEY_SIZE_384 = 384 | ECC key of 384 bits.<br><!--Device-OH_HUKS_ECC_KEY_SIZE_384 = 384--><!--Device-OH_HUKS_ECC_KEY_SIZE_384 = 384-End--> |
| OH_HUKS_ECC_KEY_SIZE_521 = 521 | ECC key of 521 bits.<br><!--Device-OH_HUKS_ECC_KEY_SIZE_521 = 521--><!--Device-OH_HUKS_ECC_KEY_SIZE_521 = 521-End--> |
| OH_HUKS_AES_KEY_SIZE_128 = 128 | AES key of 128 bits.<br><!--Device-OH_HUKS_AES_KEY_SIZE_128 = 128--><!--Device-OH_HUKS_AES_KEY_SIZE_128 = 128-End--> |
| OH_HUKS_AES_KEY_SIZE_192 = 192 | AES key of 192 bits.<br><!--Device-OH_HUKS_AES_KEY_SIZE_192 = 192--><!--Device-OH_HUKS_AES_KEY_SIZE_192 = 192-End--> |
| OH_HUKS_AES_KEY_SIZE_256 = 256 | AES key of 256 bits.<br><!--Device-OH_HUKS_AES_KEY_SIZE_256 = 256--><!--Device-OH_HUKS_AES_KEY_SIZE_256 = 256-End--> |
| OH_HUKS_AES_KEY_SIZE_512 = 512 | AES key of 512 bits.<br><!--Device-OH_HUKS_AES_KEY_SIZE_512 = 512--><!--Device-OH_HUKS_AES_KEY_SIZE_512 = 512-End--> |
| OH_HUKS_CURVE25519_KEY_SIZE_256 = 256 | Curve25519 key of 256 bits.<br><!--Device-OH_HUKS_CURVE25519_KEY_SIZE_256 = 256--><!--Device-OH_HUKS_CURVE25519_KEY_SIZE_256 = 256-End--> |
| OH_HUKS_DH_KEY_SIZE_2048 = 2048 | DH key of 2048 bits.<br><!--Device-OH_HUKS_DH_KEY_SIZE_2048 = 2048--><!--Device-OH_HUKS_DH_KEY_SIZE_2048 = 2048-End--> |
| OH_HUKS_DH_KEY_SIZE_3072 = 3072 | DH key of 3072 bits.<br><!--Device-OH_HUKS_DH_KEY_SIZE_3072 = 3072--><!--Device-OH_HUKS_DH_KEY_SIZE_3072 = 3072-End--> |
| OH_HUKS_DH_KEY_SIZE_4096 = 4096 | DH key of 4096 bits.<br><!--Device-OH_HUKS_DH_KEY_SIZE_4096 = 4096--><!--Device-OH_HUKS_DH_KEY_SIZE_4096 = 4096-End--> |
| OH_HUKS_SM2_KEY_SIZE_256 = 256 | SM2 key of 256 bits.<br><!--Device-OH_HUKS_SM2_KEY_SIZE_256 = 256--><!--Device-OH_HUKS_SM2_KEY_SIZE_256 = 256-End--> |
| OH_HUKS_SM4_KEY_SIZE_128 = 128 | SM4 key of 128 bits.<br><!--Device-OH_HUKS_SM4_KEY_SIZE_128 = 128--><!--Device-OH_HUKS_SM4_KEY_SIZE_128 = 128-End--> |
| OH_HUKS_DES_KEY_SIZE_64 = 64 | DES key of 64 bits.<br>**Since**: 18<br><!--Device-OH_HUKS_DES_KEY_SIZE_64 = 64--><!--Device-OH_HUKS_DES_KEY_SIZE_64 = 64-End--> |
| OH_HUKS_3DES_KEY_SIZE_128 = 128 | 3DES key of 128 bits.<br>**Since**: 18<br><!--Device-OH_HUKS_3DES_KEY_SIZE_128 = 128--><!--Device-OH_HUKS_3DES_KEY_SIZE_128 = 128-End--> |
| OH_HUKS_3DES_KEY_SIZE_192 = 192 | 3DES key of 192 bits.<br>**Since**: 18<br><!--Device-OH_HUKS_3DES_KEY_SIZE_192 = 192--><!--Device-OH_HUKS_3DES_KEY_SIZE_192 = 192-End--> |

### OH_Huks_KeyAlg

```c
enum OH_Huks_KeyAlg
```

**Description**

Enumerates the algorithms for keys.

<!--Device-enum OH_Huks_KeyAlg--><!--Device-enum OH_Huks_KeyAlg-End-->

**System capability**: SystemCapability.Security.Huks.Core

**Since**: 9

| Enum item | Description |
| -- | -- |
| OH_HUKS_ALG_RSA = 1 | RSA.<br><!--Device-OH_HUKS_ALG_RSA = 1--><!--Device-OH_HUKS_ALG_RSA = 1-End--> |
| OH_HUKS_ALG_ECC = 2 | ECC.<br><!--Device-OH_HUKS_ALG_ECC = 2--><!--Device-OH_HUKS_ALG_ECC = 2-End--> |
| OH_HUKS_ALG_DSA = 3 | DSA.<br><!--Device-OH_HUKS_ALG_DSA = 3--><!--Device-OH_HUKS_ALG_DSA = 3-End--> |
| OH_HUKS_ALG_AES = 20 | Advanced Encryption Standard (AES).<br><!--Device-OH_HUKS_ALG_AES = 20--><!--Device-OH_HUKS_ALG_AES = 20-End--> |
| OH_HUKS_ALG_HMAC = 50 | HMAC algorithm.<br><!--Device-OH_HUKS_ALG_HMAC = 50--><!--Device-OH_HUKS_ALG_HMAC = 50-End--> |
| OH_HUKS_ALG_HKDF = 51 | HKDF.<br><!--Device-OH_HUKS_ALG_HKDF = 51--><!--Device-OH_HUKS_ALG_HKDF = 51-End--> |
| OH_HUKS_ALG_PBKDF2 = 52 | PBKDF2.<br><!--Device-OH_HUKS_ALG_PBKDF2 = 52--><!--Device-OH_HUKS_ALG_PBKDF2 = 52-End--> |
| OH_HUKS_ALG_ECDH = 100 | ECDH.<br><!--Device-OH_HUKS_ALG_ECDH = 100--><!--Device-OH_HUKS_ALG_ECDH = 100-End--> |
| OH_HUKS_ALG_X25519 = 101 | X25519.<br><!--Device-OH_HUKS_ALG_X25519 = 101--><!--Device-OH_HUKS_ALG_X25519 = 101-End--> |
| OH_HUKS_ALG_ED25519 = 102 | Ed25519.<br><!--Device-OH_HUKS_ALG_ED25519 = 102--><!--Device-OH_HUKS_ALG_ED25519 = 102-End--> |
| OH_HUKS_ALG_DH = 103 | DH.<br><!--Device-OH_HUKS_ALG_DH = 103--><!--Device-OH_HUKS_ALG_DH = 103-End--> |
| OH_HUKS_ALG_SM2 = 150 | ShangMi2 (SM2).<br><!--Device-OH_HUKS_ALG_SM2 = 150--><!--Device-OH_HUKS_ALG_SM2 = 150-End--> |
| OH_HUKS_ALG_SM3 = 151 | SM3.<br><!--Device-OH_HUKS_ALG_SM3 = 151--><!--Device-OH_HUKS_ALG_SM3 = 151-End--> |
| OH_HUKS_ALG_SM4 = 152 | SM4.<br><!--Device-OH_HUKS_ALG_SM4 = 152--><!--Device-OH_HUKS_ALG_SM4 = 152-End--> |
| OH_HUKS_ALG_DES = 160 | DES.<br>**Since**: 18<br><!--Device-OH_HUKS_ALG_DES = 160--><!--Device-OH_HUKS_ALG_DES = 160-End--> |
| OH_HUKS_ALG_3DES = 161 | 3DES.<br>**Since**: 18<br><!--Device-OH_HUKS_ALG_3DES = 161--><!--Device-OH_HUKS_ALG_3DES = 161-End--> |
| OH_HUKS_ALG_CMAC = 162 | CMAC.<br>**Since**: 18<br><!--Device-OH_HUKS_ALG_CMAC = 162--><!--Device-OH_HUKS_ALG_CMAC = 162-End--> |

### OH_Huks_AlgSuite

```c
enum OH_Huks_AlgSuite
```

**Description**

Enumerates the algorithm suites that can be used for importing of a key in ciphertext. <br>Key material format for **OH_HUKS_UNWRAP_SUITE_X25519_AES_256_GCM_NOPADDING**: <br>\| x25519_plain_pubkey_length (4 Byte) \| x25519_plain_pubkey \| agreekey_aad_length (4 Byte) \| agreekey_aad <br>\| agreekey_nonce_length (4 Byte) \| agreekey_nonce \| agreekey_aead_tag_len(4 Byte) \| agreekey_aead_tag <br>\| kek_enc_data_length (4 Byte) \| kek_enc_data \| kek_aad_length (4 Byte) \| kek_aad <br>\| kek_nonce_length (4 Byte) \| kek_nonce \| kek_aead_tag_len (4 Byte) \| kek_aead_tag <br>\| key_material_size_len (4 Byte) \| key_material_size \| key_mat_enc_length (4 Byte) \| key_mat_enc_data<br> <br>Key material format for **OH_HUKS_UNWRAP_SUITE_ECDH_AES_256_GCM_NOPADDING**: <br>\| ECC_plain_pubkey_length (4 Byte) \| ECC_plain_pubkey \| agreekey_aad_length (4 Byte) \| agreekey_aad <br>\| agreekey_nonce_length (4 Byte) \| agreekey_nonce \| agreekey_aead_tag_len(4 Byte) \| agreekey_aead_tag <br>\| kek_enc_data_length (4 Byte) \| kek_enc_data \| kek_aad_length (4 Byte) \| kek_aad <br>\| kek_nonce_length (4 Byte) \| kek_nonce \| kek_aead_tag_len (4 Byte) \| kek_aead_tag <br>\| key_material_size_len (4 Byte) \| key_material_size \| key_mat_enc_length (4 Byte) \| key_mat_enc_data<br> <br>Key material format for **OH_HUKS_UNWRAP_SUITE_SM2_SM4_ECB_NOPADDING**: <br>\| kek_SM4_enc_length (4 Byte) \| EN_SM4_key \| importkey_enc_length (4 Byte) \| importkey_enc

<!--Device-enum OH_Huks_AlgSuite--><!--Device-enum OH_Huks_AlgSuite-End-->

**System capability**: SystemCapability.Security.Huks.Core

**Since**: 9

| Enum item | Description |
| -- | -- |
| OH_HUKS_UNWRAP_SUITE_X25519_AES_256_GCM_NOPADDING = 1 | Key material in Length-Value format, using X25519 for key agreement and AES-256-GCM for encryption and decryption. For details about the material format, see the preceding description.<br><!--Device-OH_HUKS_UNWRAP_SUITE_X25519_AES_256_GCM_NOPADDING = 1--><!--Device-OH_HUKS_UNWRAP_SUITE_X25519_AES_256_GCM_NOPADDING = 1-End--> |
| OH_HUKS_UNWRAP_SUITE_ECDH_AES_256_GCM_NOPADDING = 2 | Key material in Length-Value format, using ECDH-p256 for key agreement and AES-256-GCM for encryption and decryption. For details about the material format, see the preceding description.<br><!--Device-OH_HUKS_UNWRAP_SUITE_ECDH_AES_256_GCM_NOPADDING = 2--><!--Device-OH_HUKS_UNWRAP_SUITE_ECDH_AES_256_GCM_NOPADDING = 2-End--> |
| OH_HUKS_UNWRAP_SUITE_SM2_SM4_ECB_NOPADDING = 5 | Key material in Length-Value format, using the temporary SM4 key to encrypt the imported key and using the SM2 key that has been imported to HUKS to encrypt the SM4 key. For details about the material format, see the preceding description.<br>**Since**: 23<br><!--Device-OH_HUKS_UNWRAP_SUITE_SM2_SM4_ECB_NOPADDING = 5--><!--Device-OH_HUKS_UNWRAP_SUITE_SM2_SM4_ECB_NOPADDING = 5-End--> |

### OH_Huks_KeyGenerateType

```c
enum OH_Huks_KeyGenerateType
```

**Description**

Enumerates the types of the key generated.

<!--Device-enum OH_Huks_KeyGenerateType--><!--Device-enum OH_Huks_KeyGenerateType-End-->

**System capability**: SystemCapability.Security.Huks.Core

**Since**: 9

| Enum item | Description |
| -- | -- |
| OH_HUKS_KEY_GENERATE_TYPE_DEFAULT = 0 | Key generated by default.<br><!--Device-OH_HUKS_KEY_GENERATE_TYPE_DEFAULT = 0--><!--Device-OH_HUKS_KEY_GENERATE_TYPE_DEFAULT = 0-End--> |
| OH_HUKS_KEY_GENERATE_TYPE_DERIVE = 1 | Derived key.<br><!--Device-OH_HUKS_KEY_GENERATE_TYPE_DERIVE = 1--><!--Device-OH_HUKS_KEY_GENERATE_TYPE_DERIVE = 1-End--> |
| OH_HUKS_KEY_GENERATE_TYPE_AGREE = 2 | Key generated by key agreement.<br><!--Device-OH_HUKS_KEY_GENERATE_TYPE_AGREE = 2--><!--Device-OH_HUKS_KEY_GENERATE_TYPE_AGREE = 2-End--> |

### OH_Huks_KeyFlag

```c
enum OH_Huks_KeyFlag
```

**Description**

Enumerates the key generation types.

<!--Device-enum OH_Huks_KeyFlag--><!--Device-enum OH_Huks_KeyFlag-End-->

**System capability**: SystemCapability.Security.Huks.Core

**Since**: 9

| Enum item | Description |
| -- | -- |
| OH_HUKS_KEY_FLAG_IMPORT_KEY = 1 | Import a public key using a function.<br><!--Device-OH_HUKS_KEY_FLAG_IMPORT_KEY = 1--><!--Device-OH_HUKS_KEY_FLAG_IMPORT_KEY = 1-End--> |
| OH_HUKS_KEY_FLAG_GENERATE_KEY = 2 | Generate a key by using a function.<br><!--Device-OH_HUKS_KEY_FLAG_GENERATE_KEY = 2--><!--Device-OH_HUKS_KEY_FLAG_GENERATE_KEY = 2-End--> |
| OH_HUKS_KEY_FLAG_AGREE_KEY = 3 | Generate a key by using a key agreement function.<br><!--Device-OH_HUKS_KEY_FLAG_AGREE_KEY = 3--><!--Device-OH_HUKS_KEY_FLAG_AGREE_KEY = 3-End--> |
| OH_HUKS_KEY_FLAG_DERIVE_KEY = 4 | Derive a key by using a function.<br><!--Device-OH_HUKS_KEY_FLAG_DERIVE_KEY = 4--><!--Device-OH_HUKS_KEY_FLAG_DERIVE_KEY = 4-End--> |

### OH_Huks_KeyStorageType

```c
enum OH_Huks_KeyStorageType
```

**Description**

Enumerates the key storage types.

<!--Device-enum OH_Huks_KeyStorageType--><!--Device-enum OH_Huks_KeyStorageType-End-->

**System capability**: SystemCapability.Security.Huks.Core

**Since**: 9

| Enum item | Description |
| -- | -- |
| OH_HUKS_STORAGE_TEMP = 0 | Return the key to the service via the API.<br><!--Device-OH_HUKS_STORAGE_TEMP = 0--><!--Device-OH_HUKS_STORAGE_TEMP = 0-End--> |
| OH_HUKS_STORAGE_PERSISTENT = 1 | Store the key in HUKS.<br><!--Device-OH_HUKS_STORAGE_PERSISTENT = 1--><!--Device-OH_HUKS_STORAGE_PERSISTENT = 1-End--> |
| OH_HUKS_STORAGE_ONLY_USED_IN_HUKS = 2 | Store the key generated from key derivation or key agreement in HUKS.<br><!--Device-OH_HUKS_STORAGE_ONLY_USED_IN_HUKS = 2--><!--Device-OH_HUKS_STORAGE_ONLY_USED_IN_HUKS = 2-End--> |
| OH_HUKS_STORAGE_KEY_EXPORT_ALLOWED = 3 | Return the key generated from key derivation or key agreement to the service.<br><!--Device-OH_HUKS_STORAGE_KEY_EXPORT_ALLOWED = 3--><!--Device-OH_HUKS_STORAGE_KEY_EXPORT_ALLOWED = 3-End--> |

### OH_Huks_ImportKeyType

```c
enum OH_Huks_ImportKeyType
```

**Description**

Enumerates the types of the key to import. By default, a public key is imported. This field is not required when a symmetric key is imported.

<!--Device-enum OH_Huks_ImportKeyType--><!--Device-enum OH_Huks_ImportKeyType-End-->

**System capability**: SystemCapability.Security.Huks.Core

**Since**: 9

| Enum item | Description |
| -- | -- |
| OH_HUKS_KEY_TYPE_PUBLIC_KEY = 0 | Public key.<br><!--Device-OH_HUKS_KEY_TYPE_PUBLIC_KEY = 0--><!--Device-OH_HUKS_KEY_TYPE_PUBLIC_KEY = 0-End--> |
| OH_HUKS_KEY_TYPE_PRIVATE_KEY = 1 | Private key.<br><!--Device-OH_HUKS_KEY_TYPE_PRIVATE_KEY = 1--><!--Device-OH_HUKS_KEY_TYPE_PRIVATE_KEY = 1-End--> |
| OH_HUKS_KEY_TYPE_KEY_PAIR = 2 | Public and private key pair.<br><!--Device-OH_HUKS_KEY_TYPE_KEY_PAIR = 2--><!--Device-OH_HUKS_KEY_TYPE_KEY_PAIR = 2-End--> |

### OH_Huks_RsaPssSaltLenType

```c
enum OH_Huks_RsaPssSaltLenType
```

**Description**

Enumerates the length types of the salt value in PSS padding mode of the RSA algorithm.

<!--Device-enum OH_Huks_RsaPssSaltLenType--><!--Device-enum OH_Huks_RsaPssSaltLenType-End-->

**System capability**: SystemCapability.Security.Huks.Core

**Since**: 10

| Enum item | Description |
| -- | -- |
| OH_HUKS_RSA_PSS_SALT_LEN_DIGEST = 0 | The salt length is set to the digest length.<br><!--Device-OH_HUKS_RSA_PSS_SALT_LEN_DIGEST = 0--><!--Device-OH_HUKS_RSA_PSS_SALT_LEN_DIGEST = 0-End--> |
| OH_HUKS_RSA_PSS_SALT_LEN_MAX = 1 | The salt length is set to the maximum length.<br><!--Device-OH_HUKS_RSA_PSS_SALT_LEN_MAX = 1--><!--Device-OH_HUKS_RSA_PSS_SALT_LEN_MAX = 1-End--> |

### OH_Huks_ErrCode

```c
enum OH_Huks_ErrCode
```

**Description**

Enumerates error codes.

<!--Device-enum OH_Huks_ErrCode--><!--Device-enum OH_Huks_ErrCode-End-->

**System capability**: SystemCapability.Security.Huks.Core

**Since**: 9

| Enum item | Description |
| -- | -- |
| OH_HUKS_SUCCESS = 0 | Success.<br><!--Device-OH_HUKS_SUCCESS = 0--><!--Device-OH_HUKS_SUCCESS = 0-End--> |
| OH_HUKS_ERR_CODE_PERMISSION_FAIL = 201 | Permission verification failed.<br><!--Device-OH_HUKS_ERR_CODE_PERMISSION_FAIL = 201--><!--Device-OH_HUKS_ERR_CODE_PERMISSION_FAIL = 201-End--> |
| OH_HUKS_ERR_CODE_ILLEGAL_ARGUMENT = 401 | Invalid parameter (universal).<br><!--Device-OH_HUKS_ERR_CODE_ILLEGAL_ARGUMENT = 401--><!--Device-OH_HUKS_ERR_CODE_ILLEGAL_ARGUMENT = 401-End--> |
| OH_HUKS_ERR_CODE_NOT_SUPPORTED_API = 801 | The API is not supported.<br><!--Device-OH_HUKS_ERR_CODE_NOT_SUPPORTED_API = 801--><!--Device-OH_HUKS_ERR_CODE_NOT_SUPPORTED_API = 801-End--> |
| OH_HUKS_ERR_CODE_FEATURE_NOT_SUPPORTED = 12000001 | The feature is not supported.<br><!--Device-OH_HUKS_ERR_CODE_FEATURE_NOT_SUPPORTED = 12000001--><!--Device-OH_HUKS_ERR_CODE_FEATURE_NOT_SUPPORTED = 12000001-End--> |
| OH_HUKS_ERR_CODE_MISSING_CRYPTO_ALG_ARGUMENT = 12000002 | Key algorithm parameters are missing.<br><!--Device-OH_HUKS_ERR_CODE_MISSING_CRYPTO_ALG_ARGUMENT = 12000002--><!--Device-OH_HUKS_ERR_CODE_MISSING_CRYPTO_ALG_ARGUMENT = 12000002-End--> |
| OH_HUKS_ERR_CODE_INVALID_CRYPTO_ALG_ARGUMENT = 12000003 | Invalid key algorithm parameter.<br><!--Device-OH_HUKS_ERR_CODE_INVALID_CRYPTO_ALG_ARGUMENT = 12000003--><!--Device-OH_HUKS_ERR_CODE_INVALID_CRYPTO_ALG_ARGUMENT = 12000003-End--> |
| OH_HUKS_ERR_CODE_FILE_OPERATION_FAIL = 12000004 | File operation failed.<br><!--Device-OH_HUKS_ERR_CODE_FILE_OPERATION_FAIL = 12000004--><!--Device-OH_HUKS_ERR_CODE_FILE_OPERATION_FAIL = 12000004-End--> |
| OH_HUKS_ERR_CODE_COMMUNICATION_FAIL = 12000005 | The process communication failed.<br><!--Device-OH_HUKS_ERR_CODE_COMMUNICATION_FAIL = 12000005--><!--Device-OH_HUKS_ERR_CODE_COMMUNICATION_FAIL = 12000005-End--> |
| OH_HUKS_ERR_CODE_CRYPTO_FAIL = 12000006 | Crypto operation failed.<br><!--Device-OH_HUKS_ERR_CODE_CRYPTO_FAIL = 12000006--><!--Device-OH_HUKS_ERR_CODE_CRYPTO_FAIL = 12000006-End--> |
| OH_HUKS_ERR_CODE_KEY_AUTH_PERMANENTLY_INVALIDATED = 12000007 | Failed to access the key because the key has expired.<br><!--Device-OH_HUKS_ERR_CODE_KEY_AUTH_PERMANENTLY_INVALIDATED = 12000007--><!--Device-OH_HUKS_ERR_CODE_KEY_AUTH_PERMANENTLY_INVALIDATED = 12000007-End--> |
| OH_HUKS_ERR_CODE_KEY_AUTH_VERIFY_FAILED = 12000008 | Failed to access the key because the authentication has failed.<br><!--Device-OH_HUKS_ERR_CODE_KEY_AUTH_VERIFY_FAILED = 12000008--><!--Device-OH_HUKS_ERR_CODE_KEY_AUTH_VERIFY_FAILED = 12000008-End--> |
| OH_HUKS_ERR_CODE_KEY_AUTH_TIME_OUT = 12000009 | Key access timed out.<br><!--Device-OH_HUKS_ERR_CODE_KEY_AUTH_TIME_OUT = 12000009--><!--Device-OH_HUKS_ERR_CODE_KEY_AUTH_TIME_OUT = 12000009-End--> |
| OH_HUKS_ERR_CODE_SESSION_LIMIT = 12000010 | The number of key operation sessions has reached the limit.<br><!--Device-OH_HUKS_ERR_CODE_SESSION_LIMIT = 12000010--><!--Device-OH_HUKS_ERR_CODE_SESSION_LIMIT = 12000010-End--> |
| OH_HUKS_ERR_CODE_ITEM_NOT_EXIST = 12000011 | The entity does not exist.<br><!--Device-OH_HUKS_ERR_CODE_ITEM_NOT_EXIST = 12000011--><!--Device-OH_HUKS_ERR_CODE_ITEM_NOT_EXIST = 12000011-End--> |
| OH_HUKS_ERR_CODE_INTERNAL_ERROR = 12000012 | Internal error.<br><!--Device-OH_HUKS_ERR_CODE_INTERNAL_ERROR = 12000012--><!--Device-OH_HUKS_ERR_CODE_INTERNAL_ERROR = 12000012-End--> |
| OH_HUKS_ERR_CODE_CREDENTIAL_NOT_EXIST = 12000013 | The authentication credential does not exist.<br><!--Device-OH_HUKS_ERR_CODE_CREDENTIAL_NOT_EXIST = 12000013--><!--Device-OH_HUKS_ERR_CODE_CREDENTIAL_NOT_EXIST = 12000013-End--> |
| OH_HUKS_ERR_CODE_INSUFFICIENT_MEMORY = 12000014 | Insufficient memory.<br><!--Device-OH_HUKS_ERR_CODE_INSUFFICIENT_MEMORY = 12000014--><!--Device-OH_HUKS_ERR_CODE_INSUFFICIENT_MEMORY = 12000014-End--> |
| OH_HUKS_ERR_CODE_CALL_SERVICE_FAILED = 12000015 | Failed to invoke the service.<br><!--Device-OH_HUKS_ERR_CODE_CALL_SERVICE_FAILED = 12000015--><!--Device-OH_HUKS_ERR_CODE_CALL_SERVICE_FAILED = 12000015-End--> |
| OH_HUKS_ERR_CODE_DEVICE_PASSWORD_UNSET = 12000016 | The lock screen password required is not set.<br>**Since**: 11<br><!--Device-OH_HUKS_ERR_CODE_DEVICE_PASSWORD_UNSET = 12000016--><!--Device-OH_HUKS_ERR_CODE_DEVICE_PASSWORD_UNSET = 12000016-End--> |
| OH_HUKS_ERR_CODE_KEY_ALREADY_EXIST = 12000017 | A key with the same name already exists.<br>**Since**: 20<br><!--Device-OH_HUKS_ERR_CODE_KEY_ALREADY_EXIST = 12000017--><!--Device-OH_HUKS_ERR_CODE_KEY_ALREADY_EXIST = 12000017-End--> |
| OH_HUKS_ERR_CODE_INVALID_ARGUMENT = 12000018 | An input parameter is invalid.<br>**Since**: 20<br><!--Device-OH_HUKS_ERR_CODE_INVALID_ARGUMENT = 12000018--><!--Device-OH_HUKS_ERR_CODE_INVALID_ARGUMENT = 12000018-End--> |
| OH_HUKS_ERR_CODE_ITEM_EXISTS = 12000019 | The entity already exists.<br>**Since**: 22<br><!--Device-OH_HUKS_ERR_CODE_ITEM_EXISTS = 12000019--><!--Device-OH_HUKS_ERR_CODE_ITEM_EXISTS = 12000019-End--> |
| OH_HUKS_ERR_CODE_EXTERNAL_MODULE = 12000020 | The provider or UKey internal execution fails.<br>**Since**: 22<br><!--Device-OH_HUKS_ERR_CODE_EXTERNAL_MODULE = 12000020--><!--Device-OH_HUKS_ERR_CODE_EXTERNAL_MODULE = 12000020-End--> |
| OH_HUKS_ERR_CODE_PIN_LOCKED = 12000021 | The PIN is locked.<br>**Since**: 22<br><!--Device-OH_HUKS_ERR_CODE_PIN_LOCKED = 12000021--><!--Device-OH_HUKS_ERR_CODE_PIN_LOCKED = 12000021-End--> |
| OH_HUKS_ERR_CODE_PIN_INCORRECT = 12000022 | Incorrect PIN.<br>**Since**: 22<br><!--Device-OH_HUKS_ERR_CODE_PIN_INCORRECT = 12000022--><!--Device-OH_HUKS_ERR_CODE_PIN_INCORRECT = 12000022-End--> |
| OH_HUKS_ERR_CODE_PIN_NO_AUTH = 12000023 | PIN authentication fails.<br>**Since**: 22<br><!--Device-OH_HUKS_ERR_CODE_PIN_NO_AUTH = 12000023--><!--Device-OH_HUKS_ERR_CODE_PIN_NO_AUTH = 12000023-End--> |
| OH_HUKS_ERR_CODE_BUSY = 12000024 | The provider or UKey resources are being used.<br>**Since**: 22<br><!--Device-OH_HUKS_ERR_CODE_BUSY = 12000024--><!--Device-OH_HUKS_ERR_CODE_BUSY = 12000024-End--> |
| OH_HUKS_ERR_CODE_EXCEED_LIMIT = 12000025 | The resource limit is exceeded.<br>**Since**: 22<br><!--Device-OH_HUKS_ERR_CODE_EXCEED_LIMIT = 12000025--><!--Device-OH_HUKS_ERR_CODE_EXCEED_LIMIT = 12000025-End--> |
| OH_HUKS_ERR_CODE_NETWORK_UNAVAILABLE = 12000027 | The network is unavailable.<br>**Since**: 26.1.0<br><!--Device-OH_HUKS_ERR_CODE_NETWORK_UNAVAILABLE = 12000027--><!--Device-OH_HUKS_ERR_CODE_NETWORK_UNAVAILABLE = 12000027-End--> |

### OH_Huks_TagType

```c
enum OH_Huks_TagType
```

**Description**

Enumerates parameter types.

<!--Device-enum OH_Huks_TagType--><!--Device-enum OH_Huks_TagType-End-->

**System capability**: SystemCapability.Security.Huks.Core

**Since**: 9

| Enum item | Description |
| -- | -- |
| OH_HUKS_TAG_TYPE_INVALID = 0 << 28 | Invalid tag type.<br><!--Device-OH_HUKS_TAG_TYPE_INVALID = 0 << 28--><!--Device-OH_HUKS_TAG_TYPE_INVALID = 0 << 28-End--> |
| OH_HUKS_TAG_TYPE_INT = 1 << 28 | int32_t.<br><!--Device-OH_HUKS_TAG_TYPE_INT = 1 << 28--><!--Device-OH_HUKS_TAG_TYPE_INT = 1 << 28-End--> |
| OH_HUKS_TAG_TYPE_UINT = 2 << 28 | uint32_t.<br><!--Device-OH_HUKS_TAG_TYPE_UINT = 2 << 28--><!--Device-OH_HUKS_TAG_TYPE_UINT = 2 << 28-End--> |
| OH_HUKS_TAG_TYPE_ULONG = 3 << 28 | uint64_t.<br><!--Device-OH_HUKS_TAG_TYPE_ULONG = 3 << 28--><!--Device-OH_HUKS_TAG_TYPE_ULONG = 3 << 28-End--> |
| OH_HUKS_TAG_TYPE_BOOL = 4 << 28 | Boolean.<br><!--Device-OH_HUKS_TAG_TYPE_BOOL = 4 << 28--><!--Device-OH_HUKS_TAG_TYPE_BOOL = 4 << 28-End--> |
| OH_HUKS_TAG_TYPE_BYTES = 5 << 28 | [OH_Huks_Blob](capi-hukstypeapi-oh-huks-blob.md).<br><!--Device-OH_HUKS_TAG_TYPE_BYTES = 5 << 28--><!--Device-OH_HUKS_TAG_TYPE_BYTES = 5 << 28-End--> |

**Reference**:

[OH_Huks_Param](capi-hukstypeapi-oh-huks-param.md)


### OH_Huks_UserAuthType

```c
enum OH_Huks_UserAuthType
```

**Description**

Enumerates the user authentication types in key access control.

<!--Device-enum OH_Huks_UserAuthType--><!--Device-enum OH_Huks_UserAuthType-End-->

**System capability**: SystemCapability.Security.Huks.Core

**Since**: 9

| Enum item | Description |
| -- | -- |
| OH_HUKS_USER_AUTH_TYPE_FINGERPRINT = 1 << 0 | Fingerprint authentication.<br><!--Device-OH_HUKS_USER_AUTH_TYPE_FINGERPRINT = 1 << 0--><!--Device-OH_HUKS_USER_AUTH_TYPE_FINGERPRINT = 1 << 0-End--> |
| OH_HUKS_USER_AUTH_TYPE_FACE = 1 << 1 | Facial authentication.<br><!--Device-OH_HUKS_USER_AUTH_TYPE_FACE = 1 << 1--><!--Device-OH_HUKS_USER_AUTH_TYPE_FACE = 1 << 1-End--> |
| OH_HUKS_USER_AUTH_TYPE_PIN = 1 << 2 | PIN authentication.<br><!--Device-OH_HUKS_USER_AUTH_TYPE_PIN = 1 << 2--><!--Device-OH_HUKS_USER_AUTH_TYPE_PIN = 1 << 2-End--> |
| OH_HUKS_USER_AUTH_TYPE_TUI_PIN = 1 << 5 | TUI PIN authentication.<br>**Since**: 20<br><!--Device-OH_HUKS_USER_AUTH_TYPE_TUI_PIN = 1 << 5--><!--Device-OH_HUKS_USER_AUTH_TYPE_TUI_PIN = 1 << 5-End--> |

### OH_Huks_AuthAccessType

```c
enum OH_Huks_AuthAccessType
```

**Description**

Enumerates the rules for invalidating a key.

<!--Device-enum OH_Huks_AuthAccessType--><!--Device-enum OH_Huks_AuthAccessType-End-->

**System capability**: SystemCapability.Security.Huks.Core

**Since**: 9

| Enum item | Description |
| -- | -- |
| OH_HUKS_AUTH_ACCESS_INVALID_CLEAR_PASSWORD = 1 << 0 | The key becomes invalid after the password is cleared.<br><!--Device-OH_HUKS_AUTH_ACCESS_INVALID_CLEAR_PASSWORD = 1 << 0--><!--Device-OH_HUKS_AUTH_ACCESS_INVALID_CLEAR_PASSWORD = 1 << 0-End--> |
| OH_HUKS_AUTH_ACCESS_INVALID_NEW_BIO_ENROLL = 1 << 1 | The key becomes invalid after a new biometric feature is enrolled.<br><!--Device-OH_HUKS_AUTH_ACCESS_INVALID_NEW_BIO_ENROLL = 1 << 1--><!--Device-OH_HUKS_AUTH_ACCESS_INVALID_NEW_BIO_ENROLL = 1 << 1-End--> |
| OH_HUKS_AUTH_ACCESS_ALWAYS_VALID = 1 << 2 | The key is always valid.<br>**Since**: 11<br><!--Device-OH_HUKS_AUTH_ACCESS_ALWAYS_VALID = 1 << 2--><!--Device-OH_HUKS_AUTH_ACCESS_ALWAYS_VALID = 1 << 2-End--> |

### OH_Huks_AuthStorageLevel

```c
enum OH_Huks_AuthStorageLevel
```

**Description**

Enumerates the security levels for storing the key generated or imported.

<!--Device-enum OH_Huks_AuthStorageLevel--><!--Device-enum OH_Huks_AuthStorageLevel-End-->

**System capability**: SystemCapability.Security.Huks.Core

**Since**: 11

| Enum item | Description |
| -- | -- |
| OH_HUKS_AUTH_STORAGE_LEVEL_DE = 0 | The key can be accessed only after the device is started.<br>**Since**: 11<br><!--Device-OH_HUKS_AUTH_STORAGE_LEVEL_DE = 0--><!--Device-OH_HUKS_AUTH_STORAGE_LEVEL_DE = 0-End--> |
| OH_HUKS_AUTH_STORAGE_LEVEL_CE = 1 | The key can be accessed only after the first unlock of the device.<br>**Since**: 11<br><!--Device-OH_HUKS_AUTH_STORAGE_LEVEL_CE = 1--><!--Device-OH_HUKS_AUTH_STORAGE_LEVEL_CE = 1-End--> |
| OH_HUKS_AUTH_STORAGE_LEVEL_ECE = 2 | The key can be accessed only when the device is unlocked.<br>**Since**: 11<br><!--Device-OH_HUKS_AUTH_STORAGE_LEVEL_ECE = 2--><!--Device-OH_HUKS_AUTH_STORAGE_LEVEL_ECE = 2-End--> |

### OH_Huks_UserAuthMode

```c
enum OH_Huks_UserAuthMode
```

**Description**

Enumerates the user authentication modes in key access control.

<!--Device-enum OH_Huks_UserAuthMode--><!--Device-enum OH_Huks_UserAuthMode-End-->

**System capability**: SystemCapability.Security.Huks.Core

**Since**: 12

| Enum item | Description |
| -- | -- |
| OH_HUKS_USER_AUTH_MODE_LOCAL = 0 | Local authentication.<br>**Since**: 12<br><!--Device-OH_HUKS_USER_AUTH_MODE_LOCAL = 0--><!--Device-OH_HUKS_USER_AUTH_MODE_LOCAL = 0-End--> |
| OH_HUKS_USER_AUTH_MODE_COAUTH = 1 | Cross-device collaborative authentication.<br>**Since**: 12<br><!--Device-OH_HUKS_USER_AUTH_MODE_COAUTH = 1--><!--Device-OH_HUKS_USER_AUTH_MODE_COAUTH = 1-End--> |

### OH_Huks_ChallengeType

```c
enum OH_Huks_ChallengeType
```

**Description**

Enumerates the types of the challenge generated when a key is used.

<!--Device-enum OH_Huks_ChallengeType--><!--Device-enum OH_Huks_ChallengeType-End-->

**System capability**: SystemCapability.Security.Huks.Core

**Since**: 9

| Enum item | Description |
| -- | -- |
| OH_HUKS_CHALLENGE_TYPE_NORMAL = 0 | Normal challenge, which is of 32 bytes by default.<br><!--Device-OH_HUKS_CHALLENGE_TYPE_NORMAL = 0--><!--Device-OH_HUKS_CHALLENGE_TYPE_NORMAL = 0-End--> |
| OH_HUKS_CHALLENGE_TYPE_CUSTOM = 1 | Custom challenge, which supports one-time authentication for multiple keys. The valid value of a custom challenge is of 8 bytes.<br><!--Device-OH_HUKS_CHALLENGE_TYPE_CUSTOM = 1--><!--Device-OH_HUKS_CHALLENGE_TYPE_CUSTOM = 1-End--> |
| OH_HUKS_CHALLENGE_TYPE_NONE = 2 | Challenge is not required.<br><!--Device-OH_HUKS_CHALLENGE_TYPE_NONE = 2--><!--Device-OH_HUKS_CHALLENGE_TYPE_NONE = 2-End--> |

**Reference**:

[OH_Huks_ChallengePosition](capi-native-huks-type-h.md#oh_huks_challengeposition)


### OH_Huks_ChallengePosition

```c
enum OH_Huks_ChallengePosition
```

**Description**

Enumerates the positions of the 8-byte valid value in a custom challenge generated.

<!--Device-enum OH_Huks_ChallengePosition--><!--Device-enum OH_Huks_ChallengePosition-End-->

**System capability**: SystemCapability.Security.Huks.Core

**Since**: 9

| Enum item | Description |
| -- | -- |
| OH_HUKS_CHALLENGE_POS_0 = 0 | Bytes 0 to 7.<br><!--Device-OH_HUKS_CHALLENGE_POS_0 = 0--><!--Device-OH_HUKS_CHALLENGE_POS_0 = 0-End--> |
| OH_HUKS_CHALLENGE_POS_1 = 1 | Bytes 8 to 15.<br><!--Device-OH_HUKS_CHALLENGE_POS_1 = 1--><!--Device-OH_HUKS_CHALLENGE_POS_1 = 1-End--> |
| OH_HUKS_CHALLENGE_POS_2 = 2 | Bytes 16 to 23.<br><!--Device-OH_HUKS_CHALLENGE_POS_2 = 2--><!--Device-OH_HUKS_CHALLENGE_POS_2 = 2-End--> |
| OH_HUKS_CHALLENGE_POS_3 = 3 | Bytes 24 to 31.<br><!--Device-OH_HUKS_CHALLENGE_POS_3 = 3--><!--Device-OH_HUKS_CHALLENGE_POS_3 = 3-End--> |

### OH_Huks_SecureSignType

```c
enum OH_Huks_SecureSignType
```

**Description**

Enumerates the signature types of the key generated or imported.

<!--Device-enum OH_Huks_SecureSignType--><!--Device-enum OH_Huks_SecureSignType-End-->

**System capability**: SystemCapability.Security.Huks.Core

**Since**: 9

| Enum item | Description |
| -- | -- |
| OH_HUKS_SECURE_SIGN_WITH_AUTHINFO = 1 | The signature carries authentication information. This field is specified when a key is generated or imported. When the key is used for signing, the data will be added with the authentication information and then be signed. Note: The carried authentication information includes identity information. You need to describe the purpose, retention policy, and destruction method of the identity information in the privacy statement.<br><!--Device-OH_HUKS_SECURE_SIGN_WITH_AUTHINFO = 1--><!--Device-OH_HUKS_SECURE_SIGN_WITH_AUTHINFO = 1-End--> |

### OH_Huks_KeyClassType

```c
enum OH_Huks_KeyClassType
```

**Description**

Key type.

<!--Device-enum OH_Huks_KeyClassType--><!--Device-enum OH_Huks_KeyClassType-End-->

**System capability**: SystemCapability.Security.Huks.Core

**Since**: 22

| Enum item | Description |
| -- | -- |
| OH_HUKS_KEY_CLASS_DEFAULT = 0 | Default type. The key is stored in HUKS.<br>**Since**: 22<br><!--Device-OH_HUKS_KEY_CLASS_DEFAULT = 0--><!--Device-OH_HUKS_KEY_CLASS_DEFAULT = 0-End--> |
| OH_HUKS_KEY_CLASS_EXTENSION = 1 | The key is stored in an external encryption capability provider.<br>**Since**: 22<br><!--Device-OH_HUKS_KEY_CLASS_EXTENSION = 1--><!--Device-OH_HUKS_KEY_CLASS_EXTENSION = 1-End--> |

### OH_Huks_KeyWrapType

```c
enum OH_Huks_KeyWrapType
```

**Description**

Enumerates the wrap type of the key generated or imported.

<!--Device-enum OH_Huks_KeyWrapType--><!--Device-enum OH_Huks_KeyWrapType-End-->

**System capability**: SystemCapability.Security.Huks.Core

**Since**: 20

| Enum item | Description |
| -- | -- |
| OH_HUKS_KEY_WRAP_TYPE_HUK_BASED = 2 | Wrap type of the unique hardware key.<br>**Since**: 20<br><!--Device-OH_HUKS_KEY_WRAP_TYPE_HUK_BASED = 2--><!--Device-OH_HUKS_KEY_WRAP_TYPE_HUK_BASED = 2-End--> |

### OH_Huks_Tag

```c
enum OH_Huks_Tag
```

**Description**

Enumerates the tags contained in a parameter set. <br>1 to 200: key parameter tag values. <br>301 to 500: tag values related to access control and authentication of key usage. <br>501 to 600: tag values related to key authentication. <br>601 to 1000: reserved values for other types of tag values. <br>1001 to 9999: extended tag values. <br>11000 to 12000: reserved values. <br>20001 to N: reserved tag values.

<!--Device-enum OH_Huks_Tag--><!--Device-enum OH_Huks_Tag-End-->

**System capability**: SystemCapability.Security.Huks.Core

**Since**: 9

| Enum item | Description |
| -- | -- |
| OH_HUKS_TAG_ALGORITHM = OH_HUKS_TAG_TYPE_UINT \| 1 | Algorithm type. For details, see [OH_Huks_KeyAlg](capi-native-huks-type-h.md#oh_huks_keyalg).<br><!--Device-OH_HUKS_TAG_ALGORITHM = OH_HUKS_TAG_TYPE_UINT \| 1--><!--Device-OH_HUKS_TAG_ALGORITHM = OH_HUKS_TAG_TYPE_UINT \| 1-End--> |
| OH_HUKS_TAG_PURPOSE = OH_HUKS_TAG_TYPE_UINT \| 2 | Key purpose. For details, see [OH_Huks_KeyPurpose](capi-native-huks-type-h.md#oh_huks_keypurpose).<br><!--Device-OH_HUKS_TAG_PURPOSE = OH_HUKS_TAG_TYPE_UINT \| 2--><!--Device-OH_HUKS_TAG_PURPOSE = OH_HUKS_TAG_TYPE_UINT \| 2-End--> |
| OH_HUKS_TAG_KEY_SIZE = OH_HUKS_TAG_TYPE_UINT \| 3 | Key length, in bits. For details, see [OH_Huks_KeySize](capi-native-huks-type-h.md#oh_huks_keysize).<br><!--Device-OH_HUKS_TAG_KEY_SIZE = OH_HUKS_TAG_TYPE_UINT \| 3--><!--Device-OH_HUKS_TAG_KEY_SIZE = OH_HUKS_TAG_TYPE_UINT \| 3-End--> |
| OH_HUKS_TAG_DIGEST = OH_HUKS_TAG_TYPE_UINT \| 4 | Digest algorithm. For details, see [OH_Huks_KeyDigest](capi-native-huks-type-h.md#oh_huks_keydigest).<br><!--Device-OH_HUKS_TAG_DIGEST = OH_HUKS_TAG_TYPE_UINT \| 4--><!--Device-OH_HUKS_TAG_DIGEST = OH_HUKS_TAG_TYPE_UINT \| 4-End--> |
| OH_HUKS_TAG_PADDING = OH_HUKS_TAG_TYPE_UINT \| 5 | Padding algorithm. For details, see [OH_Huks_KeyPadding](capi-native-huks-type-h.md#oh_huks_keypadding).<br><!--Device-OH_HUKS_TAG_PADDING = OH_HUKS_TAG_TYPE_UINT \| 5--><!--Device-OH_HUKS_TAG_PADDING = OH_HUKS_TAG_TYPE_UINT \| 5-End--> |
| OH_HUKS_TAG_BLOCK_MODE = OH_HUKS_TAG_TYPE_UINT \| 6 | Encryption mode. For details, see [OH_Huks_CipherMode](capi-native-huks-type-h.md#oh_huks_ciphermode).<br><!--Device-OH_HUKS_TAG_BLOCK_MODE = OH_HUKS_TAG_TYPE_UINT \| 6--><!--Device-OH_HUKS_TAG_BLOCK_MODE = OH_HUKS_TAG_TYPE_UINT \| 6-End--> |
| OH_HUKS_TAG_KEY_TYPE = OH_HUKS_TAG_TYPE_UINT \| 7 | Key type.<br><!--Device-OH_HUKS_TAG_KEY_TYPE = OH_HUKS_TAG_TYPE_UINT \| 7--><!--Device-OH_HUKS_TAG_KEY_TYPE = OH_HUKS_TAG_TYPE_UINT \| 7-End--> |
| OH_HUKS_TAG_ASSOCIATED_DATA = OH_HUKS_TAG_TYPE_BYTES \| 8 | Associated authentication data.<br><!--Device-OH_HUKS_TAG_ASSOCIATED_DATA = OH_HUKS_TAG_TYPE_BYTES \| 8--><!--Device-OH_HUKS_TAG_ASSOCIATED_DATA = OH_HUKS_TAG_TYPE_BYTES \| 8-End--> |
| OH_HUKS_TAG_NONCE = OH_HUKS_TAG_TYPE_BYTES \| 9 | **NONCE** field for key encryption and decryption.<br><!--Device-OH_HUKS_TAG_NONCE = OH_HUKS_TAG_TYPE_BYTES \| 9--><!--Device-OH_HUKS_TAG_NONCE = OH_HUKS_TAG_TYPE_BYTES \| 9-End--> |
| OH_HUKS_TAG_IV = OH_HUKS_TAG_TYPE_BYTES \| 10 | Initialized vector (IV).<br><!--Device-OH_HUKS_TAG_IV = OH_HUKS_TAG_TYPE_BYTES \| 10--><!--Device-OH_HUKS_TAG_IV = OH_HUKS_TAG_TYPE_BYTES \| 10-End--> |
| OH_HUKS_TAG_INFO = OH_HUKS_TAG_TYPE_BYTES \| 11 | Information generated during key derivation.<br><!--Device-OH_HUKS_TAG_INFO = OH_HUKS_TAG_TYPE_BYTES \| 11--><!--Device-OH_HUKS_TAG_INFO = OH_HUKS_TAG_TYPE_BYTES \| 11-End--> |
| OH_HUKS_TAG_SALT = OH_HUKS_TAG_TYPE_BYTES \| 12 | Salt value used for key derivation.<br><!--Device-OH_HUKS_TAG_SALT = OH_HUKS_TAG_TYPE_BYTES \| 12--><!--Device-OH_HUKS_TAG_SALT = OH_HUKS_TAG_TYPE_BYTES \| 12-End--> |
| OH_HUKS_TAG_ITERATION = OH_HUKS_TAG_TYPE_UINT \| 14 | Number of iterations for key derivation.<br><!--Device-OH_HUKS_TAG_ITERATION = OH_HUKS_TAG_TYPE_UINT \| 14--><!--Device-OH_HUKS_TAG_ITERATION = OH_HUKS_TAG_TYPE_UINT \| 14-End--> |
| OH_HUKS_TAG_KEY_GENERATE_TYPE = OH_HUKS_TAG_TYPE_UINT \| 15 | Type of the generated key. For details, see [OH_Huks_KeyGenerateType](capi-native-huks-type-h.md#oh_huks_keygeneratetype).<br><!--Device-OH_HUKS_TAG_KEY_GENERATE_TYPE = OH_HUKS_TAG_TYPE_UINT \| 15--><!--Device-OH_HUKS_TAG_KEY_GENERATE_TYPE = OH_HUKS_TAG_TYPE_UINT \| 15-End--> |
| OH_HUKS_TAG_AGREE_ALG = OH_HUKS_TAG_TYPE_UINT \| 19 | Algorithm used in key agreement.<br><!--Device-OH_HUKS_TAG_AGREE_ALG = OH_HUKS_TAG_TYPE_UINT \| 19--><!--Device-OH_HUKS_TAG_AGREE_ALG = OH_HUKS_TAG_TYPE_UINT \| 19-End--> |
| OH_HUKS_TAG_AGREE_PUBLIC_KEY_IS_KEY_ALIAS = OH_HUKS_TAG_TYPE_BOOL \| 20 | Alias of the public key used for key agreement.<br><!--Device-OH_HUKS_TAG_AGREE_PUBLIC_KEY_IS_KEY_ALIAS = OH_HUKS_TAG_TYPE_BOOL \| 20--><!--Device-OH_HUKS_TAG_AGREE_PUBLIC_KEY_IS_KEY_ALIAS = OH_HUKS_TAG_TYPE_BOOL \| 20-End--> |
| OH_HUKS_TAG_AGREE_PRIVATE_KEY_ALIAS = OH_HUKS_TAG_TYPE_BYTES \| 21 | Alias of the private key used for key agreement.<br><!--Device-OH_HUKS_TAG_AGREE_PRIVATE_KEY_ALIAS = OH_HUKS_TAG_TYPE_BYTES \| 21--><!--Device-OH_HUKS_TAG_AGREE_PRIVATE_KEY_ALIAS = OH_HUKS_TAG_TYPE_BYTES \| 21-End--> |
| OH_HUKS_TAG_AGREE_PUBLIC_KEY = OH_HUKS_TAG_TYPE_BYTES \| 22 | Public key used for key agreement.<br><!--Device-OH_HUKS_TAG_AGREE_PUBLIC_KEY = OH_HUKS_TAG_TYPE_BYTES \| 22--><!--Device-OH_HUKS_TAG_AGREE_PUBLIC_KEY = OH_HUKS_TAG_TYPE_BYTES \| 22-End--> |
| OH_HUKS_TAG_KEY_ALIAS = OH_HUKS_TAG_TYPE_BYTES \| 23 | Key alias.<br><!--Device-OH_HUKS_TAG_KEY_ALIAS = OH_HUKS_TAG_TYPE_BYTES \| 23--><!--Device-OH_HUKS_TAG_KEY_ALIAS = OH_HUKS_TAG_TYPE_BYTES \| 23-End--> |
| OH_HUKS_TAG_DERIVE_KEY_SIZE = OH_HUKS_TAG_TYPE_UINT \| 24 | Size of the derived key, in bytes.<br><!--Device-OH_HUKS_TAG_DERIVE_KEY_SIZE = OH_HUKS_TAG_TYPE_UINT \| 24--><!--Device-OH_HUKS_TAG_DERIVE_KEY_SIZE = OH_HUKS_TAG_TYPE_UINT \| 24-End--> |
| OH_HUKS_TAG_IMPORT_KEY_TYPE = OH_HUKS_TAG_TYPE_UINT \| 25 | Type of the imported key. For details, see [OH_Huks_ImportKeyType](capi-native-huks-type-h.md#oh_huks_importkeytype).<br><!--Device-OH_HUKS_TAG_IMPORT_KEY_TYPE = OH_HUKS_TAG_TYPE_UINT \| 25--><!--Device-OH_HUKS_TAG_IMPORT_KEY_TYPE = OH_HUKS_TAG_TYPE_UINT \| 25-End--> |
| OH_HUKS_TAG_UNWRAP_ALGORITHM_SUITE = OH_HUKS_TAG_TYPE_UINT \| 26 | Suite of the imported encryption key. For details, see [OH_Huks_AlgSuite](capi-native-huks-type-h.md#oh_huks_algsuite).<br><!--Device-OH_HUKS_TAG_UNWRAP_ALGORITHM_SUITE = OH_HUKS_TAG_TYPE_UINT \| 26--><!--Device-OH_HUKS_TAG_UNWRAP_ALGORITHM_SUITE = OH_HUKS_TAG_TYPE_UINT \| 26-End--> |
| OH_HUKS_TAG_DERIVED_AGREED_KEY_STORAGE_FLAG = OH_HUKS_TAG_TYPE_UINT \| 29 | Storage type of the derived key or key produced after key agreement. For details, see [OH_Huks_KeyStorageType](capi-native-huks-type-h.md#oh_huks_keystoragetype).<br><!--Device-OH_HUKS_TAG_DERIVED_AGREED_KEY_STORAGE_FLAG = OH_HUKS_TAG_TYPE_UINT \| 29--><!--Device-OH_HUKS_TAG_DERIVED_AGREED_KEY_STORAGE_FLAG = OH_HUKS_TAG_TYPE_UINT \| 29-End--> |
| OH_HUKS_TAG_RSA_PSS_SALT_LEN_TYPE = OH_HUKS_TAG_TYPE_UINT \| 30 | Salt length type when the padding mode of the RSA algorithm is PSS. For details, see [OH_Huks_RsaPssSaltLenType](capi-native-huks-type-h.md#oh_huks_rsapsssaltlentype).<br><!--Device-OH_HUKS_TAG_RSA_PSS_SALT_LEN_TYPE = OH_HUKS_TAG_TYPE_UINT \| 30--><!--Device-OH_HUKS_TAG_RSA_PSS_SALT_LEN_TYPE = OH_HUKS_TAG_TYPE_UINT \| 30-End--> |
| OH_HUKS_TAG_ALL_USERS = OH_HUKS_TAG_TYPE_BOOL \| 301 | All users in the multi-user scenario.<br><!--Device-OH_HUKS_TAG_ALL_USERS = OH_HUKS_TAG_TYPE_BOOL \| 301--><!--Device-OH_HUKS_TAG_ALL_USERS = OH_HUKS_TAG_TYPE_BOOL \| 301-End--> |
| OH_HUKS_TAG_USER_ID = OH_HUKS_TAG_TYPE_UINT \| 302 | Multi-user ID.<br><!--Device-OH_HUKS_TAG_USER_ID = OH_HUKS_TAG_TYPE_UINT \| 302--><!--Device-OH_HUKS_TAG_USER_ID = OH_HUKS_TAG_TYPE_UINT \| 302-End--> |
| OH_HUKS_TAG_NO_AUTH_REQUIRED = OH_HUKS_TAG_TYPE_BOOL \| 303 | Whether key access control is required.<br><!--Device-OH_HUKS_TAG_NO_AUTH_REQUIRED = OH_HUKS_TAG_TYPE_BOOL \| 303--><!--Device-OH_HUKS_TAG_NO_AUTH_REQUIRED = OH_HUKS_TAG_TYPE_BOOL \| 303-End--> |
| OH_HUKS_TAG_USER_AUTH_TYPE = OH_HUKS_TAG_TYPE_UINT \| 304 | User authentication mode in key access control. For details, see [OH_Huks_UserAuthType](capi-native-huks-type-h.md#oh_huks_userauthtype).<br><!--Device-OH_HUKS_TAG_USER_AUTH_TYPE = OH_HUKS_TAG_TYPE_UINT \| 304--><!--Device-OH_HUKS_TAG_USER_AUTH_TYPE = OH_HUKS_TAG_TYPE_UINT \| 304-End--> |
| OH_HUKS_TAG_AUTH_TIMEOUT = OH_HUKS_TAG_TYPE_UINT \| 305 | Timeout duration for key access in key access control, in seconds.<br><!--Device-OH_HUKS_TAG_AUTH_TIMEOUT = OH_HUKS_TAG_TYPE_UINT \| 305--><!--Device-OH_HUKS_TAG_AUTH_TIMEOUT = OH_HUKS_TAG_TYPE_UINT \| 305-End--> |
| OH_HUKS_TAG_AUTH_TOKEN = OH_HUKS_TAG_TYPE_BYTES \| 306 | Authentication token for the key.<br><!--Device-OH_HUKS_TAG_AUTH_TOKEN = OH_HUKS_TAG_TYPE_BYTES \| 306--><!--Device-OH_HUKS_TAG_AUTH_TOKEN = OH_HUKS_TAG_TYPE_BYTES \| 306-End--> |
| OH_HUKS_TAG_KEY_AUTH_ACCESS_TYPE = OH_HUKS_TAG_TYPE_UINT \| 307 | Key access control type, which must be set together with the user authentication type. For details, see [OH_Huks_AuthAccessType](capi-native-huks-type-h.md#oh_huks_authaccesstype).<br><!--Device-OH_HUKS_TAG_KEY_AUTH_ACCESS_TYPE = OH_HUKS_TAG_TYPE_UINT \| 307--><!--Device-OH_HUKS_TAG_KEY_AUTH_ACCESS_TYPE = OH_HUKS_TAG_TYPE_UINT \| 307-End--> |
| OH_HUKS_TAG_KEY_SECURE_SIGN_TYPE = OH_HUKS_TAG_TYPE_UINT \| 308 | Signature type of the key generated or imported.<br><!--Device-OH_HUKS_TAG_KEY_SECURE_SIGN_TYPE = OH_HUKS_TAG_TYPE_UINT \| 308--><!--Device-OH_HUKS_TAG_KEY_SECURE_SIGN_TYPE = OH_HUKS_TAG_TYPE_UINT \| 308-End--> |
| OH_HUKS_TAG_CHALLENGE_TYPE = OH_HUKS_TAG_TYPE_UINT \| 309 | Challenge type. For details, see [OH_Huks_ChallengeType](capi-native-huks-type-h.md#oh_huks_challengetype).<br><!--Device-OH_HUKS_TAG_CHALLENGE_TYPE = OH_HUKS_TAG_TYPE_UINT \| 309--><!--Device-OH_HUKS_TAG_CHALLENGE_TYPE = OH_HUKS_TAG_TYPE_UINT \| 309-End--> |
| OH_HUKS_TAG_CHALLENGE_POS = OH_HUKS_TAG_TYPE_UINT \| 310 | Position of the 8-byte valid value in a custom challenge. For details, see [OH_Huks_ChallengePosition](capi-native-huks-type-h.md#oh_huks_challengeposition).<br><!--Device-OH_HUKS_TAG_CHALLENGE_POS = OH_HUKS_TAG_TYPE_UINT \| 310--><!--Device-OH_HUKS_TAG_CHALLENGE_POS = OH_HUKS_TAG_TYPE_UINT \| 310-End--> |
| OH_HUKS_TAG_KEY_AUTH_PURPOSE = OH_HUKS_TAG_TYPE_UINT \| 311 | Type of the key authentication purpose.<br><!--Device-OH_HUKS_TAG_KEY_AUTH_PURPOSE = OH_HUKS_TAG_TYPE_UINT \| 311--><!--Device-OH_HUKS_TAG_KEY_AUTH_PURPOSE = OH_HUKS_TAG_TYPE_UINT \| 311-End--> |
| OH_HUKS_TAG_AUTH_STORAGE_LEVEL = OH_HUKS_TAG_TYPE_UINT \| 316 | Security levels for storing the key. For details, see [OH_Huks_AuthStorageLevel](capi-native-huks-type-h.md#oh_huks_authstoragelevel).<br>**Since**: 11<br><!--Device-OH_HUKS_TAG_AUTH_STORAGE_LEVEL = OH_HUKS_TAG_TYPE_UINT \| 316--><!--Device-OH_HUKS_TAG_AUTH_STORAGE_LEVEL = OH_HUKS_TAG_TYPE_UINT \| 316-End--> |
| OH_HUKS_TAG_USER_AUTH_MODE = OH_HUKS_TAG_TYPE_UINT \| 319 | User authentication mode in key access control. For details, see [OH_Huks_UserAuthMode](capi-native-huks-type-h.md#oh_huks_userauthmode).<br>**Since**: 12<br><!--Device-OH_HUKS_TAG_USER_AUTH_MODE = OH_HUKS_TAG_TYPE_UINT \| 319--><!--Device-OH_HUKS_TAG_USER_AUTH_MODE = OH_HUKS_TAG_TYPE_UINT \| 319-End--> |
| OH_HUKS_TAG_ATTESTATION_CHALLENGE = OH_HUKS_TAG_TYPE_BYTES \| 501 | Challenge value used in the attestation.<br><!--Device-OH_HUKS_TAG_ATTESTATION_CHALLENGE = OH_HUKS_TAG_TYPE_BYTES \| 501--><!--Device-OH_HUKS_TAG_ATTESTATION_CHALLENGE = OH_HUKS_TAG_TYPE_BYTES \| 501-End--> |
| OH_HUKS_TAG_ATTESTATION_APPLICATION_ID = OH_HUKS_TAG_TYPE_BYTES \| 502 | ID of the application that has the key during key authentication.<br><!--Device-OH_HUKS_TAG_ATTESTATION_APPLICATION_ID = OH_HUKS_TAG_TYPE_BYTES \| 502--><!--Device-OH_HUKS_TAG_ATTESTATION_APPLICATION_ID = OH_HUKS_TAG_TYPE_BYTES \| 502-End--> |
| OH_HUKS_TAG_ATTESTATION_ID_ALIAS = OH_HUKS_TAG_TYPE_BYTES \| 511 | Key alias.<br><!--Device-OH_HUKS_TAG_ATTESTATION_ID_ALIAS = OH_HUKS_TAG_TYPE_BYTES \| 511--><!--Device-OH_HUKS_TAG_ATTESTATION_ID_ALIAS = OH_HUKS_TAG_TYPE_BYTES \| 511-End--> |
| OH_HUKS_TAG_ATTESTATION_ID_SEC_LEVEL_INFO = OH_HUKS_TAG_TYPE_BYTES \| 514 | Security level used in key attestation.<br><!--Device-OH_HUKS_TAG_ATTESTATION_ID_SEC_LEVEL_INFO = OH_HUKS_TAG_TYPE_BYTES \| 514--><!--Device-OH_HUKS_TAG_ATTESTATION_ID_SEC_LEVEL_INFO = OH_HUKS_TAG_TYPE_BYTES \| 514-End--> |
| OH_HUKS_TAG_ATTESTATION_ID_VERSION_INFO = OH_HUKS_TAG_TYPE_BYTES \| 515 | Version information used in key attestation.<br><!--Device-OH_HUKS_TAG_ATTESTATION_ID_VERSION_INFO = OH_HUKS_TAG_TYPE_BYTES \| 515--><!--Device-OH_HUKS_TAG_ATTESTATION_ID_VERSION_INFO = OH_HUKS_TAG_TYPE_BYTES \| 515-End--> |
| OH_HUKS_TAG_KEY_OVERRIDE = OH_HUKS_TAG_TYPE_BOOL \| 520 | Whether to overwrite the key with the same name.<br>**Since**: 20<br><!--Device-OH_HUKS_TAG_KEY_OVERRIDE = OH_HUKS_TAG_TYPE_BOOL \| 520--><!--Device-OH_HUKS_TAG_KEY_OVERRIDE = OH_HUKS_TAG_TYPE_BOOL \| 520-End--> |
| OH_HUKS_TAG_AE_TAG_LEN = OH_HUKS_TAG_TYPE_UINT \| 521 | Length of the specified AEAD in CCM mode.<br>**Since**: 22<br><!--Device-OH_HUKS_TAG_AE_TAG_LEN = OH_HUKS_TAG_TYPE_UINT \| 521--><!--Device-OH_HUKS_TAG_AE_TAG_LEN = OH_HUKS_TAG_TYPE_UINT \| 521-End--> |
| OH_HUKS_TAG_KEY_CLASS = OH_HUKS_TAG_TYPE_UINT \| 522 | Key type, which is used to distinguish the key managed by HUKS on the device from the key stored in an external device.<br>**Since**: 22<br><!--Device-OH_HUKS_TAG_KEY_CLASS = OH_HUKS_TAG_TYPE_UINT \| 522--><!--Device-OH_HUKS_TAG_KEY_CLASS = OH_HUKS_TAG_TYPE_UINT \| 522-End--> |
| OH_HUKS_TAG_KEY_ACCESS_GROUP = OH_HUKS_TAG_TYPE_BYTES \| 523 | Group ID. Keys can be shared among the same group of developers with the same developer ID.<br>**Since**: 23<br><!--Device-OH_HUKS_TAG_KEY_ACCESS_GROUP = OH_HUKS_TAG_TYPE_BYTES \| 523--><!--Device-OH_HUKS_TAG_KEY_ACCESS_GROUP = OH_HUKS_TAG_TYPE_BYTES \| 523-End--> |
| OH_HUKS_TAG_TIMEOUT = OH_HUKS_TAG_TYPE_UINT \| 529 | Asynchronous timeout duration in seconds, customizable by business logic.<br>**Since**: 26.0.1<br><!--Device-OH_HUKS_TAG_TIMEOUT = OH_HUKS_TAG_TYPE_UINT \| 529--><!--Device-OH_HUKS_TAG_TIMEOUT = OH_HUKS_TAG_TYPE_UINT \| 529-End--> |
| OH_HUKS_TAG_IS_KEY_ALIAS = OH_HUKS_TAG_TYPE_BOOL \| 1001 | Whether it is a key alias.<br><!--Device-OH_HUKS_TAG_IS_KEY_ALIAS = OH_HUKS_TAG_TYPE_BOOL \| 1001--><!--Device-OH_HUKS_TAG_IS_KEY_ALIAS = OH_HUKS_TAG_TYPE_BOOL \| 1001-End--> |
| OH_HUKS_TAG_KEY_STORAGE_FLAG = OH_HUKS_TAG_TYPE_UINT \| 1002 | Key storage mode. For details, see [OH_Huks_KeyStorageType](capi-native-huks-type-h.md#oh_huks_keystoragetype).<br><!--Device-OH_HUKS_TAG_KEY_STORAGE_FLAG = OH_HUKS_TAG_TYPE_UINT \| 1002--><!--Device-OH_HUKS_TAG_KEY_STORAGE_FLAG = OH_HUKS_TAG_TYPE_UINT \| 1002-End--> |
| OH_HUKS_TAG_IS_ALLOWED_WRAP = OH_HUKS_TAG_TYPE_BOOL \| 1003 | Whether to allow the key to be wrapped.<br><!--Device-OH_HUKS_TAG_IS_ALLOWED_WRAP = OH_HUKS_TAG_TYPE_BOOL \| 1003--><!--Device-OH_HUKS_TAG_IS_ALLOWED_WRAP = OH_HUKS_TAG_TYPE_BOOL \| 1003-End--> |
| OH_HUKS_TAG_KEY_WRAP_TYPE = OH_HUKS_TAG_TYPE_UINT \| 1004 | Key wrap type.<br><!--Device-OH_HUKS_TAG_KEY_WRAP_TYPE = OH_HUKS_TAG_TYPE_UINT \| 1004--><!--Device-OH_HUKS_TAG_KEY_WRAP_TYPE = OH_HUKS_TAG_TYPE_UINT \| 1004-End--> |
| OH_HUKS_TAG_KEY_AUTH_ID = OH_HUKS_TAG_TYPE_BYTES \| 1005 | Authentication ID.<br><!--Device-OH_HUKS_TAG_KEY_AUTH_ID = OH_HUKS_TAG_TYPE_BYTES \| 1005--><!--Device-OH_HUKS_TAG_KEY_AUTH_ID = OH_HUKS_TAG_TYPE_BYTES \| 1005-End--> |
| OH_HUKS_TAG_KEY_ROLE = OH_HUKS_TAG_TYPE_UINT \| 1006 | Role of the key.<br><!--Device-OH_HUKS_TAG_KEY_ROLE = OH_HUKS_TAG_TYPE_UINT \| 1006--><!--Device-OH_HUKS_TAG_KEY_ROLE = OH_HUKS_TAG_TYPE_UINT \| 1006-End--> |
| OH_HUKS_TAG_KEY_FLAG = OH_HUKS_TAG_TYPE_UINT \| 1007 | Key flag. For details, see [OH_Huks_KeyFlag](capi-native-huks-type-h.md#oh_huks_keyflag).<br><!--Device-OH_HUKS_TAG_KEY_FLAG = OH_HUKS_TAG_TYPE_UINT \| 1007--><!--Device-OH_HUKS_TAG_KEY_FLAG = OH_HUKS_TAG_TYPE_UINT \| 1007-End--> |
| OH_HUKS_TAG_IS_ASYNCHRONIZED = OH_HUKS_TAG_TYPE_UINT \| 1008 | Whether the invocation is asynchronous.<br><!--Device-OH_HUKS_TAG_IS_ASYNCHRONIZED = OH_HUKS_TAG_TYPE_UINT \| 1008--><!--Device-OH_HUKS_TAG_IS_ASYNCHRONIZED = OH_HUKS_TAG_TYPE_UINT \| 1008-End--> |
| OH_HUKS_TAG_KEY_DOMAIN = OH_HUKS_TAG_TYPE_UINT \| 1011 | Key domain.<br><!--Device-OH_HUKS_TAG_KEY_DOMAIN = OH_HUKS_TAG_TYPE_UINT \| 1011--><!--Device-OH_HUKS_TAG_KEY_DOMAIN = OH_HUKS_TAG_TYPE_UINT \| 1011-End--> |
| OH_HUKS_TAG_IS_DEVICE_PASSWORD_SET = OH_HUKS_TAG_TYPE_BOOL \| 1012 | Whether the key is accessible only when the user sets a lock screen password.<br> **true** indicates that the key can be generated and used only when a password is set. **false** indicates that the key can be generated and used without setting a password.<br>**Since**: 11<br><!--Device-OH_HUKS_TAG_IS_DEVICE_PASSWORD_SET = OH_HUKS_TAG_TYPE_BOOL \| 1012--><!--Device-OH_HUKS_TAG_IS_DEVICE_PASSWORD_SET = OH_HUKS_TAG_TYPE_BOOL \| 1012-End--> |
| OH_HUKS_TAG_AE_TAG = OH_HUKS_TAG_TYPE_BYTES \| 10009 | AEAD in GCM mode.<br><!--Device-OH_HUKS_TAG_AE_TAG = OH_HUKS_TAG_TYPE_BYTES \| 10009--><!--Device-OH_HUKS_TAG_AE_TAG = OH_HUKS_TAG_TYPE_BYTES \| 10009-End--> |
| OH_HUKS_TAG_SYMMETRIC_KEY_DATA = OH_HUKS_TAG_TYPE_BYTES \| 20001 | Symmetric key data.<br><!--Device-OH_HUKS_TAG_SYMMETRIC_KEY_DATA = OH_HUKS_TAG_TYPE_BYTES \| 20001--><!--Device-OH_HUKS_TAG_SYMMETRIC_KEY_DATA = OH_HUKS_TAG_TYPE_BYTES \| 20001-End--> |
| OH_HUKS_TAG_ASYMMETRIC_PUBLIC_KEY_DATA = OH_HUKS_TAG_TYPE_BYTES \| 20002 | Public key data of the asymmetric key pair.<br><!--Device-OH_HUKS_TAG_ASYMMETRIC_PUBLIC_KEY_DATA = OH_HUKS_TAG_TYPE_BYTES \| 20002--><!--Device-OH_HUKS_TAG_ASYMMETRIC_PUBLIC_KEY_DATA = OH_HUKS_TAG_TYPE_BYTES \| 20002-End--> |
| OH_HUKS_TAG_ASYMMETRIC_PRIVATE_KEY_DATA = OH_HUKS_TAG_TYPE_BYTES \| 20003 | Private key data of the asymmetric key pair.<br><!--Device-OH_HUKS_TAG_ASYMMETRIC_PRIVATE_KEY_DATA = OH_HUKS_TAG_TYPE_BYTES \| 20003--><!--Device-OH_HUKS_TAG_ASYMMETRIC_PRIVATE_KEY_DATA = OH_HUKS_TAG_TYPE_BYTES \| 20003-End--> |


