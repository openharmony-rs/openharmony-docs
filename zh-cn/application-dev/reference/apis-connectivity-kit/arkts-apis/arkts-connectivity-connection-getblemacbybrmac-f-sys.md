# getBleMacByBrMac（系统接口）

## 导入模块

```TypeScript
import { connection } from '@kit.ConnectivityKit';
```

## getBleMacByBrMac

```TypeScript
function getBleMacByBrMac(brMac: string): string
```

根据配对远端设备的真实BR地址，获取配对远端设备的真实BLE地址。

该接口用于识别配对中同一双模设备的BR表项和BLE表项。设备列表。输入brMac是配对的远程设备的真实BR地址，返回值是同一远端设备的真实BLE地址。

**起始版本：** 26.2.0

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-connection-function getBleMacByBrMac(brMac: string): string--><!--Device-connection-function getBleMacByBrMac(brMac: string): string-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| brMac | string | 是 | 配对的远端设备的真实BR地址。例如：“11:22:33:AA:BB:FF”。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回远端设备的真实BLE地址。例如，“11:22:33:AA:BB:FF”。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Non-system applications are not allowed to use system APIs. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. |
| [2900003](../errorcode-bluetoothManager.md#2900003-蓝牙开关关闭) | Bluetooth disabled. |
| [2900016](../errorcode-bluetoothManager.md#2900016-设备未配对) | Device unpaired. |
| 2900017 | No BLE address is associated with the input BR address. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |
