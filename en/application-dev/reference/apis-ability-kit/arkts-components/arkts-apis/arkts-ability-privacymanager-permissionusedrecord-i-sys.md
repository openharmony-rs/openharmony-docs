# PermissionUsedRecord (System API)

Represents the access records of a permission.

**Since:** 9

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { privacyManager } from '@kit.AbilityKit';
```

## accessCount

```TypeScript
accessCount: number
```

Total number of accesses for this permission, indicating the cumulative number of successful uses of this permission within the query time window.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.

## accessRecords

```TypeScript
accessRecords: Array<UsedRecordDetail>
```

Access record collection, effective only when flag is FLAG_PERMISSION_USAGE_DETAIL.

Default value: Query the last 10 successful access records.

**Type:** Array&lt;[UsedRecordDetail](arkts-ability-privacymanager-usedrecorddetail-i-sys.md)&gt;

**Since:** 9

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.

## enhancedIdentity

```TypeScript
enhancedIdentity?: string
```

Extension identity, with a maximum length of 48 characters.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.

## lastAccessDuration

```TypeScript
lastAccessDuration: number
```

Last access duration. Unit: milliseconds.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.

## lastAccessTime

```TypeScript
lastAccessTime: number
```

Last time when the permission was accessed. Unit: milliseconds.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.

## lastRejectTime

```TypeScript
lastRejectTime: number
```

Last time when the access to the permission was rejected. Unit: milliseconds.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.

## permissionName

```TypeScript
permissionName: Permissions
```

Permission name, used to identify the sensitive permission corresponding to the current statistical record.

**Type:** [Permissions](arkts-ability-permissions-t.md)

**Since:** 9

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.

## rejectCount

```TypeScript
rejectCount: number
```

Total number of rejections for this permission, indicating the cumulative number of failed or denied permission accesses within the query time window.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.

## rejectRecords

```TypeScript
rejectRecords: Array<UsedRecordDetail>
```

Rejection record collection, effective only when flag is FLAG_PERMISSION_USAGE_DETAIL.

Default value: Query the last 10 failed or rejected records.

**Type:** Array&lt;[UsedRecordDetail](arkts-ability-privacymanager-usedrecorddetail-i-sys.md)&gt;

**Since:** 9

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.
