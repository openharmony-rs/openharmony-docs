# unregister

## Modules to Import

```TypeScript
import { launchServiceManager } from '@kit.AbilityKit';
```

## unregister

```TypeScript
function unregister(descriptor: LaunchServiceDescriptor): Promise<void>
```

Deregister LaunchService. If the LaunchService process is running, the system stops the process when you log out. Only applications that contain the launch service can be registered or deregistered. You need to apply for the corresponding permission based on the application type. - Common applications(non-MDM applications): You need to apply for the ohos.permission.REGISTER_DAEMON_SERVICE permission. - MDM application: You need to apply for the ohos.permission.ENTERPRISE_REGISTER_DAEMON_SERVICE permission.

**Since:** 26.1.0

**Required permissions:** ohos.permission.REGISTER_DAEMON_SERVICE or ohos.permission.ENTERPRISE_REGISTER_DAEMON_SERVICE

**Model restriction:** This API can be used only in the stage model.

<!--Device-launchServiceManager-function unregister(descriptor: LaunchServiceDescriptor): Promise<void>--><!--Device-launchServiceManager-function unregister(descriptor: LaunchServiceDescriptor): Promise<void>-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| descriptor | [LaunchServiceDescriptor](arkts-ability-launchservicemanager-launchservicedescriptor-t.md) | Yes | Descriptor of the LaunchService to unregister. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: <br>1. The hardware does not support the capability. <br>2. The chip does not support the capability. <br>3. A dependent service feature is not supported. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | System service connection failed. |
| 16000211 | The specified service is not found. |
