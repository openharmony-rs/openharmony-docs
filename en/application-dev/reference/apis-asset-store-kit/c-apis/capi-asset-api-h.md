# asset_api.h

## Overview

Declares the APIs for accessing assets.

**Library**: libasset_ndk.z.so

**System capability**: SystemCapability.Security.Asset

**Since**: 11

**Related module**: [AssetApi](capi-assetapi.md)

## Summary

### Function

| Name | Description |
| -- | -- |
| [int32_t OH_Asset_Add(const Asset_Attr *attributes, uint32_t attrCnt)](#oh_asset_add) | Adds an asset. Permission ohos.permission.STORE_PERSISTENT_DATA is required when the Asset needs to be stored persistently by setting {@link ASSET_TAG_IS_PERSISTENT} tag. |
| [int32_t OH_Asset_Remove(const Asset_Attr *query, uint32_t queryCnt)](#oh_asset_remove) | Removes one or more assets. |
| [int32_t OH_Asset_Update(const Asset_Attr *query, uint32_t queryCnt, const Asset_Attr *attributesToUpdate, uint32_t updateCnt)](#oh_asset_update) | Updates an asset. |
| [int32_t OH_Asset_PreQuery(const Asset_Attr *query, uint32_t queryCnt, Asset_Blob *challenge)](#oh_asset_prequery) | Performs preprocessing for the asset query. This API is used when user authentication is required for the access to the asset. |
| [int32_t OH_Asset_Query(const Asset_Attr *query, uint32_t queryCnt, Asset_ResultSet *resultSet)](#oh_asset_query) | Queries one or more assets. |
| [int32_t OH_Asset_PostQuery(const Asset_Attr *handle, uint32_t handleCnt)](#oh_asset_postquery) | Performs postprocessing for the asset query. This API is used when user authentication is required for the access to the asset. |
| [int32_t OH_Asset_QuerySyncResult(const Asset_Attr *query, uint32_t queryCnt, Asset_SyncResult *syncResult)](#oh_asset_querysyncresult) | Queries the sync result of an asset. |
| [Asset_Attr *OH_Asset_ParseAttr(const Asset_Result *result, Asset_Tag tag)](#oh_asset_parseattr) | Parses the query result and obtains the specified attribute. |
| [void OH_Asset_FreeBlob(Asset_Blob *blob)](#oh_asset_freeblob) | Releases the memory occupied by the challenge value. |
| [void OH_Asset_FreeResultSet(Asset_ResultSet *resultSet)](#oh_asset_freeresultset) | Releases the memory occupied by the query result. |

## Function description

### OH_Asset_Add()

```c
int32_t OH_Asset_Add(const Asset_Attr *attributes, uint32_t attrCnt)
```

**Description**

Adds an asset. Permission ohos.permission.STORE_PERSISTENT_DATA is required when the Asset needs to be stored persistently by setting {@link ASSET_TAG_IS_PERSISTENT} tag.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| const Asset_Attr *attributes | Attributes of the asset to add. |
| uint32_t attrCnt | Number of the attributes of the asset to add. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link ASSET_SUCCESS} 0 - The operation is successful.<br>    {@link ASSET_PERMISSION_DENIED} 201 - Permission verification failed.<br>        The application does not have the permission required to call the API.<br>    {@link ASSET_INVALID_ARGUMENT} 401 - Parameter error. Possible causes:<br>        1. Mandatory parameters are left unspecified.<br>        2. Incorrect parameter types.<br>        3. Parameter verification failed.<br>    {@link ASSET_SERVICE_UNAVAILABLE} 24000001 - The ASSET service is unavailable.<br>    {@link ASSET_DUPLICATED} 24000003 - The asset already exists.<br>    {@link ASSET_STATUS_MISMATCH} 24000005 - The screen lock status does not match.<br>    {@link ASSET_OUT_OF_MEMORY} 24000006 - Insufficient memory.<br>    {@link ASSET_DATA_CORRUPTED} 24000007 - The asset is corrupted.<br>    {@link ASSET_DATABASE_ERROR} 24000008 - The database operation failed.<br>    {@link ASSET_CRYPTO_ERROR} 24000009 - The cryptography operation failed.<br>    {@link ASSET_IPC_ERROR} 24000010 - IPC failed.<br>    {@link ASSET_BMS_ERROR} 24000011 - Calling the Bundle Manager service failed.<br>    {@link ASSET_ACCOUNT_ERROR} 24000012 - Calling the OS Account service failed.<br>    {@link ASSET_ACCESS_TOKEN_ERROR} 24000013 - Calling the Access Token service failed.<br>    {@link ASSET_FILE_OPERATION_ERROR} 24000014 - The file operation failed.<br>    {@link ASSET_GET_SYSTEM_TIME_ERROR} 24000015 - Getting the system time failed. |

### OH_Asset_Remove()

```c
int32_t OH_Asset_Remove(const Asset_Attr *query, uint32_t queryCnt)
```

**Description**

Removes one or more assets.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| const Asset_Attr *query | Attributes of the asset to remove. |
| uint32_t queryCnt | Number of attributes. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link ASSET_SUCCESS} 0 - The operation is successful.<br>    {@link ASSET_INVALID_ARGUMENT} 401 - Parameter error. Possible causes:<br>        1. Mandatory parameters are left unspecified.<br>        2. Incorrect parameter types.<br>        3. Parameter verification failed.<br>    {@link ASSET_SERVICE_UNAVAILABLE} 24000001 - The ASSET service is unavailable.<br>    {@link ASSET_NOT_FOUND} 24000002 - The asset is not found.<br>    {@link ASSET_OUT_OF_MEMORY} 24000006 - Insufficient memory.<br>    {@link ASSET_DATA_CORRUPTED} 24000007 - The asset is corrupted.<br>    {@link ASSET_DATABASE_ERROR} 24000008 - The database operation failed.<br>    {@link ASSET_IPC_ERROR} 24000010 - IPC failed.<br>    {@link ASSET_BMS_ERROR} 24000011 - Calling the Bundle Manager service failed.<br>    {@link ASSET_ACCOUNT_ERROR} 24000012 - Calling the OS Account service failed.<br>    {@link ASSET_ACCESS_TOKEN_ERROR} 24000013 - Calling the Access Token service failed.<br>    {@link ASSET_GET_SYSTEM_TIME_ERROR} 24000015 - Getting the system time failed. |

### OH_Asset_Update()

```c
int32_t OH_Asset_Update(const Asset_Attr *query, uint32_t queryCnt, const Asset_Attr *attributesToUpdate, uint32_t updateCnt)
```

**Description**

Updates an asset.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| const Asset_Attr *query | Attributes of the asset to update. |
| uint32_t queryCnt | Number of attributes to update. |
| const Asset_Attr *attributesToUpdate | Pointer to the attributes of the asset to update. |
| uint32_t updateCnt | Number of the attributes of the asset to update. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link ASSET_SUCCESS} 0 - The operation is successful.<br>    {@link ASSET_INVALID_ARGUMENT} 401 - Parameter error. Possible causes:<br>        1. Mandatory parameters are left unspecified.<br>        2. Incorrect parameter types.<br>        3. Parameter verification failed.<br>    {@link ASSET_SERVICE_UNAVAILABLE} 24000001 - The ASSET service is unavailable.<br>    {@link ASSET_NOT_FOUND} 24000002 - The asset is not found.<br>    {@link ASSET_STATUS_MISMATCH} 24000005 - The screen lock status does not match.<br>    {@link ASSET_OUT_OF_MEMORY} 24000006 - Insufficient memory.<br>    {@link ASSET_DATA_CORRUPTED} 24000007 - The asset is corrupted.<br>    {@link ASSET_DATABASE_ERROR} 24000008 - The database operation failed.<br>    {@link ASSET_CRYPTO_ERROR} 24000009 - The cryptography operation failed.<br>    {@link ASSET_IPC_ERROR} 24000010 - IPC failed.<br>    {@link ASSET_BMS_ERROR} 24000011 - Calling the Bundle Manager service failed.<br>    {@link ASSET_ACCOUNT_ERROR} 24000012 - Calling the OS Account service failed.<br>    {@link ASSET_ACCESS_TOKEN_ERROR} 24000013 - Calling the Access Token service failed.<br>    {@link ASSET_GET_SYSTEM_TIME_ERROR} 24000015 - Getting the system time failed. |

### OH_Asset_PreQuery()

```c
int32_t OH_Asset_PreQuery(const Asset_Attr *query, uint32_t queryCnt, Asset_Blob *challenge)
```

**Description**

Performs preprocessing for the asset query. This API is used when user authentication is required for the access to the asset.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| const Asset_Attr *query | Attributes of the asset to query. |
| uint32_t queryCnt | Number of attributes. |
| Asset_Blob *challenge | Challenge value, which is used when [OH_Asset_Query](capi-asset-api-h.md#oh_asset_query) is called. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link ASSET_SUCCESS} 0 - The operation is successful.<br>    {@link ASSET_INVALID_ARGUMENT} 401 - Parameter error. Possible causes:<br>        1. Mandatory parameters are left unspecified.<br>        2. Incorrect parameter types.<br>        3. Parameter verification failed.<br>    {@link ASSET_SERVICE_UNAVAILABLE} 24000001 - The ASSET service is unavailable.<br>    {@link ASSET_NOT_FOUND} 24000002 - The asset is not found.<br>    {@link ASSET_STATUS_MISMATCH} 24000005 - The screen lock status does not match.<br>    {@link ASSET_OUT_OF_MEMORY} 24000006 - Insufficient memory.<br>    {@link ASSET_DATA_CORRUPTED} 24000007 - The asset is corrupted.<br>    {@link ASSET_DATABASE_ERROR} 24000008 - The database operation failed.<br>    {@link ASSET_CRYPTO_ERROR} 24000009 - The cryptography operation failed.<br>    {@link ASSET_IPC_ERROR} 24000010 - IPC failed.<br>    {@link ASSET_BMS_ERROR} 24000011 - Calling the Bundle Manager service failed.<br>    {@link ASSET_ACCOUNT_ERROR} 24000012 - Calling the OS Account service failed.<br>    {@link ASSET_ACCESS_TOKEN_ERROR} 24000013 - Calling the Access Token service failed.<br>    {@link ASSET_LIMIT_EXCEEDED} 24000016 - The cache exceeds the limit.<br>    {@link ASSET_UNSUPPORTED} 24000017 - The capability is not supported. |

### OH_Asset_Query()

```c
int32_t OH_Asset_Query(const Asset_Attr *query, uint32_t queryCnt, Asset_ResultSet *resultSet)
```

**Description**

Queries one or more assets.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| const Asset_Attr *query | Attributes of the asset to query. |
| uint32_t queryCnt | Number of attributes. |
| Asset_ResultSet *resultSet | Array of query results. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link ASSET_SUCCESS} 0 - The operation is successful.<br>    {@link ASSET_INVALID_ARGUMENT} 401 - Parameter error. Possible causes:<br>        1. Mandatory parameters are left unspecified.<br>        2. Incorrect parameter types.<br>        3. Parameter verification failed.<br>    {@link ASSET_SERVICE_UNAVAILABLE} 24000001 - The ASSET service is unavailable.<br>    {@link ASSET_NOT_FOUND} 24000002 - The asset is not found.<br>    {@link ASSET_ACCESS_DENIED} 24000004 - Access to the asset is denied.<br>    {@link ASSET_STATUS_MISMATCH} 24000005 - The screen lock status does not match.<br>    {@link ASSET_OUT_OF_MEMORY} 24000006 - Insufficient memory.<br>    {@link ASSET_DATA_CORRUPTED} 24000007 - The asset is corrupted.<br>    {@link ASSET_DATABASE_ERROR} 24000008 - The database operation failed.<br>    {@link ASSET_CRYPTO_ERROR} 24000009 - The cryptography operation failed.<br>    {@link ASSET_IPC_ERROR} 24000010 - IPC failed.<br>    {@link ASSET_BMS_ERROR} 24000011 - Calling the Bundle Manager service failed.<br>    {@link ASSET_ACCOUNT_ERROR} 24000012 - Calling the OS Account service failed.<br>    {@link ASSET_ACCESS_TOKEN_ERROR} 24000013 - Calling the Access Token service failed.<br>    {@link ASSET_UNSUPPORTED} 24000017 - The capability is not supported. |

### OH_Asset_PostQuery()

```c
int32_t OH_Asset_PostQuery(const Asset_Attr *handle, uint32_t handleCnt)
```

**Description**

Performs postprocessing for the asset query. This API is used when user authentication is required for the access to the asset.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| const Asset_Attr *handle | Handle of the query operation, including the challenge value returned by [OH_Asset_PreQuery](capi-asset-api-h.md#oh_asset_prequery). |
| uint32_t handleCnt | Number of elements in the handle attribute set. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link ASSET_SUCCESS} 0 - The operation is successful.<br>    {@link ASSET_INVALID_ARGUMENT} 401 - Parameter error. Possible causes:<br>        1. Mandatory parameters are left unspecified.<br>        2. Incorrect parameter types.<br>        3. Parameter verification failed.<br>    {@link ASSET_SERVICE_UNAVAILABLE} 24000001 - The ASSET service is unavailable.<br>    {@link ASSET_OUT_OF_MEMORY} 24000006 - Insufficient memory.<br>    {@link ASSET_IPC_ERROR} 24000010 - IPC failed.<br>    {@link ASSET_BMS_ERROR} 24000011 - Calling the Bundle Manager service failed.<br>    {@link ASSET_ACCOUNT_ERROR} 24000012 - Calling the OS Account service failed.<br>    {@link ASSET_ACCESS_TOKEN_ERROR} 24000013 - Calling the Access Token service failed. |

### OH_Asset_QuerySyncResult()

```c
int32_t OH_Asset_QuerySyncResult(const Asset_Attr *query, uint32_t queryCnt, Asset_SyncResult *syncResult)
```

**Description**

Queries the sync result of an asset.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| const Asset_Attr *query | Attributes of the asset to query the sync result. |
| uint32_t queryCnt | Number of attributes. |
| Asset_SyncResult *syncResult | Sync result of the queried asset. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link ASSET_SUCCESS} 0 - The operation is successful.<br>    {@link ASSET_SERVICE_UNAVAILABLE} 24000001 - The ASSET service is unavailable.<br>    {@link ASSET_OUT_OF_MEMORY} 24000006 - Insufficient memory.<br>    {@link ASSET_IPC_ERROR} 24000010 - IPC failed.<br>    {@link ASSET_BMS_ERROR} 24000011 - Calling the Bundle Manager service failed.<br>    {@link ASSET_ACCOUNT_ERROR} 24000012 - Calling the OS Account service failed.<br>    {@link ASSET_ACCESS_TOKEN_ERROR} 24000013 - Calling the Access Token service failed.<br>    {@link ASSET_FILE_OPERATION_ERROR} 24000014 - The file operation failed.<br>    {@link ASSET_PARAM_VERIFICATION_FAILED} 24000018 - Parameter verification failed. |

### OH_Asset_ParseAttr()

```c
Asset_Attr *OH_Asset_ParseAttr(const Asset_Result *result, Asset_Tag tag)
```

**Description**

Parses the query result and obtains the specified attribute.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| const Asset_Result *result | Query result returned by [OH_Asset_Query](capi-asset-api-h.md#oh_asset_query). |
| Asset_Tag tag | Key of the attribute to obtain. |

**Returns**:

| Type | Description |
| -- | -- |
| Asset_Attr * | Returns <b>Asset_Attr</b> obtained if the operation is successful; returns <b>NULL</b> otherwise.      The attribute does not need to be released by the service. |

### OH_Asset_FreeBlob()

```c
void OH_Asset_FreeBlob(Asset_Blob *blob)
```

**Description**

Releases the memory occupied by the challenge value.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| Asset_Blob *blob | Challenge value returned by [OH_Asset_PreQuery](capi-asset-api-h.md#oh_asset_prequery). |

### OH_Asset_FreeResultSet()

```c
void OH_Asset_FreeResultSet(Asset_ResultSet *resultSet)
```

**Description**

Releases the memory occupied by the query result.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| Asset_ResultSet *resultSet | Query result returned by [OH_Asset_Query](capi-asset-api-h.md#oh_asset_query). |


