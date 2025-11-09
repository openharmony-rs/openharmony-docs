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
| [int32_t OH_CertManager_GetUkeyCertificate(const OH_CM_Blob *keyUri, const OH_CM_UkeyInfo *ukeyInfo, OH_CM_CredentialDetailList *certificateList)](#oh_huks_getsdkversion) | 获取特定USB证书凭据详细信息列表。 |
| [int32_t OH_CertManager_GetPrivateCertificate(const OH_CM_Blob *keyUri, OH_CM_Credential *certificate)](#oh_huks_getsdkversion) | 获取特定应用私有证书凭据详细信息。 |
| [int32_t OH_CertManager_GetPublicCertificate(const OH_CM_Blob *keyUri, OH_CM_Credential *certificate)](#oh_huks_getsdkversion) | 获取特定用户公共证书凭据详细信息。 |
| [void OH_CertManager_FreeUkeyCertificate(OH_CM_CredentialDetailList *certificateList)](#oh_huks_getsdkversion) | 销毁证书详情信息列表。 |
| [void OH_CertManager_FreeCredential(OH_CM_Credential *certificate)](#oh_huks_getsdkversion) | 销毁证书详情信息。 |


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
| [struct OH_Huks_Blob](capi-hukstypeapi-oh-huks-blob.md) *sdkVersion | 用于存放获取到的版本信息（字符串格式）。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [struct OH_Huks_Result](capi-hukstypeapi-oh-huks-result.md) | 可能的返回码（errorCode）：<br>         OH_HUKS_SUCCESS = 0 ：操作成功。<br>         OH_HUKS_ERR_CODE_ILLEGAL_ARGUMENT = 401 ：sdkVersion或者sdkVersion->data是null，或者sdkVersion->size太小。 |


