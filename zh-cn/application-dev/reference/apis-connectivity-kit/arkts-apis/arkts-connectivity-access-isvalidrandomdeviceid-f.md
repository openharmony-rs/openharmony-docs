# isValidRandomDeviceId

## 导入模块

```TypeScript
import { access } from '@kit.ConnectivityKit';
```

## isValidRandomDeviceId

```TypeScript
function isValidRandomDeviceId(deviceId: string): boolean
```

判断对端蓝牙设备的虚拟MAC地址是否有效。

有效的虚拟MAC地址一般来源于蓝牙扫描结果，如：通过调用[startScan](arkts-connectivity-ble-blescanner-i.md#startscan)或[connection.startBluetoothDiscovery](arkts-connectivity-connection-startbluetoothdiscovery-f.md)扫描得到。

**起始版本：** 16

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**原子化服务API：** 从API版本16开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 对端设备的虚拟MAC地址，例如："XX:XX:XX:XX:XX:XX"。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 蓝牙设备的虚拟MAC地址是否是有效的。true表示有效地址，false表示无效地址。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2900003](../errorcode-bluetoothManager.md#2900003-蓝牙开关关闭) | Bluetooth disabled. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Check persistent device address failed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let deviceId = '11:22:33:44:55:66'  // 该地址可通过BLE扫描获取
    let isValid = access.isValidRandomDeviceId(deviceId);
    console.info("isValid: " + isValid);
} catch (err) {
    console.error('errCode: ' + err.code + ', errMessage: ' + err.message);
}
```
