# Group Key (C/C++)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

From API version 23, HUKS supports the group key function. For details about the HUKS key operations supported by the group key function, see [Group Key Overview](huks-group-key-overview.md). This guide describes [Encryption and Decryption Using AES/CBC/PKCS7](#encryption-and-decryption-using-aescbcpkcs7), [Asymmetric Key Negotiation Using X25519](#asymmetric-key-agreement-using-x25519), and [Key Derivation Using PBKDF2](#key-derivation-using-pbkdf2) as examples to show how to use group keys.

## Linking the Dynamic Library in the CMake Script
```txt
target_link_libraries(entry PUBLIC libhuks_ndk.z.so)
```

**Configuration file**

Before using a group key, you need to configure the group information in the **app.json5** file. For details, see the configuration method of the **assetAccessGroups** field in [Configuration File Example](../../quick-start/app-configuration-file.md#configuration-file-example).

## Encryption and Decryption Using AES/CBC/PKCS7

### How to Develop

**Key generation**

1. Set a key alias. For details about the naming rules, see [Key Generation Overview and Algorithm Specifications](huks-key-generation-overview.md).

2. Initialize the key property set. Add the group key tags [OH_HUKS_TAG_KEY_ACCESS_GROUP](../../reference/apis-universal-keystore-kit/capi-native-huks-type-h.md#oh_huks_tag) and [OH_HUKS_TAG_KEY_OVERRIDE](../../reference/apis-universal-keystore-kit/capi-native-huks-type-h.md#oh_huks_tag) to prevent the key from being overwritten.

3. Call [OH_Huks_GenerateKeyItem](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_generatekeyitem) to generate a key. For details, see [Key Generation Overview and Algorithm Specifications](huks-key-generation-overview.md).

Alternatively, you can [import a key](huks-key-import-overview.md).

**Encryption**

1. Set a key alias.

2. Specify the data to be encrypted.

3. Call [OH_Huks_InitParamSet](../../reference/apis-universal-keystore-kit/capi-native-huks-param-h.md#oh_huks_initparamset) to set algorithm parameters. Add the group key tag [OH_HUKS_TAG_KEY_ACCESS_GROUP](../../reference/apis-universal-keystore-kit/capi-native-huks-type-h.md#oh_huks_tag).

4. Call [OH_Huks_InitSession](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_initsession) to initialize a key session and obtain the session handle.

5. Call [OH_Huks_FinishSession](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_finishsession) to finish the key session and obtain the ciphertext.

**Decryption**

1. Set a key alias.

2. Specify the ciphertext to be decrypted.

3. Call [OH_Huks_InitParamSet](../../reference/apis-universal-keystore-kit/capi-native-huks-param-h.md#oh_huks_initparamset) to set algorithm parameters. Add the group key tag [OH_HUKS_TAG_KEY_ACCESS_GROUP](../../reference/apis-universal-keystore-kit/capi-native-huks-type-h.md#oh_huks_tag).

4. Call [OH_Huks_InitSession](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_initsession) to initialize a key session and obtain the session handle.

5. Call [OH_Huks_FinishSession](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_finishsession) to finish the key session and obtain the decrypted data.

**Key deletion**

1. Set a key alias.

2. Call [OH_Huks_InitParamSet](../../reference/apis-universal-keystore-kit/capi-native-huks-param-h.md#oh_huks_initparamset) to set algorithm parameters. Add the group key tag [OH_HUKS_TAG_KEY_ACCESS_GROUP](../../reference/apis-universal-keystore-kit/capi-native-huks-type-h.md#oh_huks_tag).

3. Call [OH_Huks_DeleteKeyItem](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_deletekeyitem) to delete the key. For details, see [Deleting a Key (C/C++)](huks-delete-key-ndk.md).

Call **OH_Huks_DeleteKeyItem** to delete the key that is not required. For details, see [Deleting a Key (C/C++)](huks-delete-key-ndk.md).

### Development Cases

```c++
#include "huks/native_huks_api.h"
#include "huks/native_huks_param.h"
#include "napi/native_api.h"
#include <string.h>
#include "CryptoArchitectureKit/crypto_architecture_kit.h"

static OH_Crypto_ErrCode genRandomNumber(uint32_t randomLength, uint8_t *out)
{
    /* Create a random number generator. */
    OH_CryptoRand *rand = nullptr;
    OH_Crypto_ErrCode ret = OH_CryptoRand_Create(&rand);
    if (ret != CRYPTO_SUCCESS) {
        return ret;
    }
    Crypto_DataBlob blob = {out, randomLength};
    /* Generate a random number of the given length. */
    ret = OH_CryptoRand_GenerateRandom(rand, randomLength, &blob);
    if (ret != CRYPTO_SUCCESS) {
        OH_CryptoRand_Destroy(rand);
        return ret;
    }
    OH_CryptoRand_Destroy(rand);

    return CRYPTO_SUCCESS;
}

OH_Huks_Result InitParamSet(struct OH_Huks_ParamSet **paramSet, const struct OH_Huks_Param *params, uint32_t paramCount)
{
    OH_Huks_Result ret = OH_Huks_InitParamSet(paramSet);
    if (ret.errorCode != OH_HUKS_SUCCESS) {
        return ret;
    }
    ret = OH_Huks_AddParams(*paramSet, params, paramCount);
    if (ret.errorCode != OH_HUKS_SUCCESS) {
        OH_Huks_FreeParamSet(paramSet);
        return ret;
    }
    ret = OH_Huks_BuildParamSet(paramSet);
    if (ret.errorCode != OH_HUKS_SUCCESS) {
        OH_Huks_FreeParamSet(paramSet);
        return ret;
    }
    return ret;
}
uint32_t OH_HUKS_TAG_KEY_ACCESS_GROUP = 5 << 28 | 523;
static const uint32_t IV_SIZE = 16;
static uint8_t IV[IV_SIZE] = { 0 };
static OH_Crypto_ErrCode ret = genRandomNumber(IV_SIZE, IV);
/*
 * Add the group information to the assetAccessGroups field in app.json5.
 */
static char group[] = "ohos.test.group";
static struct OH_Huks_Param g_genEncDecParams[] = {
    {
        .tag = OH_HUKS_TAG_ALGORITHM,
        .uint32Param = OH_HUKS_ALG_AES
    }, {
        .tag = OH_HUKS_TAG_PURPOSE,
        .uint32Param = OH_HUKS_KEY_PURPOSE_ENCRYPT | OH_HUKS_KEY_PURPOSE_DECRYPT
    }, {
        .tag = OH_HUKS_TAG_KEY_SIZE,
        .uint32Param = OH_HUKS_AES_KEY_SIZE_256
    }, {
        .tag = OH_HUKS_TAG_PADDING,
        .uint32Param = OH_HUKS_PADDING_PKCS7
    }, {
        .tag = OH_HUKS_TAG_BLOCK_MODE,
        .uint32Param = OH_HUKS_MODE_CBC
    }, {
        .tag = OH_HUKS_TAG_KEY_ACCESS_GROUP,
        .blob = {
            .size = (uint32_t)strlen(group),
            .data = (uint8_t *)group
        }
    }
};
static struct OH_Huks_Param g_encryptParams[] = {
    {
        .tag = OH_HUKS_TAG_ALGORITHM,
        .uint32Param = OH_HUKS_ALG_AES
    }, {
        .tag = OH_HUKS_TAG_PURPOSE,
        .uint32Param = OH_HUKS_KEY_PURPOSE_ENCRYPT
    }, {
        .tag = OH_HUKS_TAG_KEY_SIZE,
        .uint32Param = OH_HUKS_AES_KEY_SIZE_256
    }, {
        .tag = OH_HUKS_TAG_PADDING,
        .uint32Param = OH_HUKS_PADDING_PKCS7
    }, {
        .tag = OH_HUKS_TAG_BLOCK_MODE,
        .uint32Param = OH_HUKS_MODE_CBC
    }, {
        .tag = OH_HUKS_TAG_IV,
        .blob = {
            .size = IV_SIZE,
            .data = (uint8_t *)IV
        }
    }, {
        .tag = OH_HUKS_TAG_KEY_ACCESS_GROUP,
        .blob = {
            .size = (uint32_t)strlen(group),
            .data = (uint8_t *)group
        }
    }
};
static struct OH_Huks_Param g_decryptParams[] = {
    {
        .tag = OH_HUKS_TAG_ALGORITHM,
        .uint32Param = OH_HUKS_ALG_AES
    }, {
        .tag = OH_HUKS_TAG_PURPOSE,
        .uint32Param = OH_HUKS_KEY_PURPOSE_DECRYPT
    }, {
        .tag = OH_HUKS_TAG_KEY_SIZE,
        .uint32Param = OH_HUKS_AES_KEY_SIZE_256
    }, {
        .tag = OH_HUKS_TAG_PADDING,
        .uint32Param = OH_HUKS_PADDING_PKCS7
    }, {
        .tag = OH_HUKS_TAG_BLOCK_MODE,
        .uint32Param = OH_HUKS_MODE_CBC
    }, {
        .tag = OH_HUKS_TAG_IV,
        .blob = {
            .size = IV_SIZE,
            .data = (uint8_t *)IV
        }
    }, {
        .tag = OH_HUKS_TAG_KEY_ACCESS_GROUP,
        .blob = {
            .size = (uint32_t)strlen(group),
            .data = (uint8_t *)group
        }
    }
};
static const uint32_t AES_COMMON_SIZE = 1024;

OH_Huks_Result HksAesCipherTestEncrypt(
    const struct OH_Huks_Blob *keyAlias, const struct OH_Huks_ParamSet *encryptParamSet,
    const struct OH_Huks_Blob *inData, struct OH_Huks_Blob *cipherText)
{
    uint8_t handleE[sizeof(uint64_t)] = {0};
    struct OH_Huks_Blob handleEncrypt = {sizeof(uint64_t), handleE};
    OH_Huks_Result ret = OH_Huks_InitSession(keyAlias, encryptParamSet, &handleEncrypt, nullptr);
    if (ret.errorCode != OH_HUKS_SUCCESS) {
        return ret;
    }
    ret = OH_Huks_FinishSession(&handleEncrypt, encryptParamSet, inData, cipherText);
    return ret;
}

OH_Huks_Result HksAesCipherTestDecrypt(const struct OH_Huks_Blob *keyAlias,
    const struct OH_Huks_ParamSet *decryptParamSet, const struct OH_Huks_Blob *cipherText,
    struct OH_Huks_Blob *plainText, const struct OH_Huks_Blob *inData)
{
    uint8_t handleD[sizeof(uint64_t)] = {0};
    struct OH_Huks_Blob handleDecrypt = {sizeof(uint64_t), handleD};
    OH_Huks_Result ret = OH_Huks_InitSession(keyAlias, decryptParamSet, &handleDecrypt, nullptr);
    if (ret.errorCode != OH_HUKS_SUCCESS) {
        return ret;
    }
    ret = OH_Huks_FinishSession(&handleDecrypt, decryptParamSet, cipherText, plainText);
    return ret;
}

static napi_value EncDecKey(napi_env env, napi_callback_info info)
{
    char tmpKeyAlias[] = "test_enc_dec";
    struct OH_Huks_Blob keyAlias = { (uint32_t)strlen(tmpKeyAlias), (uint8_t *)tmpKeyAlias };
    struct OH_Huks_ParamSet *genParamSet = nullptr;
    struct OH_Huks_ParamSet *encryptParamSet = nullptr;
    struct OH_Huks_ParamSet *decryptParamSet = nullptr;
    OH_Huks_Result ohResult;
    do {
        /* 1. Generate Key */
        /*
         * Simulate the key generation scenario.
         * 1.1. Set a key alias.
         */
        /*
         * 1.2. Obtain the algorithm parameters for key generation.
         */
        ohResult = InitParamSet(&genParamSet, g_genEncDecParams, sizeof(g_genEncDecParams) / sizeof(OH_Huks_Param));
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
        /*
         * 1.3. Call generateKeyItem.
         */
        ohResult = OH_Huks_GenerateKeyItem(&keyAlias, genParamSet, nullptr);
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
        /* 2. Encrypt */
        /*
         * Simulate the encryption scenario.
         * 2.1. Obtain the key alias.
         */
        /*
         * 2.2. Obtain the data to be encrypted.
         */
        /*
         * 2.3. Obtain the algorithm parameters for encryption.
         */
        ohResult = InitParamSet(&encryptParamSet, g_encryptParams, sizeof(g_encryptParams) / sizeof(OH_Huks_Param));
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
        char tmpInData[] = "AES_ECB_INDATA_1";
        struct OH_Huks_Blob inData = { (uint32_t)strlen(tmpInData), (uint8_t *)tmpInData };
        uint8_t cipher[AES_COMMON_SIZE] = {0};
        struct OH_Huks_Blob cipherText = {AES_COMMON_SIZE, cipher};
        /*
         * 2.4. Call initSession to obtain a session handle.
         */
        /*
         * 2.5. Call finishSession to obtain the ciphertext.
         */
        ohResult = HksAesCipherTestEncrypt(&keyAlias, encryptParamSet, &inData, &cipherText);
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
        /* 3. Decrypt */
        /*
         * Simulate the decryption scenario.
         * 3.1. Obtain the key alias.
         */
        /*
         * 3.2. Obtain the ciphertext to be decrypted.
         */
        /*
         * 3.3 Obtain the algorithm parameters for decryption.
         */
        ohResult = InitParamSet(&decryptParamSet, g_decryptParams, sizeof(g_decryptParams) / sizeof(OH_Huks_Param));
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
        uint8_t plain[AES_COMMON_SIZE] = {0};
        struct OH_Huks_Blob plainText = {AES_COMMON_SIZE, plain};
        /*
         * 3.4. Call initSession to obtain a session handle.
         */
        /*
         * 3.5. Call finishSession to obtain the decrypted data.
         */
        ohResult = HksAesCipherTestDecrypt(&keyAlias, decryptParamSet, &cipherText, &plainText, &inData);
    } while (0);
    /* 4. Delete Key */
    /*
     * Simulate the key deletion scenario.
     * 4.1. Obtain the key alias.
     */
    /*
     * 4.2. Call deleteKeyItem to delete the key.   
     */
    (void)OH_Huks_DeleteKeyItem(&keyAlias, genParamSet);
        
    OH_Huks_FreeParamSet(&genParamSet);
    OH_Huks_FreeParamSet(&encryptParamSet);
    OH_Huks_FreeParamSet(&decryptParamSet);
    
    napi_value ret;
    napi_create_int32(env, ohResult.errorCode, &ret);
    return ret;
}
```

## Asymmetric Key Agreement Using X25519

### How to Develop

**Key generation**

Generate an asymmetric key for device A and device B each. For details, see [Key Generation Overview and Algorithm Specifications](huks-key-generation-overview.md) or [Key Import Overview and Algorithm Specifications](huks-key-import-overview.md).

When generating a key, specify [OH_HUKS_TAG_KEY_ACCESS_GROUP](../../reference/apis-universal-keystore-kit/capi-native-huks-type-h.md#oh_huks_tag) to generate a group key.

**Key export**

Export the public key of the asymmetric key pair of device A and device B. For details, see [Exporting a Key (C/C++)](huks-export-key-ndk.md).

When exporting a key, specify [OH_HUKS_TAG_KEY_ACCESS_GROUP](../../reference/apis-universal-keystore-kit/capi-native-huks-type-h.md#oh_huks_tag) to export the group key.

**Key agreement**

Perform key agreement using the public key of the peer device and private key of the local device (that is, public key of device B and private key of device A for device A, and public key of device A and private key of device B for device B) to produce a shared key.

When performing key agreement, specify [OH_HUKS_TAG_KEY_ACCESS_GROUP](../../reference/apis-universal-keystore-kit/capi-native-huks-type-h.md#oh_huks_tag) to produce a group key.

**Key deletion**

Delete the keys from device A and device B when the keys are not required. For details, see [Deleting a Key (C/C++)](huks-delete-key-ndk.md).

When deleting a key, specify [OH_HUKS_TAG_KEY_ACCESS_GROUP](../../reference/apis-universal-keystore-kit/capi-native-huks-type-h.md#oh_huks_tag) to delete the group key.

### Development Cases

```c++
#include "huks/native_huks_api.h"
#include "huks/native_huks_param.h"
#include "napi/native_api.h"
#include <cstring>

static struct OH_Huks_Blob g_group = {(uint32_t)strlen("ohos.test.group"), (uint8_t *)"ohos.test.group"};
/* Initialize parameters. */
static OH_Huks_Result InitParamSet(struct OH_Huks_ParamSet **paramSet, const struct OH_Huks_Param *params,
    uint32_t paramCount)
{
    OH_Huks_Result ret = OH_Huks_InitParamSet(paramSet);
    if (ret.errorCode != OH_HUKS_SUCCESS) {
        return ret;
    }
    ret = OH_Huks_AddParams(*paramSet, params, paramCount);
    if (ret.errorCode != OH_HUKS_SUCCESS) {
        OH_Huks_FreeParamSet(paramSet);
        return ret;
    }
    ret = OH_Huks_BuildParamSet(paramSet);
    if (ret.errorCode != OH_HUKS_SUCCESS) {
        OH_Huks_FreeParamSet(paramSet);
        return ret;
    }
    return ret;
}
static struct OH_Huks_Blob g_keyAliasFinal1001 = {(uint32_t)strlen("HksECDHAgreeKeyAliasTest001_1_final"),
                                                  (uint8_t *)"HksECDHAgreeKeyAliasTest001_1_final"};
/* Set the key parameter set. */
static struct OH_Huks_Param g_genAgreeParams[] = {
    {.tag = OH_HUKS_TAG_ALGORITHM, .uint32Param = OH_HUKS_ALG_X25519},
    {.tag = OH_HUKS_TAG_PURPOSE, .uint32Param = OH_HUKS_KEY_PURPOSE_AGREE},
    {.tag = OH_HUKS_TAG_KEY_SIZE, .uint32Param = OH_HUKS_CURVE25519_KEY_SIZE_256},
    {.tag = OH_HUKS_TAG_DIGEST, .uint32Param = OH_HUKS_DIGEST_NONE},
    {.tag = OH_HUKS_TAG_KEY_ACCESS_GROUP, .blob = g_group}
};
static struct OH_Huks_Param g_agreeParamsInit01[] = {
    {.tag = OH_HUKS_TAG_ALGORITHM, .uint32Param = OH_HUKS_ALG_X25519},
    {.tag = OH_HUKS_TAG_PURPOSE, .uint32Param = OH_HUKS_KEY_PURPOSE_AGREE},
    {.tag = OH_HUKS_TAG_KEY_SIZE, .uint32Param = OH_HUKS_CURVE25519_KEY_SIZE_256},
    {.tag = OH_HUKS_TAG_DIGEST, .uint32Param = OH_HUKS_DIGEST_NONE},
    {.tag = OH_HUKS_TAG_KEY_ACCESS_GROUP, .blob = g_group}
};
static struct OH_Huks_Param g_agreeParamsFinish01[] = {
    {.tag = OH_HUKS_TAG_DERIVED_AGREED_KEY_STORAGE_FLAG, .uint32Param = OH_HUKS_STORAGE_ONLY_USED_IN_HUKS},
    {.tag = OH_HUKS_TAG_ALGORITHM, .uint32Param = OH_HUKS_ALG_AES},
    {.tag = OH_HUKS_TAG_KEY_SIZE, .uint32Param = OH_HUKS_AES_KEY_SIZE_256},
    {.tag = OH_HUKS_TAG_PURPOSE, .uint32Param = OH_HUKS_KEY_PURPOSE_AGREE},
    {.tag = OH_HUKS_TAG_KEY_ALIAS, .blob = g_keyAliasFinal1001},
    {.tag = OH_HUKS_TAG_PADDING, .uint32Param = OH_HUKS_PADDING_NONE},
    {.tag = OH_HUKS_TAG_BLOCK_MODE, .uint32Param = OH_HUKS_MODE_ECB},
    {.tag = OH_HUKS_TAG_DIGEST, .uint32Param = OH_HUKS_DIGEST_NONE},
    {.tag = OH_HUKS_TAG_KEY_ACCESS_GROUP, .blob = g_group}
};
static struct OH_Huks_Blob g_keyAliasFinal2001 = {(uint32_t)strlen("HksX25519AgreeKeyAliasTest001_2_final"),
                                                  (uint8_t *)"HksX25519AgreeKeyAliasTest001_2_final"};
static struct OH_Huks_Param g_agreeParamsInit02[] = {
    {.tag = OH_HUKS_TAG_ALGORITHM, .uint32Param = OH_HUKS_ALG_X25519},
    {.tag = OH_HUKS_TAG_PURPOSE, .uint32Param = OH_HUKS_KEY_PURPOSE_AGREE},
    {.tag = OH_HUKS_TAG_KEY_SIZE, .uint32Param = OH_HUKS_CURVE25519_KEY_SIZE_256},
    {.tag = OH_HUKS_TAG_DIGEST, .uint32Param = OH_HUKS_DIGEST_NONE},
    {.tag = OH_HUKS_TAG_KEY_ACCESS_GROUP, .blob = g_group}
};
static struct OH_Huks_Param g_agreeParamsFinish02[] = {
    {.tag = OH_HUKS_TAG_DERIVED_AGREED_KEY_STORAGE_FLAG, .uint32Param = OH_HUKS_STORAGE_ONLY_USED_IN_HUKS},
    {.tag = OH_HUKS_TAG_ALGORITHM, .uint32Param = OH_HUKS_ALG_AES},
    {.tag = OH_HUKS_TAG_KEY_SIZE, .uint32Param = OH_HUKS_AES_KEY_SIZE_256},
    {.tag = OH_HUKS_TAG_PURPOSE, .uint32Param = OH_HUKS_KEY_PURPOSE_AGREE},
    {.tag = OH_HUKS_TAG_KEY_ALIAS, .blob = g_keyAliasFinal2001},
    {.tag = OH_HUKS_TAG_PADDING, .uint32Param = OH_HUKS_PADDING_NONE},
    {.tag = OH_HUKS_TAG_BLOCK_MODE, .uint32Param = OH_HUKS_MODE_ECB},
    {.tag = OH_HUKS_TAG_DIGEST, .uint32Param = OH_HUKS_DIGEST_NONE},
    {.tag = OH_HUKS_TAG_KEY_ACCESS_GROUP, .blob = g_group}
};
static const uint32_t X25519_COMMON_SIZE = 256;
static struct OH_Huks_Blob g_keyAlias01001 = {(uint32_t)strlen("HksX25519AgreeKeyAliasTest001_1"),
                                              (uint8_t *)"HksX25519AgreeKeyAliasTest001_1"};
static struct OH_Huks_Blob g_keyAlias02001 = {(uint32_t)strlen("HksX25519AgreeKeyAliasTest001_2"),
                                              (uint8_t *)"HksX25519AgreeKeyAliasTest001_2"};

static OH_Huks_Result MallocAndCheckBlobData(struct OH_Huks_Blob *blob, const uint32_t blobSize)
{
    struct OH_Huks_Result ret;
    ret.errorCode = OH_HUKS_SUCCESS;
    if (blobSize == 0 || blobSize > X25519_COMMON_SIZE) {
        ret.errorCode = OH_HUKS_ERR_CODE_INTERNAL_ERROR;
        return ret;
    }
    blob->data = (uint8_t *)malloc(blobSize);
    if (blob->data == NULL) {
        ret.errorCode = OH_HUKS_ERR_CODE_INTERNAL_ERROR;
    }
    return ret;
}
/* Export the key. */
OH_Huks_Result HksX25519AgreeExport(const struct OH_Huks_Blob *keyAlias1, const struct OH_Huks_Blob *keyAlias2,
    struct OH_Huks_Blob *publicKey1, struct OH_Huks_Blob *publicKey2,
    const struct OH_Huks_ParamSet *genParamSet)
{
    OH_Huks_Result ret = OH_Huks_ExportPublicKeyItem(keyAlias1, genParamSet, publicKey1);
    if (ret.errorCode != OH_HUKS_SUCCESS) {
        return ret;
    }
    ret = OH_Huks_ExportPublicKeyItem(keyAlias2, genParamSet, publicKey2);
    if (ret.errorCode != OH_HUKS_SUCCESS) {
        return ret;
    }
    return ret;
}
static const char *IN_DATA = "Hks_X25519_Agree_Test";
/* Perform key agreement. */
OH_Huks_Result HksX25519AgreeFinish(const struct OH_Huks_Blob *keyAlias, const struct OH_Huks_Blob *publicKey,
    const struct OH_Huks_ParamSet *initParamSet,
    const struct OH_Huks_ParamSet *finishParamSet, struct OH_Huks_Blob *outData)
{
    struct OH_Huks_Blob inData = {(uint32_t)strlen(IN_DATA), (uint8_t *)IN_DATA};
    uint8_t handleU[sizeof(uint64_t)] = {0};
    struct OH_Huks_Blob handle = {sizeof(uint64_t), handleU};
    OH_Huks_Result ret = OH_Huks_InitSession(keyAlias, initParamSet, &handle, nullptr);
    if (ret.errorCode != OH_HUKS_SUCCESS) {
        return ret;
    }
    uint8_t outDataU[X25519_COMMON_SIZE] = {0};
    struct OH_Huks_Blob outDataUpdate = {X25519_COMMON_SIZE, outDataU};
    ret = OH_Huks_UpdateSession(&handle, initParamSet, publicKey, &outDataUpdate);
    if (ret.errorCode != OH_HUKS_SUCCESS) {
        return ret;
    }
    ret = OH_Huks_FinishSession(&handle, finishParamSet, &inData, outData);
    if (ret.errorCode != OH_HUKS_SUCCESS) {
        return ret;
    }
    return ret;
}

static OH_Huks_Result InitializeAgreeParamSets(struct OH_Huks_ParamSet **genParamSet,
    struct OH_Huks_ParamSet **initParamSet01,
    struct OH_Huks_ParamSet **finishParamSet01,
    struct OH_Huks_ParamSet **initParamSet02,
    struct OH_Huks_ParamSet **finishParamSet02)
{
    OH_Huks_Result ohResult;
    
    ohResult = InitParamSet(genParamSet, g_genAgreeParams,
                            sizeof(g_genAgreeParams) / sizeof(OH_Huks_Param));
    if (ohResult.errorCode != OH_HUKS_SUCCESS) {
        return ohResult;
    }
    ohResult = InitParamSet(initParamSet01, g_agreeParamsInit01,
                            sizeof(g_agreeParamsInit01) / sizeof(OH_Huks_Param));
    if (ohResult.errorCode != OH_HUKS_SUCCESS) {
        return ohResult;
    }
    ohResult = InitParamSet(finishParamSet01, g_agreeParamsFinish01,
                            sizeof(g_agreeParamsFinish01) / sizeof(OH_Huks_Param));
    if (ohResult.errorCode != OH_HUKS_SUCCESS) {
        return ohResult;
    }
    ohResult = InitParamSet(initParamSet02, g_agreeParamsInit02,
                            sizeof(g_agreeParamsInit02) / sizeof(OH_Huks_Param));
    if (ohResult.errorCode != OH_HUKS_SUCCESS) {
        return ohResult;
    }
    ohResult = InitParamSet(finishParamSet02, g_agreeParamsFinish02,
                            sizeof(g_agreeParamsFinish02) / sizeof(OH_Huks_Param));
    return ohResult;
}

static OH_Huks_Result GenerateKeyPair(struct OH_Huks_ParamSet *genParamSet)
{
    OH_Huks_Result ohResult;
    
    /* Generate a key for device A. */
    ohResult = OH_Huks_GenerateKeyItem(&g_keyAlias01001, genParamSet, nullptr);
    if (ohResult.errorCode != OH_HUKS_SUCCESS) {
        return ohResult;
    }
    
    /* Generate a key for device B. */
    ohResult = OH_Huks_GenerateKeyItem(&g_keyAlias02001, genParamSet, nullptr);
    return ohResult;
}

static OH_Huks_Result KeyAgreement(struct OH_Huks_Blob *g_keyAlias,
    struct OH_Huks_Blob *publicKey,
    struct OH_Huks_Blob *outData,
    struct OH_Huks_ParamSet *initParamSet,
    struct OH_Huks_ParamSet *finishParamSet)
{
    OH_Huks_Result ohResult;
    
    ohResult = MallocAndCheckBlobData(outData, outData->size);
    if (ohResult.errorCode != OH_HUKS_SUCCESS) {
        return ohResult;
    }
    /* Perform key agreement. */
    ohResult = HksX25519AgreeFinish(g_keyAlias, publicKey, initParamSet, finishParamSet, outData);
    return ohResult;
}

static void CleanKey(struct OH_Huks_Blob *genKeyAlias,
    struct OH_Huks_Blob *genKeyAliasFinal,
    struct OH_Huks_ParamSet *genParamSet,
    struct OH_Huks_ParamSet **initParamSet,
    struct OH_Huks_ParamSet **finishParamSet)
{
    OH_Huks_DeleteKeyItem(genKeyAlias, genParamSet);
    OH_Huks_DeleteKeyItem(genKeyAliasFinal, genParamSet);
    OH_Huks_FreeParamSet(initParamSet);
    OH_Huks_FreeParamSet(finishParamSet);
}

/* Key agreement process */
napi_value X25519AgreeKey(napi_env env, napi_callback_info info)
{
    struct OH_Huks_ParamSet *genParamSet = nullptr;
    struct OH_Huks_ParamSet *initParamSet01 = nullptr;
    struct OH_Huks_ParamSet *finishParamSet01 = nullptr;
    struct OH_Huks_ParamSet *initParamSet02 = nullptr;
    struct OH_Huks_ParamSet *finishParamSet02 = nullptr;
    struct OH_Huks_Blob publicKey01 = {.size = OH_HUKS_AES_KEY_SIZE_256, .data = nullptr};
    struct OH_Huks_Blob publicKey02 = {.size = OH_HUKS_AES_KEY_SIZE_256, .data = nullptr};
    struct OH_Huks_Blob outData01 = {.size = X25519_COMMON_SIZE, .data = nullptr};
    struct OH_Huks_Blob outData02 = {.size = X25519_COMMON_SIZE, .data = nullptr};
    OH_Huks_Result ohResult;
    do {
        /* 1. Set a key alias and key parameter set. */
        ohResult = InitializeAgreeParamSets(&genParamSet, &initParamSet01, &finishParamSet01,
                                            &initParamSet02, &finishParamSet02);
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
        /* 2. Generate keys for device A and device B. */
        ohResult = GenerateKeyPair(genParamSet);
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
        ohResult = MallocAndCheckBlobData(&publicKey01, publicKey01.size);
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
        ohResult = MallocAndCheckBlobData(&publicKey02, publicKey02.size);
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
        /* 3. Export the public key from device A and device B separately. */
        ohResult = HksX25519AgreeExport(&g_keyAlias01001, &g_keyAlias02001, &publicKey01, &publicKey02, genParamSet);
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
        /* 4. Perform key agreement on device A and device B. */
        ohResult = KeyAgreement(&g_keyAlias01001, &publicKey02, &outData01, initParamSet01, finishParamSet01);
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
        ohResult = KeyAgreement(&g_keyAlias02001, &publicKey01, &outData02, initParamSet02, finishParamSet02);
    } while (0);
    free(publicKey01.data);
    free(publicKey02.data);
    free(outData01.data);
    free(outData02.data);
    /* 5. Delete the keys from device A and device B. */
    CleanKey(&g_keyAlias01001, &g_keyAliasFinal1001, genParamSet, &initParamSet01, &finishParamSet01);
    CleanKey(&g_keyAlias02001, &g_keyAliasFinal2001, genParamSet, &initParamSet02, &finishParamSet02);
    OH_Huks_FreeParamSet(&genParamSet);

    napi_value ret;
    napi_create_int32(env, ohResult.errorCode, &ret);
    return ret;
}
```

## Key Derivation Using PBKDF2

### How to Develop

**Key generation**

1. Set a key alias. For details about the naming rules, see [Key Generation Overview and Algorithm Specifications](huks-key-generation-overview.md).

2. When generating a key, specify [OH_HUKS_TAG_KEY_ACCESS_GROUP](../../reference/apis-universal-keystore-kit/capi-native-huks-type-h.md#oh_huks_tag) to generate a group key.

3. Call [OH_Huks_GenerateKeyItem](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_generatekeyitem) to generate a key. For details, see [Key Generation Overview and Algorithm Specifications](huks-key-generation-overview.md).

Alternatively, you can [import a key](huks-key-import-overview.md).

**Key derivation**

1. Obtain the key alias, specify the property parameter **HuksOptions**, and add the [OH_HUKS_TAG_KEY_ACCESS_GROUP](../../reference/apis-universal-keystore-kit//capi-native-huks-type-h.md#oh_huks_tag) parameter to derive a group key.

2. Call [OH_Huks_InitParamSet](../../reference/apis-universal-keystore-kit/capi-native-huks-param-h.md#oh_huks_initparamset) to set algorithm parameters. Add the group key tag [OH_HUKS_TAG_KEY_ACCESS_GROUP](../../reference/apis-universal-keystore-kit/capi-native-huks-type-h.md#oh_huks_tag).

3. Call [OH_Huks_InitSession](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_initsession) to initialize a key session and obtain the session handle.

4. Call [OH_Huks_UpdateSession](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_updatesession) to update the key session.

5. Call [OH_Huks_FinishSession](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_finishsession) to finish the key session and derive a key.

**Key deletion**

When a key is no longer used, you need to call [OH_Huks_DeleteKeyItem](../../reference/apis-universal-keystore-kit/capi-native-huks-api-h.md#oh_huks_deletekeyitem) to delete the key. For details, see [Deleting a Key (C/C++)](huks-delete-key-ndk.md).

When deleting a key, specify [OH_HUKS_TAG_KEY_ACCESS_GROUP](../../reference/apis-universal-keystore-kit/capi-native-huks-type-h.md#oh_huks_tag) to delete the group key.

### Development Cases

```c++
#include "huks/native_huks_api.h"
#include "huks/native_huks_param.h"
#include "napi/native_api.h"
#include <cstring>

OH_Huks_Result InitParamSet(struct OH_Huks_ParamSet **paramSet, const struct OH_Huks_Param *params,
                            uint32_t paramCount)
{
    OH_Huks_Result ret = OH_Huks_InitParamSet(paramSet);
    if (ret.errorCode != OH_HUKS_SUCCESS) {
        return ret;
    }
    ret = OH_Huks_AddParams(*paramSet, params, paramCount);
    if (ret.errorCode != OH_HUKS_SUCCESS) {
        OH_Huks_FreeParamSet(paramSet);
        return ret;
    }
    ret = OH_Huks_BuildParamSet(paramSet);
    if (ret.errorCode != OH_HUKS_SUCCESS) {
        OH_Huks_FreeParamSet(paramSet);
        return ret;
    }
    return ret;
}
static const uint32_t DERIVE_KEY_SIZE_32 = 32;
static const uint32_t DERIVE_KEY_SIZE_256 = 256;
static const uint32_t DERIVE_KEY_ITERATION = 10000;
static const uint32_t SALT_SIZE = 8;
static const char DERIVE_KEY_SALT[SALT_SIZE] = "mysalt1";
static struct OH_Huks_Blob g_deriveKeyAlias = {(uint32_t)strlen("test_derive"), (uint8_t *)"test_derive"};
static struct OH_Huks_Blob g_group = {(uint32_t)strlen("ohos.test.group"), (uint8_t *)"ohos.test.group"};
static struct OH_Huks_Param g_genDeriveParams[] = {
    {.tag = OH_HUKS_TAG_ALGORITHM, .uint32Param = OH_HUKS_ALG_AES},
    {.tag = OH_HUKS_TAG_PURPOSE, .uint32Param = OH_HUKS_KEY_PURPOSE_DERIVE},
    {.tag = OH_HUKS_TAG_DIGEST, .uint32Param = OH_HUKS_DIGEST_SHA256},
    {.tag = OH_HUKS_TAG_KEY_SIZE, .uint32Param = OH_HUKS_AES_KEY_SIZE_256},
    {.tag = OH_HUKS_TAG_KEY_ACCESS_GROUP, .blob = g_group}
};
static struct OH_Huks_Param g_hkdfParams[] = {
    {.tag = OH_HUKS_TAG_ALGORITHM, .uint32Param = OH_HUKS_ALG_PBKDF2},
    {.tag = OH_HUKS_TAG_PURPOSE, .uint32Param = OH_HUKS_KEY_PURPOSE_DERIVE},
    {.tag = OH_HUKS_TAG_DIGEST, .uint32Param = OH_HUKS_DIGEST_SHA256},
    {.tag = OH_HUKS_TAG_DERIVE_KEY_SIZE, .uint32Param = DERIVE_KEY_SIZE_32},
    {.tag = OH_HUKS_TAG_ITERATION, .uint32Param = DERIVE_KEY_ITERATION},
    {.tag = OH_HUKS_TAG_SALT, .blob = {.size = SALT_SIZE, .data = (uint8_t *) DERIVE_KEY_SALT}},
    {.tag = OH_HUKS_TAG_KEY_ACCESS_GROUP, .blob = g_group}
};
static struct OH_Huks_Param g_hkdfFinishParams[] = {
    {.tag = OH_HUKS_TAG_DERIVED_AGREED_KEY_STORAGE_FLAG, .uint32Param = OH_HUKS_STORAGE_ONLY_USED_IN_HUKS},
    {.tag = OH_HUKS_TAG_KEY_ALIAS, .blob = g_deriveKeyAlias},
    {.tag = OH_HUKS_TAG_ALGORITHM, .uint32Param = OH_HUKS_ALG_AES},
    {.tag = OH_HUKS_TAG_KEY_SIZE, .uint32Param = DERIVE_KEY_SIZE_256},
    {.tag = OH_HUKS_TAG_PURPOSE, .uint32Param = OH_HUKS_KEY_PURPOSE_DERIVE},
    {.tag = OH_HUKS_TAG_DIGEST, .uint32Param = OH_HUKS_DIGEST_NONE},
    {.tag = OH_HUKS_TAG_PADDING, .uint32Param = OH_HUKS_PADDING_NONE},
    {.tag = OH_HUKS_TAG_BLOCK_MODE, .uint32Param = OH_HUKS_MODE_ECB},
    {.tag = OH_HUKS_TAG_KEY_ACCESS_GROUP, .blob = g_group}
};
static const uint32_t COMMON_SIZE = 1024;
static const char *G_DERIVE_IN_DATA = "Hks_PBKDF2_Derive_Test_0_string";
static OH_Huks_Result PerformPbkdfDerivation(const struct OH_Huks_Blob *genAlias,
    struct OH_Huks_ParamSet *hkdfParamSet,
    struct OH_Huks_ParamSet *hkdfFinishParamSet,
    const struct OH_Huks_Blob &inData)
{
    OH_Huks_Result ohResult;
    /* Init */
    uint8_t handleD[sizeof(uint64_t)] = {0};
    struct OH_Huks_Blob handleDerive = {sizeof(uint64_t), handleD};
    ohResult = OH_Huks_InitSession(genAlias, hkdfParamSet, &handleDerive, nullptr);
    if (ohResult.errorCode != OH_HUKS_SUCCESS) {
        return ohResult;
    }
    /* Update */
    uint8_t tmpOut[COMMON_SIZE] = {0};
    struct OH_Huks_Blob outData = {COMMON_SIZE, tmpOut};
    ohResult = OH_Huks_UpdateSession(&handleDerive, hkdfParamSet, &inData, &outData);
    if (ohResult.errorCode != OH_HUKS_SUCCESS) {
        return ohResult;
    }
    /* Finish */
    uint8_t outDataD[COMMON_SIZE] = {0};
    struct OH_Huks_Blob outDataDerive = {COMMON_SIZE, outDataD};
    ohResult = OH_Huks_FinishSession(&handleDerive, hkdfFinishParamSet, &inData, &outDataDerive);
    return ohResult;
}

napi_value PbkdfDeriveKey(napi_env env, napi_callback_info info)
{
    struct OH_Huks_Blob genAlias = {(uint32_t)strlen("test_signVerify"), (uint8_t *)"test_signVerify"};
    struct OH_Huks_Blob inData = {(uint32_t)strlen(G_DERIVE_IN_DATA), (uint8_t *)G_DERIVE_IN_DATA};
    struct OH_Huks_ParamSet *genParamSet = nullptr;
    struct OH_Huks_ParamSet *hkdfParamSet = nullptr;
    struct OH_Huks_ParamSet *hkdfFinishParamSet = nullptr;
    OH_Huks_Result ohResult;
    do {
        ohResult = InitParamSet(&genParamSet, g_genDeriveParams, sizeof(g_genDeriveParams) /
                     sizeof(OH_Huks_Param));
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
        ohResult = InitParamSet(&hkdfParamSet, g_hkdfParams, sizeof(g_hkdfParams) /
                     sizeof(OH_Huks_Param));
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
        ohResult =InitParamSet(&hkdfFinishParamSet, g_hkdfFinishParams, sizeof(g_hkdfFinishParams) /
              sizeof(OH_Huks_Param));
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
        /* 1. Generate a key. */
        ohResult = OH_Huks_GenerateKeyItem(&genAlias, genParamSet, nullptr);
        if (ohResult.errorCode != OH_HUKS_SUCCESS) {
            break;
        }
        /* 2. Derive a key. */
        ohResult = PerformPbkdfDerivation(&genAlias, hkdfParamSet, hkdfFinishParamSet, inData);
    } while (0);
    (void)OH_Huks_DeleteKeyItem(&genAlias, genParamSet);
    (void)OH_Huks_DeleteKeyItem(&g_deriveKeyAlias, genParamSet);
    OH_Huks_FreeParamSet(&genParamSet);
    OH_Huks_FreeParamSet(&hkdfParamSet);
    OH_Huks_FreeParamSet(&hkdfFinishParamSet);

    napi_value ret;
    napi_create_int32(env, ohResult.errorCode, &ret);
    return ret;
}
```
