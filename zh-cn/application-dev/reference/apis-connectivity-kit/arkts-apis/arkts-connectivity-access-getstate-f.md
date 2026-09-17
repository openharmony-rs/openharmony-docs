# getState

## 导入模块

```TypeScript
import { access } from '@kit.ConnectivityKit';
```

## getState

```TypeScript
function getState(): BluetoothState
```

获取蓝牙开关状态。

**起始版本：** 10

**需要权限：** 
- API版本13+：N/A
- API版本10-12：ohos.permission.ACCESS_BLUETOOTH

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [BluetoothState](arkts-connectivity-access-bluetoothstate-e.md) | 表示蓝牙开关状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied.<br>**适用版本：** 10 - 12 |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2900001](../errorcode-bluetoothManager.md#2900001-蓝牙服务停止) | Service stopped. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let state = access.getState();
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```
