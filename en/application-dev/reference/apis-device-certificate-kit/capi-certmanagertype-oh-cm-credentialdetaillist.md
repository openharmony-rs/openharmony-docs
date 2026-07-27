# OH_CM_CredentialDetailList

<!--Kit: Device Certificate Kit-->
<!--Subsystem: Security-->
<!--Owner: @wxb_code-->
<!--Designer: @chande-->
<!--Tester: @zhangzhi1995-->
<!--Adviser: @zengyawen-->

```c
typedef struct {...} OH_CM_CredentialDetailList
```

## Overview

Defines a struct for the certificate credential detail list.

**Since**: 22

**Related module**: [CertManagerType](capi-certmanagertype.md)

**Header file**: [cm_native_type.h](capi-cm-native-type-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t credentialCount | Number of certificate credential details.|
| [OH_CM_Credential](capi-certmanagertype-oh-cm-credential.md) *credential | Pointer to the certificate credential detail list.|
