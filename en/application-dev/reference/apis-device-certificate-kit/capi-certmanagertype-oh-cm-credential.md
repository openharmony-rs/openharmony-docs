# OH_CM_Credential

<!--Kit: Device Certificate Kit-->
<!--Subsystem: Security-->
<!--Owner: @wxb_code-->
<!--Designer: @chande-->
<!--Tester: @zhangzhi1995-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=aaa6335d8ea5457389eca6d8980e9573be997e97 translatedAt=2026-11-03T06:42:07.937Z pushedAt=2026-11-04T03:11:19.890Z nl=1 -->

```c
typedef struct {...} OH_CM_Credential
```

## Overview

Defines a struct for the certificate credential details.

**Since**: 22

**Related module**: [CertManagerType](capi-certmanagertype.md)

**Header file**: [cm_native_type.h](capi-cm-native-type-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t isExist | Whether the certificate data exists. The value **0** indicates that it does not exist, and **1** indicates that it exists. |
| char type[OH_CM_MAX_LEN_TYPE_NAME] | Type of a credential. The value contains up to 1025 bytes, including the terminator **'\0'**. |
| char alias[OH_CM_MAX_LEN_CERT_ALIAS] | Alias of a credential. The value contains up to 129 bytes, including the terminator **'\0'**. |
| char keyUri[OH_CM_MAX_LEN_URI] | URI of a credential. The value contains up to 256 bytes, including the terminator **'\0'**.|
| uint32_t certNum | Number of certificates contained in the credential.|
| uint32_t keyNum | Number of keys contained in the credential. |
| [OH_CM_Blob](capi-certmanagertype-oh-cm-blob.md) credData | Binary data of a credential. The value contains up to 20480 bytes.|
| [OH_CM_CertificatePurpose](capi-cm-native-type-h.md#oh_cm_certificatepurpose) certPurpose | Purpose of a certificate credential.|


