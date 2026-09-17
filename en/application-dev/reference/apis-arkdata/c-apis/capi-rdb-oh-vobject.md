# OH_VObject

```c
typedef struct OH_VObject {...} OH_VObject
```

## Overview

Define the OH_VObject structure type.

**Since**: 10

**Related module**: [RDB](capi-rdb.md)

**Header file**: [oh_value_object.h](capi-oh-value-object-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int64_t id | The id used to uniquely identify the OH_VObject struct. |


### Member functions

| Name | Description |
| -- | -- |
| [int (\*putInt64)(OH_VObject *valueObject, int64_t *value, uint32_t count)](#putint64) | Convert the int64 input parameter to a value of type [OH_VObject](capi-rdb-oh-vobject.md). |
| [int (\*putDouble)(OH_VObject *valueObject, double *value, uint32_t count)](#putdouble) | Convert the double input parameter to a value of type [OH_VObject](capi-rdb-oh-vobject.md). |
| [int (\*putText)(OH_VObject *valueObject, const char *value)](#puttext) | Convert the char input parameter to a value of type [OH_VObject](capi-rdb-oh-vobject.md). |
| [int (\*putTexts)(OH_VObject *valueObject, const char **value, uint32_t count)](#puttexts) | Convert the char * array input parameter to a value of type [OH_VObject](capi-rdb-oh-vobject.md). |
| [int (\*destroy)(OH_VObject *valueObject)](#destroy) | Destroy the [OH_VObject](capi-rdb-oh-vobject.md) object and reclaim the memory occupied by the object. |

## Member function description

### putInt64()

```c
int (*putInt64)(OH_VObject *valueObject, int64_t *value, uint32_t count)
```

**Description**

Convert the int64 input parameter to a value of type [OH_VObject](capi-rdb-oh-vobject.md).

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_VObject](capi-rdb-oh-vobject.md) *valueObject | Represents a pointer to an [OH_VObject](capi-rdb-oh-vobject.md) instance. |
|  int64_t *value | Represents a pointer to an int64_t input parameter or the array of type int64_t. |
|  uint32_t count | If value is a pointer to a single numerical value, count = 1; if value is a pointer to an array, count is the size of the array. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. |

**Reference**:

OH_VObject


### putDouble()

```c
int (*putDouble)(OH_VObject *valueObject, double *value, uint32_t count)
```

**Description**

Convert the double input parameter to a value of type [OH_VObject](capi-rdb-oh-vobject.md).

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_VObject](capi-rdb-oh-vobject.md) *valueObject | Represents a pointer to an [OH_VObject](capi-rdb-oh-vobject.md) instance. |
|  double *value | Represents a pointer to an double input parameter or the array of type double. |
|  uint32_t count | If value is a pointer to a single numerical value, count = 1; if value is a pointer to an array, count is the size of the array. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. |

**Reference**:

OH_VObject


### putText()

```c
int (*putText)(OH_VObject *valueObject, const char *value)
```

**Description**

Convert the char input parameter to a value of type [OH_VObject](capi-rdb-oh-vobject.md).

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_VObject](capi-rdb-oh-vobject.md) *valueObject | Represents a pointer to an [OH_VObject](capi-rdb-oh-vobject.md) instance. |
|  const char *value | Indicates the const char * input parameter. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. |

**Reference**:

OH_VObject


### putTexts()

```c
int (*putTexts)(OH_VObject *valueObject, const char **value, uint32_t count)
```

**Description**

Convert the char * array input parameter to a value of type [OH_VObject](capi-rdb-oh-vobject.md).

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_VObject](capi-rdb-oh-vobject.md) *valueObject | Represents a pointer to an [OH_VObject](capi-rdb-oh-vobject.md) instance. |
|  const char **value | Indicates the const char * array input parameter. |
|  uint32_t count | Indicates the size of the value. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. |

**Reference**:

OH_VObject


### destroy()

```c
int (*destroy)(OH_VObject *valueObject)
```

**Description**

Destroy the [OH_VObject](capi-rdb-oh-vobject.md) object and reclaim the memory occupied by the object.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_VObject](capi-rdb-oh-vobject.md) *valueObject | Represents a pointer to an [OH_VObject](capi-rdb-oh-vobject.md) instance. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. |

**Reference**:

OH_VObject



