# data_asset.h

## Overview

Provides the data type of asset.

**Library**: libnative_rdb_ndk.z.so

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 10

**Related module**: [RDB](capi-rdb.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [Data_Asset](capi-rdb-data-asset.md) | Data_Asset | Define the Data_Asset structure type.<br> Provides information of an asset. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [Data_AssetStatus](#data_assetstatus) | Data_AssetStatus | Describes the status of asset. |

### Function

| Name | Description |
| -- | -- |
| [int OH_Data_Asset_SetName(Data_Asset *asset, const char *name)](#oh_data_asset_setname) | Set the name of the Data_Asset. |
| [int OH_Data_Asset_SetUri(Data_Asset *asset, const char *uri)](#oh_data_asset_seturi) | Set the uri of the Data_Asset. |
| [int OH_Data_Asset_SetPath(Data_Asset *asset, const char *path)](#oh_data_asset_setpath) | Set the path of the Data_Asset. |
| [int OH_Data_Asset_SetCreateTime(Data_Asset *asset, int64_t createTime)](#oh_data_asset_setcreatetime) | Set the create time of the Data_Asset. |
| [int OH_Data_Asset_SetModifyTime(Data_Asset *asset, int64_t modifyTime)](#oh_data_asset_setmodifytime) | Set the modify time of the Data_Asset. |
| [int OH_Data_Asset_SetSize(Data_Asset *asset, size_t size)](#oh_data_asset_setsize) | Set the size of the Data_Asset. |
| [int OH_Data_Asset_SetStatus(Data_Asset *asset, Data_AssetStatus status)](#oh_data_asset_setstatus) | Set the status of the Data_Asset. |
| [int OH_Data_Asset_GetName(Data_Asset *asset, char *name, size_t *length)](#oh_data_asset_getname) | Obtains the name of the asset. |
| [int OH_Data_Asset_GetUri(Data_Asset *asset, char *uri, size_t *length)](#oh_data_asset_geturi) | Obtains the uri of the asset. |
| [int OH_Data_Asset_GetPath(Data_Asset *asset, char *path, size_t *length)](#oh_data_asset_getpath) | Obtains the path of the asset. |
| [int OH_Data_Asset_GetCreateTime(Data_Asset *asset, int64_t *createTime)](#oh_data_asset_getcreatetime) | Obtains the create time of the asset. |
| [int OH_Data_Asset_GetModifyTime(Data_Asset *asset, int64_t *modifyTime)](#oh_data_asset_getmodifytime) | Obtains the modify time of the asset. |
| [int OH_Data_Asset_GetSize(Data_Asset *asset, size_t *size)](#oh_data_asset_getsize) | Obtains the size of the asset. |
| [int OH_Data_Asset_GetStatus(Data_Asset *asset, Data_AssetStatus *status)](#oh_data_asset_getstatus) | Obtains the status of the asset. |
| [Data_Asset *OH_Data_Asset_CreateOne(void)](#oh_data_asset_createone) | Creates an [Data_Asset](capi-rdb-data-asset.md) instance. |
| [int OH_Data_Asset_DestroyOne(Data_Asset *asset)](#oh_data_asset_destroyone) | Destroy the [Data_Asset](capi-rdb-data-asset.md) object and reclaim the memory occupied by the object. |
| [Data_Asset **OH_Data_Asset_CreateMultiple(uint32_t count)](#oh_data_asset_createmultiple) | Creates [Data_Asset](capi-rdb-data-asset.md) instances of given number. |
| [int OH_Data_Asset_DestroyMultiple(Data_Asset **assets, uint32_t count)](#oh_data_asset_destroymultiple) | Destroy the [Data_Asset](capi-rdb-data-asset.md) objects and reclaim the memory occupied by the objects. |

## Enum type description

### Data_AssetStatus

```c
enum Data_AssetStatus
```

**Description**

Describes the status of asset.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 11

| Enum item | Description |
| -- | -- |
| ASSET_NULL = 0 | Means the status of asset is null. |
| ASSET_NORMAL | Means the status of asset is normal. |
| ASSET_INSERT | Means the asset needs to be inserted. |
| ASSET_UPDATE | Means the asset needs to be updated. |
| ASSET_DELETE | Means the asset needs to be deleted. |
| ASSET_ABNORMAL | Means the status of asset is abnormal. |
| ASSET_DOWNLOADING | Means the status of asset is downloading. |


## Function description

### OH_Data_Asset_SetName()

```c
int OH_Data_Asset_SetName(Data_Asset *asset, const char *name)
```

**Description**

Set the name of the Data_Asset.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Data_Asset](capi-rdb-data-asset.md) *asset | Represents a pointer to an [Data_Asset](capi-rdb-data-asset.md) instance. |
| const char *name | Indicates the name to set. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns a specific error code.      {@link RDB_OK} - success.<br>    {@link RDB_E_INVALID_ARGS} - The error code for common invalid args.<br>Specific error codes can be referenced {@link OH_Rdb_ErrCode}. |

**Reference**:

[Data_Asset](capi-rdb-data-asset.md)


### OH_Data_Asset_SetUri()

```c
int OH_Data_Asset_SetUri(Data_Asset *asset, const char *uri)
```

**Description**

Set the uri of the Data_Asset.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Data_Asset](capi-rdb-data-asset.md) *asset | Represents a pointer to an [Data_Asset](capi-rdb-data-asset.md) instance. |
| const char *uri | Indicates the uri to set. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns a specific error code.      {@link RDB_OK} - success.<br>    {@link RDB_E_INVALID_ARGS} - The error code for common invalid args.<br>Specific error codes can be referenced {@link OH_Rdb_ErrCode}. |

**Reference**:

[Data_Asset](capi-rdb-data-asset.md)


### OH_Data_Asset_SetPath()

```c
int OH_Data_Asset_SetPath(Data_Asset *asset, const char *path)
```

**Description**

Set the path of the Data_Asset.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Data_Asset](capi-rdb-data-asset.md) *asset | Represents a pointer to an [Data_Asset](capi-rdb-data-asset.md) instance. |
| const char *path | Indicates the path to set. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns a specific error code.      {@link RDB_OK} - success.<br>    {@link RDB_E_INVALID_ARGS} - The error code for common invalid args.<br>Specific error codes can be referenced {@link OH_Rdb_ErrCode}. |

**Reference**:

[Data_Asset](capi-rdb-data-asset.md)


### OH_Data_Asset_SetCreateTime()

```c
int OH_Data_Asset_SetCreateTime(Data_Asset *asset, int64_t createTime)
```

**Description**

Set the create time of the Data_Asset.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Data_Asset](capi-rdb-data-asset.md) *asset | Represents a pointer to an [Data_Asset](capi-rdb-data-asset.md) instance. |
| int64_t createTime | Indicates the create time to set. There is no specific unit. Developers can specify it themselves. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns a specific error code.      {@link RDB_OK} - success.<br>    {@link RDB_E_INVALID_ARGS} - The error code for common invalid args.<br>Specific error codes can be referenced {@link OH_Rdb_ErrCode}. |

**Reference**:

[Data_Asset](capi-rdb-data-asset.md)


### OH_Data_Asset_SetModifyTime()

```c
int OH_Data_Asset_SetModifyTime(Data_Asset *asset, int64_t modifyTime)
```

**Description**

Set the modify time of the Data_Asset.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Data_Asset](capi-rdb-data-asset.md) *asset | Represents a pointer to an [Data_Asset](capi-rdb-data-asset.md) instance. |
| int64_t modifyTime | Indicates the create time to set. There is no specific unit. Developers can specify it themselves. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns a specific error code.      {@link RDB_OK} - success.<br>    {@link RDB_E_INVALID_ARGS} - The error code for common invalid args.<br>Specific error codes can be referenced {@link OH_Rdb_ErrCode}. |

**Reference**:

[Data_Asset](capi-rdb-data-asset.md)


### OH_Data_Asset_SetSize()

```c
int OH_Data_Asset_SetSize(Data_Asset *asset, size_t size)
```

**Description**

Set the size of the Data_Asset.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Data_Asset](capi-rdb-data-asset.md) *asset | Represents a pointer to an [Data_Asset](capi-rdb-data-asset.md) instance. |
| size_t size | Indicates the size to set. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns a specific error code.      {@link RDB_OK} - success.<br>    {@link RDB_E_INVALID_ARGS} - The error code for common invalid args.<br>Specific error codes can be referenced {@link OH_Rdb_ErrCode}. |

**Reference**:

[Data_Asset](capi-rdb-data-asset.md)


### OH_Data_Asset_SetStatus()

```c
int OH_Data_Asset_SetStatus(Data_Asset *asset, Data_AssetStatus status)
```

**Description**

Set the status of the Data_Asset.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Data_Asset](capi-rdb-data-asset.md) *asset | Represents a pointer to an [Data_Asset](capi-rdb-data-asset.md) instance. |
| [Data_AssetStatus](capi-data-asset-h.md#data_assetstatus) status | Indicates the status to set. Specific status can be referenced [Data_AssetStatus](capi-data-asset-h.md#data_assetstatus). |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns a specific error code.      {@link RDB_OK} - success.<br>    {@link RDB_E_INVALID_ARGS} - The error code for common invalid args.<br>Specific error codes can be referenced {@link OH_Rdb_ErrCode}. |

**Reference**:

Data_Asset, Data_AssetStatus


### OH_Data_Asset_GetName()

```c
int OH_Data_Asset_GetName(Data_Asset *asset, char *name, size_t *length)
```

**Description**

Obtains the name of the asset.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Data_Asset](capi-rdb-data-asset.md) *asset | Represents a pointer to an [Data_Asset](capi-rdb-data-asset.md) instance. |
| char *name | This parameter is the output parameter, and the name of the asset as a char * is written to this variable. |
| size_t *length | Indicates the length of the name. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns a specific error code.      {@link RDB_ERR} - Indicates that the function execution exception.<br>    {@link RDB_OK} - success.<br>    {@link RDB_E_INVALID_ARGS} - The error code for common invalid args.<br>Specific error codes can be referenced {@link OH_Rdb_ErrCode}. |

**Reference**:

[Data_Asset](capi-rdb-data-asset.md)


### OH_Data_Asset_GetUri()

```c
int OH_Data_Asset_GetUri(Data_Asset *asset, char *uri, size_t *length)
```

**Description**

Obtains the uri of the asset.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Data_Asset](capi-rdb-data-asset.md) *asset | Represents a pointer to an [Data_Asset](capi-rdb-data-asset.md) instance. |
| char *uri | This parameter is the output parameter, and the uri of the asset as a char * is written to this variable. |
| size_t *length | Indicates the length of the uri. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns a specific error code.      {@link RDB_ERR} - Indicates that the function execution exception.<br>    {@link RDB_OK} - success.<br>    {@link RDB_E_INVALID_ARGS} - The error code for common invalid args.<br>Specific error codes can be referenced {@link OH_Rdb_ErrCode}. |

**Reference**:

[Data_Asset](capi-rdb-data-asset.md)


### OH_Data_Asset_GetPath()

```c
int OH_Data_Asset_GetPath(Data_Asset *asset, char *path, size_t *length)
```

**Description**

Obtains the path of the asset.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Data_Asset](capi-rdb-data-asset.md) *asset | Represents a pointer to an [Data_Asset](capi-rdb-data-asset.md) instance. |
| char *path | This parameter is the output parameter, and the path of the asset as a char * is written to this variable. |
| size_t *length | Indicates the length of the path. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns a specific error code.      {@link RDB_ERR} - Indicates that the function execution exception.<br>    {@link RDB_OK} - success.<br>    {@link RDB_E_INVALID_ARGS} - The error code for common invalid args.<br>Specific error codes can be referenced {@link OH_Rdb_ErrCode}. |

**Reference**:

[Data_Asset](capi-rdb-data-asset.md)


### OH_Data_Asset_GetCreateTime()

```c
int OH_Data_Asset_GetCreateTime(Data_Asset *asset, int64_t *createTime)
```

**Description**

Obtains the create time of the asset.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Data_Asset](capi-rdb-data-asset.md) *asset | Represents a pointer to an [Data_Asset](capi-rdb-data-asset.md) instance. |
| int64_t *createTime | This parameter is the output parameter, and the create time of the asset as a int64_t is written to this variable. There is no specific unit. Developers can specify it themselves. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns a specific error code.      {@link RDB_ERR} - Indicates that the function execution exception.<br>    {@link RDB_OK} - success.<br>    {@link RDB_E_INVALID_ARGS} - The error code for common invalid args.<br>Specific error codes can be referenced {@link OH_Rdb_ErrCode}. |

**Reference**:

[Data_Asset](capi-rdb-data-asset.md)


### OH_Data_Asset_GetModifyTime()

```c
int OH_Data_Asset_GetModifyTime(Data_Asset *asset, int64_t *modifyTime)
```

**Description**

Obtains the modify time of the asset.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Data_Asset](capi-rdb-data-asset.md) *asset | Represents a pointer to an [Data_Asset](capi-rdb-data-asset.md) instance. |
| int64_t *modifyTime | This parameter is the output parameter, and the create time of the asset as a int64_t is written to this variable. There is no specific unit. Developers can specify it themselves. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns a specific error code.      {@link RDB_ERR} - Indicates that the function execution exception.<br>    {@link RDB_OK} - success.<br>    {@link RDB_E_INVALID_ARGS} - The error code for common invalid args.<br>Specific error codes can be referenced {@link OH_Rdb_ErrCode}. |

**Reference**:

[Data_Asset](capi-rdb-data-asset.md)


### OH_Data_Asset_GetSize()

```c
int OH_Data_Asset_GetSize(Data_Asset *asset, size_t *size)
```

**Description**

Obtains the size of the asset.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Data_Asset](capi-rdb-data-asset.md) *asset | Represents a pointer to an [Data_Asset](capi-rdb-data-asset.md) instance. |
| size_t *size | This parameter is the output parameter, and the size of the asset as a size_t is written to this variable. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns a specific error code.      {@link RDB_ERR} - Indicates that the function execution exception.<br>    {@link RDB_OK} - success.<br>    {@link RDB_E_INVALID_ARGS} - The error code for common invalid args.<br>Specific error codes can be referenced {@link OH_Rdb_ErrCode}. |

**Reference**:

[Data_Asset](capi-rdb-data-asset.md)


### OH_Data_Asset_GetStatus()

```c
int OH_Data_Asset_GetStatus(Data_Asset *asset, Data_AssetStatus *status)
```

**Description**

Obtains the status of the asset.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Data_Asset](capi-rdb-data-asset.md) *asset | Represents a pointer to an [Data_Asset](capi-rdb-data-asset.md) instance. |
| [Data_AssetStatus](capi-data-asset-h.md#data_assetstatus) *status | This parameter is the output parameter, and the size of the status as a [Data_AssetStatus](capi-data-asset-h.md#data_assetstatus) is written to this variable. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns a specific error code.      {@link RDB_OK} - success.<br>    {@link RDB_E_INVALID_ARGS} - The error code for common invalid args.<br>Specific error codes can be referenced {@link OH_Rdb_ErrCode}. |

**Reference**:

Data_Asset Data_AssetStatus


### OH_Data_Asset_CreateOne()

```c
Data_Asset *OH_Data_Asset_CreateOne(void)
```

**Description**

Creates an [Data_Asset](capi-rdb-data-asset.md) instance.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 11

**Returns**:

| Type | Description |
| -- | -- |
| [Data_Asset *](capi-rdb-data-asset.md) | If the creation is successful, a pointer to the instance of the @link Data_Asset} structure is returned,  otherwise NULL is returned. |

**Reference**:

Data_Asset


### OH_Data_Asset_DestroyOne()

```c
int OH_Data_Asset_DestroyOne(Data_Asset *asset)
```

**Description**

Destroy the [Data_Asset](capi-rdb-data-asset.md) object and reclaim the memory occupied by the object.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Data_Asset](capi-rdb-data-asset.md) *asset | Represents a pointer to an [Data_Asset](capi-rdb-data-asset.md) instance. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. Successful execution returns RDB_OK,      <br>while failure returns a specific error code.      <br>{@link RDB_OK} - success.<br>    <br>Specific error codes can be referenced {@link OH_Rdb_ErrCode}. |

**Reference**:

Data_Asset, OH_Rdb_ErrCode


### OH_Data_Asset_CreateMultiple()

```c
Data_Asset **OH_Data_Asset_CreateMultiple(uint32_t count)
```

**Description**

Creates [Data_Asset](capi-rdb-data-asset.md) instances of given number.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint32_t count | Represents the count of [Data_Asset](capi-rdb-data-asset.md) to create. |

**Returns**:

| Type | Description |
| -- | -- |
| [Data_Asset **](capi-rdb-data-asset.md) | If the creation is successful, a pointer to the instance of the [Data_Asset](capi-rdb-data-asset.md) structure is returned.          If the creation is unsuccessful, NULL is returned. |

**Reference**:

Data_Asset


### OH_Data_Asset_DestroyMultiple()

```c
int OH_Data_Asset_DestroyMultiple(Data_Asset **assets, uint32_t count)
```

**Description**

Destroy the [Data_Asset](capi-rdb-data-asset.md) objects and reclaim the memory occupied by the objects.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Data_Asset](capi-rdb-data-asset.md) **assets | Represents a pointer to an [Data_Asset](capi-rdb-data-asset.md) instance. |
| uint32_t count | Represents the count of [Data_Asset](capi-rdb-data-asset.md) to destroy. |

**Returns**:

| Type | Description |
| -- | -- |
| int | Returns the status code of the execution. Successful execution returns RDB_OK,      <br>while failure returns a specific error code.      <br>{@link RDB_OK} - success.<br>    <br>Specific error codes can be referenced {@link OH_Rdb_ErrCode}. |

**Reference**:

Data_Asset, OH_Rdb_ErrCode



