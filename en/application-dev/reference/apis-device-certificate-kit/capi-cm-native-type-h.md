# cm_native_type.h

<!--Kit: Device Certificate Kit-->
<!--Subsystem: Security-->
<!--Owner: @wxb_code-->
<!--Designer: @chande-->
<!--Tester: @zhangzhi1995-->
<!--Adviser: @zengyawen-->

## Overview

Provides the enums, structs, macros, and error codes used by **CertManager** APIs.

**Header file**: <device_certificate/certmanager/cm_native_type.h>

**Library**: libohcert_manager.so

**System capability**: SystemCapability.Security.CertificateManager

**Since**: 22

**Related module**: [CertManagerType](capi-certmanagertype.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_CM_Blob](capi-certmanagertype-oh-cm-blob.md) | OH_CM_Blob | Defines a struct for a binary large object (BLOB).|
| [OH_CM_Credential](capi-certmanagertype-oh-cm-credential.md) | OH_CM_Credential | Defines a struct for the certificate credential details.|
| [OH_CM_CredentialDetailList](capi-certmanagertype-oh-cm-credentialdetaillist.md) | OH_CM_CredentialDetailList | Defines a struct for the certificate credential detail list.|
| [OH_CM_UkeyInfo](capi-certmanagertype-oh-cm-ukeyinfo.md) | OH_CM_UkeyInfo | Defines a struct for the USB certificate credential information.|

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_CM_ErrorCode](#oh_cm_errorcode) | OH_CM_ErrorCode | Enumerates error codes.|
| [OH_CM_CertificatePurpose](#oh_cm_certificatepurpose) | OH_CM_CertificatePurpose | Enumerates the certificate credential purposes.|

### Macros

| Name| Description|
| -- | -- |
| OH_CM_MAX_LEN_CERTIFICATE_CHAIN   24588 | Maximum length of a certificate chain.<br>**Since**: 22|
| OH_CM_MAX_LEN_URI              256 | Maximum length of a URI.<br>**Since**: 22|
| OH_CM_MAX_LEN_CERT_ALIAS       129 | Maximum length of a certificate alias.<br>**Since**: 22|
| OH_CM_MAX_LEN_TYPE_NAME       1025 | Maximum length of a certificate type.<br>**Since**: 22|

## Enum Description

### OH_CM_ErrorCode

```c
enum OH_CM_ErrorCode
```

**Description**

Enumerates error codes.

**Since**: 22

| Enum Item| Description|
| -- | -- |
| OH_CM_SUCCESS = 0 | Operation succeeded.|
| OH_CM_HAS_NO_PERMISSION = 201 | Permission verification failed.|
| OH_CM_CAPABILITY_NOT_SUPPORTED = 801 | Not supported by the device.|
| OH_CM_INNER_FAILURE = 17500001 | Internal error. Possible causes: 1. IPC failure. 2. Memory operation error. 3. File operation error.|
| OH_CM_NOT_FOUND = 17500002 | The certificate does not exist.|
| OH_CM_INVALID_CERT_FORMAT = 17500003 | The keystore format is invalid or the keystore password is incorrect.|
| OH_CM_MAX_CERT_COUNT_REACHED = 17500004 | The number of certificates or credentials reaches the upper limit.|
| OH_CM_NO_AUTHORIZATION = 17500005 | The application is not authorized.|
| OH_CM_DEVICE_ENTER_ADVSECMODE = 17500007 | The device enters the advanced security mode.|
| OH_CM_STORE_PATH_NOT_SUPPORTED = 17500009 | The device does not support the specified certificate storage path.|
| OH_CM_ACCESS_UKEY_SERVICE_FAILED = 17500010 | Failed to access the USB certificate credential.|
| OH_CM_PARAMETER_VALIDATION_FAILED = 17500011 | Parameter verification fails. For example, the parameter format or range is invalid.|

### OH_CM_CertificatePurpose

```c
enum OH_CM_CertificatePurpose
```

**Description**

Enumerates the certificate credential purposes.

**Since**: 22

| Enum Item| Description|
| -- | -- |
| OH_CM_CERT_PURPOSE_DEFAULT = 0 | Default purpose, which is used for credential signing.|
| OH_CM_CERT_PURPOSE_ALL = 1 | All purposes, which are used to query credential functionalities.|
| OH_CM_CERT_PURPOSE_SIGN = 2 | Signing purpose.|
| OH_CM_CERT_PURPOSE_ENCRYPT = 3 | Encryption purpose.|
