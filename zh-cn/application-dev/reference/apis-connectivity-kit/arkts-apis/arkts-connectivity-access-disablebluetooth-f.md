# disableBluetooth

## 导入模块

```TypeScript
import { access } from '@kit.ConnectivityKit';
```

## disableBluetooth

```TypeScript
function disableBluetooth(): void
```

关闭蓝牙。

调用该接口时，系统弹出关闭蓝牙的对话框，由用户确认是否需要关闭蓝牙。如果应用想要感知用户操作对话框的行为，建议使用[access.disableBluetoothAsync](arkts-connectivity-access-disablebluetoothasync-f.md)。蓝牙开关状态结果可通过[access.on('stateChange')](arkts-connectivity-access-on-f.md#onstatechange)的回调函数获取到。建议蓝牙开关状态是[STATE_ON](arkts-connectivity-access-bluetoothstate-e.md)时，才调用该接口关闭蓝牙（可使用[access.getState](arkts-connectivity-access-getstate-f.md)判断当前蓝牙开关状态）。

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2900001](../errorcode-bluetoothManager.md#2900001-蓝牙服务停止) | Service stopped. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    access.disableBluetooth();
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```
