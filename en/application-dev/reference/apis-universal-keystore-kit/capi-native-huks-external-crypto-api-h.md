# native_huks_external_crypto_api.h

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

## Overview

Defines the OpenHarmony Universal KeyStore (HUKS) APIs for external key management extensions.

**File to include**: <huks/native_huks_external_crypto_api.h>

**Library**: libhuks_external_crypto.z.so

**System capability**: SystemCapability.Security.Huks.CryptoExtension

**Since**: 22

**Related modules**: [HuksExternalCryptoApi](capi-huksexternalcryptoapi.md)

## Summary

### Functions

| Name| Description|
| -- | -- |
| [struct OH_Huks_Result OH_Huks_RegisterProvider(const struct OH_Huks_Blob *providerName, const OH_Huks_ExternalCryptoParamSet *paramSet)](#oh_huks_registerprovider) | Registers an external key management extension provider.|
| [struct OH_Huks_Result OH_Huks_UnregisterProvider(const struct OH_Huks_Blob *providerName, const OH_Huks_ExternalCryptoParamSet *paramSet)](#oh_huks_unregisterprovider) | Unregisters an external key management extension provider.|
| [struct OH_Huks_Result OH_Huks_OpenResource(const struct OH_Huks_Blob *resourceId, const OH_Huks_ExternalCryptoParamSet *paramSet)](#oh_huks_openresource) | Opens a resource based on the specified resource ID.<br> Note: The opened resource must be closed using [OH_Huks_CloseResource](#oh_huks_closeresource).|
| [struct OH_Huks_Result OH_Huks_CloseResource(const struct OH_Huks_Blob *resourceId, const OH_Huks_ExternalCryptoParamSet *paramSet)](#oh_huks_closeresource) | Closes a resource based on the specified resource ID.|
| [struct OH_Huks_Result OH_Huks_GetUkeyPinAuthState(const struct OH_Huks_Blob *resourceId, const OH_Huks_ExternalCryptoParamSet *paramSet, OH_Huks_ExternalPinAuthState *authState)](#oh_huks_getukeypinauthstate) | Obtains the PIN authorization state of the specified Ukey resource ID.|
| [struct OH_Huks_Result OH_Huks_GetProperty(const struct OH_Huks_Blob *resourceId, const struct OH_Huks_Blob *propertyId, const OH_Huks_ExternalCryptoParamSet *paramSetIn, OH_Huks_ExternalCryptoParamSet **paramSetOut)](#oh_huks_getproperty) | Obtains the property information of the external key management extension provider.|
| [struct OH_Huks_Result OH_Huks_InitExternalCryptoParamSet(OH_Huks_ExternalCryptoParamSet **paramSet)](#oh_huks_initexternalcryptoparamset) | Initializes a parameter set.|
| [struct OH_Huks_Result OH_Huks_AddExternalCryptoParams(OH_Huks_ExternalCryptoParamSet *paramSet, const OH_Huks_ExternalCryptoParam *params, uint32_t paramCnt)](#oh_huks_addexternalcryptoparams) | Adds parameters to a parameter set.|
| [struct OH_Huks_Result OH_Huks_BuildExternalCryptoParamSet(OH_Huks_ExternalCryptoParamSet **paramSet)](#oh_huks_buildexternalcryptoparamset) | Builds a parameter set.|
| [void OH_Huks_FreeExternalCryptoParamSet(OH_Huks_ExternalCryptoParamSet **paramSet)](#oh_huks_freeexternalcryptoparamset) | Destroys a parameter set and releases related memory.|
| [struct OH_Huks_Result OH_Huks_GetExternalCryptoParam(OH_Huks_ExternalCryptoParamSet *paramSet, const uint32_t tag, OH_Huks_ExternalCryptoParam **param)](#oh_huks_getexternalcryptoparam) | Obtains a specified parameter from a parameter set.|

## Function Description

### OH_Huks_RegisterProvider()

```c
struct OH_Huks_Result OH_Huks_RegisterProvider(const struct OH_Huks_Blob *providerName, const OH_Huks_ExternalCryptoParamSet *paramSet)
```

**Description**

Registers an external key management extension provider.

**Required permissions**: ohos.permission.CRYPTO_EXTENSION_REGISTER

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [const struct OH_Huks_Blob](capi-hukstypeapi-oh-huks-blob.md) *providerName | Name of the provider.|
| [const OH_Huks_ExternalCryptoParamSet](capi-huksexternalcryptotypeapi-oh-huks-externalcryptoparamset.md) *paramSet | Pointer to the registration parameters.|

**Returns**

| Type| Description|
| -- | -- |
| [struct OH_Huks_Result](capi-hukstypeapi-oh-huks-result.md) | Possible error codes (**errorCode**):<br>         **OH_HUKS_SUCCESS 0**: Operation successful.<br>         **OH_HUKS_ERR_CODE_PERMISSION_FAIL 201**: Permission verification fails. Apply for the required permission first.<br>         **OH_HUKS_ERR_CODE_NOT_SUPPORTED_API 801**: Unsupported API.<br>         **OH_HUKS_ERR_CODE_MISSING_CRYPTO_ALG_ARGUMENT 12000002**: Failed to obtain the provider parameters.<br>         **OH_HUKS_ERR_CODE_COMMUNICATION_FAIL 12000005**: IPC communication failed.<br>         **OH_HUKS_ERR_CODE_INSUFFICIENT_MEMORY 12000014**: Insufficient memory.<br>         **OH_HUKS_ERR_CODE_ILLEGAL_ARGUMENT 12000018**: Invalid **providerName** or **paramSet**.<br>         **OH_HUKS_ERR_CODE_ITEM_NOT_EXIST 12000019**: The provider has been registered.<br>         **OH_HUKS_ERR_CODE_EXTERNAL_ERROR 12000020**: An error occurs in the dependent module.<br>         **OH_HUKS_ERR_CODE_EXCEED_LIMIT 12000025**: The number of providers exceeds the upper limit.|

### OH_Huks_UnregisterProvider()

```c
struct OH_Huks_Result OH_Huks_UnregisterProvider(const struct OH_Huks_Blob *providerName, const OH_Huks_ExternalCryptoParamSet *paramSet)
```

**Description**

Unregisters an external key management extension provider.

**Required permissions**: ohos.permission.CRYPTO_EXTENSION_REGISTER

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [const struct OH_Huks_Blob](capi-hukstypeapi-oh-huks-blob.md) *providerName | Name of the provider.|
| [const OH_Huks_ExternalCryptoParamSet](capi-huksexternalcryptotypeapi-oh-huks-externalcryptoparamset.md) *paramSet | Pointer to the registration parameters.|

**Returns**

| Type| Description|
| -- | -- |
| [struct OH_Huks_Result](capi-hukstypeapi-oh-huks-result.md) | Possible error codes (**errorCode**):<br>         **OH_HUKS_SUCCESS 0**: Operation successful.<br>         **OH_HUKS_ERR_CODE_PERMISSION_FAIL 201**: Permission verification fails. Apply for the required permission first.<br>         **OH_HUKS_ERR_CODE_NOT_SUPPORTED_API 801**: Unsupported API.<br>         **OH_HUKS_ERR_CODE_COMMUNICATION_FAIL 12000005**: IPC communication failed.<br>         **OH_HUKS_ERR_CODE_ITEM_NOT_EXIST 12000011**: The specified provider is not found.<br>         **OH_HUKS_ERR_CODE_INTERNAL_ERROR = 12000012**: An internal system error occurs. The key management extension module is not loaded.<br>          **OH_HUKS_ERR_CODE_INSUFFICIENT_MEMORY 12000014**: Insufficient memory.<br>         **OH_HUKS_ERR_CODE_ILLEGAL_ARGUMENT 12000018**: Invalid **providerName**.|

### OH_Huks_OpenResource()

```c
struct OH_Huks_Result OH_Huks_OpenResource(const struct OH_Huks_Blob *resourceId, const OH_Huks_ExternalCryptoParamSet *paramSet)
```

**Description**

Opens a resource based on the specified resource ID.<br> Note: The opened resource must be closed using [OH_Huks_CloseResource](#oh_huks_closeresource).

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [const struct OH_Huks_Blob](capi-hukstypeapi-oh-huks-blob.md) *resourceId | Resource ID of the specified provider.|
| [const OH_Huks_ExternalCryptoParamSet](capi-huksexternalcryptotypeapi-oh-huks-externalcryptoparamset.md) *paramSet | Pointer to the handle operation parameters.|

**Returns**

| Type| Description|
| -- | -- |
| [struct OH_Huks_Result](capi-hukstypeapi-oh-huks-result.md) | Possible error codes (**errorCode**):<br>         **OH_HUKS_SUCCESS 0**: Operation successful.<br>         **OH_HUKS_ERR_CODE_NOT_SUPPORTED_API 801**: Unsupported API.<br>         **OH_HUKS_ERR_CODE_COMMUNICATION_FAIL 12000005**: IPC communication failed.<br>         **OH_HUKS_ERR_CODE_CRYPTO_FAIL 12000006**: Ukey driver error.<br>         **OH_HUKS_ERR_CODE_ITEM_NOT_EXIST 12000011**: The cached resource handle is not found. Open the resource based on the resource ID first.<br>      **OH_HUKS_ERR_CODE_INTERNAL_ERROR 12000012**: An internal system error occurs. The processing function is not found.<br>      **OH_HUKS_ERR_CODE_INSUFFICIENT_MEMORY 12000014**: Insufficient memory.<br>         **OH_HUKS_ERR_CODE_KEY_ALREADY_EXIST 12000017**: The resource is already open.<br>  **OH_HUKS_ERR_CODE_ILLEGAL_ARGUMENT 12000018**: Invalid **resourceId** or **paramSet**.<br>         **OH_HUKS_ERR_CODE_EXTERNAL_ERROR 12000020**: Provider execution fails.<br>           **OH_HUKS_ERR_CODE_BUSY 12000024**: The provider or Ukey is busy.<br>         **OH_HUKS_ERR_CODE_EXCEED_LIMIT 12000025**: The number of opened resources exceeds the limit.|

### OH_Huks_CloseResource()

```c
struct OH_Huks_Result OH_Huks_CloseResource(const struct OH_Huks_Blob *resourceId, const OH_Huks_ExternalCryptoParamSet *paramSet)
```

**Description**

Closes a resource based on the specified resource ID.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [const struct OH_Huks_Blob](capi-hukstypeapi-oh-huks-blob.md) *resourceId | Resource ID of the specified provider.|
| [const OH_Huks_ExternalCryptoParamSet](capi-huksexternalcryptotypeapi-oh-huks-externalcryptoparamset.md) *paramSet | Pointer to the handle operation parameters.|

**Returns**

| Type| Description|
| -- | -- |
| [struct OH_Huks_Result](capi-hukstypeapi-oh-huks-result.md) | Possible error codes (**errorCode**):<br>         **OH_HUKS_SUCCESS 0**: Operation successful.<br>         **OH_HUKS_ERR_CODE_NOT_SUPPORTED_API 801**: Unsupported API.<br>         **OH_HUKS_ERR_CODE_COMMUNICATION_FAIL 12000005**: IPC communication failed.<br>         **OH_HUKS_ERR_CODE_CRYPTO_FAIL 12000006**: Ukey driver error.<br>          **OH_HUKS_ERR_CODE_INTERNAL_ERROR 12000012**: An internal system error occurs. The processing function is not found.<br>       **OH_HUKS_ERR_CODE_INSUFFICIENT_MEMORY 12000014**: Insufficient memory.<br>         **OH_HUKS_ERR_CODE_ILLEGAL_ARGUMENT 12000018**: Invalid **resourceId** or **paramSet**.<br>         **OH_HUKS_ERR_CODE_EXTERNAL_ERROR 12000020**: Provider execution fails.<br>         **OH_HUKS_ERR_CODE_BUSY 12000024**: The provider or Ukey is busy.|

### OH_Huks_GetUkeyPinAuthState()

```c
struct OH_Huks_Result OH_Huks_GetUkeyPinAuthState(const struct OH_Huks_Blob *resourceId, const OH_Huks_ExternalCryptoParamSet *paramSet, OH_Huks_ExternalPinAuthState *authState)
```

**Description**

Obtains the PIN authorization state of the specified Ukey resource ID.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [const struct OH_Huks_Blob](capi-hukstypeapi-oh-huks-blob.md) *resourceId | Resource ID of the specified provider.|
| [const OH_Huks_ExternalCryptoParamSet](capi-huksexternalcryptotypeapi-oh-huks-externalcryptoparamset.md) *paramSet | Pointer to the PIN authorization parameters.|
| bool *authState | Whether a specified index is authorized.|

**Returns**

| Type| Description|
| -- | -- |
| [struct OH_Huks_Result](capi-hukstypeapi-oh-huks-result.md) | Possible error codes (**errorCode**):<br>         **OH_HUKS_SUCCESS 0**: Operation successful.<br>         **OH_HUKS_ERR_CODE_NOT_SUPPORTED_API 801**: Unsupported API.<br>         **OH_HUKS_ERR_CODE_COMMUNICATION_FAIL 12000005**: IPC communication failed.<br>         **OH_HUKS_ERR_CODE_CRYPTO_FAIL 12000006**: Ukey driver error.<br>         **OH_HUKS_ERR_CODE_ITEM_NOT_EXIST 12000011**: The specified resource ID is invalid.<br>         **OH_HUKS_ERR_CODE_INTERNAL_ERROR 12000012**: An internal system error occurs. The processing function is not found.<br>      **OH_HUKS_ERR_CODE_INSUFFICIENT_MEMORY 12000014**: Insufficient memory.<br>         **OH_HUKS_ERR_CODE_ILLEGAL_ARGUMENT 12000018**: Invalid **resourceId** or **paramSet**.<br>         **OH_HUKS_ERR_CODE_EXTERNAL_ERROR 12000020**: Provider execution fails.<br>       **OH_HUKS_ERR_CODE_BUSY 12000024**: The provider or Ukey is busy.|

### OH_Huks_GetProperty()

```c
struct OH_Huks_Result OH_Huks_GetProperty(const struct OH_Huks_Blob *resourceId, const struct OH_Huks_Blob *propertyId, const OH_Huks_ExternalCryptoParamSet *paramSetIn, OH_Huks_ExternalCryptoParamSet **paramSetOut)
```

**Description**

Obtains the property information of the external key management extension provider.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [const struct OH_Huks_Blob](capi-hukstypeapi-oh-huks-blob.md) *resourceId | Resource ID of the specified provider.|
| [const struct OH_Huks_Blob](capi-hukstypeapi-oh-huks-blob.md) *propertyId | Name of the property function defined by GMT 0016-2023.|
| [const OH_Huks_ExternalCryptoParamSet](capi-huksexternalcryptotypeapi-oh-huks-externalcryptoparamset.md) *paramSetIn | Pointer to the input operation parameters.|
| [OH_Huks_ExternalCryptoParamSet](capi-huksexternalcryptotypeapi-oh-huks-externalcryptoparamset.md) **paramSetOut | Pointer to the output parameters, which must contain the **OH_HUKS_EXT_CRYPTO_TAG_EXTRA_DATA** parameter.|

**Returns**

| Type| Description|
| -- | -- |
| [struct OH_Huks_Result](capi-hukstypeapi-oh-huks-result.md) | Possible error codes (**errorCode**):<br>         **OH_HUKS_SUCCESS 0**: Operation successful.<br>         **OH_HUKS_ERR_CODE_NOT_SUPPORTED_API 801**: Unsupported API.<br>         **OH_HUKS_ERR_CODE_COMMUNICATION_FAIL 12000005**: IPC communication failed.<br>         **OH_HUKS_ERR_CODE_CRYPTO_FAIL 12000006**: Driver error.<br>         **OH_HUKS_ERR_CODE_ITEM_NOT_EXIST 12000011**: The specified handle in the cache is not found.<br>         **OH_HUKS_ERR_CODE_INTERNAL_ERROR 12000012**: An internal system error occurs. The processing function is not found.<br>      **OH_HUKS_ERR_CODE_INSUFFICIENT_MEMORY 12000014**: Insufficient memory.<br>         **OH_HUKS_ERR_CODE_ILLEGAL_ARGUMENT 12000018**: Invalid **resourceId**, **propertyId**, **paramSet**, or callback.<br>         **OH_HUKS_ERR_CODE_EXTERNAL_ERROR 12000020**: The provider or Ukey internal execution fails.<br>         **OH_HUKS_ERR_CODE_PIN_LOCKED 12000021**: The PIN is locked.<br>         **OH_HUKS_ERR_CODE_PIN_NO_AUTH 12000023**: PIN authentication fails.<br>         **OH_HUKS_ERR_CODE_BUSY 12000024**: The resources in the provider or Ukey are being used.|

### OH_Huks_InitExternalCryptoParamSet()

```c
struct OH_Huks_Result OH_Huks_InitExternalCryptoParamSet(OH_Huks_ExternalCryptoParamSet **paramSet)
```

**Description**

Initializes a parameter set.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Huks_ExternalCryptoParamSet](capi-huksexternalcryptotypeapi-oh-huks-externalcryptoparamset.md) **paramSet | Level-2 pointer to the parameter set to initialize.|

**Returns**

| Type| Description|
| -- | -- |
| [struct OH_Huks_Result](capi-hukstypeapi-oh-huks-result.md) | Possible error codes (**errorCode**):<br>         **OH_HUKS_SUCCESS 0**: Operation successful.<br>         **OH_HUKS_ERR_CODE_INSUFFICIENT_MEMORY 12000014**: Insufficient memory.<br>         **OH_HUKS_ERR_CODE_INVALID_ARGUMENT 12000018**: **params** is NULL or **paramSet** is invalid.|

### OH_Huks_AddExternalCryptoParams()

```c
struct OH_Huks_Result OH_Huks_AddExternalCryptoParams(OH_Huks_ExternalCryptoParamSet *paramSet, const OH_Huks_ExternalCryptoParam *params, uint32_t paramCnt)
```

**Description**

Adds parameters to a parameter set.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Huks_ExternalCryptoParamSet](capi-huksexternalcryptotypeapi-oh-huks-externalcryptoparamset.md) *paramSet | Pointer to the parameter set to which parameters are to be added.|
| [const OH_Huks_ExternalCryptoParam](capi-huksexternalcryptotypeapi-oh-huks-externalcryptoparam.md) *params | Pointer to the parameter array to be added.|
| uint32_t paramCnt | Number of parameters to be added.|

**Returns**

| Type| Description|
| -- | -- |
| [struct OH_Huks_Result](capi-hukstypeapi-oh-huks-result.md) | Possible error codes (**errorCode**):<br>         **OH_HUKS_SUCCESS 0**: Operation successful.<br>         **OH_HUKS_ERR_CODE_INVALID_ARGUMENT 12000018**: **params** is NULL or **paramSet** is invalid.|

### OH_Huks_BuildExternalCryptoParamSet()

```c
struct OH_Huks_Result OH_Huks_BuildExternalCryptoParamSet(OH_Huks_ExternalCryptoParamSet **paramSet)
```

**Description**

Builds a parameter set.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Huks_ExternalCryptoParamSet](capi-huksexternalcryptotypeapi-oh-huks-externalcryptoparamset.md) **paramSet | Level-2 pointer to the parameter set to build.|

**Returns**

| Type| Description|
| -- | -- |
| [struct OH_Huks_Result](capi-hukstypeapi-oh-huks-result.md) | Possible error codes (**errorCode**):<br>         **OH_HUKS_SUCCESS 0**: Operation successful.<br>         **OH_HUKS_ERR_CODE_INVALID_ARGUMENT 12000018** - Invalid **paramSet**.<br>         **OH_HUKS_ERR_CODE_INSUFFICIENT_MEMORY 12000014**: Insufficient memory.|

### OH_Huks_FreeExternalCryptoParamSet()

```c
void OH_Huks_FreeExternalCryptoParamSet(OH_Huks_ExternalCryptoParamSet **paramSet)
```

**Description**

Destroys a parameter set and releases related memory.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Huks_ExternalCryptoParamSet](capi-huksexternalcryptotypeapi-oh-huks-externalcryptoparamset.md) **paramSet | Level-2 pointer to the parameter set to destroy.|

### OH_Huks_GetExternalCryptoParam()

```c
struct OH_Huks_Result OH_Huks_GetExternalCryptoParam(OH_Huks_ExternalCryptoParamSet *paramSet, const uint32_t tag, OH_Huks_ExternalCryptoParam **param)
```

**Description**

Obtains a specified parameter from a parameter set.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Huks_ExternalCryptoParamSet](capi-huksexternalcryptotypeapi-oh-huks-externalcryptoparamset.md) *paramSet | Pointer to the target parameter set.|
| const uint32_t tag | Tag value of the parameter to obtain.|
| [OH_Huks_ExternalCryptoParam](capi-huksexternalcryptotypeapi-oh-huks-externalcryptoparam.md) **param | Level-2 pointer used to return the obtained parameter.|

**Returns**

| Type| Description|
| -- | -- |
| [struct OH_Huks_Result](capi-hukstypeapi-oh-huks-result.md) | Possible error codes (**errorCode**):<br>         **OH_HUKS_SUCCESS 0**: Operation successful.<br>         **OH_HUKS_ERR_CODE_INVALID_ARGUMENT 12000018** - **paramSet** or **param** is invalid, or the parameter does not exist in the set.|
