# Tag

Enumerate the keys of asset attributes ([AssetMap](arkts-assetstore-asset-assetmap-t.md)), which are in key-value (KV) pairs.

**Since:** 11

**System capability:** SystemCapability.Security.Asset

## SECRET

```TypeScript
SECRET = TagType.BYTES | 0x01
```

Asset plaintext.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Security.Asset

## ALIAS

```TypeScript
ALIAS = TagType.BYTES | 0x02
```

Asset alias, which uniquely identifies an asset.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Security.Asset

## ACCESSIBILITY

```TypeScript
ACCESSIBILITY = TagType.NUMBER | 0x03
```

Access control based on the lock screen status.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Security.Asset

## REQUIRE_PASSWORD_SET

```TypeScript
REQUIRE_PASSWORD_SET = TagType.BOOL | 0x04
```

Whether the asset is accessible only when a lock screen password is set.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Security.Asset

## AUTH_TYPE

```TypeScript
AUTH_TYPE = TagType.NUMBER | 0x05
```

Type of user authentication required for accessing the asset.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Security.Asset

## AUTH_VALIDITY_PERIOD

```TypeScript
AUTH_VALIDITY_PERIOD = TagType.NUMBER | 0x06
```

Validity period of the user authentication.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Security.Asset

## AUTH_CHALLENGE

```TypeScript
AUTH_CHALLENGE = TagType.BYTES | 0x07
```

Challenge for the user authentication.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Security.Asset

## AUTH_TOKEN

```TypeScript
AUTH_TOKEN = TagType.BYTES | 0x08
```

Authorization token obtained after the user authentication is successful.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Security.Asset

## SYNC_TYPE

```TypeScript
SYNC_TYPE = TagType.NUMBER | 0x10
```

Asset sync type.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Security.Asset

## IS_PERSISTENT

```TypeScript
IS_PERSISTENT = TagType.BOOL | 0x11
```

Whether to retain the asset when the application is uninstalled.

**Since:** 11

**System capability:** SystemCapability.Security.Asset

## DATA_LABEL_CRITICAL_1

```TypeScript
DATA_LABEL_CRITICAL_1 = TagType.BYTES | 0x20
```

Additional asset data customized by the service with integrity protection.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Security.Asset

## DATA_LABEL_CRITICAL_2

```TypeScript
DATA_LABEL_CRITICAL_2 = TagType.BYTES | 0x21
```

Additional asset data customized by the service with integrity protection.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Security.Asset

## DATA_LABEL_CRITICAL_3

```TypeScript
DATA_LABEL_CRITICAL_3 = TagType.BYTES | 0x22
```

Additional asset data customized by the service with integrity protection.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Security.Asset

## DATA_LABEL_CRITICAL_4

```TypeScript
DATA_LABEL_CRITICAL_4 = TagType.BYTES | 0x23
```

Additional asset data customized by the service with integrity protection.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Security.Asset

## DATA_LABEL_NORMAL_1

```TypeScript
DATA_LABEL_NORMAL_1 = TagType.BYTES | 0x30
```

Additional asset data customized by the service without integrity protection.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Security.Asset

## DATA_LABEL_NORMAL_2

```TypeScript
DATA_LABEL_NORMAL_2 = TagType.BYTES | 0x31
```

Additional asset data customized by the service without integrity protection.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Security.Asset

## DATA_LABEL_NORMAL_3

```TypeScript
DATA_LABEL_NORMAL_3 = TagType.BYTES | 0x32
```

Additional asset data customized by the service without integrity protection.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Security.Asset

## DATA_LABEL_NORMAL_4

```TypeScript
DATA_LABEL_NORMAL_4 = TagType.BYTES | 0x33
```

Additional asset data customized by the service without integrity protection.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Security.Asset

## DATA_LABEL_NORMAL_LOCAL_1

```TypeScript
DATA_LABEL_NORMAL_LOCAL_1 = TagType.BYTES | 0x34
```

Local information about the asset. The value is assigned by the service without integrity protection and will not be synced.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Security.Asset

## DATA_LABEL_NORMAL_LOCAL_2

```TypeScript
DATA_LABEL_NORMAL_LOCAL_2 = TagType.BYTES | 0x35
```

Local information about the asset. The value is assigned by the service without integrity protection and will not be synced.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Security.Asset

## DATA_LABEL_NORMAL_LOCAL_3

```TypeScript
DATA_LABEL_NORMAL_LOCAL_3 = TagType.BYTES | 0x36
```

Local information about the asset. The value is assigned by the service without integrity protection and will not be synced.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Security.Asset

## DATA_LABEL_NORMAL_LOCAL_4

```TypeScript
DATA_LABEL_NORMAL_LOCAL_4 = TagType.BYTES | 0x37
```

Local information about the asset. The value is assigned by the service without integrity protection and will not be synced.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Security.Asset

## RETURN_TYPE

```TypeScript
RETURN_TYPE = TagType.NUMBER | 0x40
```

Type of the asset query result to return.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Security.Asset

## RETURN_LIMIT

```TypeScript
RETURN_LIMIT = TagType.NUMBER | 0x41
```

Maximum number of asset records to return.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Security.Asset

## RETURN_OFFSET

```TypeScript
RETURN_OFFSET = TagType.NUMBER | 0x42
```

Offset of the asset query result.

**Note:**  This parameter specifies the starting asset record to return in batch asset query.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Security.Asset

## RETURN_ORDERED_BY

```TypeScript
RETURN_ORDERED_BY = TagType.NUMBER | 0x43
```

Sorting order of the query results. Currently, the results can be sorted only by **ASSET_TAG_DATA_LABEL**.

**Note:**  By default, assets are returned in the order in which they are added.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Security.Asset

## CONFLICT_RESOLUTION

```TypeScript
CONFLICT_RESOLUTION = TagType.NUMBER | 0x44
```

Policy for resolving the conflict (for example, a duplicate alias).

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Security.Asset

## UPDATE_TIME

```TypeScript
UPDATE_TIME = TagType.BYTES | 0x45
```

Data update time, in timestamp.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Security.Asset

## OPERATION_TYPE

```TypeScript
OPERATION_TYPE = TagType.NUMBER | 0x46
```

Additional operation type.

**Since:** 12

**System capability:** SystemCapability.Security.Asset

## REQUIRE_ATTR_ENCRYPTED

```TypeScript
REQUIRE_ATTR_ENCRYPTED = TagType.BOOL | 0x47
```

Whether to encrypt the additional asset information customized by the service.

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Security.Asset

## GROUP_ID

```TypeScript
GROUP_ID = TagType.BYTES | 0x48
```

Group to which the asset belongs.

**Since:** 18

**System capability:** SystemCapability.Security.Asset

## WRAP_TYPE

```TypeScript
WRAP_TYPE = TagType.NUMBER | 0x49
```

Encrypted import/export type supported by the asset.

**Since:** 18

**System capability:** SystemCapability.Security.Asset
