# utd.h

## Overview

Provides uniform type descriptor(UTD) related functions and struct.

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
| [void OH_Utd_Destroy(OH_Utd* pThis)](#oh_utd_destroy) | Destroy a pointer that points to the [OH_Utd](capi-udmf-oh-utd.md) instance. |
| [const char* OH_Utd_GetTypeId(OH_Utd* pThis)](#oh_utd_gettypeid) | Get type id from the [OH_Utd](capi-udmf-oh-utd.md). |
| [const char* OH_Utd_GetDescription(OH_Utd* pThis)](#oh_utd_getdescription) | Get description from the [OH_Utd](capi-udmf-oh-utd.md). |
| [const char* OH_Utd_GetReferenceUrl(OH_Utd* pThis)](#oh_utd_getreferenceurl) | Get url from the [OH_Utd](capi-udmf-oh-utd.md). |
| [const char* OH_Utd_GetIconFile(OH_Utd* pThis)](#oh_utd_geticonfile) | Get icon file from the [OH_Utd](capi-udmf-oh-utd.md). |
| [const char** OH_Utd_GetBelongingToTypes(OH_Utd* pThis, unsigned int* count)](#oh_utd_getbelongingtotypes) | Get belong to type id of the current [OH_Utd](capi-udmf-oh-utd.md). |
| [const char** OH_Utd_GetFilenameExtensions(OH_Utd* pThis, unsigned int* count)](#oh_utd_getfilenameextensions) | Get filename extensions of the current [OH_Utd](capi-udmf-oh-utd.md). |
| [const char** OH_Utd_GetMimeTypes(OH_Utd* pThis, unsigned int* count)](#oh_utd_getmimetypes) | Get mime types of the current [OH_Utd](capi-udmf-oh-utd.md). |
| [const char** OH_Utd_GetTypesByFilenameExtension(const char* extension, unsigned int* count)](#oh_utd_gettypesbyfilenameextension) | Get type id by file name extension. |
| [const char** OH_Utd_GetTypesByMimeType(const char* mimeType, unsigned int* count)](#oh_utd_gettypesbymimetype) | Get type id by mime type. |
| [bool OH_Utd_BelongsTo(const char* srcTypeId, const char* destTypeId)](#oh_utd_belongsto) | Calculate relationships of two types. |
| [bool OH_Utd_IsLower(const char* srcTypeId, const char* destTypeId)](#oh_utd_islower) | Calculate relationships of two types. |
| [bool OH_Utd_IsHigher(const char* srcTypeId, const char* destTypeId)](#oh_utd_ishigher) | Calculate relationships of two types. |
| [bool OH_Utd_Equals(OH_Utd* utd1, OH_Utd* utd2)](#oh_utd_equals) | Calculate two [OH_Utd](capi-udmf-oh-utd.md)s are equal. |
| [void OH_Utd_DestroyStringList(const char** list, unsigned int count)](#oh_utd_destroystringlist) | Destroy string list memory. |

## Function description

### OH_Utd_Create()

```c
OH_Utd* OH_Utd_Create(const char* typeId)
```

**Description**

Creates a pointer to the instance of the [OH_Utd](capi-udmf-oh-utd.md).

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char* typeId | Represents type of UTD, reference udmf_meta.h. |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_Utd*](capi-udmf-oh-utd.md) | If the operation is successful, a pointer to the instance of the [OH_Utd](capi-udmf-oh-utd.md)  structure is returned.If the operation is failed, nullptr is returned.  Must be destroyed with [OH_Utd_Destroy](capi-utd-h.md#oh_utd_destroy) when not needed. |

**Reference**:

OH_Utd


### OH_Utd_Destroy()

```c
void OH_Utd_Destroy(OH_Utd* pThis)
```

**Description**

Destroy a pointer that points to the [OH_Utd](capi-udmf-oh-utd.md) instance.

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

Get type id from the [OH_Utd](capi-udmf-oh-utd.md).

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

Get description from the [OH_Utd](capi-udmf-oh-utd.md).

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

Get url from the [OH_Utd](capi-udmf-oh-utd.md).

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

Get icon file from the [OH_Utd](capi-udmf-oh-utd.md).

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

Get belong to type id of the current [OH_Utd](capi-udmf-oh-utd.md).

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

Get filename extensions of the current [OH_Utd](capi-udmf-oh-utd.md).

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

Get mime types of the current [OH_Utd](capi-udmf-oh-utd.md).

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

Get type id by file name extension.

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

Get type id by mime type.

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

Calculate relationships of two types.

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

Calculate relationships of two types.

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

Calculate relationships of two types.

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

Calculate two [OH_Utd](capi-udmf-oh-utd.md)s are equal.

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

Destroy string list memory.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char** list | Represents a point to string list. |
| unsigned int count | Represents string count in list. |


