# @ohos.fileshare

Provides fileshare APIS

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
| [activatePermission](arkts-corefile-fileshare-activatepermission-f.md#activatepermission-1) | Enable the URI that have been permanently authorized |
| [checkPersistentPermission](arkts-corefile-fileshare-checkpersistentpermission-f.md#checkpersistentpermission-1) | Check persistent permissions for the URI. |
| [deactivatePermission](arkts-corefile-fileshare-deactivatepermission-f.md#deactivatepermission-1) | Stop the authorized URI that has been enabled |
| [persistPermission](arkts-corefile-fileshare-persistpermission-f.md#persistpermission-1) | Set persistence permissions for the URI |
| [revokePermission](arkts-corefile-fileshare-revokepermission-f.md#revokepermission-1) | Revoke persistence permissions for the URI |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [checkPathPermission](arkts-corefile-fileshare-checkpathpermission-f-sys.md#checkpathpermission-1) | Check permissions for the path. |
| [getPersistentPolicy](arkts-corefile-fileshare-getpersistentpolicy-f-sys.md#getpersistentpolicy-1) | Get all persistence permissions for the application. |
| [getSharedDirectoryInfo](arkts-corefile-fileshare-getshareddirectoryinfo-f-sys.md#getshareddirectoryinfo-1) | Gets the shared sandbox directories of applications |
| [getStatusByPermission](arkts-corefile-fileshare-getstatusbypermission-f-sys.md#getstatusbypermission-1) | Get the status of URIs permission for applications. |
| [grantPermissionByUser](arkts-corefile-fileshare-grantpermissionbyuser-f-sys.md#grantpermissionbyuser-1) | Grant the URIs permission by user. |
| [grantSharedDirectoryPermission](arkts-corefile-fileshare-grantshareddirectorypermission-f-sys.md#grantshareddirectorypermission-1) | Provides a permission grant for application-shared directories |
| [grantUriPermission](arkts-corefile-fileshare-granturipermission-f-sys.md#granturipermission-1) | Provides grant uri permission for app |
| [grantUriPermission](arkts-corefile-fileshare-granturipermission-f-sys.md#granturipermission-2) | Provides grant uri permission for app |
| [grantUriPermission](arkts-corefile-fileshare-granturipermission-f-sys.md#granturipermission-3) | Grant URI permissions for an application. |
| [revokePermission](arkts-corefile-fileshare-revokepermission-f-sys.md#revokepermission-2) | Revoke all persistence permissions for the application. |
| [revokePermission](arkts-corefile-fileshare-revokepermission-f-sys.md#revokepermission-3) | Revoke persistence permissions for the URI. |
| [revokePermissionByUser](arkts-corefile-fileshare-revokepermissionbyuser-f-sys.md#revokepermissionbyuser-1) | Revoke the URIs permission by user. |
| [revokeSharedDirectoryPermission](arkts-corefile-fileshare-revokeshareddirectorypermission-f-sys.md#revokeshareddirectorypermission-1) | Revokes permission for application-shared directories |
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
| [PermissionStatusInfo](arkts-corefile-fileshare-permissionstatusinfo-i-sys.md) | Indicates the URI permission status information of the application. |
| [SharedDirectoryInfo](arkts-corefile-fileshare-shareddirectoryinfo-i-sys.md) | The directory information shared with the system by the application. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [GrantStatus](arkts-corefile-fileshare-grantstatus-e.md) | Enumerates the status of the URI permission granted by user. |
| [OperationMode](arkts-corefile-fileshare-operationmode-e.md) | Enumerates the uri operate mode types. |
| [PolicyErrorCode](arkts-corefile-fileshare-policyerrorcode-e.md) | Enumerates the error code of the permission policy for the URI operation. |
| [PolicyType](arkts-corefile-fileshare-policytype-e.md) | Indicates the policy type of the path. |
