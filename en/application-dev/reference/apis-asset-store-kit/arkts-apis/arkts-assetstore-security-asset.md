# @ohos.security.asset(Asset Store Service)

This module provides the capabilities for life cycle management of sensitive user data (Asset) such as passwords and tokens, including adding, removing, updating, and querying.

**Since:** 11

**System capability:** SystemCapability.Security.Asset

## Modules to Import

```TypeScript
import { asset } from '@kit.AssetStoreKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [add](arkts-assetstore-asset-add-f.md) | Adds an asset. This API uses a promise to return the result. |
| [addSync](arkts-assetstore-asset-addsync-f.md) | Adds an asset. This API returns the result synchronously. |
| [batchAdd](arkts-assetstore-asset-batchadd-f.md) | Adds assets in batches based on an attributes array. To set [IS_PERSISTENT](arkts-assetstore-asset-tag-e.md#is_persistent), the application must have the ohos.permission.STORE_PERSISTENT_DATA permission. |
| [batchRemove](arkts-assetstore-asset-batchremove-f.md) | Removes assets in batches based on an alias list. |
| [batchUpdate](arkts-assetstore-asset-batchupdate-f.md) | Updates assets in batches based on an attributes array. |
| [postQuery](arkts-assetstore-asset-postquery-f.md) | Performs postprocessing for the asset query. This API is used when user authentication is required for the access to an asset. This API must be used with [asset.preQuery](arkts-assetstore-asset-prequery-f.md) together. This API uses a promise to return the result. |
| [postQuerySync](arkts-assetstore-asset-postquerysync-f.md) | Performs postprocessing for the asset query. This API is used when user authentication is required for the access to the asset. This API must be used with [asset.preQuerySync](arkts-assetstore-asset-prequerysync-f.md) together. This API returns the result synchronously. |
| [preQuery](arkts-assetstore-asset-prequery-f.md) | Performs preprocessing for the asset query. This API is used when user authentication is required for the access to the asset. After the user authentication is successful, call [asset.query](arkts-assetstore-asset-query-f.md) and [asset.postQuery](arkts-assetstore-asset-postquery-f.md). This API uses a promise to return the result. |
| [preQuerySync](arkts-assetstore-asset-prequerysync-f.md) | Performs preprocessing for the asset query. This API is used when user authentication is required for the access to the asset. After the user authentication is successful, call [asset.querySync](arkts-assetstore-asset-querysync-f.md) and [asset.postQuerySync](arkts-assetstore-asset-postquerysync-f.md). This API returns the result synchronously. |
| [query](arkts-assetstore-asset-query-f.md) | Queries one or more assets. If user authentication is required for the access to the asset, call [asset.preQuery](arkts-assetstore-asset-prequery-f.md) before this API and call [asset.postQuery](arkts-assetstore-asset-postquery-f.md) after this API. For details about the development procedure, see [Development Guidance](../../../security/AssetStoreKit/asset-js-query-auth.md). This API uses a promise to return the result. |
| [querySync](arkts-assetstore-asset-querysync-f.md) | Queries one or more assets. If user authentication is required for the access to the asset, call [asset.preQuerySync](arkts-assetstore-asset-prequerysync-f.md) before this API and call [asset.postQuerySync](arkts-assetstore-asset-postquerysync-f.md) after this API. For details about the development procedure, see [Development Guidance](../../../security/AssetStoreKit/asset-js-query-auth.md). This API returns the result synchronously. |
| [querySyncResult](arkts-assetstore-asset-querysyncresult-f.md) | Queries the result of the sync operation. This API uses a promise to return the result. |
| [remove](arkts-assetstore-asset-remove-f.md) | Removes one or more assets. This API uses a promise to return the result. |
| [removeSync](arkts-assetstore-asset-removesync-f.md) | Removes one or more assets. This API returns the result synchronously. |
| [update](arkts-assetstore-asset-update-f.md) | Updates an asset. This API uses a promise to return the result. |
| [updateSync](arkts-assetstore-asset-updatesync-f.md) | Updates an asset. This API returns the result synchronously. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [addAsUser](arkts-assetstore-asset-addasuser-f-sys.md) | Adds an asset in the specified user space. This API uses a promise to return the result. |
| [postQueryAsUser](arkts-assetstore-asset-postqueryasuser-f-sys.md) | Performs postprocessing for the asset query in the specified user space. This API is used when user authentication is required for the access to an asset. This API must be used with [asset.preQueryAsUser](arkts-assetstore-asset-prequeryasuser-f-sys.md) together. This API uses a promise to return the result. |
| [preQueryAsUser](arkts-assetstore-asset-prequeryasuser-f-sys.md) | Performs preprocessing for the asset query in the specified user space. This API is used when user authentication is required for the access to an asset. After the user authentication is successful, call [asset.queryAsUser](arkts-assetstore-asset-queryasuser-f-sys.md) and [asset.postQueryAsUser](arkts-assetstore-asset-postqueryasuser-f-sys.md). This API uses a promise to return the result. |
| [queryAsUser](arkts-assetstore-asset-queryasuser-f-sys.md) | Queries one or more assets in the specified user space. If user authentication is required for the access to the asset, call [asset.preQueryAsUser](arkts-assetstore-asset-prequeryasuser-f-sys.md) before this API and call [asset.postQueryAsUser](arkts-assetstore-asset-postqueryasuser-f-sys.md) after this API. For details about the development procedure, see [Development Guidance](../../../security/AssetStoreKit/asset-js-query-auth.md). This API uses a promise to return the result. |
| [removeAsUser](arkts-assetstore-asset-removeasuser-f-sys.md) | Removes one or more assets in the specified user space. This API uses a promise to return the result. |
| [updateAsUser](arkts-assetstore-asset-updateasuser-f-sys.md) | Updates an asset in the specified user space. This API uses a promise to return the result. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [BatchErrInfo](arkts-assetstore-asset-batcherrinfo-i.md) | Result object containing error information with a specific index, error code, and message for a single asset. |
| [BatchResult](arkts-assetstore-asset-batchresult-i.md) | Result object containing batch operation,including [batchAdd](arkts-assetstore-asset-batchadd-f.md) and [batchUpdate](arkts-assetstore-asset-batchupdate-f.md). |
| [SyncResult](arkts-assetstore-asset-syncresult-i.md) | Represents the sync result of an asset. |

### Enums

| Name | Description |
| --- | --- |
| [Accessibility](arkts-assetstore-asset-accessibility-e.md) | Enumerates the types of access control based on the lock screen status. |
| [AuthType](arkts-assetstore-asset-authtype-e.md) | Enumerates the types of user authentication supported by an asset. |
| [ConflictResolution](arkts-assetstore-asset-conflictresolution-e.md) | Enumerates the policies for resolving conflicts (for example, a duplicate alias) when an asset is added. |
| [ErrorCode](arkts-assetstore-asset-errorcode-e.md) | Enumerates the error codes. |
| [OperationType](arkts-assetstore-asset-operationtype-e.md) | Enumerates the types of additional operation to perform. |
| [ReturnType](arkts-assetstore-asset-returntype-e.md) | Enumerates the type of information returned by an asset query operation. |
| [SyncType](arkts-assetstore-asset-synctype-e.md) | Enumerates the sync types supported by an asset. |
| [Tag](arkts-assetstore-asset-tag-e.md) | Enumerate the keys of asset attributes ([AssetMap](arkts-assetstore-asset-assetmap-t.md)), which are in key-value (KV) pairs. |
| [TagType](arkts-assetstore-asset-tagtype-e.md) | Enumerates the asset attribute types. |
| [WrapType](arkts-assetstore-asset-wraptype-e.md) | Enumerates the encrypted import/export types supported by the asset. |

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [AuthType](arkts-assetstore-asset-authtype-e-sys.md) | Enumerates the types of user authentication supported by an asset. |
<!--DelEnd-->

### Types

| Name | Description |
| --- | --- |
| [AssetMap](arkts-assetstore-asset-assetmap-t.md) | Represents a set of asset attributes in the form of KV pairs. |
| [Value](arkts-assetstore-asset-value-t.md) | Represents the value of each attribute in [AssetMap](arkts-assetstore-asset-assetmap-t.md). |
