# PermissionUsingOptions (System API)

Represents the optional parameter set for using a permission.

**Since:** 26.0.0

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

Extension identity, used to identify additional identity information of the caller. This field is passed in when it is necessary to distinguish permission usage records from different call sources within the same application. The length must not exceed 48 characters. Passing an excessively long value when calling [startUsingPermission](arkts-ability-privacymanager-startusingpermission-f-sys.md) or [stopUsingPermission](arkts-ability-privacymanager-stopusingpermission-f-sys.md) will return error code 12100001.

Default value: empty string.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.
