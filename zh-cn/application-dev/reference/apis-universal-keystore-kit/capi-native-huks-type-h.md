# native_huks_type.h

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

## 概述

提供huks中的枚举变量、结构体定义与宏定义。

**引用文件：** <huks/native_huks_type.h>

**库：** libhuks_ndk.z.so

**系统能力：** SystemCapability.Security.Huks.Core

在API 9-19，系统能力为SystemCapability.Security.Huks；从API 20起，系统能力变更为SystemCapability.Security.Huks.Core

**起始版本：** 9

**相关模块：** [HuksTypeApi](capi-hukstypeapi.md)

## 汇总

### 结构体

| 名称 | 描述 |
| -- | -- |
| [OH_Huks_Result](capi-hukstypeapi-oh-huks-result.md) | 表示状态返回数据，包括返回码和消息。 |
| [OH_Huks_Blob](capi-hukstypeapi-oh-huks-blob.md) | 定义存放数据的结构体类型。 |
| [OH_Huks_Param](capi-hukstypeapi-oh-huks-param.md) | 定义参数集中的参数结构体类型。 |
| [OH_Huks_ParamSet](capi-hukstypeapi-oh-huks-paramset.md) | 定义参数集的结构体类型。 |
| [OH_Huks_CertChain](capi-hukstypeapi-oh-huks-certchain.md) | 定义证书链的结构体类型。 |
| [OH_Huks_KeyInfo](capi-hukstypeapi-oh-huks-keyinfo.md) | 定义密钥信息的结构体类型。 |
| [OH_Huks_PubKeyInfo](capi-hukstypeapi-oh-huks-pubkeyinfo.md) | 定义公钥信息的结构体类型。 |
| [OH_Huks_KeyMaterialRsa](capi-hukstypeapi-oh-huks-keymaterialrsa.md) | 定义Rsa密钥的结构体类型。 |
| [OH_Huks_KeyMaterialEcc](capi-hukstypeapi-oh-huks-keymaterialecc.md) | 定义Ecc密钥的结构体类型。 |
| [OH_Huks_KeyMaterialDsa](capi-hukstypeapi-oh-huks-keymaterialdsa.md) | 定义Dsa密钥的结构体类型。 |
| [OH_Huks_KeyMaterialDh](capi-hukstypeapi-oh-huks-keymaterialdh.md) | 定义Dh密钥的结构体类型。 |
| [OH_Huks_KeyMaterial25519](capi-hukstypeapi-oh-huks-keymaterial25519.md) | 定义25519类型密钥的结构体类型。 |
| [OH_Huks_KeyAliasSet](capi-hukstypeapi-oh-huks-keyaliasset.md) | 定义密钥别名集的结构体类型。 |

### 枚举

