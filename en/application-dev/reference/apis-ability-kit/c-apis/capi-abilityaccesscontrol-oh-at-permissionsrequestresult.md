# OH_AT_PermissionsRequestResult

```c
typedef struct OH_AT_PermissionsRequestResult {...} OH_AT_PermissionsRequestResult
```

## Overview

Permission request result.

<!--Device-struct OH_AT_PermissionsRequestResult {...}--><!--Device-struct OH_AT_PermissionsRequestResult {...}-End-->

**System capability**: SystemCapability.Security.AccessToken

**Since**: 26.1.0

**Related module**: [AbilityAccessControl](capi-ability-kit-abilityaccesscontrol.md)

**Header file**: [ability_access_control.h](capi-ability-access-control-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [OH_AT_AbilityAccessControlErrorCode](capi-ability-access-control-h.md#oh_at_abilityaccesscontrolerrorcode) errorCode | Request error code. For details, see [OH_AT_AbilityAccessControlErrorCode](capi-ability-access-control-h.md#oh_at_abilityaccesscontrolerrorcode).<br>**Since**: 26.1.0 |
| const char **permissions | Permission array of the current request.<br>**Since**: 26.1.0 |
| int32_t permCount | Number of permissions requested to be granted.<br>**Since**: 26.1.0 |
| [OH_AT_PermissionOperResult](capi-ability-access-control-h.md#oh_at_permissionoperresult) *operResults | The operation result of each permission corresponds to the permission.<br>**Since**: 26.1.0 |
| bool *dialogShownResults | Indicates whether the authorization pop-up window is displayed for each permission during this application. true indicates that the authorization pop-up window is displayed, and false indicates that the authorization pop-up window is not displayed.<br>**Since**: 26.1.0 |


