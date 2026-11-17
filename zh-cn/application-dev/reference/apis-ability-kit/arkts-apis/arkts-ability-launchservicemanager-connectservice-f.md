# connectService

## 导入模块

```TypeScript
import { launchServiceManager } from '@kit.AbilityKit';
```

## connectService

```TypeScript
function connectService(descriptor: LaunchServiceDescriptor, callback: LaunchServiceConnectCallback): number
```

连接LaunchService进程，用于IPC通信。目标LaunchService必须已声明IPC服务。若该LaunchService进程尚未运行，系统会在建立连接前自动将其启动。目标服务和调用者必须属于同一个开发者。连接结果通过callback中的回调下发。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.USE_DAEMON_SERVICE

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-launchServiceManager-function connectService(descriptor: LaunchServiceDescriptor, callback: LaunchServiceConnectCallback): int--><!--Device-launchServiceManager-function connectService(descriptor: LaunchServiceDescriptor, callback: LaunchServiceConnectCallback): int-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| descriptor | [LaunchServiceDescriptor](arkts-ability-launchservicemanager-launchservicedescriptor-t.md) | 是 | 要连接的LaunchService的描述符。 |
| callback | [LaunchServiceConnectCallback](arkts-ability-launchservicemanager-launchserviceconnectcallback-t.md) | 是 | 用于返回连接的回调状态，包括onConnect、onDisconnect、onFailed。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 连接ID。大于**0**的值表示连接请求被接受。可以将此ID传递给[disconnectService](arkts-ability-launchservicemanager-disconnectservice-f.md)以断开连接。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. Possible causes: <br>1. The hardware does not support the capability. <br>2. The chip does not support the capability. <br>3. A dependent service feature is not supported. |
