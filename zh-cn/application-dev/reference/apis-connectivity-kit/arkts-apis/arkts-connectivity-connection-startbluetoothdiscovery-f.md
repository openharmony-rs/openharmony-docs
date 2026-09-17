# startBluetoothDiscovery

## 导入模块

```TypeScript
import { connection } from '@kit.ConnectivityKit';
```

## startBluetoothDiscovery

```TypeScript
function startBluetoothDiscovery(): void
```

开启蓝牙扫描，发现对端蓝牙设备。

该接口支持发现传统蓝牙设备和低功耗蓝牙设备，整个蓝牙扫描过程大约持续12s。扫描结果可通过API version 10开始支持的[connection.on('bluetoothDeviceFind')](arkts-connectivity-connection-on-f.md#onbluetoothdevicefind)或者API version 18开始支持的[connection.on('discoveryResult')](arkts-connectivity-connection-on-f.md#ondiscoveryresult)的回调函数获取到。推荐使用[connection.on('discoveryResult')](arkts-connectivity-connection-on-f.md#ondiscoveryresult)，该方式可以获取到更多设备信息。若在扫描过程中，请勿重复调用该方法（可使用[connection.isBluetoothDiscovering](arkts-connectivity-connection-isbluetoothdiscovering-f.md)判断蓝牙当前是否处于扫描过程中）。调用[connection.stopBluetoothDiscovery](arkts-connectivity-connection-stopbluetoothdiscovery-f.md)可以停止该方法开启的扫描流程，扫描停止后，才能开启下一次蓝牙扫描。

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2900001](../errorcode-bluetoothManager.md#2900001-蓝牙服务停止) | Service stopped. |
| [2900003](../errorcode-bluetoothManager.md#2900003-蓝牙开关关闭) | Bluetooth disabled. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
function onReceiveEvent(data: Array<string>) {
    console.info('data length' + data.length);
}
try {
    connection.on('bluetoothDeviceFind', onReceiveEvent);
    connection.startBluetoothDiscovery();
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```
