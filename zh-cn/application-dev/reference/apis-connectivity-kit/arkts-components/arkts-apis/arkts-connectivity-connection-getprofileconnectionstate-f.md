# getProfileConnectionState

## 导入模块

```TypeScript
import { connection } from '@kit.ConnectivityKit';
```

## getProfileConnectionState

```TypeScript
function getProfileConnectionState(profileId?: ProfileId): ProfileConnectionState
```

获取蓝牙Profile协议的连接状态，其中ProfileId为可选参数。

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| profileId | [ProfileId](arkts-connectivity-connection-profileid-t.md) | 否 | 表示Profile协议的枚举值。如果携带ProfileId，则返回指定Profile协议的连接状态。如果未携带ProfileId，则检查所有支持的Profile连接状态，按如下优先级顺序检查并返回：存在已连接的Profile协议，则返回[STATE_CONNECTED](arkts-connectivity-constant-profileconnectionstate-e.md)。存在正在连接的Profile协议，则返回[STATE_CONNECTING](arkts-connectivity-constant-profileconnectionstate-e.md)。存在正在断连的Profile协议，则返回[STATE_DISCONNECTING](arkts-connectivity-constant-profileconnectionstate-e.md)。以上条件均不满足，则返回[STATE_DISCONNECTED](arkts-connectivity-constant-profileconnectionstate-e.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ProfileConnectionState](arkts-connectivity-connection-profileconnectionstate-t.md) | Profile协议的连接状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameter. Possible causes: 1. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2900001](../errorcode-bluetoothManager.md#2900001-蓝牙服务停止) | Service stopped. |
| [2900003](../errorcode-bluetoothManager.md#2900003-蓝牙开关关闭) | Bluetooth disabled. |
| [2900004](../errorcode-bluetoothManager.md#2900004-配置文件不支持) | Profile not supported. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { constant } from '@kit.ConnectivityKit';
try {
    let result: connection.ProfileConnectionState = connection.getProfileConnectionState(constant.ProfileId.PROFILE_A2DP_SOURCE);
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```
