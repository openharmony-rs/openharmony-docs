# OH_CM_Blob

<!--Kit: Device Certificate Kit-->
<!--Subsystem: Security-->
<!--Owner: @wxb_code-->
<!--Designer: @chande-->
<!--Tester: @zhangzhi1995-->
<!--Adviser: @zengyawen-->

```c
typedef struct {...} OH_CM_Blob
```

## Overview

Defines a struct for a binary large object (BLOB).

**Since**: 22

**Related module**: [CertManagerType](capi-certmanagertype.md)

**Header file**: [cm_native_type.h](capi-cm-native-type-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t size | Data size.|
| uint8_t *data | Pointer to the memory in which the data is stored.|
