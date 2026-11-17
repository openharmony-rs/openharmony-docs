# LaunchServiceConnectCallback

```TypeScript
declare interface LaunchServiceConnectCallback
```

定义连接LaunchService时的回调接口。作为[connectService](arkts-ability-launchservicemanager-connectservice-f.md)的入参使用，用于连接成功时接收IPC通信的IRemoteObject实例、连接失败时感知错误码、断连时接收事件。

**起始版本：** 26.1.0

<!--Device-unnamed-declare interface LaunchServiceConnectCallback--><!--Device-unnamed-declare interface LaunchServiceConnectCallback-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## onConnect

```TypeScript
onConnect(descriptor: LaunchServiceDescriptor, remote: rpc.IRemoteObject): void
```

在建立连接时调用。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LaunchServiceConnectCallback-onConnect(descriptor: LaunchServiceDescriptor, remote: rpc.IRemoteObject): void--><!--Device-LaunchServiceConnectCallback-onConnect(descriptor: LaunchServiceDescriptor, remote: rpc.IRemoteObject): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| descriptor | [LaunchServiceDescriptor](arkts-ability-launchservicedescriptor-i.md) | 是 | 连接的LaunchService的描述符。 |
| remote | [rpc.IRemoteObject](../../apis-ipc-kit/arkts-apis/arkts-ipc-rpc-iremoteobject-c.md) | 是 | IRemoteObject实例用于与LaunchService通信。 |

## onDisconnect

```TypeScript
onDisconnect(descriptor: LaunchServiceDescriptor): void
```

当连接中断时调用。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LaunchServiceConnectCallback-onDisconnect(descriptor: LaunchServiceDescriptor): void--><!--Device-LaunchServiceConnectCallback-onDisconnect(descriptor: LaunchServiceDescriptor): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| descriptor | [LaunchServiceDescriptor](arkts-ability-launchservicedescriptor-i.md) | 是 | 断开连接的LaunchService的描述符。 |

## onFailed

```TypeScript
onFailed(code: number): void
```

当连接失败时调用。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LaunchServiceConnectCallback-onFailed(code: int): void--><!--Device-LaunchServiceConnectCallback-onFailed(code: int): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| code | number | 是 | 连接失败时返回的错误码。16000211 -找不到指定的服务。16000050 -系统服务连接失败。<br>取值限定为整数。 |
