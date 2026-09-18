# onBatteryChange（系统接口）

## 导入模块

```TypeScript
import { bas } from '@kit.ConnectivityKit';
```

## onBatteryChange

```TypeScript
function onBatteryChange(callback: Callback<BatteryInfo>): void
```

订阅远端设备电量状态变化事件。

只有支持蓝牙标准协议定义的电量服务（UUID：0000180F-0000-1000-8000-00805F9B34FB）的BLE远端设备才支持上报电量信息，不可与[connection.on('batteryChange')](arkts-connectivity-connection-on-f.md#onbatterychange)混用。调用此接口会立即上报已连接电量服务设备的最新有效电量信息，后续仅当远端设备电量信息发生变化时上报电量信息。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[BatteryInfo](arkts-connectivity-connection-batteryinfo-i.md)&gt; | 是 | 回调函数，返回电量信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications are not allowed to use system APIs. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Only can be called on phone, tablet, and 2in1 devices. Failed to call the API when the short-range chip is not inserted on 2in1 device. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |
