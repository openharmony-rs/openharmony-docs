# PermissionUsedRequest (System API)

Represents the request for querying permission usage records.

**Since:** 9

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { privacyManager } from '@kit.AbilityKit';
```

## beginTime

```TypeScript
beginTime?: number
```

Start time of the query. Unit: milliseconds. Default value: **0**, indicating no limit on the start time.

**Type:** number

**Default:** 0

**Since:** 9

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.

## bundleName

```TypeScript
bundleName?: string
```

Bundle name of the target application.

Default value: queries all applications.

**Type:** string

**Since:** 9

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.

## deviceId

```TypeScript
deviceId?: string
```

ID of the device where the target application is located.

Default value: local device ID.

**Type:** string

**Since:** 9

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.

## endTime

```TypeScript
endTime?: number
```

End time of the query. It must not be earlier than beginTime; otherwise, error code 12100001 is returned. Unit: milliseconds. Default value: **0**, indicating no limit on the end time.

**Type:** number

**Default:** 0

**Since:** 9

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.

## flag

```TypeScript
flag: PermissionUsageFlag
```

Used to specify the query mode. When set to **FLAG_PERMISSION_USAGE_SUMMARY**, summary information is returned; when set to **FLAG_PERMISSION_USAGE_DETAIL**, detailed records are returned.

**Type:** [PermissionUsageFlag](arkts-ability-privacymanager-permissionusageflag-e-sys.md)

**Since:** 9

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.

## isRemote

```TypeScript
isRemote?: boolean
```

Used to specify whether to query remote devices. The value **false** means to query the permission usage records of the local device, and **true** means to query the records of remote devices.

Default value: **false**.

**Type:** boolean

**Default:** false

**Since:** 9

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.

## permissionNames

```TypeScript
permissionNames?: Array<Permissions>
```

Set of permissions to query. Default value: Empty string. Means querying usage records of all permissions.

**Type:** Array&lt;[Permissions](arkts-ability-permissions-t.md)&gt;

**Since:** 9

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.

## tokenId

```TypeScript
tokenId?: number
```

Identity identifier of the target application. It can be obtained through the [accessTokenId](arkts-ability-applicationinfo-i.md#accesstokenid) field of ApplicationInfo.

Default value: **0**, queries all applications.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.
