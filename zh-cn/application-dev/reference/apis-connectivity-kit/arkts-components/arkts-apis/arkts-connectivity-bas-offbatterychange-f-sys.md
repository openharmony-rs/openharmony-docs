# offBatteryChange（系统接口）

## 导入模块

```TypeScript
import { bas } from '@kit.ConnectivityKit';
```

## offBatteryChange

```TypeScript
function offBatteryChange(callback?: Callback<BatteryInfo>): void
```

取消订阅远端设备电量状态变化事件。

不可与[connection.off('batteryChange')](arkts-connectivity-connection-off-f.md#offbatterychange)混用。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[BatteryInfo](arkts-connectivity-connection-batteryinfo-i.md)&gt; | 否 | 回调函数。若传参，则需与[bas.onBatteryChange](arkts-connectivity-bas-onbatterychange-f-sys.md)中的回调函数一致；若无传参，则取消订阅电量变化所有回调函数通知。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications are not allowed to use system APIs. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Only can be called on phone, tablet, and 2in1 devices. Failed to call the API when the short-range chip is not inserted on 2in1 device. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |
