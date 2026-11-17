# disconnectService

## 导入模块

```TypeScript
import { launchServiceManager } from '@kit.AbilityKit';
```

## disconnectService

```TypeScript
function disconnectService(connectionId: number): Promise<void>
```

断开与LaunchService进程的连接。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.USE_DAEMON_SERVICE

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-launchServiceManager-function disconnectService(connectionId: int): Promise<void>--><!--Device-launchServiceManager-function disconnectService(connectionId: int): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| connectionId | number | 是 | 返回的连接ID [connectService](arkts-ability-launchservicemanager-connectservice-f.md)。<br>取值限定为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 不返回任何值的Promise。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. Possible causes: <br>1. The hardware does not support the capability. <br>2. The chip does not support the capability. <br>3. A dependent service feature is not supported. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | System service connection failed. |
| 16000216 | The specified connection is invalid. |
