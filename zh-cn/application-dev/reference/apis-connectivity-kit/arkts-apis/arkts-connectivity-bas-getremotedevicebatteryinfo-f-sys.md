# getRemoteDeviceBatteryInfo（系统接口）

## 导入模块

```TypeScript
import { bas } from '@kit.ConnectivityKit';
```

## getRemoteDeviceBatteryInfo

```TypeScript
function getRemoteDeviceBatteryInfo(deviceId: BluetoothAddress): Promise<BatteryInfo>
```

查询远端设备的电量信息。

使用此接口前建议使用[isBasSupported](arkts-connectivity-bas-isbassupported-f-sys.md)查询本机是否支持获取远端设备的电量。只有支持蓝牙标准协议定义的电量服务（UUID：0000180F-0000-1000-8000-00805F9B34FB）的BLE远端设备才支持获取电量信息。对端蓝牙设备的电量信息变更通过[onBatteryChange](arkts-connectivity-bas-onbatterychange-f-sys.md)的回调结果获取。此接口支持使用对端设备的实际MAC地址和随机MAC地址获取电量信息。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | BluetoothAddress | 是 | 表示远端设备的地址信息。BluetoothAddress中的address、addressType、rawAddressType均为必选参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[BatteryInfo](arkts-connectivity-connection-batteryinfo-i.md)&gt; | Promise对象，返回远端设备的电量信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications are not allowed to use system APIs. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Only can be called on phone, tablet, and 2in1 devices. Failed to call the API when the short-range chip is not inserted on 2in1 device. |
| [2900001](../errorcode-bluetoothManager.md#2900001-蓝牙服务停止) | Service stopped. |
| [2900003](../errorcode-bluetoothManager.md#2900003-蓝牙开关关闭) | Bluetooth disabled. |
| [2900004](../errorcode-bluetoothManager.md#2900004-配置文件不支持) | Remote Device profile not supported. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |
| [2901003](../errorcode-bluetoothManager.md#2901003-gatt未连接) | Connection not established. |
