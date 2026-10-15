# @ohos.fileshare

Provides fileshare APIS

@namespace fileShare

**Since:** 9

<!--Device-unnamed-declare namespace fileShare--><!--Device-unnamed-declare namespace fileShare-End-->

**System capability:** SystemCapability.FileManagement.AppFileService

## Modules to Import

```TypeScript
import { fileShare } from '@kit.CoreFileKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [activatePermission](arkts-corefile-fileshare-activatepermission-f.md#activatepermission) | Enable the URI that have been permanently authorized |
| [checkPersistentPermission](arkts-corefile-fileshare-checkpersistentpermission-f.md#checkpersistentpermission) | Check persistent permissions for the URI. |
| [deactivatePermission](arkts-corefile-fileshare-deactivatepermission-f.md#deactivatepermission) | Stop the authorized URI that has been enabled |
| [persistPermission](arkts-corefile-fileshare-persistpermission-f.md#persistpermission) | Set persistence permissions for the URI |
| [revokePermission](arkts-corefile-fileshare-revokepermission-f.md#revokepermission1) | Revoke persistence permissions for the URI |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [checkPathPermission](arkts-corefile-fileshare-checkpathpermission-f-sys.md#checkpathpermission) | Check permissions for the path. |
| [getPersistentPolicy](arkts-corefile-fileshare-getpersistentpolicy-f-sys.md#getpersistentpolicy) | Get all persistence permissions for the application. |
| [getSharedDirectoryInfo](arkts-corefile-fileshare-getshareddirectoryinfo-f-sys.md#getshareddirectoryinfo) | Gets the shared sandbox directories of applications |
| [grantSharedDirectoryPermission](arkts-corefile-fileshare-grantshareddirectorypermission-f-sys.md#grantshareddirectorypermission) | Provides a permission grant for application-shared directories |
| [grantUriPermission](arkts-corefile-fileshare-granturipermission-f-sys.md#granturipermission1) | Provides grant uri permission for app |
| [grantUriPermission](arkts-corefile-fileshare-granturipermission-f-sys.md#granturipermission2) | Provides grant uri permission for app |
| [grantUriPermission](arkts-corefile-fileshare-granturipermission-f-sys.md#granturipermission3) | Grant URI permissions for an application. |
| [revokePermission](arkts-corefile-fileshare-revokepermission-f-sys.md#revokepermission2) | Revoke all persistence permissions for the application. |
| [revokePermission](arkts-corefile-fileshare-revokepermission-f-sys.md#revokepermission3) | Revoke persistence permissions for the URI. |
| [revokeSharedDirectoryPermission](arkts-corefile-fileshare-revokeshareddirectorypermission-f-sys.md#revokeshareddirectorypermission) | Revokes permission for application-shared directories |
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
