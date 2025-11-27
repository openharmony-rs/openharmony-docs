# OH_CM_CredentialDetailList

<!--Kit: Device Certificate Kit-->
<!--Subsystem: Security-->
<!--Owner: @wxb_code-->
<!--Designer: @chande-->
<!--Tester: @zhangzhi1995-->
<!--Adviser: @zengyawen-->

```
typedef struct {...} OH_CM_CredentialDetailList
```

## 概述

定义证书凭据详情列表的结构体类型。

**起始版本：** 22

**相关模块：** [CertManagerType](capi-certmanagertype.md)

**所在头文件：** [cm_native_type.h](capi-cm-native-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint32_t credentialCount | 表示证书凭据详情的个数。 |
| [OH_CM_Credential](capi-certmanagertype-oh-cm-credential.md) *credential | 表示证书凭据详情列表。 |


