# LaunchServiceConnectCallback

```TypeScript
declare interface LaunchServiceConnectCallback
```

Define the callback interface for connecting to LaunchService. Used as the input parameter of [connectService] _{@link../@ohos.app.ability.launchServiceManager:launchServiceManager.connectService} to receive the IRemoteObject instance of IPC communication when the connection is successful, detect error codes when the connection fails, and receive events when the connection is disconnected.

**Since:** 26.1.0

<!--Device-unnamed-declare interface LaunchServiceConnectCallback--><!--Device-unnamed-declare interface LaunchServiceConnectCallback-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## onConnect

```TypeScript
onConnect(descriptor: LaunchServiceDescriptor, remote: rpc.IRemoteObject): void
```

Called when a connection is set up.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-LaunchServiceConnectCallback-onConnect(descriptor: LaunchServiceDescriptor, remote: rpc.IRemoteObject): void--><!--Device-LaunchServiceConnectCallback-onConnect(descriptor: LaunchServiceDescriptor, remote: rpc.IRemoteObject): void-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| descriptor | [LaunchServiceDescriptor](arkts-ability-launchservicedescriptor-i.md) | Yes | Descriptor of the LaunchService for the connection. |
| remote | [rpc.IRemoteObject](../../apis-ipc-kit/arkts-apis/arkts-ipc-rpc-iremoteobject-c.md) | Yes | The IRemoteObject instance is used to communicate with LaunchService. |

## onDisconnect

```TypeScript
onDisconnect(descriptor: LaunchServiceDescriptor): void
```

Called when a connection is interrupted.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-LaunchServiceConnectCallback-onDisconnect(descriptor: LaunchServiceDescriptor): void--><!--Device-LaunchServiceConnectCallback-onDisconnect(descriptor: LaunchServiceDescriptor): void-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| descriptor | [LaunchServiceDescriptor](arkts-ability-launchservicedescriptor-i.md) | Yes | Descriptor of the LaunchService that is disconnected. |

## onFailed

```TypeScript
onFailed(code: number): void
```

Called when a connection fails.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-LaunchServiceConnectCallback-onFailed(code: int): void--><!--Device-LaunchServiceConnectCallback-onFailed(code: int): void-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| code | number | Yes | Error code returned when the connection fails. 16000211 - The specified service is not found. 16000050 - System service connection failed. <br>The value should be an integer. |
