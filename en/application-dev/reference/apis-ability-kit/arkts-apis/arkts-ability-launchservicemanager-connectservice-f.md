# connectService

## Modules to Import

```TypeScript
import { launchServiceManager } from '@kit.AbilityKit';
```

## connectService

```TypeScript
function connectService(descriptor: LaunchServiceDescriptor, callback: LaunchServiceConnectCallback): number
```

Connects to the LaunchService process for IPC communication. The target LaunchService must have declared the IPC service. If the LaunchService process is not running, the system automatically starts it before the connection is established. The target service and invoker must belong to the same developer. The connection result is delivered through callback in callback.

**Since:** 26.1.0

**Required permissions:** ohos.permission.USE_DAEMON_SERVICE

**Model restriction:** This API can be used only in the stage model.

<!--Device-launchServiceManager-function connectService(descriptor: LaunchServiceDescriptor, callback: LaunchServiceConnectCallback): int--><!--Device-launchServiceManager-function connectService(descriptor: LaunchServiceDescriptor, callback: LaunchServiceConnectCallback): int-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| descriptor | [LaunchServiceDescriptor](arkts-ability-launchservicemanager-launchservicedescriptor-t.md) | Yes | Descriptor of the LaunchService to connect to. |
| callback | [LaunchServiceConnectCallback](arkts-ability-launchservicemanager-launchserviceconnectcallback-t.md) | Yes | Callbacks used to return the connection status, including onConnect, onDisconnect, and onFailed. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Connection ID. A value greater than **0** indicates that the connection request is accepted. You can pass this ID to [disconnectService](arkts-ability-launchservicemanager-disconnectservice-f.md) for disconnection. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: <br>1. The hardware does not support the capability. <br>2. The chip does not support the capability. <br>3. A dependent service feature is not supported. |
