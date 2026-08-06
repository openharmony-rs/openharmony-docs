# cm_native_type.h

## 概述

Provides the enums, structs, macros, and error codes used by **CertManager** APIs.

**库：** libohcert_manager.z.so

**系统能力：** SystemCapability.Security.CertificateManager

**起始版本：** 22

**相关模块：** [CertManagerType](capi-certmanagertype.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_CM_Blob](capi-certmanagertype-oh-cm-blob.md) | OH_CM_Blob | Defines a struct for a binary large object (BLOB). |
| [OH_CM_Credential](capi-certmanagertype-oh-cm-credential.md) | OH_CM_Credential | Defines a struct for the certificate credential details. |
| [OH_CM_CredentialDetailList](capi-certmanagertype-oh-cm-credentialdetaillist.md) | OH_CM_CredentialDetailList | Defines a struct for the certificate credential detail list. |
| [OH_CM_UkeyInfo](capi-certmanagertype-oh-cm-ukeyinfo.md) | OH_CM_UkeyInfo | Defines a struct for the USB certificate credential information. |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_CM_ErrorCode](#oh_cm_errorcode) | OH_CM_ErrorCode | Enumerates error codes. |
| [OH_CM_CertificatePurpose](#oh_cm_certificatepurpose) | OH_CM_CertificatePurpose | 证书凭据用途类型。 |

### 宏定义

| 名称 | 描述 |
| -- | -- |
| OH_CM_MAX_LEN_CERTIFICATE_CHAIN   24588 | Maximum size of a certificate chain, in bytes.<br>**起始版本：** 22 |
| OH_CM_MAX_LEN_URI              256 | Maximum URI length, in bytes.<br>**起始版本：** 22 |
| OH_CM_MAX_LEN_CERT_ALIAS       129 | Maximum length of a certificate alias, in bytes.<br>**起始版本：** 22 |
| OH_CM_MAX_LEN_TYPE_NAME       1025 | Maximum length of a certificate type, in bytes.<br>**起始版本：** 22 |

## 枚举类型说明

### OH_CM_ErrorCode

```c
enum OH_CM_ErrorCode
```

**描述**

Enumerates error codes.

**起始版本：** 22

| 枚举项 | 描述 |
| -- | -- |
| OH_CM_SUCCESS = 0 | Operation succeeded. |
| OH_CM_HAS_NO_PERMISSION = 201 | Permission verification failed. |
| OH_CM_CAPABILITY_NOT_SUPPORTED = 801 | Not supported by the device. |
| OH_CM_INNER_FAILURE = 17500001 | Internal error. Possible causes: 1. IPC failure. 2. Memory operation error. 3. File operation error. |
| OH_CM_NOT_FOUND = 17500002 | The certificate does not exist. |
| OH_CM_INVALID_CERT_FORMAT = 17500003 | The keystore format is invalid or the keystore password is incorrect. |
| OH_CM_MAX_CERT_COUNT_REACHED = 17500004 | The number of certificates or credentials reaches the upper limit. |
| OH_CM_NO_AUTHORIZATION = 17500005 | The application is not authorized. |
| OH_CM_DEVICE_ENTER_ADVSECMODE = 17500007 | The device enters the advanced security mode.In this mode, CA certificate installation is restricted. |
| OH_CM_STORE_PATH_NOT_SUPPORTED = 17500009 | The device does not support the specified certificate storage path. |
| OH_CM_ACCESS_UKEY_SERVICE_FAILED = 17500010 | Failed to access the USB certificate credential. |
| OH_CM_PARAMETER_VALIDATION_FAILED = 17500011 | Parameter verification fails. For example, the parameter format or range is invalid. |

### OH_CM_CertificatePurpose

```c
enum OH_CM_CertificatePurpose
```

**描述**

证书凭据用途类型。

**起始版本：** 22

| 枚举项 | 描述 |
| -- | -- |
| OH_CM_CERT_PURPOSE_DEFAULT = 0 | 默认用途，用于凭据签名用途。 |
| OH_CM_CERT_PURPOSE_ALL = 1 | 所有用途，用于查询凭据功能。 |
| OH_CM_CERT_PURPOSE_SIGN = 2 | 签名用途。 |
| OH_CM_CERT_PURPOSE_ENCRYPT = 3 | 加密用途。 |


