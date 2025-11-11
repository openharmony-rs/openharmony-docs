# cm_native_api.h

<!--Kit: Device Certificate Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

## 概述

声明用于访问certManager的API。

**引用文件：** <device_certificate/certmanager/cm_native_api.h>

**库：** libohcert_manager.z.so

**系统能力：** SystemCapability.Security.CertificateManager

**起始版本：** 22

**相关模块：** [CertManager](capi-certmanager.md)

## 汇总

### 函数

| 名称 | 描述 |
| -- | -- |
| [int32_t OH_CertManager_GetUkeyCertificate(const OH_CM_Blob *keyUri, const OH_CM_UkeyInfo *ukeyInfo, OH_CM_CredentialDetailList *certificateList)](#OH_CertManager_GetUkeyCertificate) | 获取特定USB证书凭据详细信息列表。 |
| [int32_t OH_CertManager_GetPrivateCertificate(const OH_CM_Blob *keyUri, OH_CM_Credential *certificate)](#OH_CertManager_GetPrivateCertificate) | 获取特定应用私有证书凭据详细信息。 |
| [int32_t OH_CertManager_GetPublicCertificate(const OH_CM_Blob *keyUri, OH_CM_Credential *certificate)](#OH_CertManager_GetPublicCertificate) | 获取特定用户公共证书凭据详细信息。 |
| [void OH_CertManager_FreeUkeyCertificate(OH_CM_CredentialDetailList *certificateList)](#OH_CertManager_FreeUkeyCertificate) | 销毁证书详情信息列表。 |
| [void OH_CertManager_FreeCredential(OH_CM_Credential *certificate)](#OH_CertManager_FreeCredential) | 销毁证书详情信息。 |


## 函数说明

### OH_CertManager_GetUkeyCertificate()

```
int32_t OH_CertManager_GetUkeyCertificate(const OH_CM_Blob *keyUri, const OH_CM_UkeyInfo *ukeyInfo, OH_CM_CredentialDetailList *certificateList)
```

**描述**

获取特定USB证书凭据详细信息列表。

**起始版本：** 22


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_CM_Blob](capi-certmanagertype-oh-cm-blob.md) *keyUri | 用于存放证书凭据的唯一标识（字符串格式）。 |
| [OH_CM_UkeyInfo](capi-certmanagertype-oh-cm-ukeyinfo.md) *ukeyInfo | USB凭据属性信息。 |
| [OH_CM_CredentialDetailList](capi-certmanagertype-oh-cm-credentialdetaillist.md) *certificateList | 获取到的USB证书凭据详细信息列表。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 可能的返回码（errorCode）：<br>         OH_CM_SUCCESS = 0 ：操作成功。<br>         OH_CM_HAS_NO_PERMISSION = 201 ：权限校验失败。<br>OH_CM_CAPABILITY_NOT_SUPPORTED = 801 ：设备不支持。<br>OH_CM_INNER_FAILURE = 17500001 ：内部错误。<br>OH_CM_NOT_FOUND = 17500002 ：证书不存在。<br>OH_CM_ACCESS_UKEY_SERVICE_FAILED = 17500010 ：USB证书凭据服务访问失败。<br>OH_CM_PARAMETER_VALIDATION_FAILED = 1700011 ：入参校验失败，例如参数格式错误或参数范围无效。 |

### OH_CertManager_GetPrivateCertificate()

```
int32_t OH_CertManager_GetPrivateCertificate(const OH_CM_Blob *keyUri, OH_CM_Credential *certificate)
```

**描述**

获取特定应用私有证书凭据详细信息。

**起始版本：** 22


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_CM_Blob](capi-certmanagertype-oh-cm-blob.md) *keyUri | 用于存放证书凭据的唯一标识（字符串格式）。 |
| [OH_CM_Credential](capi-certmanagertype-oh-cm-credential.md) *certificate | 获取到的应用私有凭据的详细信息。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 可能的返回码（errorCode）：<br>         OH_CM_SUCCESS = 0 ：操作成功。<br>         OH_CM_HAS_NO_PERMISSION = 201 ：权限校验失败。<br>OH_CM_INNER_FAILURE = 17500001 ：内部错误。<br>OH_CM_NOT_FOUND = 17500002 ：证书不存在。<br>OH_CM_PARAMETER_VALIDATION_FAILED = 1700011 ：入参校验失败，例如参数格式错误或参数范围无效。 |

### OH_CertManager_GetPublicCertificate()

```
int32_t OH_CertManager_GetPublicCertificate(const OH_CM_Blob *keyUri, OH_CM_Credential *certificate)
```

**描述**

获取特定用户公共证书凭据详细信息。

**起始版本：** 22


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_CM_Blob](capi-certmanagertype-oh-cm-blob.md) *keyUri | 用于存放证书凭据的唯一标识（字符串格式）。 |
| [OH_CM_Credential](capi-certmanagertype-oh-cm-credential.md) *certificate | 获取到的用户公共凭据的详细信息。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 可能的返回码（errorCode）：<br>         OH_CM_SUCCESS = 0 ：操作成功。<br>         OH_CM_HAS_NO_PERMISSION = 201 ：权限校验失败。<br>OH_CM_INNER_FAILURE = 17500001 ：内部错误。<br>OH_CM_NOT_FOUND = 17500002 ：证书不存在。<br>OH_CM_NO_AUTHORIZATION = 17500005 ：应用未获得用户授权。<br>OH_CM_PARAMETER_VALIDATION_FAILED = 1700011 ：入参校验失败，例如参数格式错误或参数范围无效。 |

### OH_CertManager_FreeUkeyCertificate()

```
void OH_CertManager_FreeUkeyCertificate(OH_CM_CredentialDetailList *certificateList);
```

**描述**

销毁证书详情信息列表。

**起始版本：** 22


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_CM_CredentialDetailList](capi-certmanagertype-oh-cm-credentialdetaillist.md) *certificate | 待销毁的证书凭据详细信息列表。 |

### OH_CertManager_FreeCredential()

```
void OH_CertManager_FreeCredential(OH_CM_Credential *certificate);
```

**描述**

销毁证书详情信息。

**起始版本：** 22


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_CM_Credential](capi-certmanagertype-oh-cm-credential.md) *certificate | 待销毁的证书凭据详细信息。 |
