# register

## Modules to Import

```TypeScript
import { launchServiceManager } from '@kit.AbilityKit';
```

## register

```TypeScript
function register(descriptor: LaunchServiceDescriptor): Promise<void>
```

Register the LaunchService. In the module.json5 configuration file, runAtLoad is set to true, the service is registered successfully, and the status is Enabled. The system automatically starts the LaunchService process. Only the applications that contain the launch service can be registered. You need to apply for the corresponding permission based on the application type. - Common applications(non-MDM applications): You need to apply for the ohos.permission.REGISTER_DAEMON_SERVICE permission. - MDM application: You need to apply for the ohos.permission.ENTERPRISE_REGISTER_DAEMON_SERVICE permission.

**Since:** 26.1.0

**Required permissions:** ohos.permission.REGISTER_DAEMON_SERVICE or ohos.permission.ENTERPRISE_REGISTER_DAEMON_SERVICE

**Model restriction:** This API can be used only in the stage model.

<!--Device-launchServiceManager-function register(descriptor: LaunchServiceDescriptor): Promise<void>--><!--Device-launchServiceManager-function register(descriptor: LaunchServiceDescriptor): Promise<void>-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| descriptor | [LaunchServiceDescriptor](arkts-ability-launchservicemanager-launchservicedescriptor-t.md) | Yes | Descriptor of the LaunchService to register. |

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
| 16000212 | The specified service is already registered. |
