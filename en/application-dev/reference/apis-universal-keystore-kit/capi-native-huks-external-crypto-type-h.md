# native_huks_external_crypto_type.h

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

## Overview

Defines the structs and enums for external key management extensions.

**File to include**: <huks/native_huks_external_crypto_type.h>

**Library**: libhuks_external_crypto.z.so

**System capability**: SystemCapability.Security.Huks.CryptoExtension

**Since**: 22

**Related modules**: [HuksExternalCryptoTypeApi](capi-huksexternalcryptotypeapi.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_Huks_ExternalCryptoParam](capi-huksexternalcryptotypeapi-oh-huks-externalcryptoparam.md) | OH_Huks_ExternalCryptoParam | Defines a single parameter in a parameter set.|
| [OH_Huks_ExternalCryptoParamSet](capi-huksexternalcryptotypeapi-oh-huks-externalcryptoparamset.md) | OH_Huks_ExternalCryptoParamSet | Defines an external cryptographic parameter set.|

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_Huks_ExternalCryptoTag](#oh_huks_externalcryptotag) | OH_Huks_ExternalCryptoTag | Enumerates the tag values used in a parameter set.|

### Macros

| Name| Description|
| -- | -- |
| OH_HUKS_EXTERNAL_CRYPTO_MAX_PROVIDER_NAME_LEN 100 | Maximum byte length of the provider name.<br>**Since**: 22|
| OH_HUKS_EXTERNAL_CRYPTO_MAX_RESOURCE_ID_LEN 512 | Maximum byte length of the **resourceId** name.<br>**Since**: 22|

## Enum Description

### OH_Huks_ExternalCryptoTag

```c
enum OH_Huks_ExternalCryptoTag
```

**Description**

Enumerates the tag values used in a parameter set.

**Since**: 22

| Value| Description|
| -- | -- |
| OH_HUKS_EXT_CRYPTO_TAG_UKEY_PIN = OH_HUKS_TAG_TYPE_BYTES \| 200001 | PIN code.|
| OH_HUKS_EXT_CRYPTO_TAG_ABILITY_NAME = OH_HUKS_TAG_TYPE_BYTES \| 200002 | Ability name.|
| OH_HUKS_EXT_CRYPTO_TAG_EXTRA_DATA = OH_HUKS_TAG_TYPE_BYTES \| 200003 | Extra data.|
| OH_HUKS_EXT_CRYPTO_TAG_UID = OH_HUKS_TAG_TYPE_INT \| 200004 | UID of the caller.|
| OH_HUKS_EXT_CRYPTO_TAG_PURPOSE = OH_HUKS_TAG_TYPE_INT \| 200005 | Purpose of the certificate chain.|
| OH_HUKS_EXT_CRYPTO_TAG_TIMEOUT = OH_HUKS_TAG_TYPE_UINT \| 200006 | Timeout interval for obtaining properties, in seconds.|

### OH_Huks_ExternalPinAuthState

```c
enum OH_Huks_ExternalPinAuthState
```

**Description**

Enumerates the Ukey PIN authentication states.

**Since**: 22

| Value| Description|
| -- | -- |
| OH_HUKS_EXT_CRYPTO_PIN_NO_AUTH = 0 | PIN code not authenticated.|
| OH_HUKS_EXT_CRYPTO_PIN_AUTH_SUCCEEDED = 1 | PIN code authentication succeeded.|
| OH_HUKS_EXT_CRYPTO_PIN_LOCKED = 2 | PIN code locked.|
