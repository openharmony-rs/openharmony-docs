# getPersistentDeviceIds

## 导入模块

```TypeScript
import { access } from '@kit.ConnectivityKit';
```

## getPersistentDeviceIds

```TypeScript
function getPersistentDeviceIds(): string[]
```

获取应用持久化存储过的蓝牙虚拟MAC地址。

**起始版本：** 16

**需要权限：** ohos.permission.ACCESS_BLUETOOTH and ohos.permission.PERSISTENT_BLUETOOTH_PEERS_MAC

**原子化服务API：** 从API版本16开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string[] | 持久化存储过的蓝牙虚拟MAC地址列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2900003](../errorcode-bluetoothManager.md#2900003-蓝牙开关关闭) | Bluetooth disabled. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Get persistent device address failed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let deviceIds = access.getPersistentDeviceIds();
} catch (err) {
    console.error('errCode: ' + err.code + ', errMessage: ' + err.message);
}
```
