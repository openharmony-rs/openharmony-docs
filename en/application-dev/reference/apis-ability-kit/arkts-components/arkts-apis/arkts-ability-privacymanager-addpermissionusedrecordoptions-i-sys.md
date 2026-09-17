# AddPermissionUsedRecordOptions (System API)

Represents the options for adding a permission usage record.

**Since:** 12

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { privacyManager } from '@kit.AbilityKit';
```

## enhancedIdentity

```TypeScript
enhancedIdentity?: string
```

Extension identity, used to identify additional identity information of the caller. This field is passed in when it is necessary to distinguish permission usage records from different call sources under the same application. The length does not exceed 48 characters. Passing an excessively long value when calling [addPermissionUsedRecord](arkts-ability-privacymanager-addpermissionusedrecord-f-sys.md) will return error code 12100001. The maximum length is 48. Default value: empty string.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.

## usedType

```TypeScript
usedType?: PermissionUsedType
```

Sensitive permission usage type.

Default value: NORMAL_TYPE.

**Type:** [PermissionUsedType](arkts-ability-privacymanager-permissionusedtype-e-sys.md)

**Since:** 12

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.
