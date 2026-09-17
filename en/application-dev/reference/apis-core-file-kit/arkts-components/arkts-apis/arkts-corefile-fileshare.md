# @ohos.fileshare

Provides fileshare APIS

@namespace fileShare

**Since:** 9

**System capability:** SystemCapability.FileManagement.AppFileService

## Modules to Import

```TypeScript
import { fileShare } from '@kit.CoreFileKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [activatePermission](arkts-corefile-fileshare-activatepermission-f.md) | Enable the URI that have been permanently authorized |
| [checkPersistentPermission](arkts-corefile-fileshare-checkpersistentpermission-f.md) | Check persistent permissions for the URI. |
| [deactivatePermission](arkts-corefile-fileshare-deactivatepermission-f.md) | Stop the authorized URI that has been enabled |
| [persistPermission](arkts-corefile-fileshare-persistpermission-f.md) | Set persistence permissions for the URI |
| [revokePermission](arkts-corefile-fileshare-revokepermission-f.md) | Revoke persistence permissions for the URI |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [checkPathPermission](arkts-corefile-fileshare-checkpathpermission-f-sys.md) | Check permissions for the path. |
| [getPersistentPolicy](arkts-corefile-fileshare-getpersistentpolicy-f-sys.md) | Get all persistence permissions for the application. |
| [getSharedDirectoryInfo](arkts-corefile-fileshare-getshareddirectoryinfo-f-sys.md) | Gets the shared sandbox directories of applications |
| [grantSharedDirectoryPermission](arkts-corefile-fileshare-grantshareddirectorypermission-f-sys.md) | Provides a permission grant for application-shared directories |
| [grantUriPermission](arkts-corefile-fileshare-granturipermission-f-sys.md) | Provides grant uri permission for app |
| [grantUriPermission](arkts-corefile-fileshare-granturipermission-f-sys.md) | Provides grant uri permission for app |
| [grantUriPermission](arkts-corefile-fileshare-granturipermission-f-sys.md) | Grant URI permissions for an application. |
| [revokePermission](arkts-corefile-fileshare-revokepermission-f-sys.md) | Revoke all persistence permissions for the application. |
| [revokePermission](arkts-corefile-fileshare-revokepermission-f-sys.md) | Revoke persistence permissions for the URI. |
| [revokeSharedDirectoryPermission](arkts-corefile-fileshare-revokeshareddirectorypermission-f-sys.md) | Revokes permission for application-shared directories |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [PathPolicyInfo](arkts-corefile-fileshare-pathpolicyinfo-i.md) | Policy information to manager permissions on a path. |
| [PolicyErrorResult](arkts-corefile-fileshare-policyerrorresult-i.md) | Failed policy result on URI. |
| [PolicyInfo](arkts-corefile-fileshare-policyinfo-i.md) | Policy information to manager permissions on a URI. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [SharedDirectoryInfo](arkts-corefile-fileshare-shareddirectoryinfo-i-sys.md) | The directory information shared with the system by the application. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [OperationMode](arkts-corefile-fileshare-operationmode-e.md) | Enumerates the uri operate mode types. |
| [PolicyErrorCode](arkts-corefile-fileshare-policyerrorcode-e.md) | Enumerates the error code of the permission policy for the URI operation. |
| [PolicyType](arkts-corefile-fileshare-policytype-e.md) | Indicates the policy type of the path. |