| 名称 | 描述 |
| -- | -- |
| [OH_Huks_KeyPurpose](#oh_huks_keypurpose) | 密钥用途类型。 |
| [OH_Huks_KeyDigest](#oh_huks_keydigest) | 摘要算法类型。 |
| [OH_Huks_KeyPadding](#oh_huks_keypadding) | 补齐算法类型。 |
| [OH_Huks_CipherMode](#oh_huks_ciphermode) | 加解密算法工作模式。 |
| [OH_Huks_KeySize](#oh_huks_keysize) | 算法密钥长度。 |
| [OH_Huks_KeyAlg](#oh_huks_keyalg) | 密钥使用的算法。 |
| [OH_Huks_AlgSuite](#oh_huks_algsuite) | 密文导入所需的算法套件类型。 |
| [OH_Huks_KeyGenerateType](#oh_huks_keygeneratetype) | 生成的密钥类型。 |
| [OH_Huks_KeyFlag](#oh_huks_keyflag) | 密钥的产生方式。 |
| [OH_Huks_KeyStorageType](#oh_huks_keystoragetype) | 密钥的存储方式。 |
| [OH_Huks_ImportKeyType](#oh_huks_importkeytype) | 导入密钥的类型，默认为导入公钥，导入对称密钥时不需要该字段。 |
| [OH_Huks_RsaPssSaltLenType](#oh_huks_rsapsssaltlentype) | 枚举密钥存储格式。 |
| [OH_Huks_ErrCode](#oh_huks_errcode) | 错误码。 |
| [OH_Huks_TagType](#oh_huks_tagtype) | 参数集中参数类型的掩码值。 |
| [OH_Huks_UserAuthType](#oh_huks_userauthtype) | 密钥访问控制中的用户认证类型。 |
| [OH_Huks_AuthAccessType](#oh_huks_authaccesstype) | 安全访问控制类型，表示密钥失效的原则。 |
| [OH_Huks_AuthStorageLevel](#oh_huks_authstoragelevel) | 表示生成或导入密钥时，指定该密钥的存储安全等级。 |
| [OH_Huks_ChallengeType](#oh_huks_challengetype) | 密钥使用时生成challenge的类型。 |
| [OH_Huks_UserAuthMode](#oh_huks_userauthmode) | 密钥访问控制中的用户认证模式。 |
| [OH_Huks_ChallengePosition](#oh_huks_challengeposition) | challenge类型为用户自定义类型时，生成的challenge有效长度仅为8字节连续的数据，且仅支持4种位置。 |
| [OH_Huks_SecureSignType](#oh_huks_securesigntype) | 生成或导入密钥时，指定该密钥的安全签名类型。 |
| [OH_Huks_KeyWrapType](#oh_huks_keywraptype) | 生成或导入密钥时，指定该密钥的封装类型。 |
| [OH_Huks_Tag](#oh_huks_tag) | 参数集所用的TAG值枚举。 |

## 枚举类型说明

### OH_Huks_KeyPurpose

```
enum OH_Huks_KeyPurpose
```

**描述**

密钥用途类型。

**起始版本：** 9

| 枚举项 | 描述 |
| -- | -- |
| OH_HUKS_KEY_PURPOSE_ENCRYPT = 1 | 表示密钥用于对明文进行加密操作。 |
| OH_HUKS_KEY_PURPOSE_DECRYPT = 2 | 表示密钥用于对密文进行解密操作。 |
| OH_HUKS_KEY_PURPOSE_SIGN = 4 | 表示密钥用于对数据进行签名。 |
| OH_HUKS_KEY_PURPOSE_VERIFY = 8 | 表示密钥用于验证签名后的数据。 |
| OH_HUKS_KEY_PURPOSE_DERIVE = 16 | 表示密钥用于派生密钥。 |
| OH_HUKS_KEY_PURPOSE_WRAP = 32 | 表示密钥用于加密导出。 |
| OH_HUKS_KEY_PURPOSE_UNWRAP = 64 | 表示密钥加密导入。 |
| OH_HUKS_KEY_PURPOSE_MAC = 128 | 表示密钥用于生成mac消息验证码。 |
| OH_HUKS_KEY_PURPOSE_AGREE = 256 | 表示密钥用于进行密钥协商。 |

### OH_Huks_KeyDigest

```
enum OH_Huks_KeyDigest
```

**描述**

摘要算法类型。

**起始版本：** 9

| 枚举项 | 描述 |
| -- | -- |
| OH_HUKS_DIGEST_NONE = 0 | 无摘要算法。 |
| OH_HUKS_DIGEST_MD5 = 1 | MD5摘要算法。 |
| OH_HUKS_DIGEST_SM3 = 2 | SM3摘要算法。 |
| OH_HUKS_DIGEST_SHA1 = 10 | SHA1摘要算法。 |
| OH_HUKS_DIGEST_SHA224 = 11 | SHA224摘要算法。 |
| OH_HUKS_DIGEST_SHA256 = 12 | SHA256摘要算法。 |
| OH_HUKS_DIGEST_SHA384 = 13 | SHA384摘要算法。 |
| OH_HUKS_DIGEST_SHA512 = 14 | SHA512摘要算法。 |

### OH_Huks_KeyPadding

```
enum OH_Huks_KeyPadding
```

**描述**

补齐算法类型。

**起始版本：** 9

| 枚举项 | 描述 |
| -- | -- |
| OH_HUKS_PADDING_NONE = 0 | 不使用补齐算法。 |
| OH_HUKS_PADDING_OAEP = 1 | 使用OAEP补齐算法。 |
| OH_HUKS_PADDING_PSS = 2 | 使用PSS补齐算法。 |
| OH_HUKS_PADDING_PKCS1_V1_5 = 3 | 使用PKCS1_V1_5补齐算法。 |
| OH_HUKS_PADDING_PKCS5 = 4 | 使用PKCS5补齐算法。 |
| OH_HUKS_PADDING_PKCS7 = 5 | 使用PKCS7补齐算法。 |
| OH_HUKS_PADDING_ISO_IEC_9796_2 = 6 | 使用ISO IEC 9796-2补齐算法。<br>**起始版本：** 18 |
| OH_HUKS_PADDING_ISO_IEC_9797_1 = 7 | 使用ISO IEC 9797-1补齐算法。<br>**起始版本：** 18 |

### OH_Huks_CipherMode

```
enum OH_Huks_CipherMode
```

**描述**

加解密算法工作模式。

**起始版本：** 9

| 枚举项 | 描述 |
| -- | -- |
| OH_HUKS_MODE_ECB = 1 | 使用ECB加密模式。 |
| OH_HUKS_MODE_CBC = 2 | 使用CBC加密模式。 |
| OH_HUKS_MODE_CTR = 3 | 使用CTR加密模式。 |
| OH_HUKS_MODE_OFB = 4 | 使用OFB加密模式。 |
| OH_HUKS_MODE_CFB = 5 | 使用CFB加密模式。<br>**起始版本：** 12 |
| OH_HUKS_MODE_CCM = 31 | 使用CCM加密模式。 |
| OH_HUKS_MODE_GCM = 32 | 使用GCM加密模式。 |

### OH_Huks_KeySize

```
enum OH_Huks_KeySize
```

**描述**

算法密钥长度。

**起始版本：** 9

| 枚举项 | 描述 |
| -- | -- |
| OH_HUKS_RSA_KEY_SIZE_512 = 512 | 使用RSA算法的密钥长度为512bit。 |
| OH_HUKS_RSA_KEY_SIZE_768 = 768 | 使用RSA算法的密钥长度为768bit。 |
| OH_HUKS_RSA_KEY_SIZE_1024 = 1024 | 使用RSA算法的密钥长度为1024bit。 |
| OH_HUKS_RSA_KEY_SIZE_2048 = 2048 | 使用RSA算法的密钥长度为2048bit。 |
| OH_HUKS_RSA_KEY_SIZE_3072 = 3072 | 使用RSA算法的密钥长度为3072bit。 |
| OH_HUKS_RSA_KEY_SIZE_4096 = 4096 | 使用RSA算法的密钥长度为4096bit。 |
| OH_HUKS_ECC_KEY_SIZE_224 = 224 | 使用ECC算法的密钥长度为224bit。 |
| OH_HUKS_ECC_KEY_SIZE_256 = 256 | 使用ECC算法的密钥长度为256bit。 |
| OH_HUKS_ECC_KEY_SIZE_384 = 384 | 使用ECC算法的密钥长度为384bit。 |
| OH_HUKS_ECC_KEY_SIZE_521 = 521 | 使用ECC算法的密钥长度为521bit。 |
| OH_HUKS_AES_KEY_SIZE_128 = 128 | 使用AES算法的密钥长度为128bit。 |
| OH_HUKS_AES_KEY_SIZE_192 = 192 | 使用AES算法的密钥长度为192bit。 |
| OH_HUKS_AES_KEY_SIZE_256 = 256 | 使用AES算法的密钥长度为256bit。 |
| OH_HUKS_AES_KEY_SIZE_512 = 512 | 使用AES算法的密钥长度为512bit。 |
| OH_HUKS_CURVE25519_KEY_SIZE_256 = 256 | 使用CURVE25519算法的密钥长度为256bit。 |
| OH_HUKS_DH_KEY_SIZE_2048 = 2048 | 使用DH算法的密钥长度为2048bit。 |
| OH_HUKS_DH_KEY_SIZE_3072 = 3072 | 使用DH算法的密钥长度为3072bit。 |
| OH_HUKS_DH_KEY_SIZE_4096 = 4096 | 使用DH算法的密钥长度为4096bit。 |
| OH_HUKS_SM2_KEY_SIZE_256 = 256 | 使用SM2算法的密钥长度为256bit。 |
| OH_HUKS_SM4_KEY_SIZE_128 = 128 | 使用SM4算法支持的密钥长度为128位。 |
| OH_HUKS_DES_KEY_SIZE_64 = 64 | 使用DES算法的密钥长度为64bit。<br>**起始版本：** 18 |
| OH_HUKS_3DES_KEY_SIZE_128 = 128 | 使用3DES算法的密钥长度为128bit。<br>**起始版本：** 18 |
| OH_HUKS_3DES_KEY_SIZE_192 = 192 | 使用3DES算法的密钥长度为192bit。<br>**起始版本：** 18 |

### OH_Huks_KeyAlg

```
enum OH_Huks_KeyAlg
```

**描述**

密钥使用的算法。

**起始版本：** 9

| 枚举项 | 描述 |
| -- | -- |
| OH_HUKS_ALG_RSA = 1 | 使用RSA算法。 |
| OH_HUKS_ALG_ECC = 2 | 使用ECC算法。 |
| OH_HUKS_ALG_DSA = 3 | 使用DSA算法。 |
| OH_HUKS_ALG_AES = 20 | 使用AES算法。 |
| OH_HUKS_ALG_HMAC = 50 | 使用HMAC算法。 |
| OH_HUKS_ALG_HKDF = 51 | 使用HKDF算法。 |
| OH_HUKS_ALG_PBKDF2 = 52 | 使用PBKDF2算法。 |
| OH_HUKS_ALG_ECDH = 100 | 使用ECDH算法。 |
| OH_HUKS_ALG_X25519 = 101 | 使用X25519算法。 |
| OH_HUKS_ALG_ED25519 = 102 | 使用ED25519算法。 |
| OH_HUKS_ALG_DH = 103 | 使用DH算法。 |
| OH_HUKS_ALG_SM2 = 150 | 使用SM2算法。 |
| OH_HUKS_ALG_SM3 = 151 | 使用SM3算法。 |
| OH_HUKS_ALG_SM4 = 152 | 使用SM4算法。 |
| OH_HUKS_ALG_DES = 160 | 使用DES算法。<br>**起始版本：** 18 |
| OH_HUKS_ALG_3DES = 161 | 使用3DES算法。<br>**起始版本：** 18 |
| OH_HUKS_ALG_CMAC = 162 | 使用CMAC算法。<br>**起始版本：** 18 |

### OH_Huks_AlgSuite

```
enum OH_Huks_AlgSuite
```

**描述**

密文导入所需的算法套件类型。

OH_HUKS_UNWRAP_SUITE_X25519_AES_256_GCM_NOPADDING对应的密钥材料格式：

```
| x25519_plain_pubkey_length  (4 Byte) | x25519_plain_pubkey |  agreekey_aad_length (4 Byte) | agreekey_aad
|   agreekey_nonce_length     (4 Byte) |   agreekey_nonce    | agreekey_aead_tag_len(4 Byte) | agreekey_aead_tag 
|    kek_enc_data_length      (4 Byte) |    kek_enc_data     |    kek_aad_length    (4 Byte) | kek_aad     
|      kek_nonce_length       (4 Byte) |      kek_nonce      |   kek_aead_tag_len   (4 Byte) | kek_aead_tag
|   key_material_size_len     (4 Byte) |  key_material_size  |   key_mat_enc_length (4 Byte) | key_mat_enc_data
```

OH_HUKS_UNWRAP_SUITE_ECDH_AES_256_GCM_NOPADDING对应的密钥材料格式：
```
|  ECC_plain_pubkey_length    (4 Byte) |  ECC_plain_pubkey   |  agreekey_aad_length (4 Byte) | agreekey_aad
|   agreekey_nonce_length     (4 Byte) |   agreekey_nonce    | agreekey_aead_tag_len(4 Byte) | agreekey_aead_tag
|    kek_enc_data_length      (4 Byte) |    kek_enc_data     |    kek_aad_length    (4 Byte) | kek_aad 
|      kek_nonce_length       (4 Byte) |      kek_nonce      |   kek_aead_tag_len   (4 Byte) | kek_aead_tag 
|   key_material_size_len     (4 Byte) |  key_material_size  |   key_mat_enc_length (4 Byte) | key_mat_enc_data
```

**起始版本：** 9

| 枚举项 | 描述 |
| -- | -- |
| OH_HUKS_UNWRAP_SUITE_X25519_AES_256_GCM_NOPADDING = 1 | 密文导入密钥材料格式（Length-Value格式）采用X25519密钥协商同时采用AES-256-GCM加解密。具体材料格式见上方枚举描述。 |
| OH_HUKS_UNWRAP_SUITE_ECDH_AES_256_GCM_NOPADDING = 2 | 密文导入密钥材料格式（Length-Value格式）采用ECDH-p256密钥协商同时采用AES-256-GCM加解密。具体材料格式见上方枚举描述。 |

### OH_Huks_KeyGenerateType

```
enum OH_Huks_KeyGenerateType
```

**描述**

生成的密钥类型。

**起始版本：** 9

| 枚举项 | 描述 |
| -- | -- |
| OH_HUKS_KEY_GENERATE_TYPE_DEFAULT = 0 | 默认生成的密钥。 |
| OH_HUKS_KEY_GENERATE_TYPE_DERIVE = 1 | 派生生成的密钥。 |
| OH_HUKS_KEY_GENERATE_TYPE_AGREE = 2 | 协商生成的密钥。 |

### OH_Huks_KeyFlag

```
enum OH_Huks_KeyFlag
```

**描述**

密钥的产生方式。

**起始版本：** 9

| 枚举项 | 描述 |
| -- | -- |
| OH_HUKS_KEY_FLAG_IMPORT_KEY = 1 | 通过导入公钥接口导入的密钥。 |
| OH_HUKS_KEY_FLAG_GENERATE_KEY = 2 | 通过生成密钥接口生成的密钥。 |
| OH_HUKS_KEY_FLAG_AGREE_KEY = 3 | 通过生成密钥协商接口生成的密钥。 |
| OH_HUKS_KEY_FLAG_DERIVE_KEY = 4 | 通过生成密钥派生接口生成的密钥。 |

### OH_Huks_KeyStorageType

```
enum OH_Huks_KeyStorageType
```

**描述**

密钥的存储方式。

**起始版本：** 9

| 枚举项 | 描述 |
| -- | -- |
| OH_HUKS_STORAGE_TEMP = 0 | 通过接口返回给业务。 |
| OH_HUKS_STORAGE_PERSISTENT = 1 | 密钥托管在HUKS中。 |
| OH_HUKS_STORAGE_ONLY_USED_IN_HUKS = 2 | 在进行密钥派生或协商时，结果密钥托管在HUKS中。 |
| OH_HUKS_STORAGE_KEY_EXPORT_ALLOWED = 3 | 在进行密钥派生或协商时，结果密钥可以返回给业务。 |

### OH_Huks_ImportKeyType

```
enum OH_Huks_ImportKeyType
```

**描述**

导入密钥的类型，默认为导入公钥，导入对称密钥时不需要该字段。

**起始版本：** 9

| 枚举项 | 描述 |
| -- | -- |
| OH_HUKS_KEY_TYPE_PUBLIC_KEY = 0 | 导入的密钥类型为公钥。 |
| OH_HUKS_KEY_TYPE_PRIVATE_KEY = 1 | 导入的密钥类型为私钥。 |
| OH_HUKS_KEY_TYPE_KEY_PAIR = 2 | 导入的密钥类型为公私钥对。 |

### OH_Huks_RsaPssSaltLenType

```
enum OH_Huks_RsaPssSaltLenType
```

**描述**

枚举密钥存储格式。

**起始版本：** 10

| 枚举项 | 描述 |
| -- | -- |
| OH_HUKS_RSA_PSS_SALT_LEN_DIGEST = 0 | 以摘要长度设置盐值长度。 |
| OH_HUKS_RSA_PSS_SALT_LEN_MAX = 1 | 以最大长度设置盐值长度。 |

### OH_Huks_ErrCode

```
enum OH_Huks_ErrCode
```

**描述**

错误码。

**起始版本：** 9

| 枚举项 | 描述 |
| -- | -- |
| OH_HUKS_SUCCESS = 0 | 成功。 |
| OH_HUKS_ERR_CODE_PERMISSION_FAIL = 201 | 权限校验失败。 |
| OH_HUKS_ERR_CODE_ILLEGAL_ARGUMENT = 401 | 非法参数（通用）。 |
| OH_HUKS_ERR_CODE_NOT_SUPPORTED_API = 801 | 不支持该API。 |
| OH_HUKS_ERR_CODE_FEATURE_NOT_SUPPORTED = 12000001 | 不支持该子功能（特性）。 |
| OH_HUKS_ERR_CODE_MISSING_CRYPTO_ALG_ARGUMENT = 12000002 | 缺少密钥算法参数。 |
| OH_HUKS_ERR_CODE_INVALID_CRYPTO_ALG_ARGUMENT = 12000003 | 无效的密钥算法参数。 |
| OH_HUKS_ERR_CODE_FILE_OPERATION_FAIL = 12000004 | 文件错误。 |
| OH_HUKS_ERR_CODE_COMMUNICATION_FAIL = 12000005 | 进程通信错误。 |
| OH_HUKS_ERR_CODE_CRYPTO_FAIL = 12000006 | 算法库操作失败。 |
| OH_HUKS_ERR_CODE_KEY_AUTH_PERMANENTLY_INVALIDATED = 12000007 | 密钥访问失败 - 密钥已失效。 |
| OH_HUKS_ERR_CODE_KEY_AUTH_VERIFY_FAILED = 12000008 | 密钥访问失败 - 密钥认证失败。 |
| OH_HUKS_ERR_CODE_KEY_AUTH_TIME_OUT = 12000009 | 密钥访问失败 - 密钥访问超时。 |
| OH_HUKS_ERR_CODE_SESSION_LIMIT = 12000010 | 密钥操作会话数已达上限。 |
| OH_HUKS_ERR_CODE_ITEM_NOT_EXIST = 12000011 | 该项实体不存在。 |
| OH_HUKS_ERR_CODE_INTERNAL_ERROR = 12000012 | 内部错误。 |
| OH_HUKS_ERR_CODE_CREDENTIAL_NOT_EXIST = 12000013 | 认证凭据不存在。 |
| OH_HUKS_ERR_CODE_INSUFFICIENT_MEMORY = 12000014 | 内存不足。 |
| OH_HUKS_ERR_CODE_CALL_SERVICE_FAILED = 12000015 | 调用服务失败。 |
| OH_HUKS_ERR_CODE_DEVICE_PASSWORD_UNSET = 12000016 | 需要锁屏密码，但没有设置。<br>**起始版本：** 11 |
| OH_HUKS_ERR_CODE_KEY_ALREADY_EXIST = 12000017 | 同名密钥已存在。<br>**起始版本：** 20 |
| OH_HUKS_ERR_CODE_INVALID_ARGUMENT = 12000018 | 输入的参数无效。<br>**起始版本：** 20 |

### OH_Huks_TagType

```
enum OH_Huks_TagType
```

**描述**

参数集中参数类型的掩码值。

**起始版本：** 9

| 枚举项 | 描述 |
| -- | -- |
| OH_HUKS_TAG_TYPE_INVALID = 0 << 28 | 非法的Tag类型。 |
| OH_HUKS_TAG_TYPE_INT = 1 << 28 | 该Tag的数据类型为int32_t类型。 |
| OH_HUKS_TAG_TYPE_UINT = 2 << 28 | 该Tag的数据类型为uin32_t类型。 |
| OH_HUKS_TAG_TYPE_ULONG = 3 << 28 | 该Tag的数据类型为uin64_t类型。 |
| OH_HUKS_TAG_TYPE_BOOL = 4 << 28 | 该Tag的数据类型为bool类型。 |
| OH_HUKS_TAG_TYPE_BYTES = 5 << 28 | 该Tag的数据类型为[OH_Huks_Blob](capi-hukstypeapi-oh-huks-blob.md)类型。 |

### OH_Huks_UserAuthType

```
enum OH_Huks_UserAuthType
```

**描述**

密钥访问控制中的用户认证类型。

**起始版本：** 9

| 枚举项 | 描述 |
| -- | -- |
| OH_HUKS_USER_AUTH_TYPE_FINGERPRINT = 1 << 0 | 用户认证类型为指纹。 |
| OH_HUKS_USER_AUTH_TYPE_FACE = 1 << 1 | 用户认证类型为人脸。 |
| OH_HUKS_USER_AUTH_TYPE_PIN = 1 << 2 | 用户认证类型为PIN码。 |
| OH_HUKS_USER_AUTH_TYPE_TUI_PIN = 1 << 5 | 用户认证类型为TUI PIN码。<br>**起始版本：** 20 |

### OH_Huks_AuthAccessType

```
enum OH_Huks_AuthAccessType
```

**描述**

安全访问控制类型，表示密钥失效的原则。

**起始版本：** 9

| 枚举项 | 描述 |
| -- | -- |
| OH_HUKS_AUTH_ACCESS_INVALID_CLEAR_PASSWORD = 1 << 0 | 安全访问控制类型为清除密码后密钥无效。 |
| OH_HUKS_AUTH_ACCESS_INVALID_NEW_BIO_ENROLL = 1 << 1 | 安全访问控制类型为新录入生物特征后密钥无效。 |
| OH_HUKS_AUTH_ACCESS_ALWAYS_VALID = 1 << 2 | 安全访问控制类型为该密钥总是有效。<br>**起始版本：** 11 |

### OH_Huks_AuthStorageLevel

```
enum OH_Huks_AuthStorageLevel
```

**描述**

表示生成或导入密钥时，指定该密钥的存储安全等级。

**起始版本：** 11

| 枚举项 | 描述 |
| -- | -- |
| OH_HUKS_AUTH_STORAGE_LEVEL_DE = 0 | 表示密钥仅在开机后可访问。 |
| OH_HUKS_AUTH_STORAGE_LEVEL_CE = 1 | 表示密钥仅在首次解锁后可访问。 |
| OH_HUKS_AUTH_STORAGE_LEVEL_ECE = 2 | 表示密钥仅在解锁状态时可访问。 |

### OH_Huks_ChallengeType

```
enum OH_Huks_ChallengeType
```

**描述**

密钥使用时生成challenge的类型。

**起始版本：** 9

| 枚举项 | 描述 |
| -- | -- |
| OH_HUKS_CHALLENGE_TYPE_NORMAL = 0 | challenge为普通类型，默认32字节。 |
| OH_HUKS_CHALLENGE_TYPE_CUSTOM = 1 | challenge为用户自定义类型。支持使用多个密钥仅一次认证，challenge长度8字节有效。 |
| OH_HUKS_CHALLENGE_TYPE_NONE = 2 | 免challenge类型。 |

### OH_Huks_UserAuthMode

```
enum OH_Huks_UserAuthMode
```

**描述**

密钥访问控制中的用户认证模式。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| OH_HUKS_USER_AUTH_MODE_LOCAL = 0 | 本地认证模式。 |
| OH_HUKS_USER_AUTH_MODE_COAUTH = 1 | 跨端协同认证模式。 |

### OH_Huks_ChallengePosition

```
enum OH_Huks_ChallengePosition
```

**描述**

challenge类型为用户自定义类型时，生成的challenge有效长度仅为8字节连续的数据，且仅支持4种位置。

**起始版本：** 9

| 枚举项 | 描述 |
| -- | -- |
| OH_HUKS_CHALLENGE_POS_0 = 0 | 0~7字节为当前密钥的有效challenge。 |
| OH_HUKS_CHALLENGE_POS_1 | 8~15字节为当前密钥的有效challenge。 |
| OH_HUKS_CHALLENGE_POS_2 | 16~23字节为当前密钥的有效challenge。 |
| OH_HUKS_CHALLENGE_POS_3 | 24~31字节为当前密钥的有效challenge。 |

### OH_Huks_SecureSignType

```
enum OH_Huks_SecureSignType
```

**描述**

生成或导入密钥时，指定该密钥的安全签名类型。

**起始版本：** 9

| 枚举项 | 描述 |
| -- | -- |
| OH_HUKS_SECURE_SIGN_WITH_AUTHINFO = 1 | 签名类型为携带认证信息。生成或导入密钥时指定该字段，则在使用密钥进行签名时，对待签名的数据添加认证信息后进行签名。<br>**注意**：携带的认证信息包含身份信息，开发者需在其隐私声明中对此身份信息的使用目的、存留策略和销毁方式进行说明。 |

### OH_Huks_KeyWrapType

```
enum OH_Huks_KeyWrapType
```

**描述**

生成或导入密钥时，指定该密钥的封装类型。

**起始版本：** 20

| 枚举项 | 描述 |
| -- | -- |
| OH_HUKS_KEY_WRAP_TYPE_HUK_BASED = 2 | 硬件唯一密钥的封装类型。 |

### OH_Huks_Tag

```
enum OH_Huks_Tag
```

**描述**

参数集所用的TAG值枚举。<br> 1-200：密钥参数标签值。<br> 301-500：密钥使用访问控制和使用认证相关的标签值。<br> 501-600：密钥认证相关的标签值。<br> 601-1000：其他类型的标签值预留值。<br> 1001-9999：扩展标签值。<br> 11000-12000：预留值。<br> 20001-N：其他标签预留值。

**起始版本：** 9

| 枚举项 | 描述 |
| -- | -- |
| OH_HUKS_TAG_ALGORITHM = OH_HUKS_TAG_TYPE_UINT \| 1 | 算法类型。 |
| OH_HUKS_TAG_PURPOSE = OH_HUKS_TAG_TYPE_UINT \| 2 | 密钥用途。 |
| OH_HUKS_TAG_KEY_SIZE = OH_HUKS_TAG_TYPE_UINT \| 3 | 密钥长度 。 |
| OH_HUKS_TAG_DIGEST = OH_HUKS_TAG_TYPE_UINT \| 4 | 摘要算法。 |
| OH_HUKS_TAG_PADDING = OH_HUKS_TAG_TYPE_UINT \| 5 | 补齐算法。 |
| OH_HUKS_TAG_BLOCK_MODE = OH_HUKS_TAG_TYPE_UINT \| 6 | 加密模式。 |
| OH_HUKS_TAG_KEY_TYPE = OH_HUKS_TAG_TYPE_UINT \| 7 | 密钥类型。 |
| OH_HUKS_TAG_ASSOCIATED_DATA = OH_HUKS_TAG_TYPE_BYTES \| 8 | 附加身份验证数据。 |
| OH_HUKS_TAG_NONCE = OH_HUKS_TAG_TYPE_BYTES \| 9 | 密钥加解密的字段。 |
| OH_HUKS_TAG_IV = OH_HUKS_TAG_TYPE_BYTES \| 10 | 初始化的向量。 |
| OH_HUKS_TAG_INFO = OH_HUKS_TAG_TYPE_BYTES \| 11 | 密钥派生时的信息。 |
| OH_HUKS_TAG_SALT = OH_HUKS_TAG_TYPE_BYTES \| 12 | 派生盐值。 |
| OH_HUKS_TAG_ITERATION = OH_HUKS_TAG_TYPE_UINT \| 14 | 派生迭代次数。 |
| OH_HUKS_TAG_KEY_GENERATE_TYPE = OH_HUKS_TAG_TYPE_UINT \| 15 | 生成密钥的类型，类型可在枚举[OH_Huks_KeyGenerateType](#oh_huks_keygeneratetype)中选择。 |
| OH_HUKS_TAG_AGREE_ALG = OH_HUKS_TAG_TYPE_UINT \| 19 | 密钥协商时的算法类型。 |
| OH_HUKS_TAG_AGREE_PUBLIC_KEY_IS_KEY_ALIAS = OH_HUKS_TAG_TYPE_BOOL \| 20 | 密钥协商时的公钥别名。 |
| OH_HUKS_TAG_AGREE_PRIVATE_KEY_ALIAS = OH_HUKS_TAG_TYPE_BYTES \| 21 | 密钥协商时的私钥别名。 |
| OH_HUKS_TAG_AGREE_PUBLIC_KEY = OH_HUKS_TAG_TYPE_BYTES \| 22 | 用于协商的公钥。 |
| OH_HUKS_TAG_KEY_ALIAS = OH_HUKS_TAG_TYPE_BYTES \| 23 | 密钥别名。 |
| OH_HUKS_TAG_DERIVE_KEY_SIZE = OH_HUKS_TAG_TYPE_UINT \| 24 | 派生密钥大小。 |
| OH_HUKS_TAG_IMPORT_KEY_TYPE = OH_HUKS_TAG_TYPE_UINT \| 25 | 导入密钥类型，类型可在枚举[OH_Huks_ImportKeyType](#oh_huks_importkeytype)中选择。 |
| OH_HUKS_TAG_UNWRAP_ALGORITHM_SUITE = OH_HUKS_TAG_TYPE_UINT \| 26 | 导入加密密钥的套件。 |
| OH_HUKS_TAG_DERIVED_AGREED_KEY_STORAGE_FLAG = OH_HUKS_TAG_TYPE_UINT \| 29 | 派生密钥/协商密钥的存储类型，类型可在枚举[OH_Huks_KeyStorageType](#oh_huks_keystoragetype)中选择。 |
| OH_HUKS_TAG_RSA_PSS_SALT_LEN_TYPE = OH_HUKS_TAG_TYPE_UINT \| 30 | RSA算法，填充模式为PSS时的盐值长度类型。 |
| OH_HUKS_TAG_ALL_USERS = OH_HUKS_TAG_TYPE_BOOL \| 301 | 多用户中的所有用户。 |
| OH_HUKS_TAG_USER_ID = OH_HUKS_TAG_TYPE_UINT \| 302 | 表示多用户id。 |
| OH_HUKS_TAG_NO_AUTH_REQUIRED = OH_HUKS_TAG_TYPE_BOOL \| 303 | 表示是否需要密钥访问控制。 |
| OH_HUKS_TAG_USER_AUTH_TYPE = OH_HUKS_TAG_TYPE_UINT \| 304 | 表示密钥访问控制中用户认证类型。 |
| OH_HUKS_TAG_AUTH_TIMEOUT = OH_HUKS_TAG_TYPE_UINT \| 305 | 表示密钥访问控制类型中密钥访问的超时时间。 |
| OH_HUKS_TAG_AUTH_TOKEN = OH_HUKS_TAG_TYPE_BYTES \| 306 | 表示密钥访问控制中使用密钥时传入的authtoken的类型。 |
| OH_HUKS_TAG_KEY_AUTH_ACCESS_TYPE = OH_HUKS_TAG_TYPE_UINT \| 307 | 表示安全访问控制类型，需要和用户认证类型同时设置，类型可在枚举[OH_Huks_AuthAccessType](#oh_huks_authaccesstype)中选择。 |
| OH_HUKS_TAG_KEY_SECURE_SIGN_TYPE = OH_HUKS_TAG_TYPE_UINT \| 308 | 表示生成或导入密钥时，指定该密钥的签名类型。 |
| OH_HUKS_TAG_CHALLENGE_TYPE = OH_HUKS_TAG_TYPE_UINT \| 309 | 表示密钥使用时生成的challenge类型，类型可在枚举[OH_Huks_ChallengeType](#oh_huks_challengetype)中选择。 |
| OH_HUKS_TAG_CHALLENGE_POS = OH_HUKS_TAG_TYPE_UINT \| 310 | 表示challenge类型为用户自定义类型时，huks产生的challenge有效长度仅为8字节连续的数据的位置，类型可在枚举[OH_Huks_ChallengePosition](#oh_huks_challengeposition)中选择。 |
| OH_HUKS_TAG_KEY_AUTH_PURPOSE = OH_HUKS_TAG_TYPE_UINT \| 311 | 表示密钥认证用途的类型。 |
| OH_HUKS_TAG_AUTH_STORAGE_LEVEL = OH_HUKS_TAG_TYPE_UINT \| 316 | 密钥文件存储访问控制的类别，类型可在枚举[OH_Huks_AuthStorageLevel](#oh_huks_authstoragelevel)中选择。<br>**起始版本：** 11 |
| OH_HUKS_TAG_USER_AUTH_MODE = OH_HUKS_TAG_TYPE_UINT \| 319 | 表示密钥访问控制中用户认证模式，类型可在枚举[OH_Huks_UserAuthMode](#oh_huks_userauthmode)中选择。<br>**起始版本：** 12 |
| OH_HUKS_TAG_ATTESTATION_CHALLENGE = OH_HUKS_TAG_TYPE_BYTES \| 501 | 密钥认证时的挑战值。 |
| OH_HUKS_TAG_ATTESTATION_APPLICATION_ID = OH_HUKS_TAG_TYPE_BYTES \| 502 | 密钥认证时拥有该密钥的application的Id。 |
| OH_HUKS_TAG_ATTESTATION_ID_ALIAS = OH_HUKS_TAG_TYPE_BYTES \| 511 | 密钥别名。 |
| OH_HUKS_TAG_ATTESTATION_ID_SEC_LEVEL_INFO = OH_HUKS_TAG_TYPE_BYTES \| 514 | 密钥认证时的安全凭据。 |
| OH_HUKS_TAG_ATTESTATION_ID_VERSION_INFO = OH_HUKS_TAG_TYPE_BYTES \| 515 | 密钥认证时的版本号。 |
| OH_HUKS_TAG_KEY_OVERRIDE = OH_HUKS_TAG_TYPE_BOOL \| 520 | 是否覆写同名密钥。<br>**起始版本：** 20 |
| OH_HUKS_TAG_IS_KEY_ALIAS = OH_HUKS_TAG_TYPE_BOOL \| 1001 | 是否是密钥别名。 |
| OH_HUKS_TAG_KEY_STORAGE_FLAG = OH_HUKS_TAG_TYPE_UINT \| 1002 | 密钥存储方式的标签，类型可在枚举 [OH_Huks_KeyStorageType](#oh_huks_keystoragetype)选择。 |
| OH_HUKS_TAG_IS_ALLOWED_WRAP = OH_HUKS_TAG_TYPE_BOOL \| 1003 | 是否允许密钥封装。 |
| OH_HUKS_TAG_KEY_WRAP_TYPE = OH_HUKS_TAG_TYPE_UINT \| 1004 | 密钥封装的类型。 |
| OH_HUKS_TAG_KEY_AUTH_ID = OH_HUKS_TAG_TYPE_BYTES \| 1005 | 密钥认证的ID。 |
| OH_HUKS_TAG_KEY_ROLE = OH_HUKS_TAG_TYPE_UINT \| 1006 | 密钥角色。 |
| OH_HUKS_TAG_KEY_FLAG = OH_HUKS_TAG_TYPE_UINT \| 1007 | 密钥标记，类型可在枚举[OH_Huks_KeyFlag](#oh_huks_keyflag)选择。 |
| OH_HUKS_TAG_IS_ASYNCHRONIZED = OH_HUKS_TAG_TYPE_UINT \| 1008 | 是否异步。 |
| OH_HUKS_TAG_KEY_DOMAIN = OH_HUKS_TAG_TYPE_UINT \| 1011 | 密钥域。 |
| OH_HUKS_TAG_IS_DEVICE_PASSWORD_SET = OH_HUKS_TAG_TYPE_BOOL \| 1012 | 表示密钥锁屏密码访问控制字段，可限制密钥只有在用户设置了锁屏密码时可用。<br> True表示只有在密码设置时才能生成和使用密钥。<br>**起始版本：** 11|
| OH_HUKS_TAG_AE_TAG = OH_HUKS_TAG_TYPE_BYTES \| 10009 | 用于传入GCM模式中的AEAD数据的字段。 |
| OH_HUKS_TAG_SYMMETRIC_KEY_DATA = OH_HUKS_TAG_TYPE_BYTES \| 20001 | 对称密钥数据。 |
| OH_HUKS_TAG_ASYMMETRIC_PUBLIC_KEY_DATA = OH_HUKS_TAG_TYPE_BYTES \| 20002 | 非对称密钥公钥数据。 |
| OH_HUKS_TAG_ASYMMETRIC_PRIVATE_KEY_DATA = OH_HUKS_TAG_TYPE_BYTES \| 20003 | 非对称密钥私钥数据。 |


