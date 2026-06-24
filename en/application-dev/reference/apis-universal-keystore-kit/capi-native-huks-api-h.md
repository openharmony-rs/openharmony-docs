# native_huks_api.h

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

## Overview

Declares the APIs used to access HUKS.

**File to include**: <huks/native_huks_api.h>

**Library**: libhuks_ndk.z.so

**System capability**:

- API version 20 +: SystemCapability.Security.Huks.Core
- API version 9 - 19: SystemCapability.Security.Huks

**Since**: 9

**Related module**: [HuksKeyApi](capi-hukskeyapi.md)

## Summary

### Functions

| Name| Description|
| -- | -- |
| [struct OH_Huks_Result OH_Huks_GetSdkVersion(struct OH_Huks_Blob *sdkVersion)](#oh_huks_getsdkversion) | Obtains the current HUKS SDK version number.|
| [struct OH_Huks_Result OH_Huks_GenerateKeyItem(const struct OH_Huks_Blob *keyAlias, const struct OH_Huks_ParamSet *paramSetIn, struct OH_Huks_ParamSet *paramSetOut)](#oh_huks_generatekeyitem) | Generates a key.|
| [struct OH_Huks_Result OH_Huks_ImportKeyItem(const struct OH_Huks_Blob *keyAlias, const struct OH_Huks_ParamSet *paramSet, const struct OH_Huks_Blob *key)](#oh_huks_importkeyitem) | Imports a key in plaintext.|
| [struct OH_Huks_Result OH_Huks_ImportWrappedKeyItem(const struct OH_Huks_Blob *keyAlias, const struct OH_Huks_Blob *wrappingKeyAlias, const struct OH_Huks_ParamSet *paramSet, const struct OH_Huks_Blob *wrappedKeyData)](#oh_huks_importwrappedkeyitem) | Imports a key in ciphertext.|
| [struct OH_Huks_Result OH_Huks_ExportPublicKeyItem(const struct OH_Huks_Blob *keyAlias, const struct OH_Huks_ParamSet *paramSet, struct OH_Huks_Blob *key)](#oh_huks_exportpublickeyitem) | Exports the public key.|
| [struct OH_Huks_Result OH_Huks_DeleteKeyItem(const struct OH_Huks_Blob *keyAlias, const struct OH_Huks_ParamSet *paramSet)](#oh_huks_deletekeyitem) | Deletes a key.|
| [struct OH_Huks_Result OH_Huks_GetKeyItemParamSet(const struct OH_Huks_Blob *keyAlias, const struct OH_Huks_ParamSet *paramSetIn, struct OH_Huks_ParamSet *paramSetOut)](#oh_huks_getkeyitemparamset) | Obtains the properties of a key.|
| [struct OH_Huks_Result OH_Huks_IsKeyItemExist(const struct OH_Huks_Blob *keyAlias, const struct OH_Huks_ParamSet *paramSet)](#oh_huks_iskeyitemexist) | Checks whether a key exists.|
| [struct OH_Huks_Result OH_Huks_AttestKeyItem(const struct OH_Huks_Blob *keyAlias, const struct OH_Huks_ParamSet *paramSet, struct OH_Huks_CertChain *certChain)](#oh_huks_attestkeyitem) | Obtains the certificate chain of a key. This API is open only to system applications.|
| [struct OH_Huks_Result OH_Huks_AnonAttestKeyItem(const struct OH_Huks_Blob *keyAlias, const struct OH_Huks_ParamSet *paramSet, struct OH_Huks_CertChain *certChain)](#oh_huks_anonattestkeyitem) | Obtains the certificate chain of a key.<br> This function involves time-consuming network operation. The caller can obtain the certificate chain through an asynchronous thread.|
| [struct OH_Huks_Result OH_Huks_InitSession(const struct OH_Huks_Blob *keyAlias, const struct OH_Huks_ParamSet *paramSet, struct OH_Huks_Blob *handle, struct OH_Huks_Blob *token)](#oh_huks_initsession) | Initializes a key session. This function returns a session handle (mandatory) and a challenge value (optional).|
| [struct OH_Huks_Result OH_Huks_UpdateSession(const struct OH_Huks_Blob *handle, const struct OH_Huks_ParamSet *paramSet, const struct OH_Huks_Blob *inData, struct OH_Huks_Blob *outData)](#oh_huks_updatesession) | Adds data by segment for the key operation, performs the related key operation, and outputs the processed data.|
| [struct OH_Huks_Result OH_Huks_FinishSession(const struct OH_Huks_Blob *handle, const struct OH_Huks_ParamSet *paramSet, const struct OH_Huks_Blob *inData, struct OH_Huks_Blob *outData)](#oh_huks_finishsession) | Finishes a key session.|
| [struct OH_Huks_Result OH_Huks_AbortSession(const struct OH_Huks_Blob *handle, const struct OH_Huks_ParamSet *paramSet)](#oh_huks_abortsession) | Aborts a key session.|
| [struct OH_Huks_Result OH_Huks_ListAliases(const struct OH_Huks_ParamSet *paramSet, struct OH_Huks_KeyAliasSet **outData)](#oh_huks_listaliases) | Obtains the key alias set.|
| [struct OH_Huks_Result OH_Huks_WrapKey(const struct OH_Huks_Blob *keyAlias, const struct OH_Huks_ParamSet *paramSet, struct OH_Huks_Blob *wrappedKey)](#oh_huks_wrapkey) | Exports a wrapped key.|
| [struct OH_Huks_Result OH_Huks_UnwrapKey(const struct OH_Huks_Blob *keyAlias, const struct OH_Huks_ParamSet *paramSet, struct OH_Huks_Blob *wrappedKey)](#oh_huks_unwrapkey) | Imports a wrapped key.|

## Function Description

### OH_Huks_GetSdkVersion()

```c
struct OH_Huks_Result OH_Huks_GetSdkVersion(struct OH_Huks_Blob *sdkVersion)
```

**Description**

Obtains the current HUKS SDK version number.

**Since**: 9

**Parameters**

| Name| Description|
| -- | -- |
| [struct OH_Huks_Blob](capi-hukstypeapi-oh-huks-blob.md) *sdkVersion | Pointer to the SDK version (string) obtained.|

**Returns**

| Type| Description|
| -- | -- |
| [struct OH_Huks_Result](capi-hukstypeapi-oh-huks-result.md) | Possible error codes (**errorCode**):<br>         **OH_HUKS_SUCCESS 0**: Operation successful.<br>         **OH_HUKS_ERR_CODE_ILLEGAL_ARGUMENT 401**: The value of **sdkVersion** or **sdkVersion->data** is null, or the value of **sdkVersion->size** is too small.|

### OH_Huks_GenerateKeyItem()

```c
struct OH_Huks_Result OH_Huks_GenerateKeyItem(const struct OH_Huks_Blob *keyAlias, const struct OH_Huks_ParamSet *paramSetIn, struct OH_Huks_ParamSet *paramSetOut)
```

**Description**

Generates a key.

**Since**: 9

**Parameters**

| Name| Description|
| -- | -- |
| [const struct OH_Huks_Blob](capi-hukstypeapi-oh-huks-blob.md) *keyAlias | Pointer to the alias of the key to generate. The alias must be unique in the process of the service.|
| [const struct OH_Huks_ParamSet](capi-hukstypeapi-oh-huks-paramset.md) *paramSetIn | Pointer to the parameters for generating the key.|
| [struct OH_Huks_ParamSet](capi-hukstypeapi-oh-huks-paramset.md) *paramSetOut | If a temporary key is generated, this parameter stores the key data. If a non-temporary key is generated, this parameter can be left empty.|

**Returns**

| Type| Description|
| -- | -- |
| [struct OH_Huks_Result](capi-hukstypeapi-oh-huks-result.md) | Possible error codes (**errorCode**):<br>         **OH_HUKS_SUCCESS 0**: Operation successful.<br>         **OH_HUKS_ERR_CODE_ILLEGAL_ARGUMENT 401**: The **keyAlias**, **paramSetIn**, or **paramSetOut** parameter is invalid.<br>         **OH_HUKS_ERR_CODE_FEATURE_NOT_SUPPORTED 12000001**: This feature is not supported currently.<br>         **OH_HUKS_ERR_CODE_MISSING_CRYPTO_ALG_ARGUMENT 12000002**: Failed to obtain the key parameter.<br>         **OH_HUKS_ERR_CODE_INVALID_CRYPTO_ALG_ARGUMENT 12000003**: The key parameter is invalid.<br>         **OH_HUKS_ERR_CODE_FILE_OPERATION_FAIL 12000004**: Failed to delete or write the file.<br>         **OH_HUKS_ERR_CODE_COMMUNICATION_FAIL 12000005**: IPC communication failed.<br>         **OH_HUKS_ERR_CODE_CRYPTO_FAIL 12000006**: The encryption engine fails.<br>         **OH_HUKS_ERR_CODE_ITEM_NOT_EXIST 12000011**: The basic key file does not exist.<br>         **OH_HUKS_ERR_CODE_INTERNAL_ERROR 12000012**: The device environment or input parameters are abnormal.<br>         **OH_HUKS_ERR_CODE_INSUFFICIENT_MEMORY 12000014**: Insufficient memory.<br>         **OH_HUKS_ERR_CODE_CALL_SERVICE_FAILED 12000015**: Failed to connect to the user IAM.<br>         **OH_HUKS_ERR_CODE_DEVICE_PASSWORD_UNSET 12000016**: No device password is set.<br>         **OH_HUKS_ERR_CODE_KEY_ALREADY_EXIST 12000017**: A key with the same name already exists. (This error code is added in API version 20.)<br>         **OH_HUKS_ERR_CODE_INVALID_ARGUMENT 12000018**: The group name specified by accessing the group tag is invalid. (This error code is added in API version 23.)|

### OH_Huks_ImportKeyItem()

```c
struct OH_Huks_Result OH_Huks_ImportKeyItem(const struct OH_Huks_Blob *keyAlias, const struct OH_Huks_ParamSet *paramSet, const struct OH_Huks_Blob *key)
```

**Description**

Imports a key in plaintext.

**Since**: 9

**Parameters**

| Name| Description|
| -- | -- |
| [const struct OH_Huks_Blob](capi-hukstypeapi-oh-huks-blob.md) *keyAlias | Pointer to the alias of the key to import. The alias must be unique in the process of the service.|
| [const struct OH_Huks_ParamSet](capi-hukstypeapi-oh-huks-paramset.md) *paramSet | Pointer to the properties of the key to import.|
| [const struct OH_Huks_Blob](capi-hukstypeapi-oh-huks-blob.md) *key | Pointer to the data of the key to import, complying with the format requirements of HUKS. For details, see [native_huks_type.h](capi-native-huks-type-h.md).|

**Returns**

| Type| Description|
| -- | -- |
| [struct OH_Huks_Result](capi-hukstypeapi-oh-huks-result.md) | Possible error codes (**errorCode**):<br>         **OH_HUKS_SUCCESS 0**: Operation successful.<br>         **OH_HUKS_ERR_CODE_ILLEGAL_ARGUMENT 401**: The **keyAlias**, **paramSet**, or **key** parameter is invalid.<br>         **OH_HUKS_ERR_CODE_FEATURE_NOT_SUPPORTED 12000001**: This feature is not supported currently.<br>         **OH_HUKS_ERR_CODE_MISSING_CRYPTO_ALG_ARGUMENT 12000002**: Failed to obtain the key parameter.<br>         **OH_HUKS_ERR_CODE_INVALID_CRYPTO_ALG_ARGUMENT 12000003**: The key parameter is invalid.<br>         **OH_HUKS_ERR_CODE_FILE_OPERATION_FAIL 12000004**: Failed to delete or write the file.<br>         **OH_HUKS_ERR_CODE_COMMUNICATION_FAIL 12000005**: IPC communication failed.<br>         **OH_HUKS_ERR_CODE_INTERNAL_ERROR 12000012**: The device environment or input parameters are abnormal.<br>         **OH_HUKS_ERR_CODE_INSUFFICIENT_MEMORY 12000014**: Insufficient memory.<br>         **OH_HUKS_ERR_CODE_CALL_SERVICE_FAILED 12000015**: Failed to connect to the user IAM.<br>         **OH_HUKS_ERR_CODE_KEY_ALREADY_EXIST 12000017**: A key with the same name already exists. (This error code is added in API version 20.)<br>         **OH_HUKS_ERR_CODE_INVALID_ARGUMENT 12000018**: The group name specified by accessing the group tag is invalid. (This error code is added in API version 23.)|

### OH_Huks_ImportWrappedKeyItem()

```c
struct OH_Huks_Result OH_Huks_ImportWrappedKeyItem(const struct OH_Huks_Blob *keyAlias, const struct OH_Huks_Blob *wrappingKeyAlias, const struct OH_Huks_ParamSet *paramSet, const struct OH_Huks_Blob *wrappedKeyData)
```

**Description**

Imports a key in ciphertext.

**Since**: 9

**Parameters**

| Name| Description|
| -- | -- |
| [const struct OH_Huks_Blob](capi-hukstypeapi-oh-huks-blob.md) *keyAlias | Pointer to the alias of the key to import. The alias must be unique in the process of the service.|
| [const struct OH_Huks_Blob](capi-hukstypeapi-oh-huks-blob.md) *wrappingKeyAlias | Pointer to the alias of the key used for key negotiation or digital envelope decryption. The negotiated or decrypted key is then used to decrypt the key to import.|
| [const struct OH_Huks_ParamSet](capi-hukstypeapi-oh-huks-paramset.md) *paramSet | Pointer to the parameters for importing the key in ciphertext.|
| [const struct OH_Huks_Blob](capi-hukstypeapi-oh-huks-blob.md) *wrappedKeyData | Pointer to the data of the key to import, complying with the format requirements of HUKS. For details, see [OH_Huks_AlgSuite](capi-native-huks-type-h.md#oh_huks_algsuite).|

**Returns**

| Type| Description|
| -- | -- |
| [struct OH_Huks_Result](capi-hukstypeapi-oh-huks-result.md) | Possible error codes (**errorCode**):<br>         **OH_HUKS_SUCCESS 0**: Operation successful.<br>         **OH_HUKS_ERR_CODE_ILLEGAL_ARGUMENT 401**: One or more of the **keyAlias**, **wrappingKeyAlias**, **paramSet**, and **wrappedKeyData** parameters are invalid.<br>         **OH_HUKS_ERR_CODE_FEATURE_NOT_SUPPORTED 12000001**: This feature is not supported currently.<br>         **OH_HUKS_ERR_CODE_MISSING_CRYPTO_ALG_ARGUMENT 12000002**: Failed to obtain the key parameter.<br>         **OH_HUKS_ERR_CODE_INVALID_CRYPTO_ALG_ARGUMENT 12000003**: The key parameter is invalid.<br>         **OH_HUKS_ERR_CODE_FILE_OPERATION_FAIL 12000004**: Failed to delete or write the file.<br>         **OH_HUKS_ERR_CODE_COMMUNICATION_FAIL 12000005**: IPC communication failed.<br>         **OH_HUKS_ERR_CODE_CRYPTO_FAIL 12000006**: The encryption engine fails.<br>         **OH_HUKS_ERR_CODE_INTERNAL_ERROR 12000012**: The device environment or input parameters are abnormal.<br>         **OH_HUKS_ERR_CODE_INSUFFICIENT_MEMORY 12000014**: Insufficient memory.<br>         **OH_HUKS_ERR_CODE_CALL_SERVICE_FAILED 12000015**: Failed to connect to the user IAM.<br>         **OH_HUKS_ERR_CODE_KEY_ALREADY_EXIST 12000017**: A key with the same name already exists. (This error code is added in API version 20.)<br>         **OH_HUKS_ERR_CODE_INVALID_ARGUMENT 12000018**: The group name specified by accessing the group tag is invalid. (This error code is added in API version 23.)|

### OH_Huks_ExportPublicKeyItem()

```c
struct OH_Huks_Result OH_Huks_ExportPublicKeyItem(const struct OH_Huks_Blob *keyAlias, const struct OH_Huks_ParamSet *paramSet, struct OH_Huks_Blob *key)
```

**Description**

Exports the public key.

**Since**: 9

**Parameters**

| Name| Description|
| -- | -- |
| [const struct OH_Huks_Blob](capi-hukstypeapi-oh-huks-blob.md) *keyAlias | Pointer to the alias of the public key to export. It must be the same as the alias used for generating the key.|
| [const struct OH_Huks_ParamSet](capi-hukstypeapi-oh-huks-paramset.md) *paramSet | Pointer to the parameters for exporting the public key.|
| [struct OH_Huks_Blob](capi-hukstypeapi-oh-huks-blob.md) *key | Pointer to the public key exported.|

**Returns**

| Type| Description|
| -- | -- |
| [struct OH_Huks_Result](capi-hukstypeapi-oh-huks-result.md) | Possible error codes (**errorCode**):<br>         **OH_HUKS_SUCCESS 0**: Operation successful.<br>         **OH_HUKS_ERR_CODE_ILLEGAL_ARGUMENT 401**: The **keyAlias**, **paramSet**, or **key** parameter is invalid.<br>         **OH_HUKS_ERR_CODE_FEATURE_NOT_SUPPORTED 12000001**: This feature is not supported currently.<br>         **OH_HUKS_ERR_CODE_MISSING_CRYPTO_ALG_ARGUMENT 12000002**: Failed to obtain the key parameter.<br>         **OH_HUKS_ERR_CODE_INVALID_CRYPTO_ALG_ARGUMENT 12000003**: The key parameter is invalid.<br>         **OH_HUKS_ERR_CODE_COMMUNICATION_FAIL 12000005**: IPC communication failed.<br>         **OH_HUKS_ERR_CODE_ITEM_NOT_EXIST 12000011**: The key file does not exist.<br>         **OH_HUKS_ERR_CODE_INTERNAL_ERROR 12000012**: The device environment or input parameters are abnormal.<br>         **OH_HUKS_ERR_CODE_INSUFFICIENT_MEMORY 12000014**: Insufficient memory.<br>         **OH_HUKS_ERR_CODE_INVALID_ARGUMENT 12000018**: The group name specified by accessing the group tag is invalid. (This error code is added in API version 23.)|

### OH_Huks_DeleteKeyItem()

```c
struct OH_Huks_Result OH_Huks_DeleteKeyItem(const struct OH_Huks_Blob *keyAlias, const struct OH_Huks_ParamSet *paramSet)
```

**Description**

Deletes a key.

**Since**: 9

**Parameters**

| Name| Description|
| -- | -- |
| [const struct OH_Huks_Blob](capi-hukstypeapi-oh-huks-blob.md) *keyAlias | Pointer to the alias of the key to delete. It must be the same as the alias used for generating the key.|
| [const struct OH_Huks_ParamSet](capi-hukstypeapi-oh-huks-paramset.md) *paramSet | Pointer to the parameters for deleting the key. By default, this parameter is a null pointer. The default key storage level is [OH_HUKS_AUTH_STORAGE_LEVEL_CE](capi-native-huks-type-h.md#oh_huks_authstoragelevel).|

**Returns**

| Type| Description|
| -- | -- |
| [struct OH_Huks_Result](capi-hukstypeapi-oh-huks-result.md) | Possible error codes (**errorCode**):<br>         **OH_HUKS_SUCCESS 0**: Operation successful.<br>         **OH_HUKS_ERR_CODE_ILLEGAL_ARGUMENT 401**: The **keyAlias** or **paramSet** parameter is invalid.<br>         **OH_HUKS_ERR_CODE_MISSING_CRYPTO_ALG_ARGUMENT 12000002**: Failed to obtain the key parameter.<br>         **OH_HUKS_ERR_CODE_INVALID_CRYPTO_ALG_ARGUMENT 12000003**: The key parameter is invalid.<br>         **OH_HUKS_ERR_CODE_COMMUNICATION_FAIL 12000005**: IPC communication failed.<br>         **OH_HUKS_ERR_CODE_ITEM_NOT_EXIST 12000011**: The key file does not exist.<br>         **OH_HUKS_ERR_CODE_INTERNAL_ERROR 12000012**: The device environment or input parameters are abnormal.<br>         **OH_HUKS_ERR_CODE_INSUFFICIENT_MEMORY 12000014**: Insufficient memory.<br>         **OH_HUKS_ERR_CODE_INVALID_ARGUMENT 12000018**: The group name specified by accessing the group tag is invalid. (This error code is added in API version 23.)|

### OH_Huks_GetKeyItemParamSet()

```c
struct OH_Huks_Result OH_Huks_GetKeyItemParamSet(const struct OH_Huks_Blob *keyAlias, const struct OH_Huks_ParamSet *paramSetIn, struct OH_Huks_ParamSet *paramSetOut)
```

**Description**

Obtains the properties of a key.

**Since**: 9

**Parameters**

| Name| Description|
| -- | -- |
| [const struct OH_Huks_Blob](capi-hukstypeapi-oh-huks-blob.md) *keyAlias | Pointer to the alias of the target key.|
| [const struct OH_Huks_ParamSet](capi-hukstypeapi-oh-huks-paramset.md) *paramSetIn | Pointer to the tag required for obtaining the properties. By default, this parameter is a null pointer.|
| [struct OH_Huks_ParamSet](capi-hukstypeapi-oh-huks-paramset.md) *paramSetOut | Pointer to the key properties obtained.|

**Returns**

| Type| Description|
| -- | -- |
| [struct OH_Huks_Result](capi-hukstypeapi-oh-huks-result.md) | Possible error codes (**errorCode**):<br>         **OH_HUKS_SUCCESS 0**: Operation successful.<br>         **OH_HUKS_ERR_CODE_ILLEGAL_ARGUMENT 401**: The **keyAlias**, **paramSetIn**, or **paramSetOut** parameter is invalid.<br>         **OH_HUKS_ERR_CODE_FEATURE_NOT_SUPPORTED 12000001**: This feature is not supported currently.<br>         **OH_HUKS_ERR_CODE_MISSING_CRYPTO_ALG_ARGUMENT 12000002**: Failed to obtain the key parameter.<br>         **OH_HUKS_ERR_CODE_INVALID_CRYPTO_ALG_ARGUMENT 12000003**: The key parameter is invalid.<br>         **OH_HUKS_ERR_CODE_COMMUNICATION_FAIL 12000005**: IPC communication failed.<br>         **OH_HUKS_ERR_CODE_ITEM_NOT_EXIST 12000011**: The key file does not exist.<br>         **OH_HUKS_ERR_CODE_INTERNAL_ERROR 12000012**: The device environment or input parameters are abnormal.<br>         **OH_HUKS_ERR_CODE_INSUFFICIENT_MEMORY 12000014**: Insufficient memory.<br>         **OH_HUKS_ERR_CODE_INVALID_ARGUMENT 12000018**: The group name specified by accessing the group tag is invalid. (This error code is added in API version 23.)|

### OH_Huks_IsKeyItemExist()

```c
struct OH_Huks_Result OH_Huks_IsKeyItemExist(const struct OH_Huks_Blob *keyAlias, const struct OH_Huks_ParamSet *paramSet)
```

**Description**

Checks whether a key exists.

**Since**: 9

**Parameters**

| Name| Description|
| -- | -- |
| [const struct OH_Huks_Blob](capi-hukstypeapi-oh-huks-blob.md) *keyAlias | Pointer to the alias of the key to check.|
| [const struct OH_Huks_ParamSet](capi-hukstypeapi-oh-huks-paramset.md) *paramSet | Pointer to the parameters for checking the key. By default, this parameter is a null pointer.|

**Returns**

| Type| Description|
| -- | -- |
| [struct OH_Huks_Result](capi-hukstypeapi-oh-huks-result.md) | Possible error codes (**errorCode**):<br>         **OH_HUKS_SUCCESS 0**: Operation successful.<br>         **OH_HUKS_ERR_CODE_ILLEGAL_ARGUMENT 401**: The **keyAlias** or **paramSet** parameter is invalid.<br>         **OH_HUKS_ERR_CODE_MISSING_CRYPTO_ALG_ARGUMENT 12000002**: Failed to obtain the key parameter.<br>         **OH_HUKS_ERR_CODE_INVALID_CRYPTO_ALG_ARGUMENT 12000003**: The key parameter is invalid.<br>         **OH_HUKS_ERR_CODE_COMMUNICATION_FAIL 12000005**: IPC communication failed.<br>         **OH_HUKS_ERR_CODE_ITEM_NOT_EXIST 12000011**: The key file does not exist.<br>         **OH_HUKS_ERR_CODE_INTERNAL_ERROR 12000012**: The device environment or input parameters are abnormal.<br>         **OH_HUKS_ERR_CODE_INSUFFICIENT_MEMORY 12000014**: Insufficient memory.<br>         **OH_HUKS_ERR_CODE_INVALID_ARGUMENT 12000018**: The group name specified by accessing the group tag is invalid. (This error code is added in API version 23.)|

### OH_Huks_AttestKeyItem()

```c
struct OH_Huks_Result OH_Huks_AttestKeyItem(const struct OH_Huks_Blob *keyAlias, const struct OH_Huks_ParamSet *paramSet, struct OH_Huks_CertChain *certChain)
```

**Description**

Obtains the certificate chain of a key. This API is open only to system applications.

**Required permissions**: ohos.permission.ATTEST_KEY (available only for system applications)

**Since**: 9

<!--RP1-->
> **NOTE**<br>
>
> The certificate chain generated during non-anonymous certificate key attestation may contain the device identifier (confirm the specific implementation with the vendor). If the device identifier is included, you can determine its use, retention, and destruction. It is recommended that you describe the use purpose, retention policy, and destruction method in the privacy statement.
<!--RP1End-->

**Parameters**

| Name| Description|
| -- | -- |
| [const struct OH_Huks_Blob](capi-hukstypeapi-oh-huks-blob.md) *keyAlias | Pointer to the alias of the target key.|
| [const struct OH_Huks_ParamSet](capi-hukstypeapi-oh-huks-paramset.md) *paramSet | Pointer to the parameters for obtaining the certificate chain.|
| [struct OH_Huks_CertChain](capi-hukstypeapi-oh-huks-certchain.md) *certChain | Pointer to the certificate chain obtained.|

**Returns**

| Type| Description|
| -- | -- |
| [struct OH_Huks_Result](capi-hukstypeapi-oh-huks-result.md) | Possible error codes (**errorCode**):<br>         **OH_HUKS_SUCCESS 0**: Operation successful.<br>         **OH_HUKS_ERR_CODE_PERMISSION_FAIL 201**: Permission check failed. Request the permission first.<br>         **OH_HUKS_ERR_CODE_ILLEGAL_ARGUMENT 401**: The **keyAlias**, **paramSet**, or **certChain** parameter is invalid.<br>         **OH_HUKS_ERR_CODE_FEATURE_NOT_SUPPORTED 12000001**: This feature is not supported currently.<br>         **OH_HUKS_ERR_CODE_MISSING_CRYPTO_ALG_ARGUMENT 12000002**: Failed to obtain the key parameter.<br>         **OH_HUKS_ERR_CODE_INVALID_CRYPTO_ALG_ARGUMENT 12000003**: The key parameter is invalid.<br>         **OH_HUKS_ERR_CODE_COMMUNICATION_FAIL 12000005**: IPC communication failed.<br>         **OH_HUKS_ERR_CODE_CRYPTO_FAIL 12000006**: The encryption engine fails.<br>         **OH_HUKS_ERR_CODE_ITEM_NOT_EXIST 12000011**: The key file does not exist.<br>         **OH_HUKS_ERR_CODE_INTERNAL_ERROR 12000012**: The device environment or input parameters are abnormal.<br>         **OH_HUKS_ERR_CODE_INSUFFICIENT_MEMORY 12000014**: Insufficient memory.<br>         **OH_HUKS_ERR_CODE_INVALID_ARGUMENT 12000018**: The group name specified by accessing the group tag is invalid. (This error code is added in API version 23.)|

### OH_Huks_AnonAttestKeyItem()

```c
struct OH_Huks_Result OH_Huks_AnonAttestKeyItem(const struct OH_Huks_Blob *keyAlias, const struct OH_Huks_ParamSet *paramSet, struct OH_Huks_CertChain *certChain)
```

**Description**

Obtains the certificate chain of a key.<br> This function involves time-consuming network operation. The caller can obtain the certificate chain through an asynchronous thread.

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [const struct OH_Huks_Blob](capi-hukstypeapi-oh-huks-blob.md) *keyAlias | Pointer to the alias of the target key.|
| [const struct OH_Huks_ParamSet](capi-hukstypeapi-oh-huks-paramset.md) *paramSet | Pointer to the parameters for obtaining the certificate chain.|
| [struct OH_Huks_CertChain](capi-hukstypeapi-oh-huks-certchain.md) *certChain | Pointer to the certificate chain obtained.|

**Returns**

| Type| Description|
| -- | -- |
| [struct OH_Huks_Result](capi-hukstypeapi-oh-huks-result.md) | Possible error codes (**errorCode**):<br>         **OH_HUKS_SUCCESS 0**: Operation successful.<br>         **OH_HUKS_ERR_CODE_ILLEGAL_ARGUMENT 401**: The **keyAlias**, **paramSet**, or **certChain** parameter is invalid.<br>         **OH_HUKS_ERR_CODE_FEATURE_NOT_SUPPORTED 12000001**: This feature is not supported currently.<br>         **OH_HUKS_ERR_CODE_MISSING_CRYPTO_ALG_ARGUMENT 12000002**: Failed to obtain the key parameter.<br>         **OH_HUKS_ERR_CODE_INVALID_CRYPTO_ALG_ARGUMENT 12000003**: The key parameter is invalid.<br>         **OH_HUKS_ERR_CODE_COMMUNICATION_FAIL 12000005**: IPC communication failed.<br>         **OH_HUKS_ERR_CODE_CRYPTO_FAIL 12000006**: The encryption engine fails.<br>         **OH_HUKS_ERR_CODE_ITEM_NOT_EXIST 12000011**: The key file does not exist.<br>         **OH_HUKS_ERR_CODE_INTERNAL_ERROR 12000012**: The device environment or input parameters are abnormal.<br>         **OH_HUKS_ERR_CODE_INSUFFICIENT_MEMORY 12000014**: Insufficient memory.<br>         **OH_HUKS_ERR_CODE_INVALID_ARGUMENT 12000018**: The group name specified by accessing the group tag is invalid. (This error code is added in API version 23.)|

### OH_Huks_InitSession()

```c
struct OH_Huks_Result OH_Huks_InitSession(const struct OH_Huks_Blob *keyAlias, const struct OH_Huks_ParamSet *paramSet, struct OH_Huks_Blob *handle, struct OH_Huks_Blob *token)
```

**Description**

Initializes a key session. This function returns a session handle (mandatory) and a challenge value (optional).

**Since**: 9

**Parameters**

| Name| Description|
| -- | -- |
| [const struct OH_Huks_Blob](capi-hukstypeapi-oh-huks-blob.md) *keyAlias | Pointer to the alias of the key to be operated.|
| [const struct OH_Huks_ParamSet](capi-hukstypeapi-oh-huks-paramset.md) *paramSet | Pointer to the parameters for the initialization operation.|
| [struct OH_Huks_Blob](capi-hukstypeapi-oh-huks-blob.md) *handle | Pointer to the handle of the key session. This handle is required for subsequent operations of the same key, including [OH_Huks_UpdateSession](capi-native-huks-api-h.md#oh_huks_updatesession), [OH_Huks_FinishSession](capi-native-huks-api-h.md#oh_huks_finishsession) and [OH_Huks_AbortSession](capi-native-huks-api-h.md#oh_huks_abortsession).|
| [struct OH_Huks_Blob](capi-hukstypeapi-oh-huks-blob.md) *token | Pointer to the token used for key access control.|

**Returns**

| Type| Description|
| -- | -- |
| [struct OH_Huks_Result](capi-hukstypeapi-oh-huks-result.md) | Possible error codes (**errorCode**):<br>         **OH_HUKS_SUCCESS 0**: Operation successful.<br>         **OH_HUKS_ERR_CODE_ILLEGAL_ARGUMENT 401**: The **keyAlias**, **paramSet**, **handle**, or **token** parameter is invalid.<br>         **OH_HUKS_ERR_CODE_FEATURE_NOT_SUPPORTED 12000001**: This feature is not supported currently.<br>         **OH_HUKS_ERR_CODE_MISSING_CRYPTO_ALG_ARGUMENT 12000002**: Failed to obtain the key parameter.<br>         **OH_HUKS_ERR_CODE_INVALID_CRYPTO_ALG_ARGUMENT 12000003**: The key parameter is invalid.<br>         **OH_HUKS_ERR_CODE_COMMUNICATION_FAIL 12000005**: IPC communication failed.<br>         **OH_HUKS_ERR_CODE_CRYPTO_FAIL 12000006**: The encryption engine fails.<br>         **OH_HUKS_ERR_CODE_SESSION_LIMIT 12000010**: Hit the session limit.<br>         **OH_HUKS_ERR_CODE_ITEM_NOT_EXIST 12000011**: The key file does not exist.<br>         **OH_HUKS_ERR_CODE_INTERNAL_ERROR 12000012**: The device environment or input parameters are abnormal.<br>         **OH_HUKS_ERR_CODE_INSUFFICIENT_MEMORY 12000014**: Insufficient memory.<br>         **OH_HUKS_ERR_CODE_INVALID_ARGUMENT 12000018**: The specified AEAD length is invalid or the group name specified by accessing the group tag is invalid. (This error code is added in API version 22.)<br>         **OH_HUKS_ERR_CODE_EXTERNAL_MODULE 12000020**: The provider or UKey internal execution fails. (This error code is added in API version 22.)<br>         **OH_HUKS_ERR_CODE_PIN_LOCKED 12000021**: The PIN is locked. (This error code is added in API version 22.)<br>         **OH_HUKS_ERR_CODE_PIN_NO_AUTH 12000023**: The PIN authentication fails. (This error code is added in API version 22.)<br>         **OH_HUKS_ERR_CODE_BUSY 12000024**: The resource in the provider or UKey is being used. (This error code is added in API version 22.) |

**Reference**

[OH_Huks_UpdateSession](capi-native-huks-api-h.md#oh_huks_updatesession)

[OH_Huks_FinishSession](capi-native-huks-api-h.md#oh_huks_finishsession)

[OH_Huks_AbortSession](capi-native-huks-api-h.md#oh_huks_abortsession)


### OH_Huks_UpdateSession()

```c
struct OH_Huks_Result OH_Huks_UpdateSession(const struct OH_Huks_Blob *handle, const struct OH_Huks_ParamSet *paramSet, const struct OH_Huks_Blob *inData, struct OH_Huks_Blob *outData)
```

**Description**

Adds data by segment for the key operation, performs the related key operation, and outputs the processed data.

**Since**: 9

**Parameters**

| Name| Description|
| -- | -- |
| [const struct OH_Huks_Blob](capi-hukstypeapi-oh-huks-blob.md) *handle | Pointer to the key session handle, which is returned by [OH_Huks_InitSession](capi-native-huks-api-h.md#oh_huks_initsession).|
| [const struct OH_Huks_ParamSet](capi-hukstypeapi-oh-huks-paramset.md) *paramSet | Pointer to the parameters required for the key operation.|
| [const struct OH_Huks_Blob](capi-hukstypeapi-oh-huks-blob.md) *inData | Pointer to the data to be processed. If there is a large amount of data to be processed, you can call this function multiple times to process data by segment.|
| [struct OH_Huks_Blob](capi-hukstypeapi-oh-huks-blob.md) *outData | Pointer to the output data.|

**Returns**

| Type| Description|
| -- | -- |
| [struct OH_Huks_Result](capi-hukstypeapi-oh-huks-result.md) | Possible error codes (**errorCode**):<br>         **OH_HUKS_SUCCESS 0**: Operation successful.<br>         **OH_HUKS_ERR_CODE_ILLEGAL_ARGUMENT 401**: Invalid **handle**, **paramSet**, **inData**, or **outData**.<br>         **OH_HUKS_ERR_CODE_FEATURE_NOT_SUPPORTED 12000001**: This feature is not supported currently.<br>         **OH_HUKS_ERR_CODE_MISSING_CRYPTO_ALG_ARGUMENT 12000002**: Failed to obtain the key parameter.<br>         **OH_HUKS_ERR_CODE_INVALID_CRYPTO_ALG_ARGUMENT 12000003**: The key parameter is invalid.<br>         **OH_HUKS_ERR_CODE_COMMUNICATION_FAIL 12000005**: IPC communication failed.<br>         **OH_HUKS_ERR_CODE_CRYPTO_FAIL 12000006**: The encryption engine fails.<br>         **OH_HUKS_ERR_CODE_KEY_AUTH_PERMANENTLY_INVALIDATED 12000007**: Failed to verify the access token information.<br>         **OH_HUKS_ERR_CODE_KEY_AUTH_VERIFY_FAILED 12000008**: Failed to verify the authentication token.<br>         **OH_HUKS_ERR_CODE_KEY_AUTH_TIME_OUT 12000009**: The authentication token times out.<br>         **OH_HUKS_ERR_CODE_ITEM_NOT_EXIST 12000011**: The key file or the handle does not exist.<br>         **OH_HUKS_ERR_CODE_INTERNAL_ERROR 12000012**: The device environment or input parameters are abnormal.<br>         **OH_HUKS_ERR_CODE_CREDENTIAL_NOT_EXIST 12000013**: The certificate does not exist.<br>         **OH_HUKS_ERR_CODE_INSUFFICIENT_MEMORY 12000014**: Insufficient memory.<br>         **OH_HUKS_ERR_CODE_DEVICE_PASSWORD_UNSET 12000016**: No device password is set.<br>         **OH_HUKS_ERR_CODE_INVALID_ARGUMENT 12000018**: The group name specified by accessing the group tag is invalid. (This error code is added in API version 23.)<br>         **OH_HUKS_ERR_CODE_EXTERNAL_MODULE 12000020**: The provider or UKey internal execution fails. (This error code is added in API version 22.)<br>         **OH_HUKS_ERR_CODE_PIN_LOCKED 12000021**: The PIN is locked. (This error code is added in API version 22.)<br>         **OH_HUKS_ERR_CODE_PIN_NO_AUTH 12000023**: The PIN authentication fails. (This error code is added in API version 22.)<br>         **OH_HUKS_ERR_CODE_BUSY 12000024**: The resource in the provider or UKey is being used. (This error code is added in API version 22.) |

**Reference**

[OH_Huks_InitSession](capi-native-huks-api-h.md#oh_huks_initsession)

[OH_Huks_FinishSession](capi-native-huks-api-h.md#oh_huks_finishsession)

[OH_Huks_AbortSession](capi-native-huks-api-h.md#oh_huks_abortsession)


### OH_Huks_FinishSession()

```c
struct OH_Huks_Result OH_Huks_FinishSession(const struct OH_Huks_Blob *handle, const struct OH_Huks_ParamSet *paramSet, const struct OH_Huks_Blob *inData, struct OH_Huks_Blob *outData)
```

**Description**

Finishes a key session.

**Since**: 9

**Parameters**

| Name| Description|
| -- | -- |
| [const struct OH_Huks_Blob](capi-hukstypeapi-oh-huks-blob.md) *handle | Pointer to the key session handle, which is returned by [OH_Huks_InitSession](capi-native-huks-api-h.md#oh_huks_initsession).|
| [const struct OH_Huks_ParamSet](capi-hukstypeapi-oh-huks-paramset.md) *paramSet | Pointer to the parameters required for the key operation.|
| [const struct OH_Huks_Blob](capi-hukstypeapi-oh-huks-blob.md) *inData | Pointer to the data to be passed in.|
| [struct OH_Huks_Blob](capi-hukstypeapi-oh-huks-blob.md) *outData | Pointer to the output data.|

**Returns**

| Type| Description|
| -- | -- |
| [struct OH_Huks_Result](capi-hukstypeapi-oh-huks-result.md) | Possible error codes (**errorCode**):<br>         **OH_HUKS_SUCCESS 0**: Operation successful.<br>         **OH_HUKS_ERR_CODE_ILLEGAL_ARGUMENT 401**: Invalid **handle**, **paramSet**, **inData**, or **outData**.<br>         **OH_HUKS_ERR_CODE_FEATURE_NOT_SUPPORTED 12000001**: This feature is not supported currently.<br>         **OH_HUKS_ERR_CODE_MISSING_CRYPTO_ALG_ARGUMENT 12000002**: Failed to obtain the key parameter.<br>         **OH_HUKS_ERR_CODE_INVALID_CRYPTO_ALG_ARGUMENT 12000003**: The key parameter is invalid.<br>         **OH_HUKS_ERR_CODE_COMMUNICATION_FAIL 12000005**: IPC communication failed.<br>         **OH_HUKS_ERR_CODE_CRYPTO_FAIL 12000006**: The encryption engine fails.<br>         **OH_HUKS_ERR_CODE_KEY_AUTH_PERMANENTLY_INVALIDATED 12000007**: Failed to verify the access token information.<br>         **OH_HUKS_ERR_CODE_KEY_AUTH_VERIFY_FAILED 12000008**: Failed to verify the authentication token.<br>         **OH_HUKS_ERR_CODE_KEY_AUTH_TIME_OUT 12000009**: The authentication token times out.<br>         **OH_HUKS_ERR_CODE_ITEM_NOT_EXIST 12000011**: The key file or the handle does not exist.<br>         **OH_HUKS_ERR_CODE_INTERNAL_ERROR 12000012**: The device environment or input parameters are abnormal.<br>         **OH_HUKS_ERR_CODE_CREDENTIAL_NOT_EXIST 12000013**: The certificate does not exist.<br>         **OH_HUKS_ERR_CODE_INSUFFICIENT_MEMORY 12000014**: Insufficient memory.<br>         **OH_HUKS_ERR_CODE_DEVICE_PASSWORD_UNSET 12000016**: No device password is set.<br>         **OH_HUKS_ERR_CODE_KEY_ALREADY_EXIST 12000017**: A key with the same name already exists. (This error code is added in API version 20.)<br>         **OH_HUKS_ERR_CODE_INVALID_ARGUMENT 12000018**: The group name specified by accessing the group tag is invalid. (This error code is added in API version 23.)<br>         **OH_HUKS_ERR_CODE_EXTERNAL_MODULE 12000020**: The provider or UKey internal execution fails. (This error code is added in API version 22.)<br>         **OH_HUKS_ERR_CODE_PIN_LOCKED 12000021**: The PIN is locked. (This error code is added in API version 22.)<br>         **OH_HUKS_ERR_CODE_PIN_NO_AUTH 12000023**: The PIN authentication fails. (This error code is added in API version 22.)<br>         **OH_HUKS_ERR_CODE_BUSY 12000024**: The resource in the provider or UKey is being used. (This error code is added in API version 22.) |

**Reference**

[OH_Huks_InitSession](capi-native-huks-api-h.md#oh_huks_initsession)

[OH_Huks_UpdateSession](capi-native-huks-api-h.md#oh_huks_updatesession)

[OH_Huks_AbortSession](capi-native-huks-api-h.md#oh_huks_abortsession)


### OH_Huks_AbortSession()

```c
struct OH_Huks_Result OH_Huks_AbortSession(const struct OH_Huks_Blob *handle, const struct OH_Huks_ParamSet *paramSet)
```

**Description**

Aborts a key session.

**Since**: 9

**Parameters**

| Name| Description|
| -- | -- |
| [const struct OH_Huks_Blob](capi-hukstypeapi-oh-huks-blob.md) *handle | Pointer to the key session handle, which is returned by [OH_Huks_InitSession](capi-native-huks-api-h.md#oh_huks_initsession).|
| [const struct OH_Huks_ParamSet](capi-hukstypeapi-oh-huks-paramset.md) *paramSet | Pointer to the parameters for aborting the key session. By default, this parameter is a null pointer.|

**Returns**

| Type| Description|
| -- | -- |
| [struct OH_Huks_Result](capi-hukstypeapi-oh-huks-result.md) | Possible error codes (**errorCode**):<br>         **OH_HUKS_SUCCESS 0**: Operation successful.<br>         **OH_HUKS_ERR_CODE_ILLEGAL_ARGUMENT 401**: The **handle** or **paramSet** parameter is invalid.<br>         **OH_HUKS_ERR_CODE_MISSING_CRYPTO_ALG_ARGUMENT 12000002**: Failed to obtain the key parameter.<br>         **OH_HUKS_ERR_CODE_INVALID_CRYPTO_ALG_ARGUMENT 12000003**: The key parameter is invalid.<br>         **OH_HUKS_ERR_CODE_COMMUNICATION_FAIL 12000005**: IPC communication failed.<br>         **OH_HUKS_ERR_CODE_ITEM_NOT_EXIST 12000011**: The key file or the handle does not exist.<br>         **OH_HUKS_ERR_CODE_INTERNAL_ERROR 12000012**: The device environment or input parameters are abnormal.<br>         **OH_HUKS_ERR_CODE_CREDENTIAL_NOT_EXIST 12000013**: The certificate does not exist.<br>         **OH_HUKS_ERR_CODE_INSUFFICIENT_MEMORY 12000014**: Insufficient memory.<br>         **OH_HUKS_ERR_CODE_INVALID_ARGUMENT 12000018**: The group name specified by accessing the group tag is invalid. (This error code is added in API version 23.)<br>         **OH_HUKS_ERR_CODE_EXTERNAL_MODULE 12000020**: The provider or UKey internal execution fails. (This error code is added in API version 22.)<br>         **OH_HUKS_ERR_CODE_BUSY 12000024**: The resource in the provider or UKey is being used. (This error code is added in API version 22.) |

**Reference**

[OH_Huks_InitSession](capi-native-huks-api-h.md#oh_huks_initsession)

[OH_Huks_UpdateSession](capi-native-huks-api-h.md#oh_huks_updatesession)

[OH_Huks_FinishSession](capi-native-huks-api-h.md#oh_huks_finishsession)



### OH_Huks_ListAliases()

```c
struct OH_Huks_Result OH_Huks_ListAliases(const struct OH_Huks_ParamSet *paramSet, struct OH_Huks_KeyAliasSet **outData)
```

**Description**

Obtains the key alias set.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [const struct OH_Huks_ParamSet](capi-hukstypeapi-oh-huks-paramset.md) *paramSet | Pointer to the parameters for obtaining the key alias set. By default, this parameter is a null pointer.|
| [struct OH_Huks_KeyAliasSet](capi-hukstypeapi-oh-huks-keyaliasset.md) **outData | Double pointer to the obtained key alias set. After the key alias set is used, you need to use [OH_Huks_FreeKeyAliasSet](capi-native-huks-param-h.md#oh_huks_freekeyaliasset) to release the memory allocated by the system.|

**Returns**

| Type| Description|
| -- | -- |
| [struct OH_Huks_Result](capi-hukstypeapi-oh-huks-result.md) | Possible error codes (**errorCode**):<br>         **OH_HUKS_SUCCESS 0**: Operation successful.<br>         **OH_HUKS_ERR_CODE_ILLEGAL_ARGUMENT 401**: The **paramSet** or **outData** parameter is invalid.<br>         **OH_HUKS_ERR_CODE_COMMUNICATION_FAIL 12000005**: IPC communication failed.<br>         **OH_HUKS_ERR_CODE_INTERNAL_ERROR 12000012**: The device environment or input parameters are abnormal.<br>         **OH_HUKS_ERR_CODE_INSUFFICIENT_MEMORY 12000014**: Insufficient memory.<br>         **OH_HUKS_ERR_CODE_INVALID_ARGUMENT 12000018**: The group name specified by accessing the group tag is invalid. (This error code is added in API version 23.)|

### OH_Huks_WrapKey()

```c
struct OH_Huks_Result OH_Huks_WrapKey(const struct OH_Huks_Blob *keyAlias, const struct OH_Huks_ParamSet *paramSet, struct OH_Huks_Blob *wrappedKey)
```

**Description**

Exports a wrapped key.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [const struct OH_Huks_Blob](capi-hukstypeapi-oh-huks-blob.md) *keyAlias | Pointer to the alias of the key to export.|
| [const struct OH_Huks_ParamSet](capi-hukstypeapi-oh-huks-paramset.md) *paramSet | Pointer to the parameters for encrypting the exported key.|
| [struct OH_Huks_Blob](capi-hukstypeapi-oh-huks-blob.md) *wrappedKey | Pointer to the wrapped key to export.|

**Returns**

| Type| Description|
| -- | -- |
| [struct OH_Huks_Result](capi-hukstypeapi-oh-huks-result.md) | Possible error codes (**errorCode**):<br>         **OH_HUKS_SUCCESS 0**: Operation successful.<br>         **OH_HUKS_ERR_CODE_NOT_SUPPORTED_API 801**: The API is not supported.<br>         **OH_HUKS_ERR_CODE_FILE_OPERATION_FAIL 12000004**: Failed to delete or write the file.<br>         **OH_HUKS_ERR_CODE_COMMUNICATION_FAIL 12000005**: IPC communication failed.<br>         **OH_HUKS_ERR_CODE_ITEM_NOT_EXIST 12000011**: The key file does not exist.<br>         **OH_HUKS_ERR_CODE_INTERNAL_ERROR 12000012**: The device environment or input parameters are abnormal.<br>         **OH_HUKS_ERR_CODE_INSUFFICIENT_MEMORY 12000014**: Insufficient memory.<br>         **OH_HUKS_ERR_CODE_INVALID_ARGUMENT 12000018**: The key alias, parameter set, or wrapped key is invalid.|

### OH_Huks_UnwrapKey()

```c
struct OH_Huks_Result OH_Huks_UnwrapKey(const struct OH_Huks_Blob *keyAlias, const struct OH_Huks_ParamSet *paramSet, struct OH_Huks_Blob *wrappedKey)
```

**Description**

Imports a wrapped key.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [const struct OH_Huks_Blob](capi-hukstypeapi-oh-huks-blob.md) *keyAlias | Pointer to the alias of the key to import. The alias must be unique in the service process. Otherwise, the key will be overwritten.|
| [const struct OH_Huks_ParamSet](capi-hukstypeapi-oh-huks-paramset.md) *paramSet | Pointer to the parameters for encrypting the imported key.|
| [struct OH_Huks_Blob](capi-hukstypeapi-oh-huks-blob.md) *wrappedKey | Pointer to the wrapped key to import.|

**Returns**

| Type| Description|
| -- | -- |
| [struct OH_Huks_Result](capi-hukstypeapi-oh-huks-result.md) | Possible error codes (**errorCode**):<br>         **OH_HUKS_SUCCESS 0**: Operation successful.<br>         **OH_HUKS_ERR_CODE_NOT_SUPPORTED_API 801**: The API is not supported.<br>         **OH_HUKS_ERR_CODE_FILE_OPERATION_FAIL 12000004**: Failed to delete or write the file.<br>         **OH_HUKS_ERR_CODE_COMMUNICATION_FAIL 12000005**: IPC communication failed.<br>         **OH_HUKS_ERR_CODE_INTERNAL_ERROR 12000012**: The device environment or input parameters are abnormal.<br>         **OH_HUKS_ERR_CODE_INSUFFICIENT_MEMORY 12000014**: Insufficient memory.<br>         **OH_HUKS_ERR_CODE_CALL_SERVICE_FAILED 12000015**: Failed to connect to the user IAM.<br>         **OH_HUKS_ERR_CODE_INVALID_ARGUMENT 12000018**: The key alias, parameter set, or wrapped key is invalid.|
