# verifyControlledDevicePackage (System API)

## Modules to Import

```TypeScript
```

## verifyControlledDevicePackage

```TypeScript
export function verifyControlledDevicePackage(ticketInfo: RemoteAuthPackage[]): Promise<boolean[]>
```

Verifies the authorization package from the controlled device. This function verifies the remote authorization package sent by the controlled device. It validates the ticket to ensure the authorization is legitimate.

**Since:** 26.1.0

**Required permissions:** ohos.permission.QUERY_TOOL_PERMISSIONS

**System capability:** SystemCapability.Security.Asset

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ticketInfo | [RemoteAuthPackage](arkts-ability-abilitytoolaccessctrl-remoteauthpackage-i-sys.md)[] | Yes | Remote authorization package list. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean[]&gt; | Promise used to return &#36;{boolean[]}. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denial. The interface caller does not have permission "ohos.permission.QUERY_TOOL_PERMISSIONS". |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The caller is not a system application. |
| [24010000](../errorcode-abilityToolAccessCtrl-sys.md#24010000-invalid-parameter) | Invalid parameter. Format of ticketInfo is invalid. |
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
abilityToolAccessCtrl.verifyControlledDevicePackage(ticketInfo).then((data: Array<boolean>) => {
  console.info('verifyControlledDevicePackage success, data: ' + JSON.stringify(data));
}).catch((err: BusinessError): void => {
  console.error(`verifyControlledDevicePackage fail, code: ${err.code}, message: ${err.message}`);
});
```
