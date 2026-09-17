# generateControllerDevicePackage (System API)

## Modules to Import

```TypeScript
```

## generateControllerDevicePackage

```TypeScript
export function generateControllerDevicePackage(remoteUserAuthResult: RemoteUserAuthResults[]):
    Promise<RemoteAuthPackage[]>
```

Generates an authorization package for the controller device. This function generates a remote authorization package based on the remote user authorization results. The generated package can be sent to the controlled device for permission verification.

**Since:** 26.1.0

**Required permissions:** ohos.permission.QUERY_TOOL_PERMISSIONS

**System capability:** SystemCapability.Security.Asset

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| remoteUserAuthResult | [RemoteUserAuthResults](arkts-ability-abilitytoolaccessctrl-remoteuserauthresults-i-sys.md)[] | Yes | Remote user authorization result list. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[RemoteAuthPackage](arkts-ability-abilitytoolaccessctrl-remoteauthpackage-i-sys.md)[]&gt; | Promise used to return &#36;{RemoteAuthPackage[]}. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denial. The interface caller does not have permission "ohos.permission.QUERY_TOOL_PERMISSIONS". |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The caller is not a system application. |
| [24010000](../errorcode-abilityToolAccessCtrl-sys.md#24010000-invalid-parameter) | Invalid parameter. OperationType and operationInfo do not match, specified callerTokenId does not exist, etc. |
| [24010001](../errorcode-abilityToolAccessCtrl-sys.md#24010001-system-service-abnormal) | Service is abnormal. Possible cause: IPC failed. |
| [24010002](../errorcode-abilityToolAccessCtrl-sys.md#24010002-internal-service-error) | Common internal error. Possible cause: dependent service unavailable, resource access failure, etc. |
| [24010003](../errorcode-abilityToolAccessCtrl-sys.md#24010003-environment-error) | The account is not logged in, network is unavailable, timeout, etc. |

**Examples**

```TypeScript
import { abilityToolAccessCtrl } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let remoteUserAuthResult: Array<abilityToolAccessCtrl.RemoteUserAuthResults> = [{
  results: [{
    permission: 'ohos.permission.cli.BUNDLE_ACTIVE_INFO',
    authResult: 'GRANTED'
  }],
  permissionQuery: {
    operationInfo: [{
      operationType: abilityToolAccessCtrl.OperationType.CLI,
      info: {
        cliCmdName: 'ohos-displayManager',
        subCliCmdName: 'set-brightness'
      }
    }],
    needTicket: true
  }
}];
abilityToolAccessCtrl.generateControllerDevicePackage(remoteUserAuthResult).then((data: Array<abilityToolAccessCtrl.RemoteAuthPackage>) => {
  console.info('generateControllerDevicePackage success, data: ' + JSON.stringify(data));
}).catch((err: BusinessError): void => {
  console.error(`generateControllerDevicePackage fail, code: ${err.code}, message: ${err.message}`);
});
```
