# addPersistentDeviceId

## 导入模块

```TypeScript
import { access } from '@kit.ConnectivityKit';
```

## addPersistentDeviceId

```TypeScript
function addPersistentDeviceId(deviceId: string): Promise<void>
```

持久化存储蓝牙设备的虚拟MAC地址。使用Promise异步回调。

应用通过蓝牙相关接口，如扫描等途径获取到的设备地址（虚拟MAC地址）和实际的设备MAC地址不同。蓝牙子系统会保存一个虚拟MAC地址和实际设备MAC地址的映射关系。若应用想长期对该蓝牙设备进行操作使用，建议用此接口持久化存储该设备的虚拟MAC地址，后续可直接使用，该地址映射关系不会再改变。指定持久化存储的虚拟MAC地址需是有效的（可使用[access.isValidRandomDeviceId](arkts-connectivity-access-isvalidrandomdeviceid-f.md)判断）。使用该接口时，开发者应确保该虚拟MAC地址对应的对端蓝牙设备实际地址是保持不变的，若对端设备实际地址发生变化，持久化存储的地址信息将失效，无法继续使用。可调用[access.deletePersistentDeviceId](arkts-connectivity-access-deletepersistentdeviceid-f.md)删除已持久化存储的虚拟MAC地址。

**起始版本：** 16

**需要权限：** ohos.permission.ACCESS_BLUETOOTH and ohos.permission.PERSISTENT_BLUETOOTH_PEERS_MAC

**原子化服务API：** 从API版本16开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 对端设备的虚拟MAC地址，例如："XX:XX:XX:XX:XX:XX"。该地址一般来源于蓝牙扫描结果，如：可通过调用[startScan](arkts-connectivity-ble-blescanner-i.md#startscan)或[connection.startBluetoothDiscovery](arkts-connectivity-connection-startbluetoothdiscovery-f.md)扫描得到。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2900003](../errorcode-bluetoothManager.md#2900003-蓝牙开关关闭) | Bluetooth disabled. |
| [2900010](../errorcode-bluetoothManager.md#2900010-资源达到上限) | The number of supported device addresses has reached the upper limit. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Add persistent device address failed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let deviceId = '11:22:33:44:55:66'  // 该地址可通过BLE扫描获取
try {
    access.addPersistentDeviceId(deviceId);
} catch (err) {
    console.error('errCode: ' + err.code + ', errMessage: ' + err.message);
}
```
