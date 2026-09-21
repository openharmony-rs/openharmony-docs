# grantToolPermissionsByUser (System API)

## Modules to Import

```TypeScript
```

## grantToolPermissionsByUser

```TypeScript
export function grantToolPermissionsByUser(userAuthResult: UserAuthResult[]): Promise<TicketInfo[]>
```

Grants tool permissions based on user authorization results. This function grants permissions for tools (CLI commands or APIs) according to the user's authorization decisions. After successful authorization, tickets are generated which can be used for permission verification.

**Since:** 26.0.0

**Required permissions:** ohos.permission.MANAGE_TOOL_RUNTIME_PERMISSIONS

**Model restriction:** This API can be used in both the stage model and FA model.

**System capability:** SystemCapability.Security.Asset

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| userAuthResult | [UserAuthResult](arkts-ability-abilitytoolaccessctrl-userauthresult-i-sys.md)[] | Yes | User authorization result list. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[TicketInfo](arkts-ability-abilitytoolaccessctrl-ticketinfo-i-sys.md)[]&gt; | Promise used to return ${TicketInfo[]}. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denial. The interface caller does not have permission "ohos.permission.MANAGE_TOOL_RUNTIME_PERMISSIONS". |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The caller is not a system application. |
| [24010000](../errorcode-abilityToolAccessCtrl-sys.md#24010000-invalid-parameter) | Invalid parameter. PermissionName exceeds 256 characters, permissionStatus is invalid, etc. |
| [24010001](../errorcode-abilityToolAccessCtrl-sys.md#24010001-system-service-abnormal) | Service is abnormal. Possible cause: IPC failed. |
| [24010002](../errorcode-abilityToolAccessCtrl-sys.md#24010002-internal-service-error) | Common internal error. Possible cause: dependent service unavailable, resource access failure, etc. |
| [24010003](../errorcode-abilityToolAccessCtrl-sys.md#24010003-environment-error) | The account is not logged in, network is unavailable, timeout, etc. |
| [24010004](../errorcode-abilityToolAccessCtrl-sys.md#24010004-permission-does-not-exist) | Invalid permission. A permission in permissionInfo does not exist. |
| [24010005](../errorcode-abilityToolAccessCtrl-sys.md#24010005-authorization-failed) | Grant permission failed. The application specified by the tokenID is not allowed to be granted with the specified permission, the specified permission cannot be granted by user, etc. |

**Examples**

```TypeScript
import { abilityToolAccessCtrl, abilityAccessCtrl, Permissions } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let userAuthResult: Array<abilityToolAccessCtrl.UserAuthResult> = [{
  permissionInfo: [{
    permission: 'ohos.permission.cli.BUNDLE_ACTIVE_INFO' as Permissions,
    permissionStatus: abilityAccessCtrl.PermissionStatus.GRANTED
  }],
  permissionQuery: {
    operationInfo: [{
      operationType: abilityToolAccessCtrl.OperationType.CLI,
      info: 'ohos.permission.cli.BUNDLE_ACTIVE_INFO'
    }],
    needTicket: true
  }
}];
abilityToolAccessCtrl.grantToolPermissionsByUser(userAuthResult).then((data: Array<abilityToolAccessCtrl.TicketInfo>) => {
  console.info('grantToolPermissionsByUser success, data: ' + JSON.stringify(data));
}).catch((err: BusinessError): void => {
  console.error(`grantToolPermissionsByUser fail, code: ${err.code}, message: ${err.message}`);
});
```
