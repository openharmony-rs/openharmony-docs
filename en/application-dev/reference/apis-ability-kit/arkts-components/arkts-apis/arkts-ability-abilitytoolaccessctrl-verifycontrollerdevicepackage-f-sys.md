# verifyControllerDevicePackage (System API)

## Modules to Import

```TypeScript
```

## verifyControllerDevicePackage

```TypeScript
export function verifyControllerDevicePackage(ticketInfo: RemoteAuthPackage[], remoteInfo: RemoteInfo):
    Promise<boolean[]>
```

Verifies the authorization package from the controller device. This function verifies the remote authorization package sent by the controller device. It validates the ticket and remote device information to ensure the authorization is legitimate.

**Since:** 26.0.1

**Required permissions:** ohos.permission.QUERY_TOOL_PERMISSIONS

**Model restriction:** This API can be used in both the stage model and FA model.

**System capability:** SystemCapability.Security.Asset

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ticketInfo | [RemoteAuthPackage](arkts-ability-abilitytoolaccessctrl-remoteauthpackage-i-sys.md)[] | Yes | Remote authorization package list. |
| remoteInfo | [RemoteInfo](arkts-ability-abilitytoolaccessctrl-remoteinfo-i-sys.md) | Yes | Remote device information. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean[]&gt; | Promise used to return ${boolean[]}. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denial. The interface caller does not have permission "ohos.permission.QUERY_TOOL_PERMISSIONS". |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The caller is not a system application. |
| [24010000](../errorcode-abilityToolAccessCtrl-sys.md#24010000-invalid-parameter) | Invalid parameter. Format of ticketInfo or remoteInfo is invalid. |
| [24010001](../errorcode-abilityToolAccessCtrl-sys.md#24010001-system-service-abnormal) | Service is abnormal. Possible cause: IPC failed. |
| [24010002](../errorcode-abilityToolAccessCtrl-sys.md#24010002-internal-service-error) | Common internal error. Possible cause: dependent service unavailable, resource access failure, etc. |
| [24010003](../errorcode-abilityToolAccessCtrl-sys.md#24010003-environment-error) | The account is not logged in, network is unavailable, timeout, etc. |

**Examples**

```TypeScript
import { abilityToolAccessCtrl } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let ticketInfo: Array<abilityToolAccessCtrl.RemoteAuthPackage> = [{
  remoteMessage: 'test_message',
  challenge: 'test_challenge',
  ticket: 'test_ticket'
}];
let remoteInfo: abilityToolAccessCtrl.RemoteInfo = {
  role: abilityToolAccessCtrl.Role.CONTROLLER,
  remoteId: 'device123',
  domainId: 'domain456'
};
abilityToolAccessCtrl.verifyControllerDevicePackage(ticketInfo, remoteInfo).then((data: Array<boolean>) => {
  console.info('verifyControllerDevicePackage success, data: ' + JSON.stringify(data));
}).catch((err: BusinessError): void => {
  console.error(`verifyControllerDevicePackage fail, code: ${err.code}, message: ${err.message}`);
});
```
