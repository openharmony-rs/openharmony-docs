# asset_type.h

<!--Kit: Asset Store Kit-->
<!--Subsystem: Security-->
<!--Owner: @HarMonkey-->
<!--Designer: @wkr321_ent-->
<!--Tester: @nacyli-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=c780ec602b8a429e3e53fe261f8afc5ed18a2559 translatedAt=2026-11-06T11:51:30.785Z pushedAt=2026-11-09T11:55:58.792Z nl=1 -->

## Overview

Defines the enums, structs, and error codes used in the asset store service.

**File to include**: <asset/asset_type.h>

**Library**: libasset_ndk.z.so

**System capability**: SystemCapability.Security.Asset

**Since**: 11

**Related module**: [AssetType](capi-assettype.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [Asset_Blob](capi-assettype-asset-blob.md) | Asset_Blob | Defines a binary array, that is, an array of bytes with variable length.|
| [Asset_Value](capi-assettype-asset-value.md) | Asset_Value | The value (content) of a key asset attribute. |
| [Asset_Attr](capi-assettype-asset-attr.md) | Asset_Attr | Critical asset attribute, which consists of tags and values in the form of key-value pairs. |
| [Asset_Result](capi-assettype-asset-result.md) | Asset_Result | Query result of a single critical asset. |
| [Asset_ResultSet](capi-assettype-asset-resultset.md) | Asset_ResultSet | Query result of multiple critical assets. |
| [Asset_SyncResult](capi-assettype-asset-syncresult.md) | Asset_SyncResult | Represents the sync result of an asset.|

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [Asset_TagType](#asset_tagtype) | Asset_TagType | Type of the critical asset attribute tag. |
| [Asset_Tag](#asset_tag) | Asset_Tag | Tag of the critical asset attribute. |
| [Asset_ResultCode](#asset_resultcode) | Asset_ResultCode | Result code used by the ASSET API. |
| [Asset_Accessibility](#asset_accessibility) | Asset_Accessibility | Enumerates the types of the access control based on the lock screen status.|
| [Asset_AuthType](#asset_authtype) | Asset_AuthType | Enumerates the user authentication types supported by assets.|
| [Asset_SyncType](#asset_synctype) | Asset_SyncType | Enumerates the asset sync types.|
| [Asset_WrapType](#asset_wraptype) | Asset_WrapType | Encrypted import/export type supported by the asset.|
| [Asset_ConflictResolution](#asset_conflictresolution) | Asset_ConflictResolution | Enumerates the policies for resolving the conflict (for example, a duplicate alias).|
| [Asset_ReturnType](#asset_returntype) | Asset_ReturnType | Enumerates the types of the asset query result to return.|
| [Asset_OperationType](#asset_operationtype) | Asset_OperationType | Enumerates the additional asset operation types.|

### Macros

| Name| Description|
| -- | -- |
| ASSET_TAG_TYPE_MASK (0xF << 28) | Defines the mask used to obtain the key type of an asset attribute.<br>**Since**: 11|

## Enum Description

### Asset_TagType

```c
enum Asset_TagType
```

**Description**

Type of the critical asset attribute tag.

**Since**: 11

| Enum| Description|
| -- | -- |
| ASSET_TYPE_BOOL = 0x1 << 28 | Indicates that the type of the critical asset attribute is bool. |
| ASSET_TYPE_NUMBER = 0x2 << 28 | Indicates that the type of the critical asset attribute is uint32_t. |
| ASSET_TYPE_BYTES = 0x3 << 28 | Indicates that the type of the critical asset attribute is a byte array. |

### Asset_Tag

```c
enum Asset_Tag
```

**Description**

Tag of the critical asset attribute.

**Since**: 11

| Enum| Description|
| -- | -- |
| ASSET_TAG_SECRET = ASSET_TYPE_BYTES \| 0x01 | Sensitive user data in the form of bytes, such as passwords and tokens.|
| ASSET_TAG_ALIAS = ASSET_TYPE_BYTES \| 0x02 | Asset alias (identifier) in the form of bytes.|
| ASSET_TAG_ACCESSIBILITY = ASSET_TYPE_NUMBER \| 0x03 | Access control based on the lock screen status. The value is of the uint32_t type.|
| ASSET_TAG_REQUIRE_PASSWORD_SET = ASSET_TYPE_BOOL \| 0x04 | Indicates whether the critical asset is available when the device has a lock screen password set. The value is of the bool type. true indicates that the asset is accessible only when a lock screen password is set, and false indicates that it is not restricted by the lock screen password. |
| ASSET_TAG_AUTH_TYPE = ASSET_TYPE_NUMBER \| 0x05 | User authentication type for the asset. The value is of the uint32_t type.|
| ASSET_TAG_AUTH_VALIDITY_PERIOD = ASSET_TYPE_NUMBER \| 0x06 | Validity period of the user authentication, in seconds. The value is of the uint32_t type, in seconds.|
| ASSET_TAG_AUTH_CHALLENGE = ASSET_TYPE_BYTES \| 0x07 | Challenge value, in the form of bytes, used for anti-replay during the authentication.|
| ASSET_TAG_AUTH_TOKEN = ASSET_TYPE_BYTES \| 0x08 | Authentication token, in the form of bytes, obtained after a successful user authentication.|
| ASSET_TAG_SYNC_TYPE = ASSET_TYPE_NUMBER \| 0x10 | Asset sync type. The value is of the uint32_t type.|
| ASSET_TAG_IS_PERSISTENT = ASSET_TYPE_BOOL \| 0x11 | Indicates whether the critical asset needs to be stored persistently. The value is of the bool type. true indicates that the critical asset is retained when the application is uninstalled, and false indicates that the critical asset is not retained. When this attribute is passed in calling the OH_Asset_Add function, the permission ohos.permission.STORE_PERSISTENT_DATA needs to be verified. For details about how to request the permission, see [Declaring Permissions](../../security/AccessToken/declare-permissions.md). |
| ASSET_TAG_DATA_LABEL_CRITICAL_1 = ASSET_TYPE_BYTES \| 0x20 | Custom data, which is of the bytes type and cannot be changed.|
| ASSET_TAG_DATA_LABEL_CRITICAL_2 = ASSET_TYPE_BYTES \| 0x21 | Custom data, which is of the bytes type and cannot be changed.|
| ASSET_TAG_DATA_LABEL_CRITICAL_3 = ASSET_TYPE_BYTES \| 0x22 | Custom data, which is of the bytes type and cannot be changed.|
| ASSET_TAG_DATA_LABEL_CRITICAL_4 = ASSET_TYPE_BYTES \| 0x23 | Custom data, which is of the bytes type and cannot be changed.|
| ASSET_TAG_DATA_LABEL_NORMAL_1 = ASSET_TYPE_BYTES \| 0x30 | Custom data, which is of the bytes type and can be changed.|
| ASSET_TAG_DATA_LABEL_NORMAL_2 = ASSET_TYPE_BYTES \| 0x31 | Custom data, which is of the bytes type and can be changed.|
| ASSET_TAG_DATA_LABEL_NORMAL_3 = ASSET_TYPE_BYTES \| 0x32 | Custom data, which is of the bytes type and can be changed.|
| ASSET_TAG_DATA_LABEL_NORMAL_4 = ASSET_TYPE_BYTES \| 0x33 | Custom data, which is of the bytes type and can be changed.|
| ASSET_TAG_DATA_LABEL_NORMAL_LOCAL_1 = ASSET_TYPE_BYTES \| 0x34 | Custom data, which is of the bytes type, can be changed, but cannot be synced.<br>**Since**: 12|
| ASSET_TAG_DATA_LABEL_NORMAL_LOCAL_2 = ASSET_TYPE_BYTES \| 0x35 | Custom data, which is of the bytes type, can be changed, but cannot be synced.<br>**Since**: 12|
| ASSET_TAG_DATA_LABEL_NORMAL_LOCAL_3 = ASSET_TYPE_BYTES \| 0x36 | Custom data, which is of the bytes type, can be changed, but cannot be synced.<br>**Since**: 12|
| ASSET_TAG_DATA_LABEL_NORMAL_LOCAL_4 = ASSET_TYPE_BYTES \| 0x37 | Custom data, which is of the bytes type, can be changed, but cannot be synced.<br>**Since**: 12|
| ASSET_TAG_RETURN_TYPE = ASSET_TYPE_NUMBER \| 0x40 | Type of asset information to return. The value is of the uint32_t type.|
| ASSET_TAG_RETURN_LIMIT = ASSET_TYPE_NUMBER \| 0x41 | Maximum number of assets that can be returned in a query operation. The value is of the uint32_t type.|
| ASSET_TAG_RETURN_OFFSET = ASSET_TYPE_NUMBER \| 0x42 | Offset of the returned assets in a batch query. The value is of the uint32_t type.|
| ASSET_TAG_RETURN_ORDERED_BY = ASSET_TYPE_NUMBER \| 0x43 | Sorting order of the assets in the query result. The value is of the uint32_t type.|
| ASSET_TAG_CONFLICT_RESOLUTION = ASSET_TYPE_NUMBER \| 0x44 | Policy for resolving the conflict when an asset is added. The value is of the uint32_t type.|
| ASSET_TAG_UPDATE_TIME = ASSET_TYPE_BYTES \| 0x45 | Asset update time, in timestamp format. The value is of the bytes type.<br>**Since**: 12|
| ASSET_TAG_OPERATION_TYPE = ASSET_TYPE_NUMBER \| 0x46 | Additional operation type. The value is of the uint32_t type.<br>**Since**: 12|
| ASSET_TAG_REQUIRE_ATTR_ENCRYPTED = ASSET_TYPE_BOOL \| 0x47 | Indicates whether to encrypt the service-defined auxiliary information. The value is of the bool type. true indicates that the service-defined auxiliary information is encrypted, and false indicates that it is not encrypted.<br>**Since:** 14 |
| ASSET_TAG_GROUP_ID = ASSET_TYPE_BYTES \| 0x48 | Group to which the asset belongs. The value is of the bytes type.<br>**Since**: 18|
| ASSET_TAG_WRAP_TYPE = ASSET_TYPE_NUMBER \| 0x49 | Encrypted import/export type supported by the asset. The value is of the uint32_t type.<br>**Since**: 18|

### Asset_ResultCode

```c
enum Asset_ResultCode
```

**Description**

Result code used by the ASSET API.

**Since**: 11

| Enum| Description|
| -- | -- |
| ASSET_SUCCESS = 0 | The operation is successful.|
| ASSET_PERMISSION_DENIED = 201 | Indicates that permission verification fails. The application does not have the permission to use this API and needs to apply for the permission. |
| ASSET_INVALID_ARGUMENT = 401 | Indicates invalid parameters. Possible causes: 1. A mandatory parameter is not specified. 2. The parameter type is incorrect. 3. Parameter verification fails. |
| ASSET_SERVICE_UNAVAILABLE = 24000001 | The asset store service is unavailable.|
| ASSET_NOT_FOUND = 24000002 | The asset is not found.|
| ASSET_DUPLICATED = 24000003 | The asset already exists.|
| ASSET_ACCESS_DENIED = 24000004 | The access to the asset is denied.|
| ASSET_STATUS_MISMATCH = 24000005 | The lock screen status does not match.|
| ASSET_OUT_OF_MEMORY = 24000006 | The system memory is insufficient.|
| ASSET_DATA_CORRUPTED = 24000007 | The asset is corrupted.|
| ASSET_DATABASE_ERROR = 24000008 | The database operation failed.|
| ASSET_CRYPTO_ERROR = 24000009 | The cryptographic operation failed.|
| ASSET_IPC_ERROR = 24000010 | The IPC failed.|
| ASSET_BMS_ERROR = 24000011 | The Bundle Manager service is abnormal.|
| ASSET_ACCOUNT_ERROR = 24000012 | The Account service is abnormal.|
| ASSET_ACCESS_TOKEN_ERROR = 24000013 | The Access Token service is abnormal.|
| ASSET_FILE_OPERATION_ERROR = 24000014 | The file operation failed.|
| ASSET_GET_SYSTEM_TIME_ERROR = 24000015 | Failed to obtain the system time.|
| ASSET_LIMIT_EXCEEDED = 24000016 | The number of cached assets exceeds the limit.|
| ASSET_UNSUPPORTED = 24000017 | The function is not supported.|
| ASSET_PARAM_VERIFICATION_FAILED = 24000018 | The parameter verification fails.<br>**Since**: 20|

### Asset_Accessibility

```c
enum Asset_Accessibility
```

**Description**

Enumerates the types of the access control based on the lock screen status.

**Since**: 11

| Enum| Description|
| -- | -- |
| ASSET_ACCESSIBILITY_DEVICE_POWERED_ON = 0 | The asset can be accessed after the device is powered on.|
| ASSET_ACCESSIBILITY_DEVICE_FIRST_UNLOCKED = 1 | The asset can be accessed only after the device is unlocked for the first time.|
| ASSET_ACCESSIBILITY_DEVICE_UNLOCKED = 2 | The asset can be accessed only after the device is unlocked.|

### Asset_AuthType

```c
enum Asset_AuthType
```

**Description**

Enumerates the user authentication types supported by assets.

**Since**: 11

| Enum| Description|
| -- | -- |
| ASSET_AUTH_TYPE_NONE = 0x00 | No user authentication is required before the asset is accessed.|
| ASSET_AUTH_TYPE_ANY = 0xFF | The asset can be accessed if any user authentication (such as PIN, facial, or fingerprint authentication) is successful.|

### Asset_SyncType

```c
enum Asset_SyncType
```

**Description**

Asset sync type.

**Since**: 11

| Enum| Description|
| -- | -- |
| ASSET_SYNC_TYPE_NEVER = 0 | Asset sync is not allowed.|
| ASSET_SYNC_TYPE_THIS_DEVICE = 1 << 0 | Asset sync is allowed only on the local device, for example, in data restore on the local device.|
| ASSET_SYNC_TYPE_TRUSTED_DEVICE = 1 << 1 | Asset sync is allowed only between trusted devices, for example, in the case of cloning.|
| ASSET_SYNC_TYPE_TRUSTED_ACCOUNT = 1 << 2 | Asset sync is allowed only between the devices that are logged in with trusted accounts, for example, in cloud sync scenarios.<br>**Since**: 12|

### Asset_WrapType

```c
enum Asset_WrapType
```

**Description**

Encrypted import/export type supported by the asset.

**Since**: 18

| Enum| Description|
| -- | -- |
| ASSET_WRAP_TYPE_NEVER = 0 | Encrypted import/export is not allowed for the asset.|
| ASSET_WRAP_TYPE_TRUSTED_ACCOUNT = 1 | Encrypted import/export is allowed for the asset only on devices where a trusted account is logged in.|

### Asset_ConflictResolution

```c
enum Asset_ConflictResolution
```

**Description**

Policy for resolving the conflict (for example, a duplicate alias).

**Since**: 11

| Enum| Description|
| -- | -- |
| ASSET_CONFLICT_OVERWRITE = 0 | Overwrite the original asset.|
| ASSET_CONFLICT_THROW_ERROR = 1 | Throw an exception for the service to perform subsequent processing.|

### Asset_ReturnType

```c
enum Asset_ReturnType
```

**Description**

Type of the asset query result to return.

**Since**: 11

| Enum| Description|
| -- | -- |
| ASSET_RETURN_ALL = 0 | The query result contains the asset plaintext and its attributes.|
| ASSET_RETURN_ATTRIBUTES = 1 | The query result contains only the asset attributes.|

### Asset_OperationType

```c
enum Asset_OperationType
```

**Description**

Enumerates the additional asset operation types.

**Since**: 12

| Enum| Description|
| -- | -- |
| ASSET_NEED_SYNC = 0 | Sync.|
| ASSET_NEED_LOGOUT = 1 | Logout.|
