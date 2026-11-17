# getInformation

## Modules to Import

```TypeScript
import { launchServiceManager } from '@kit.AbilityKit';
```

## getInformation

```TypeScript
function getInformation(descriptor: LaunchServiceDescriptor): Promise<LaunchServiceInformation>
```

This method is used to obtain information about a specified LaunchService. If the application is installed but LaunchService is not registered, the status returned is NOT_REGISTERED and the pid is 0.

**Since:** 26.1.0

**Required permissions:** ohos.permission.USE_DAEMON_SERVICE

**Model restriction:** This API can be used only in the stage model.

<!--Device-launchServiceManager-function getInformation(descriptor: LaunchServiceDescriptor): Promise<LaunchServiceInformation>--><!--Device-launchServiceManager-function getInformation(descriptor: LaunchServiceDescriptor): Promise<LaunchServiceInformation>-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| descriptor | [LaunchServiceDescriptor](arkts-ability-launchservicemanager-launchservicedescriptor-t.md) | Yes | Descriptor of the LaunchService to query. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[LaunchServiceInformation](arkts-ability-launchservicemanager-launchserviceinformation-t.md)&gt; | Promise is used to return LaunchService information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: <br>1. The hardware does not support the capability. <br>2. The chip does not support the capability. <br>3. A dependent service feature is not supported. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | System service connection failed. |
| 16000211 | The specified service is not found. |
