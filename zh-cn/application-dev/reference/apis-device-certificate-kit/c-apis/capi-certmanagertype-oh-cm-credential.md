# OH_CM_Credential

```c
typedef struct OH_CM_Credential {...} OH_CM_Credential
```

## 概述

Defines a struct for the certificate credential details.

<!--Device-typedef struct OH_CM_Credential {...} OH_CM_Credential--><!--Device-typedef struct OH_CM_Credential {...} OH_CM_Credential-End-->

**系统能力：** SystemCapability.Security.CertificateManager

**起始版本：** 22

**相关模块：** [CertManagerType](capi-device-certificate-kit-certmanagertype.md)

**所在头文件：** [cm_native_type.h](capi-cm-native-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint32_t isExist | Whether a certificate data exists.<br><!--Device-uint32_t isExist--><!--Device-uint32_t isExist-End--> |
| char type[OH_CM_MAX_LEN_TYPE_NAME] | Indicates the type of Credential. The value include the terminator('\0') char.<br><!--Device-char type[OH_CM_MAX_LEN_TYPE_NAME]--><!--Device-char type[OH_CM_MAX_LEN_TYPE_NAME]-End--> |
| char alias[OH_CM_MAX_LEN_CERT_ALIAS] | Indicates the alias of Credential. The value include the terminator('\0') char.<br><!--Device-char alias[OH_CM_MAX_LEN_CERT_ALIAS]--><!--Device-char alias[OH_CM_MAX_LEN_CERT_ALIAS]-End--> |
| char keyUri[OH_CM_MAX_LEN_URI] | Indicates the uri of Credential.<br><!--Device-char keyUri[OH_CM_MAX_LEN_URI]--><!--Device-char keyUri[OH_CM_MAX_LEN_URI]-End--> |
| uint32_t certNum | Number of certificates contained in the credential.<br><!--Device-uint32_t certNum--><!--Device-uint32_t certNum-End--> |
| uint32_t keyNum | Number of keys contained in the credential.<br><!--Device-uint32_t keyNum--><!--Device-uint32_t keyNum-End--> |
| [OH_CM_Blob](capi-certmanagertype-oh-cm-blob.md) credData | Binary data of a credential. The value contains up to 20480 bytes.<br><!--Device-OH_CM_Blob credData--><!--Device-OH_CM_Blob credData-End--> |
| [OH_CM_CertificatePurpose](capi-cm-native-type-h.md#oh_cm_certificatepurpose) certPurpose | Purpose of a certificate credential.<br><!--Device-OH_CM_CertificatePurpose certPurpose--><!--Device-OH_CM_CertificatePurpose certPurpose-End--> |


