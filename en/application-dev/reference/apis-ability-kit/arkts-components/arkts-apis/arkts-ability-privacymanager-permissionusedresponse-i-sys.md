# PermissionUsedResponse (System API)

Represents the access records of all applications or devices.

**Since:** 9

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { privacyManager } from '@kit.AbilityKit';
```

## beginTime

```TypeScript
beginTime: number
```

Start time of the query. Unit: milliseconds.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.

## bundleRecords

```TypeScript
bundleRecords: Array<BundleUsedRecord>
```

Each element represents the permission access record under an application dimension. Developers can further traverse permissionRecords to obtain specific permission usage details.

**Type:** Array&lt;[BundleUsedRecord](arkts-ability-privacymanager-bundleusedrecord-i-sys.md)&gt;

**Since:** 9

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.

## endTime

```TypeScript
endTime: number
```

End time of the query. Unit: milliseconds.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.
