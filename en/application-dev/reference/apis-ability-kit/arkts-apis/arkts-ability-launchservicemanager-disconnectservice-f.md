# disconnectService

## Modules to Import

```TypeScript
import { launchServiceManager } from '@kit.AbilityKit';
```

## disconnectService

```TypeScript
function disconnectService(connectionId: number): Promise<void>
```

Disconnect from the LaunchService process.

**Since:** 26.1.0

**Required permissions:** ohos.permission.USE_DAEMON_SERVICE

**Model restriction:** This API can be used only in the stage model.

<!--Device-launchServiceManager-function disconnectService(connectionId: int): Promise<void>--><!--Device-launchServiceManager-function disconnectService(connectionId: int): Promise<void>-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| connectionId | number | Yes | Returned connection ID [connectService](arkts-ability-launchservicemanager-connectservice-f.md). <br>The value must be an integer. |

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
| 16000216 | The specified connection is invalid. |
