# cm_native_type.h

<!--Kit: Device Certificate Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

## 概述

提供CertManager中的枚举变量、结构体定义与宏定义。

**引用文件：** <device_certificate/certmanager/cm_native_type.h>

**库：** libohcert_manager.z.so

**系统能力：** SystemCapability.Security.CertificateManager

**起始版本：** 22

**相关模块：** [CertManager](capi-certmanager.md)

## 汇总

### 结构体

| 名称 | 描述 |
| -- | -- |
| [OH_CM_Blob](capi-certmanagertype-oh-cm-blob.md) | 定义存放数据的结构体类型。 |
| [OH_CM_Credential](capi-certmanagertype-oh-cm-credential.md) | 定义证书凭据详细信息的结构体类型。 |
| [OH_CM_CredentialDetailList](capi-hukstypeapi-oh-huks-param.md) | 定义证书凭据详细信息列表的结构体类型。 |
| [OH_CM_UkeyInfo](capi-hukstypeapi-oh-huks-paramset.md) | 定义USB证书凭据信息的结构体类型。 |

### 枚举

| 名称 | 描述 |
| -- | -- |
| [OH_CM_ErrorCode](#oh_cm_errorcode) | 错误码。 |
| [OH_CM_CertificatePurpose](#oh_cm_certificatepurpose) | 证书凭据用途类型。 |

### 宏定义

| 名称 | 描述 |
| -- | -- |
| OH_CM_MAX_LEN_CERTIFICATE_CHAIN 24588 | 证书链的最大字节数<br>**起始版本：** 22 |
| OH_CM_MAX_LEN_URI 256 | 证书凭据唯一标识的最大字节数<br>**起始版本：** 22 |
| OH_CM_MAX_LEN_CERT_ALIAS 129 | 证书凭据别名的最大字节长度。<br>**起始版本：** 22 |
| OH_CM_MAX_LEN_TYPE_NAME 1025 | 证书凭据类型的最大字节数。<br>**起始版本：** 22 |

## 枚举类型说明

### OH_CM_ErrorCode

```
enum OH_CM_ErrorCode
```

**描述**

错误码。

**起始版本：** 22

| 枚举项 | 描述 |
| -- | -- |
| OH_CM_SUCCESS = 0 | 成功。 |
| OH_CM_HAS_NO_PERMISSION = 201 | 权限校验失败。 |
| OH_CM_CAPABILITY_NOT_SUPPORTED = 801 | 内部错误。 |
| OH_CM_INNER_FAILURE = 17500001 | 不支持该子功能（特性）。 |
| OH_CM_NOT_FOUND = 17500002 | 证书不存在。 |
| OH_CM_INVALID_CERT_FORMAT = 17500003 | 证书或凭据无效。 |
| OH_CM_MAX_CERT_COUNT_REACHED = 17500004 | 证书或凭据数量达到上限。 |
| OH_CM_NO_AUTHORIZATION = 17500005 | 应用未经用户授权。 |
| OH_CM_DEVICE_ENTER_ADVSECMODE = 17500007 | 设备进入剑盾守护模式 |
| OH_CM_STORE_PATH_NOT_SUPPORTED = 17500009 | 不支持指定的证书存储路径。 |
| OH_CM_ACCESS_UKEY_SERVICE_FAILED = 17500010 | USB证书凭据访问失败。 |
| OH_CM_PARAMETER_VALIDATION_FAILED = 17500011 | 参数校验失败，例如参数格式或参数范围无效。 |

### OH_CM_CertificatePurpose

```
enum OH_CM_CertificatePurpose
```

**描述**

证书凭据用途类型。

**起始版本：** 22

| 枚举项 | 描述 |
| -- | -- |
| OH_CM_CERT_PURPOSE_DEFAULT = 0 | 表示凭据默认用途。 |
| OH_CM_CERT_PURPOSE_ALL = 1 | 表示凭据所有用途，用于查询凭据功能。 |
| OH_CM_CERT_PURPOSE_SIGN = 2 | 表示凭据签名用途。 |
| OH_CM_CERT_PURPOSE_ENCRYPT = 3 | 表示凭据加密用途。 |



