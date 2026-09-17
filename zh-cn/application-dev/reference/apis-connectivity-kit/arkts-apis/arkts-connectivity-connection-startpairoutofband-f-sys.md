# startPairOutOfBand（系统接口）

## 导入模块

```TypeScript
import { connection } from '@kit.ConnectivityKit';
```

## startPairOutOfBand

```TypeScript
function startPairOutOfBand(deviceId: string, transport: BluetoothTransport, p192Data?: OobData,
    p256Data?: OobData): Promise<void>
```

使用带外机制开始与特定的远程蓝牙设备配对。该函数为异步函数，通过监听bondStateChange事件获取配对状态。如果没有使用p192Data和p256Data，函数调用将失败。如果同时使用p192Data和p256Data，则以p256Data生效。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 设备ID。例如，“11:22:33:AA:BB:FF”。 |
| transport | [BluetoothTransport](arkts-connectivity-connection-bluetoothtransport-e.md) | 是 | 指示远程蓝牙设备的传输。 |
| p192Data | [OobData](arkts-connectivity-connection-oobdata-i-sys.md) | 否 | 带外数据(P192)。 |
| p256Data | [OobData](arkts-connectivity-connection-oobdata-i-sys.md) | 否 | 带外数据(P256)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 不会返回任何值的Promise。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications are not allowed to use system APIs. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2900003](../errorcode-bluetoothManager.md#2900003-蓝牙开关关闭) | Bluetooth disabled. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |
