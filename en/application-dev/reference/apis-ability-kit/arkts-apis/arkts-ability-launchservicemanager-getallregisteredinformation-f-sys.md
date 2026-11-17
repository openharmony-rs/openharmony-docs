# getAllRegisteredInformation (System API)

## Modules to Import

```TypeScript
import { launchServiceManager } from '@kit.AbilityKit';
```

## getAllRegisteredInformation

```TypeScript
function getAllRegisteredInformation(userId?: number): Promise<Array<LaunchServiceInformation>>
```

This method is used to obtain information about all registered LaunchServices.

**Since:** 26.1.0

**Required permissions:** ohos.permission.MANAGE_DAEMON_SERVICE

**Model restriction:** This API can be used only in the stage model.

<!--Device-launchServiceManager-function getAllRegisteredInformation(userId?: int): Promise<Array<LaunchServiceInformation>>--><!--Device-launchServiceManager-function getAllRegisteredInformation(userId?: int): Promise<Array<LaunchServiceInformation>>-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| userId | number | No | If the userId parameter is specified, the registered LaunchServices under the userId parameter are queried. If userId is not specified, the registered LaunchServices of all users are queried. <br>The value must be an integer. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[LaunchServiceInformation](arkts-ability-launchservicemanager-launchserviceinformation-t.md)&gt;&gt; | Promise object, which returns an array of LaunchService information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: <br>1. The hardware does not support the capability. <br>2. The chip does not support the capability. <br>3. A dependent service feature is not supported. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | System service connection failed. |
