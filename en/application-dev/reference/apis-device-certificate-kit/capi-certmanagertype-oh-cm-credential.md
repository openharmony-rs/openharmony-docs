# OH_CM_Credential

<!--Kit: Device Certificate Kit-->
<!--Subsystem: Security-->
<!--Owner: @wxb_code-->
<!--Designer: @chande-->
<!--Tester: @zhangzhi1995-->
<!--Adviser: @zengyawen-->

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
| uint32_t isExist | Whether a certificate data exists.|
| char type[OH_CM_MAX_LEN_TYPE_NAME] | Type of a credential. The value contains up to 8 bytes, including the terminator **'\0'**.|
| char alias[OH_CM_MAX_LEN_CERT_ALIAS] | Alias of a credential. The value contains up to 128 bytes, including the terminator **'\0'**.|
| char keyUri[OH_CM_MAX_LEN_URI] | URI of a credential. The value contains up to 256 bytes, including the terminator **'\0'**.|
| uint32_t certNum | Number of certificates contained in the credential.|
| uint32_t keyNum | Number of keys contained in the credential.|
| [OH_CM_Blob](capi-certmanagertype-oh-cm-blob.md) credData | Binary data of a credential. The value contains up to 20480 bytes.|
| [OH_CM_CertificatePurpose](capi-cm-native-type-h.md#oh_cm_certificatepurpose) certPurpose | Purpose of a certificate credential.|
