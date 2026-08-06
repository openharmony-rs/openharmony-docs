# OH_CM_CredentialDetailList

```c
typedef struct OH_CM_CredentialDetailList {...} OH_CM_CredentialDetailList
```

## 概述

Defines a struct for the certificate credential detail list.

**起始版本：** 22

**相关模块：** [CertManagerType](capi-certmanagertype.md)

**所在头文件：** [cm_native_type.h](capi-cm-native-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint32_t credentialCount | Number of certificate credential details. |
| [OH_CM_Credential](capi-certmanagertype-oh-cm-credential.md) *credential | Indicates the credential data. |


