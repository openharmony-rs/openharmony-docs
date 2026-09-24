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
| [int32_t OH_Asset_Add(const Asset_Attr *attributes, uint32_t attrCnt)](#oh_asset_add) | Adds an asset. Permission ohos.permission.STORE_PERSISTENT_DATA is required when the Asset needs to be stored persistently by setting [ASSET_TAG_IS_PERSISTENT](capi-asset-type-h.md#asset_tag) tag. |
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

Adds an asset. Permission ohos.permission.STORE_PERSISTENT_DATA is required when the Asset needs to be stored persistently by setting [ASSET_TAG_IS_PERSISTENT](capi-asset-type-h.md#asset_tag) tag.

**System capability**: SystemCapability.Security.Asset

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| const Asset_Attr *attributes | Attributes of the asset to add. |
| uint32_t attrCnt | Number of the attributes of the asset to add. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | [ASSET_SUCCESS](capi-asset-type-h.md#asset_resultcode) 0 - The operation is successful.      [ASSET_PERMISSION_DENIED](capi-asset-type-h.md#asset_resultcode) 201 - Permission verification failed.          The application does not have the permission required to call the API.      [ASSET_INVALID_ARGUMENT](capi-asset-type-h.md#asset_resultcode) 401 - Parameter error. Possible causes:          1. Mandatory parameters are left unspecified.          2. Incorrect parameter types.          3. Parameter verification failed.      [ASSET_SERVICE_UNAVAILABLE](capi-asset-type-h.md#asset_resultcode) 24000001 - The ASSET service is unavailable.      [ASSET_DUPLICATED](capi-asset-type-h.md#asset_resultcode) 24000003 - The asset already exists.      [ASSET_STATUS_MISMATCH](capi-asset-type-h.md#asset_resultcode) 24000005 - The screen lock status does not match.      [ASSET_OUT_OF_MEMORY](capi-asset-type-h.md#asset_resultcode) 24000006 - Insufficient memory.      [ASSET_DATA_CORRUPTED](capi-asset-type-h.md#asset_resultcode) 24000007 - The asset is corrupted.      [ASSET_DATABASE_ERROR](capi-asset-type-h.md#asset_resultcode) 24000008 - The database operation failed.      [ASSET_CRYPTO_ERROR](capi-asset-type-h.md#asset_resultcode) 24000009 - The cryptography operation failed.      [ASSET_IPC_ERROR](capi-asset-type-h.md#asset_resultcode) 24000010 - IPC failed.      [ASSET_BMS_ERROR](capi-asset-type-h.md#asset_resultcode) 24000011 - Calling the Bundle Manager service failed.      [ASSET_ACCOUNT_ERROR](capi-asset-type-h.md#asset_resultcode) 24000012 - Calling the OS Account service failed.      [ASSET_ACCESS_TOKEN_ERROR](capi-asset-type-h.md#asset_resultcode) 24000013 - Calling the Access Token service failed.      [ASSET_FILE_OPERATION_ERROR](capi-asset-type-h.md#asset_resultcode) 24000014 - The file operation failed.      [ASSET_GET_SYSTEM_TIME_ERROR](capi-asset-type-h.md#asset_resultcode) 24000015 - Getting the system time failed. |

### OH_Asset_Remove()

```c
int32_t OH_Asset_Remove(const Asset_Attr *query, uint32_t queryCnt)
```

**Description**

Removes one or more assets.

**System capability**: SystemCapability.Security.Asset

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| const Asset_Attr *query | Attributes of the asset to remove. |
| uint32_t queryCnt | Number of attributes. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | [ASSET_SUCCESS](capi-asset-type-h.md#asset_resultcode) 0 - The operation is successful.      [ASSET_INVALID_ARGUMENT](capi-asset-type-h.md#asset_resultcode) 401 - Parameter error. Possible causes:          1. Mandatory parameters are left unspecified.          2. Incorrect parameter types.          3. Parameter verification failed.      [ASSET_SERVICE_UNAVAILABLE](capi-asset-type-h.md#asset_resultcode) 24000001 - The ASSET service is unavailable.      [ASSET_NOT_FOUND](capi-asset-type-h.md#asset_resultcode) 24000002 - The asset is not found.      [ASSET_OUT_OF_MEMORY](capi-asset-type-h.md#asset_resultcode) 24000006 - Insufficient memory.      [ASSET_DATA_CORRUPTED](capi-asset-type-h.md#asset_resultcode) 24000007 - The asset is corrupted.      [ASSET_DATABASE_ERROR](capi-asset-type-h.md#asset_resultcode) 24000008 - The database operation failed.      [ASSET_IPC_ERROR](capi-asset-type-h.md#asset_resultcode) 24000010 - IPC failed.      [ASSET_BMS_ERROR](capi-asset-type-h.md#asset_resultcode) 24000011 - Calling the Bundle Manager service failed.      [ASSET_ACCOUNT_ERROR](capi-asset-type-h.md#asset_resultcode) 24000012 - Calling the OS Account service failed.      [ASSET_ACCESS_TOKEN_ERROR](capi-asset-type-h.md#asset_resultcode) 24000013 - Calling the Access Token service failed.      [ASSET_GET_SYSTEM_TIME_ERROR](capi-asset-type-h.md#asset_resultcode) 24000015 - Getting the system time failed. |

### OH_Asset_Update()

```c
int32_t OH_Asset_Update(const Asset_Attr *query, uint32_t queryCnt, const Asset_Attr *attributesToUpdate, uint32_t updateCnt)
```

**Description**

Updates an asset.

**System capability**: SystemCapability.Security.Asset

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
| int32_t | [ASSET_SUCCESS](capi-asset-type-h.md#asset_resultcode) 0 - The operation is successful.      [ASSET_INVALID_ARGUMENT](capi-asset-type-h.md#asset_resultcode) 401 - Parameter error. Possible causes:          1. Mandatory parameters are left unspecified.          2. Incorrect parameter types.          3. Parameter verification failed.      [ASSET_SERVICE_UNAVAILABLE](capi-asset-type-h.md#asset_resultcode) 24000001 - The ASSET service is unavailable.      [ASSET_NOT_FOUND](capi-asset-type-h.md#asset_resultcode) 24000002 - The asset is not found.      [ASSET_STATUS_MISMATCH](capi-asset-type-h.md#asset_resultcode) 24000005 - The screen lock status does not match.      [ASSET_OUT_OF_MEMORY](capi-asset-type-h.md#asset_resultcode) 24000006 - Insufficient memory.      [ASSET_DATA_CORRUPTED](capi-asset-type-h.md#asset_resultcode) 24000007 - The asset is corrupted.      [ASSET_DATABASE_ERROR](capi-asset-type-h.md#asset_resultcode) 24000008 - The database operation failed.      [ASSET_CRYPTO_ERROR](capi-asset-type-h.md#asset_resultcode) 24000009 - The cryptography operation failed.      [ASSET_IPC_ERROR](capi-asset-type-h.md#asset_resultcode) 24000010 - IPC failed.      [ASSET_BMS_ERROR](capi-asset-type-h.md#asset_resultcode) 24000011 - Calling the Bundle Manager service failed.      [ASSET_ACCOUNT_ERROR](capi-asset-type-h.md#asset_resultcode) 24000012 - Calling the OS Account service failed.      [ASSET_ACCESS_TOKEN_ERROR](capi-asset-type-h.md#asset_resultcode) 24000013 - Calling the Access Token service failed.      [ASSET_GET_SYSTEM_TIME_ERROR](capi-asset-type-h.md#asset_resultcode) 24000015 - Getting the system time failed. |

### OH_Asset_PreQuery()

```c
int32_t OH_Asset_PreQuery(const Asset_Attr *query, uint32_t queryCnt, Asset_Blob *challenge)
```

**Description**

Performs preprocessing for the asset query. This API is used when user authentication is required for the access to the asset.

**System capability**: SystemCapability.Security.Asset

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
| int32_t | [ASSET_SUCCESS](capi-asset-type-h.md#asset_resultcode) 0 - The operation is successful.      [ASSET_INVALID_ARGUMENT](capi-asset-type-h.md#asset_resultcode) 401 - Parameter error. Possible causes:          1. Mandatory parameters are left unspecified.          2. Incorrect parameter types.          3. Parameter verification failed.      [ASSET_SERVICE_UNAVAILABLE](capi-asset-type-h.md#asset_resultcode) 24000001 - The ASSET service is unavailable.      [ASSET_NOT_FOUND](capi-asset-type-h.md#asset_resultcode) 24000002 - The asset is not found.      [ASSET_STATUS_MISMATCH](capi-asset-type-h.md#asset_resultcode) 24000005 - The screen lock status does not match.      [ASSET_OUT_OF_MEMORY](capi-asset-type-h.md#asset_resultcode) 24000006 - Insufficient memory.      [ASSET_DATA_CORRUPTED](capi-asset-type-h.md#asset_resultcode) 24000007 - The asset is corrupted.      [ASSET_DATABASE_ERROR](capi-asset-type-h.md#asset_resultcode) 24000008 - The database operation failed.      [ASSET_CRYPTO_ERROR](capi-asset-type-h.md#asset_resultcode) 24000009 - The cryptography operation failed.      [ASSET_IPC_ERROR](capi-asset-type-h.md#asset_resultcode) 24000010 - IPC failed.      [ASSET_BMS_ERROR](capi-asset-type-h.md#asset_resultcode) 24000011 - Calling the Bundle Manager service failed.      [ASSET_ACCOUNT_ERROR](capi-asset-type-h.md#asset_resultcode) 24000012 - Calling the OS Account service failed.      [ASSET_ACCESS_TOKEN_ERROR](capi-asset-type-h.md#asset_resultcode) 24000013 - Calling the Access Token service failed.      [ASSET_LIMIT_EXCEEDED](capi-asset-type-h.md#asset_resultcode) 24000016 - The cache exceeds the limit.      [ASSET_UNSUPPORTED](capi-asset-type-h.md#asset_resultcode) 24000017 - The capability is not supported. |

### OH_Asset_Query()

```c
int32_t OH_Asset_Query(const Asset_Attr *query, uint32_t queryCnt, Asset_ResultSet *resultSet)
```

**Description**

Queries one or more assets.

**System capability**: SystemCapability.Security.Asset

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
| int32_t | [ASSET_SUCCESS](capi-asset-type-h.md#asset_resultcode) 0 - The operation is successful.      [ASSET_INVALID_ARGUMENT](capi-asset-type-h.md#asset_resultcode) 401 - Parameter error. Possible causes:          1. Mandatory parameters are left unspecified.          2. Incorrect parameter types.          3. Parameter verification failed.      [ASSET_SERVICE_UNAVAILABLE](capi-asset-type-h.md#asset_resultcode) 24000001 - The ASSET service is unavailable.      [ASSET_NOT_FOUND](capi-asset-type-h.md#asset_resultcode) 24000002 - The asset is not found.      [ASSET_ACCESS_DENIED](capi-asset-type-h.md#asset_resultcode) 24000004 - Access to the asset is denied.      [ASSET_STATUS_MISMATCH](capi-asset-type-h.md#asset_resultcode) 24000005 - The screen lock status does not match.      [ASSET_OUT_OF_MEMORY](capi-asset-type-h.md#asset_resultcode) 24000006 - Insufficient memory.      [ASSET_DATA_CORRUPTED](capi-asset-type-h.md#asset_resultcode) 24000007 - The asset is corrupted.      [ASSET_DATABASE_ERROR](capi-asset-type-h.md#asset_resultcode) 24000008 - The database operation failed.      [ASSET_CRYPTO_ERROR](capi-asset-type-h.md#asset_resultcode) 24000009 - The cryptography operation failed.      [ASSET_IPC_ERROR](capi-asset-type-h.md#asset_resultcode) 24000010 - IPC failed.      [ASSET_BMS_ERROR](capi-asset-type-h.md#asset_resultcode) 24000011 - Calling the Bundle Manager service failed.      [ASSET_ACCOUNT_ERROR](capi-asset-type-h.md#asset_resultcode) 24000012 - Calling the OS Account service failed.      [ASSET_ACCESS_TOKEN_ERROR](capi-asset-type-h.md#asset_resultcode) 24000013 - Calling the Access Token service failed.      [ASSET_UNSUPPORTED](capi-asset-type-h.md#asset_resultcode) 24000017 - The capability is not supported. |

### OH_Asset_PostQuery()

```c
int32_t OH_Asset_PostQuery(const Asset_Attr *handle, uint32_t handleCnt)
```

**Description**

Performs postprocessing for the asset query. This API is used when user authentication is required for the access to the asset.

**System capability**: SystemCapability.Security.Asset

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| const Asset_Attr *handle | Handle of the query operation, including the challenge value returned by [OH_Asset_PreQuery](capi-asset-api-h.md#oh_asset_prequery). |
| uint32_t handleCnt | Number of elements in the handle attribute set. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | [ASSET_SUCCESS](capi-asset-type-h.md#asset_resultcode) 0 - The operation is successful.      [ASSET_INVALID_ARGUMENT](capi-asset-type-h.md#asset_resultcode) 401 - Parameter error. Possible causes:          1. Mandatory parameters are left unspecified.          2. Incorrect parameter types.          3. Parameter verification failed.      [ASSET_SERVICE_UNAVAILABLE](capi-asset-type-h.md#asset_resultcode) 24000001 - The ASSET service is unavailable.      [ASSET_OUT_OF_MEMORY](capi-asset-type-h.md#asset_resultcode) 24000006 - Insufficient memory.      [ASSET_IPC_ERROR](capi-asset-type-h.md#asset_resultcode) 24000010 - IPC failed.      [ASSET_BMS_ERROR](capi-asset-type-h.md#asset_resultcode) 24000011 - Calling the Bundle Manager service failed.      [ASSET_ACCOUNT_ERROR](capi-asset-type-h.md#asset_resultcode) 24000012 - Calling the OS Account service failed.      [ASSET_ACCESS_TOKEN_ERROR](capi-asset-type-h.md#asset_resultcode) 24000013 - Calling the Access Token service failed. |

### OH_Asset_QuerySyncResult()

```c
int32_t OH_Asset_QuerySyncResult(const Asset_Attr *query, uint32_t queryCnt, Asset_SyncResult *syncResult)
```

**Description**

Queries the sync result of an asset.

**System capability**: SystemCapability.Security.Asset

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
| int32_t | [ASSET_SUCCESS](capi-asset-type-h.md#asset_resultcode) 0 - The operation is successful.      [ASSET_SERVICE_UNAVAILABLE](capi-asset-type-h.md#asset_resultcode) 24000001 - The ASSET service is unavailable.      [ASSET_OUT_OF_MEMORY](capi-asset-type-h.md#asset_resultcode) 24000006 - Insufficient memory.      [ASSET_IPC_ERROR](capi-asset-type-h.md#asset_resultcode) 24000010 - IPC failed.      [ASSET_BMS_ERROR](capi-asset-type-h.md#asset_resultcode) 24000011 - Calling the Bundle Manager service failed.      [ASSET_ACCOUNT_ERROR](capi-asset-type-h.md#asset_resultcode) 24000012 - Calling the OS Account service failed.      [ASSET_ACCESS_TOKEN_ERROR](capi-asset-type-h.md#asset_resultcode) 24000013 - Calling the Access Token service failed.      [ASSET_FILE_OPERATION_ERROR](capi-asset-type-h.md#asset_resultcode) 24000014 - The file operation failed.      [ASSET_PARAM_VERIFICATION_FAILED](capi-asset-type-h.md#asset_resultcode) 24000018 - Parameter verification failed. |

### OH_Asset_ParseAttr()

```c
Asset_Attr *OH_Asset_ParseAttr(const Asset_Result *result, Asset_Tag tag)
```

**Description**

Parses the query result and obtains the specified attribute.

**System capability**: SystemCapability.Security.Asset

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

**System capability**: SystemCapability.Security.Asset

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

**System capability**: SystemCapability.Security.Asset

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| Asset_ResultSet *resultSet | Query result returned by [OH_Asset_Query](capi-asset-api-h.md#oh_asset_query). |


