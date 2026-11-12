# generateControllerDevicePackage (System API)

## Modules to Import

```TypeScript
import { abilityToolAccessCtrl } from '@kit.AbilityKit';
```

## generateControllerDevicePackage

```TypeScript
export function generateControllerDevicePackage(remoteUserAuthResult: RemoteUserAuthResults[]):
    Promise<RemoteAuthPackage[]>
```

Generate the authorization package of the main control device. Generate a remote authorization package based on the remote user authorization result. The generated package can be sent to the controlled device for permission verification.

**Since:** 26.0.1

**Required permissions:** ohos.permission.QUERY_TOOL_PERMISSIONS

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-abilityToolAccessCtrl-export function generateControllerDevicePackage(remoteUserAuthResult: RemoteUserAuthResults[]):    Promise<RemoteAuthPackage[]>--><!--Device-abilityToolAccessCtrl-export function generateControllerDevicePackage(remoteUserAuthResult: RemoteUserAuthResults[]):    Promise<RemoteAuthPackage[]>-End-->

**System capability:** SystemCapability.Security.Asset

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| remoteUserAuthResult | [RemoteUserAuthResults](arkts-ability-abilitytoolaccessctrl-remoteuserauthresults-i-sys.md)[] | Yes | Remote user authorization result list. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[RemoteAuthPackage](arkts-ability-abilitytoolaccessctrl-remoteauthpackage-i-sys.md)[]&gt; | Promise object that returns ${RemoteAuthPackage[]}. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [24010000](../errorcode-abilityToolAccessCtrl-sys.md#24010000-invalid-parameter) | Invalid parameter. OperationType and operationInfo do not match, specified callerTokenId does not exist, etc. |
| [24010001](../errorcode-abilityToolAccessCtrl-sys.md#24010001-system-service-abnormal) | Service is abnormal. Possible cause: IPC failed. |
| [24010002](../errorcode-abilityToolAccessCtrl-sys.md#24010002-internal-service-error) | Common internal error. Possible cause: dependent service unavailable, resource access failure, etc. |
| [24010003](../errorcode-abilityToolAccessCtrl-sys.md#24010003-environment-error) | The account is not logged in, network is unavailable, timeout, etc. |

<!--Del-->
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

<!--DelEnd-->
