# UsedRecordDetail (System API)

Represents the details of a single access record.

**Since:** 9

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { privacyManager } from '@kit.AbilityKit';
```

## accessDuration

```TypeScript
accessDuration: number
```

Access duration. Unit: milliseconds.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.

## count

```TypeScript
count?: number
```

Number of accesses. In accessRecords, it indicates the number of successful accesses; in rejectRecords, it indicates the number of failures or rejections.

Default value: 0.

**Type:** number

**Since:** 11

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.

## lockScreenStatus

```TypeScript
lockScreenStatus?: number
```

Lock screen status at the time of access.

- 1: Indicates permission usage in a non-lock-screen scenario.  
- 2: Indicates permission usage in a lock-screen scenario.

Default value: 1.

**Type:** number

**Since:** 11

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.

## status

```TypeScript
status: number
```

Access status. 0 indicates stopped usage, 1 indicates foreground usage, and 2 indicates background usage.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.

## timestamp

```TypeScript
timestamp: number
```

Access timestamp. Unit: milliseconds.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.

## usedType

```TypeScript
usedType?: PermissionUsedType
```

Sensitive permission access method.

Default value: NORMAL_TYPE.

**Type:** [PermissionUsedType](arkts-ability-privacymanager-permissionusedtype-e-sys.md)

**Since:** 12

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.
