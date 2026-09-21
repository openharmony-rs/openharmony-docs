# utd.h

## Overview

Defines APIs and structs related to the Uniform Type Descriptors (UTDs). If the parameter type is char*, the string must end with a null character ('\0').

**Library**: libudmf.so

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 12

**Related module**: [UDMF](capi-udmf.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_Utd](capi-udmf-oh-utd.md) | OH_Utd | Describes the unified data type descriptor. |

### Function

| Name | Description |
| -- | -- |
| [OH_Utd* OH_Utd_Create(const char* typeId)](#oh_utd_create) | Creates a pointer to the instance of the [OH_Utd](capi-udmf-oh-utd.md). |
| [void OH_Utd_Destroy(OH_Utd* pThis)](#oh_utd_destroy) | Destroys an [OH_Utd](capi-udmf-oh-utd.md) instance. After the pointer is destroyed, it becomes invalid and cannot be used again. Otherwise, undefined behavior may occur. |
| [const char* OH_Utd_GetTypeId(OH_Utd* pThis)](#oh_utd_gettypeid) | Obtains the type ID from an [OH_Utd](capi-udmf-oh-utd.md) instance. |
| [const char* OH_Utd_GetDescription(OH_Utd* pThis)](#oh_utd_getdescription) | Obtains the description from an [OH_Utd](capi-udmf-oh-utd.md) instance. |
| [const char* OH_Utd_GetReferenceUrl(OH_Utd* pThis)](#oh_utd_getreferenceurl) | Obtains the URL from an [OH_Utd](capi-udmf-oh-utd.md) instance. |
| [const char* OH_Utd_GetIconFile(OH_Utd* pThis)](#oh_utd_geticonfile) | Obtains the path of the default icon file from an [OH_Utd](capi-udmf-oh-utd.md) instance. |
| [const char** OH_Utd_GetBelongingToTypes(OH_Utd* pThis, unsigned int* count)](#oh_utd_getbelongingtotypes) | Obtains the relationships between the data from an [OH_Utd](capi-udmf-oh-utd.md) instance. |
| [const char** OH_Utd_GetFilenameExtensions(OH_Utd* pThis, unsigned int* count)](#oh_utd_getfilenameextensions) | Obtains the file name extensions associated with an [OH_Utd](capi-udmf-oh-utd.md) instance. |
| [const char** OH_Utd_GetMimeTypes(OH_Utd* pThis, unsigned int* count)](#oh_utd_getmimetypes) | Obtains the MIME types associated with an [OH_Utd](capi-udmf-oh-utd.md) instance. |
| [const char** OH_Utd_GetTypesByFilenameExtension(const char* extension, unsigned int* count)](#oh_utd_gettypesbyfilenameextension) | Obtains the UTDs based on the file name extensions. |
| [const char** OH_Utd_GetTypesByMimeType(const char* mimeType, unsigned int* count)](#oh_utd_gettypesbymimetype) | Obtains the UTDs based on the MIME types. |
| [bool OH_Utd_BelongsTo(const char* srcTypeId, const char* destTypeId)](#oh_utd_belongsto) | Checks whether a UTD belongs to the target UTD. |
| [bool OH_Utd_IsLower(const char* srcTypeId, const char* destTypeId)](#oh_utd_islower) | Checks whether a UTD is a lower-level type of the target UTD. For example, TYPE_SCRIPT is a lower-level type of SOURCE_CODE, and TYPE_SCRIPT and SOURCE_CODE are lower-level types of PLAIN_TEXT. |
| [bool OH_Utd_IsHigher(const char* srcTypeId, const char* destTypeId)](#oh_utd_ishigher) | Checks whether a UTD is a higher-level type of the target UTD. For example, SOURCE_CODE is a higher-level type of TYPE_SCRIPT, and PLAIN_TEXT is a higher-level type of SOURCE_CODE and TYPE_SCRIPT. |
| [bool OH_Utd_Equals(OH_Utd* utd1, OH_Utd* utd2)](#oh_utd_equals) | Checks whether two UTDs are the same. |
| [void OH_Utd_DestroyStringList(const char** list, unsigned int count)](#oh_utd_destroystringlist) | Destroys a UTD list. After the list is destroyed, it becomes invalid and cannot be used again. Otherwise, undefined behavior may occur. |

## Function description

### OH_Utd_Create()

```c
OH_Utd* OH_Utd_Create(const char* typeId)
```

**Description**

Creates a pointer to the instance of the [OH_Utd](capi-udmf-oh-utd.md).

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char* typeId | Represents type of UTD, reference udmf_meta.h. |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_Utd*](capi-udmf-oh-utd.md) | Returns a pointer to the [OH_Utd](capi-udmf-oh-utd.md)instance created if the operation is successful; returns nullptr      otherwise. If this pointer is no longer required, use [OH_Utd_Destroy](capi-utd-h.md#oh_utd_destroy) to destroy it. Otherwise,      memory leaks may occur. |

**Reference**:

OH_Utd


### OH_Utd_Destroy()

```c
void OH_Utd_Destroy(OH_Utd* pThis)
```

**Description**

Destroys an [OH_Utd](capi-udmf-oh-utd.md) instance. After the pointer is destroyed, it becomes invalid and cannot be used again. Otherwise, undefined behavior may occur.

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Utd](capi-udmf-oh-utd.md)* pThis | Represents a pointer to an instance of [OH_Utd](capi-udmf-oh-utd.md). |

**Reference**:

OH_Utd


### OH_Utd_GetTypeId()

```c
const char* OH_Utd_GetTypeId(OH_Utd* pThis)
```

**Description**

Obtains the type ID from an [OH_Utd](capi-udmf-oh-utd.md) instance.

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Utd](capi-udmf-oh-utd.md)* pThis | Represents a pointer to an instance of [OH_Utd](capi-udmf-oh-utd.md). |

**Returns**:

| Type | Description |
| -- | -- |
| const char* | Returns a string pointer when input args normally, otherwise return nullptr. |

**Reference**:

OH_Utd


### OH_Utd_GetDescription()

```c
const char* OH_Utd_GetDescription(OH_Utd* pThis)
```

**Description**

Obtains the description from an [OH_Utd](capi-udmf-oh-utd.md) instance.

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Utd](capi-udmf-oh-utd.md)* pThis | Represents a pointer to an instance of [OH_Utd](capi-udmf-oh-utd.md). |

**Returns**:

| Type | Description |
| -- | -- |
| const char* | Returns a string pointer when input args normally, otherwise return nullptr. |

**Reference**:

OH_Utd


### OH_Utd_GetReferenceUrl()

```c
const char* OH_Utd_GetReferenceUrl(OH_Utd* pThis)
```

**Description**

Obtains the URL from an [OH_Utd](capi-udmf-oh-utd.md) instance.

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Utd](capi-udmf-oh-utd.md)* pThis | Represents a pointer to an instance of [OH_Utd](capi-udmf-oh-utd.md). |

**Returns**:

| Type | Description |
| -- | -- |
| const char* | Returns a string pointer when input args normally, otherwise return nullptr. |

**Reference**:

OH_Utd


### OH_Utd_GetIconFile()

```c
const char* OH_Utd_GetIconFile(OH_Utd* pThis)
```

**Description**

Obtains the path of the default icon file from an [OH_Utd](capi-udmf-oh-utd.md) instance.

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Utd](capi-udmf-oh-utd.md)* pThis | Represents a pointer to an instance of [OH_Utd](capi-udmf-oh-utd.md). |

**Returns**:

| Type | Description |
| -- | -- |
| const char* | Returns a string pointer when input args normally, otherwise return nullptr. |

**Reference**:

OH_Utd


### OH_Utd_GetBelongingToTypes()

```c
const char** OH_Utd_GetBelongingToTypes(OH_Utd* pThis, unsigned int* count)
```

**Description**

Obtains the relationships between the data from an [OH_Utd](capi-udmf-oh-utd.md) instance.

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Utd](capi-udmf-oh-utd.md)* pThis | Represents a pointer to an instance of [OH_Utd](capi-udmf-oh-utd.md). |
| unsigned int* count | Represents the return types count. |

**Returns**:

| Type | Description |
| -- | -- |
| const char** | Returns string array when input args normally, otherwise return nullptr. |

**Reference**:

OH_Utd


### OH_Utd_GetFilenameExtensions()

```c
const char** OH_Utd_GetFilenameExtensions(OH_Utd* pThis, unsigned int* count)
```

**Description**

Obtains the file name extensions associated with an [OH_Utd](capi-udmf-oh-utd.md) instance.

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Utd](capi-udmf-oh-utd.md)* pThis | Represents a pointer to an instance of [OH_Utd](capi-udmf-oh-utd.md). |
| unsigned int* count | Represents the return file extensions count. |

**Returns**:

| Type | Description |
| -- | -- |
| const char** | Returns string array when input args normally, otherwise return nullptr. |

**Reference**:

OH_Utd


### OH_Utd_GetMimeTypes()

```c
const char** OH_Utd_GetMimeTypes(OH_Utd* pThis, unsigned int* count)
```

**Description**

Obtains the MIME types associated with an [OH_Utd](capi-udmf-oh-utd.md) instance.

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Utd](capi-udmf-oh-utd.md)* pThis | Represents a pointer to an instance of [OH_Utd](capi-udmf-oh-utd.md). |
| unsigned int* count | Represents the mime types count. |

**Returns**:

| Type | Description |
| -- | -- |
| const char** | Returns string array when input args normally, otherwise return nullptr. |

**Reference**:

OH_Utd


### OH_Utd_GetTypesByFilenameExtension()

```c
const char** OH_Utd_GetTypesByFilenameExtension(const char* extension, unsigned int* count)
```

**Description**

Obtains the UTDs based on the file name extensions.

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char* extension | Represents file name extension. |
| unsigned int* count | Represents the types count. |

**Returns**:

| Type | Description |
| -- | -- |
| const char** | Returns string list of types. Must be destroyed with [OH_Utd_DestroyStringList](capi-utd-h.md#oh_utd_destroystringlist) when not needed. |

### OH_Utd_GetTypesByMimeType()

```c
const char** OH_Utd_GetTypesByMimeType(const char* mimeType, unsigned int* count)
```

**Description**

Obtains the UTDs based on the MIME types.

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char* mimeType | Represents mime type |
| unsigned int* count | Represents the types count. |

**Returns**:

| Type | Description |
| -- | -- |
| const char** | Returns string list of types. Must be destroyed with [OH_Utd_DestroyStringList](capi-utd-h.md#oh_utd_destroystringlist) when not needed. |

### OH_Utd_BelongsTo()

```c
bool OH_Utd_BelongsTo(const char* srcTypeId, const char* destTypeId)
```

**Description**

Checks whether a UTD belongs to the target UTD.

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char* srcTypeId | Represents source type id. |
| const char* destTypeId | Represents target type id. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Returns the status code of the execution.          {@code false} Represents srcTypeId not belongs to destTypeId.<br>        {@code true} Represents srcTypeId belongs to destTypeId. |

### OH_Utd_IsLower()

```c
bool OH_Utd_IsLower(const char* srcTypeId, const char* destTypeId)
```

**Description**

Checks whether a UTD is a lower-level type of the target UTD. For example, TYPE_SCRIPT is a lower-level type of SOURCE_CODE, and TYPE_SCRIPT and SOURCE_CODE are lower-level types of PLAIN_TEXT.

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char* srcTypeId | Represents source type id. |
| const char* destTypeId | Represents target type id. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Returns the status code of the execution.          {@code false} Represents srcTypeId not lower level to destTypeId.<br>        {@code true} Represents srcTypeId lower level to destTypeId. |

### OH_Utd_IsHigher()

```c
bool OH_Utd_IsHigher(const char* srcTypeId, const char* destTypeId)
```

**Description**

Checks whether a UTD is a higher-level type of the target UTD. For example, SOURCE_CODE is a higher-level type of TYPE_SCRIPT, and PLAIN_TEXT is a higher-level type of SOURCE_CODE and TYPE_SCRIPT.

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char* srcTypeId | Represents source type id. |
| const char* destTypeId | Represents target type id. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Returns the status code of the execution.          {@code false} Represents srcTypeId not higher level to destTypeId.<br>        {@code true} Represents srcTypeId higher level to destTypeId. |

### OH_Utd_Equals()

```c
bool OH_Utd_Equals(OH_Utd* utd1, OH_Utd* utd2)
```

**Description**

Checks whether two UTDs are the same.

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Utd](capi-udmf-oh-utd.md)* utd1 | Represents a pointer to [OH_Utd](capi-udmf-oh-utd.md) instance. |
| [OH_Utd](capi-udmf-oh-utd.md)* utd2 | Represents a pointer to [OH_Utd](capi-udmf-oh-utd.md) instance. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Returns the status code of the execution.          {@code false} Represents utd1 and utd2 are not equal.<br>        {@code true} Represents utd1 and utd2 are equal. |

### OH_Utd_DestroyStringList()

```c
void OH_Utd_DestroyStringList(const char** list, unsigned int count)
```

**Description**

Destroys a UTD list. After the list is destroyed, it becomes invalid and cannot be used again. Otherwise, undefined behavior may occur.

**System capability**: SystemCapability.DistributedDataManager.UDMF.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char** list | Represents a point to string list. |
| unsigned int count | Represents string count in list. |


