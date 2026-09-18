# setCarKeyDfxData（系统接口）

## 导入模块

```TypeScript
import { connection } from '@kit.ConnectivityKit';
```

## setCarKeyDfxData

```TypeScript
function setCarKeyDfxData(deviceId: string, action: CarKeyActionType): void
```

把车钥匙执行开卡、删卡操作的事件通知蓝牙，以便蓝牙模块记录相应的维测（DFX）数据用于后续问题定位。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 表示远端设备MAC地址，例如："XX:XX:XX:XX:XX:XX"。 |
| action | [CarKeyActionType](arkts-connectivity-connection-carkeyactiontype-e-sys.md) | 是 | 表示车钥匙执行的操作，例如开卡、删卡。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications are not allowed to use system APIs. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call the API when the short-range chip is not inserted on 2in1 device. |
| [2900003](../errorcode-bluetoothManager.md#2900003-蓝牙开关关闭) | Bluetooth disabled. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |

**示例**

```TypeScript
try {
    connection.setCarKeyDfxData('11:22:33:44:55:66', connection.CarKeyActionType.CAR_KEY_ACTION_ADD);
} catch (err) {
    console.error(`Failed to set car key dfx data. Code: ${err.code}, message: ${err.message}`);
}
```
