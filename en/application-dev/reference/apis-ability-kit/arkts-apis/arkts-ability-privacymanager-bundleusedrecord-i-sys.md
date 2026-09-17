# BundleUsedRecord (System API)

Represents the access records of an application or device.

**Since:** 9

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { privacyManager } from '@kit.AbilityKit';
```

## bundleName

```TypeScript
bundleName: string
```

Bundle name of the application using the permission. In local scenarios, it can be used to directly locate the target application; this field is invalid in distributed scenarios.

**Type:** string

**Since:** 9

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.

## deviceId

```TypeScript
deviceId: string
```

ID of the device where the application using the permission is located. Mainly used to identify the source of a remote device in distributed scenarios; this field can usually be ignored in local scenarios.

**Type:** string

**Since:** 9

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.

## deviceName

```TypeScript
deviceName?: string
```

Name of the device where the application using the permission is located, used only in distributed scenarios. It can be used to display a more understandable device identifier in the UI. Default value: Empty string.

**Type:** string

**Since:** 24

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.

## isRemote

```TypeScript
isRemote: boolean
```

Whether it is an access record in a distributed scenario. false indicates a local application record, and true indicates a permission usage record on a remote device.

**Type:** boolean

**Since:** 9

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.

## permissionRecords

```TypeScript
permissionRecords: Array<PermissionUsedRecord>
```

Collection of permission usage records under the current application or device. Each element corresponds to a specific permission, allowing further viewing of access count, rejection count, last access time, and detailed records.

**Type:** Array&lt;[PermissionUsedRecord](arkts-ability-privacymanager-permissionusedrecord-i-sys.md)&gt;

**Since:** 9

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.

## tokenId

```TypeScript
tokenId: number
```

Application identity identifier for using the permission. This field is invalid in distributed scenarios; the source device must be identified using deviceId and deviceName.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.
