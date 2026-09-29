# __TEE_ObjectHandle

```c
struct __TEE_ObjectHandle {...}
```

## Overview

Defines an object handle.

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Related module**: [TeeTrusted](capi-teetrusted.md)

**Header file**: [tee_defines.h](capi-tee-defines-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| void *dataPtr | Pointer to the data. |
| uint32_t dataLen | Length of the data. |
| uint8_t dataName[OBJECT_NAME_LEN_MAX] | Name of the data. |
| TEE_ObjectInfo *ObjectInfo | Pointer to the object information. |
| TEE_Attribute *Attribute | Pointer to the attributes of the object. |
| uint32_t attributesLen | Length of the attributes. |
| uint32_t CRTMode | CRT mode. |
| void *infoattrfd | File descriptor for info attributes. |
| uint32_t generate_flag | Flag for object generation. |
| uint32_t storage_id | Storage ID for the object. |


