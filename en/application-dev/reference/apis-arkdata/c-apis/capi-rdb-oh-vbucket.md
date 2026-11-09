# OH_VBucket

```c
typedef struct OH_VBucket {...} OH_VBucket
```

## Overview

Define the OH_VBucket structure type.

<!--Device-typedef struct OH_VBucket {...} OH_VBucket--><!--Device-typedef struct OH_VBucket {...} OH_VBucket-End-->

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 10

**Related module**: [RDB](capi-arkdata-rdb.md)

**Header file**: [oh_values_bucket.h](capi-oh-values-bucket-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int64_t id | The id used to uniquely identify the OH_VBucket struct. |
| uint16_t capability | Indicates the capability of OH_VBucket. |


### Member functions

| Name | Description |
| -- | -- |
| [int (\*putText)(OH_VBucket *bucket, const char *field, const char *value)](#puttext) | - | Put the const char * value to this [OH_VBucket](capi-rdb-oh-vbucket.md) object for the given column name. |
| [int (\*putInt64)(OH_VBucket *bucket, const char *field, int64_t value)](#putint64) | - | Put the int64 value to this [OH_VBucket](capi-rdb-oh-vbucket.md) object for the given column name. |
| [int (\*putReal)(OH_VBucket *bucket, const char *field, double value)](#putreal) | - | Put the double value to this [OH_VBucket](capi-rdb-oh-vbucket.md) object for the given column name. |
| [int (\*putBlob)(OH_VBucket *bucket, const char *field, const uint8_t *value, uint32_t size)](#putblob) | - | Put the const uint8_t * value to this [OH_VBucket](capi-rdb-oh-vbucket.md) object for the given column name. |
| [int (\*putNull)(OH_VBucket *bucket, const char *field)](#putnull) | - | Put NULL to this [OH_VBucket](capi-rdb-oh-vbucket.md) object for the given column name. |
| [int (\*clear)(OH_VBucket *bucket)](#clear) | - | Clear the [OH_VBucket](capi-rdb-oh-vbucket.md) object's values. |
| [int (\*destroy)(OH_VBucket *bucket)](#destroy) | - | Destroy the [OH_VBucket](capi-rdb-oh-vbucket.md) object and reclaim the memory occupied by the object. |

## Member function description

### putText()

```c
int (*putText)(OH_VBucket *bucket, const char *field, const char *value)
```

**Description**

Put the const char * value to this [OH_VBucket](capi-rdb-oh-vbucket.md) object for the given column name.

<!--Device-int (*putText)(OH_VBucket *bucket, const char *field, const char *value)--><!--Device-int (*putText)(OH_VBucket *bucket, const char *field, const char *value)-End-->

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_VBucket](capi-rdb-oh-vbucket.md) *bucket | Represents a pointer to an [OH_VBucket](capi-rdb-oh-vbucket.md) instance. |
|  const char *field | Indicates the name of the column. |
|  const char *value | Indicates the const char * value. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. |

**Reference**:

[OH_VBucket](capi-rdb-oh-vbucket.md)


### putInt64()

```c
int (*putInt64)(OH_VBucket *bucket, const char *field, int64_t value)
```

**Description**

Put the int64 value to this [OH_VBucket](capi-rdb-oh-vbucket.md) object for the given column name.

<!--Device-int (*putInt64)(OH_VBucket *bucket, const char *field, int64_t value)--><!--Device-int (*putInt64)(OH_VBucket *bucket, const char *field, int64_t value)-End-->

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_VBucket](capi-rdb-oh-vbucket.md) *bucket | Represents a pointer to an [OH_VBucket](capi-rdb-oh-vbucket.md) instance. |
|  const char *field | Indicates the name of the column. |
|  int64_t value | Indicates the int64 value. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. |

**Reference**:

[OH_VBucket](capi-rdb-oh-vbucket.md)


### putReal()

```c
int (*putReal)(OH_VBucket *bucket, const char *field, double value)
```

**Description**

Put the double value to this [OH_VBucket](capi-rdb-oh-vbucket.md) object for the given column name.

<!--Device-int (*putReal)(OH_VBucket *bucket, const char *field, double value)--><!--Device-int (*putReal)(OH_VBucket *bucket, const char *field, double value)-End-->

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_VBucket](capi-rdb-oh-vbucket.md) *bucket | Represents a pointer to an [OH_VBucket](capi-rdb-oh-vbucket.md) instance. |
|  const char *field | Indicates the name of the column. |
|  double value | Indicates the double value. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. |

**Reference**:

[OH_VBucket](capi-rdb-oh-vbucket.md)


### putBlob()

```c
int (*putBlob)(OH_VBucket *bucket, const char *field, const uint8_t *value, uint32_t size)
```

**Description**

Put the const uint8_t * value to this [OH_VBucket](capi-rdb-oh-vbucket.md) object for the given column name.

<!--Device-int (*putBlob)(OH_VBucket *bucket, const char *field, const uint8_t *value, uint32_t size)--><!--Device-int (*putBlob)(OH_VBucket *bucket, const char *field, const uint8_t *value, uint32_t size)-End-->

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_VBucket](capi-rdb-oh-vbucket.md) *bucket | Represents a pointer to an [OH_VBucket](capi-rdb-oh-vbucket.md) instance. |
|  const char *field | Indicates the name of the column. |
|  const uint8_t *value | Indicates the const uint8_t * value. |
|  uint32_t size | Indicates the size of value. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. |

**Reference**:

[OH_VBucket](capi-rdb-oh-vbucket.md)


### putNull()

```c
int (*putNull)(OH_VBucket *bucket, const char *field)
```

**Description**

Put NULL to this [OH_VBucket](capi-rdb-oh-vbucket.md) object for the given column name.

<!--Device-int (*putNull)(OH_VBucket *bucket, const char *field)--><!--Device-int (*putNull)(OH_VBucket *bucket, const char *field)-End-->

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_VBucket](capi-rdb-oh-vbucket.md) *bucket | Represents a pointer to an [OH_VBucket](capi-rdb-oh-vbucket.md) instance. |
|  const char *field | Indicates the name of the column. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. |

**Reference**:

[OH_VBucket](capi-rdb-oh-vbucket.md)


### clear()

```c
int (*clear)(OH_VBucket *bucket)
```

**Description**

Clear the [OH_VBucket](capi-rdb-oh-vbucket.md) object's values.

<!--Device-int (*clear)(OH_VBucket *bucket)--><!--Device-int (*clear)(OH_VBucket *bucket)-End-->

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_VBucket](capi-rdb-oh-vbucket.md) *bucket | Represents a pointer to an [OH_VBucket](capi-rdb-oh-vbucket.md) instance. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. |

**Reference**:

[OH_VBucket](capi-rdb-oh-vbucket.md)


### destroy()

```c
int (*destroy)(OH_VBucket *bucket)
```

**Description**

Destroy the [OH_VBucket](capi-rdb-oh-vbucket.md) object and reclaim the memory occupied by the object.

<!--Device-int (*destroy)(OH_VBucket *bucket)--><!--Device-int (*destroy)(OH_VBucket *bucket)-End-->

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_VBucket](capi-rdb-oh-vbucket.md) *bucket | Represents a pointer to an [OH_VBucket](capi-rdb-oh-vbucket.md) instance. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. |

**Reference**:

[OH_VBucket](capi-rdb-oh-vbucket.md)



