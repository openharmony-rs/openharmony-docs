# cm_native_api.h

## Overview

Declares the APIs used to obtain details of specific certificates.

**Library**: libohcert_manager.z.so

**System capability**: SystemCapability.Security.CertificateManager

**Since**: 22

**Related module**: [CertManager](capi-certmanager.md)

## Summary

### Function

| Name | Description |
| -- | -- |
| [int32_t OH_CertManager_GetUkeyCertificate(const OH_CM_Blob *keyUri, const OH_CM_UkeyInfo *ukeyInfo, OH_CM_CredentialDetailList *certificateList)](#oh_certmanager_getukeycertificate) | Obtains the detail list of USB certificate credentials. After the call is complete, call OH_CertManager_FreeUkeyCertificate to release the certificateList memory. |
| [int32_t OH_CertManager_GetPrivateCertificate(const OH_CM_Blob *keyUri, OH_CM_Credential *certificate)](#oh_certmanager_getprivatecertificate) | Obtains the details of a private certificate credential of a specific application. After the call is complete, call OH_CertManager_FreeCredential to release the certificate memory. |
| [int32_t OH_CertManager_GetPublicCertificate(const OH_CM_Blob *keyUri, OH_CM_Credential *certificate)](#oh_certmanager_getpubliccertificate) | Obtains the details of a public certificate credential of a specific user. After the call is complete, call OH_CertManager_FreeCredential to release the certificate memory. |
| [void OH_CertManager_FreeUkeyCertificate(OH_CM_CredentialDetailList *certificateList)](#oh_certmanager_freeukeycertificate) | Destroys the certificate detail list. |
| [void OH_CertManager_FreeCredential(OH_CM_Credential *certificate)](#oh_certmanager_freecredential) | Destroys the certificate details. |

## Function description

### OH_CertManager_GetUkeyCertificate()

```c
int32_t OH_CertManager_GetUkeyCertificate(const OH_CM_Blob *keyUri, const OH_CM_UkeyInfo *ukeyInfo, OH_CM_CredentialDetailList *certificateList)
```

**Description**

Obtains the detail list of USB certificate credentials. After the call is complete, call OH_CertManager_FreeUkeyCertificate to release the certificateList memory.

**Required permission**: ohos.permission.ACCESS_CERT_MANAGER

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_CM_Blob *keyUri | Pointer to the URI that stores the USB certificate credentials, in string format. |
| const OH_CM_UkeyInfo *ukeyInfo | Pointer to the property information of the USB certificate credential. |
| OH_CM_CredentialDetailList *certificateList | Pointer to the USB certificate credential detail list obtained. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>  <li>{@link OH_CM_ErrorCode} : </li>  <li>OH_CM_SUCCESS = 0: Operation successful.</li>  <li>OH_CM_HAS_NO_PERMISSION = 201: Permission verification failed.</li>  <li>OH_CM_CAPABILITY_NOT_SUPPORTED = 801: The device is not supported.</li>  <li>OH_CM_PARAMETER_VALIDATION_FAILED = 17500011: Input parameter verification failed. Possible causes:  1. Incorrect parameter format.  2. Invalid parameter value range.</li>  <li>OH_CM_INNER_FAILURE = 17500001: Internal error. Possible causes:  1. IPC failure.  2. Memory operation error.  3. File operation error.</li>  <li>OH_CM_NOT_FOUND = 17500002: The certificate does not exist.</li>  <li>OH_CM_ACCESS_UKEY_SERVICE_FAILED = 17500010: Failed to access the USB certificate credential.</li>  </ul> |

### OH_CertManager_GetPrivateCertificate()

```c
int32_t OH_CertManager_GetPrivateCertificate(const OH_CM_Blob *keyUri, OH_CM_Credential *certificate)
```

**Description**

Obtains the details of a private certificate credential of a specific application. After the call is complete, call OH_CertManager_FreeCredential to release the certificate memory.

**Required permission**: ohos.permission.ACCESS_CERT_MANAGER

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_CM_Blob *keyUri | Pointer to the URI that stores the application's private certificate credentials, in string format. |
| OH_CM_Credential *certificate | Pointer to the details of the application's private credentials obtained. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>  <li>{@link OH_CM_ErrorCode} : </li>  <li>OH_CM_SUCCESS = 0: Operation successful.</li>  <li>OH_CM_HAS_NO_PERMISSION = 201: Permission verification failed.</li>  <li>OH_CM_PARAMETER_VALIDATION_FAILED = 17500011: Input parameter verification failed. Possible causes:  1. Incorrect parameter format.  2. Invalid parameter value range.</li>  <li>OH_CM_INNER_FAILURE = 17500001: Internal error. Possible causes:  1. IPC failure.  2. Memory operation error.  3. File operation error.</li>  <li>OH_CM_NOT_FOUND = 17500002: The certificate does not exist.</li>  </ul> |

### OH_CertManager_GetPublicCertificate()

```c
int32_t OH_CertManager_GetPublicCertificate(const OH_CM_Blob *keyUri, OH_CM_Credential *certificate)
```

**Description**

Obtains the details of a public certificate credential of a specific user. After the call is complete, call OH_CertManager_FreeCredential to release the certificate memory.

**Required permission**: ohos.permission.ACCESS_CERT_MANAGER

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_CM_Blob *keyUri | Pointer to the URI that stores the user's public certificate credentials, in string format. |
| OH_CM_Credential *certificate | Pointer to the details of the user's public certificate credential obtained. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>  <li>{@link OH_CM_ErrorCode} : </li>  <li>OH_CM_SUCCESS = 0: Operation successful.</li>  <li>OH_CM_HAS_NO_PERMISSION = 201: Permission verification failed.</li>  <li>OH_CM_PARAMETER_VALIDATION_FAILED = 17500011: Input parameter verification failed. Possible causes:  1. Incorrect parameter format.  2. Invalid parameter value range.</li>  <li>OH_CM_INNER_FAILURE = 17500001: Internal error. Possible causes:  1. IPC failure.  2. Memory operation error.  3. File operation error.</li>  <li>OH_CM_NOT_FOUND = 17500002: The certificate does not exist.</li>  <li>OH_CM_NO_AUTHORIZATION = 17500005: The application is not authorized.</li>  </ul> |

### OH_CertManager_FreeUkeyCertificate()

```c
void OH_CertManager_FreeUkeyCertificate(OH_CM_CredentialDetailList *certificateList)
```

**Description**

Destroys the certificate detail list.

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_CM_CredentialDetailList *certificateList | Pointer to the certificate credential detail list to be destroyed. |

### OH_CertManager_FreeCredential()

```c
void OH_CertManager_FreeCredential(OH_CM_Credential *certificate)
```

**Description**

Destroys the certificate details.

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_CM_Credential *certificate | Pointer to the certificate credential details to be destroyed. |


