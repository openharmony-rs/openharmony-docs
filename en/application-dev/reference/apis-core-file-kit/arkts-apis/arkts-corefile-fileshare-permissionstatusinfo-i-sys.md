# PermissionStatusInfo (System API)

```TypeScript
export interface PermissionStatusInfo
```

Indicates the URI permission status information of the application.

**Since:** 26.1.0

<!--Device-fileShare-export interface PermissionStatusInfo--><!--Device-fileShare-export interface PermissionStatusInfo-End-->

**System capability:** SystemCapability.FileManagement.AppFileService.FolderAuthorization

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { fileShare } from '@kit.CoreFileKit';
```

## grantStatus

```TypeScript
grantStatus: GrantStatus
```

URI permission authorization status.

**Type:** [GrantStatus](arkts-corefile-fileshare-grantstatus-e.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-PermissionStatusInfo-grantStatus: GrantStatus--><!--Device-PermissionStatusInfo-grantStatus: GrantStatus-End-->

**System capability:** SystemCapability.FileManagement.AppFileService.FolderAuthorization

**System API:** This is a system API.

## policyInfo

```TypeScript
policyInfo: PolicyInfo
```

Policy information of the URI permission.

**Type:** [PolicyInfo](arkts-corefile-fileshare-policyinfo-i.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-PermissionStatusInfo-policyInfo: PolicyInfo--><!--Device-PermissionStatusInfo-policyInfo: PolicyInfo-End-->

**System capability:** SystemCapability.FileManagement.AppFileService.FolderAuthorization

**System API:** This is a system API.

## tokenID

```TypeScript
tokenID: number
```

Token ID of the application. The value should be an integer.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-PermissionStatusInfo-tokenID: int--><!--Device-PermissionStatusInfo-tokenID: int-End-->

**System capability:** SystemCapability.FileManagement.AppFileService.FolderAuthorization

**System API:** This is a system API.
