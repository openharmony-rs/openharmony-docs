# stopBluetoothDiscovery

## 导入模块

```TypeScript
import { bluetooth } from '@kit.ConnectivityKit';
```

## stopBluetoothDiscovery

```TypeScript
function stopBluetoothDiscovery(): boolean
```

关闭蓝牙扫描。

从API version 8开始支持，从API version 9开始废弃。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [stopBluetoothDiscovery](arkts-connectivity-bluetoothmanager-stopbluetoothdiscovery-f.md)

**需要权限：** ohos.permission.DISCOVER_BLUETOOTH

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 关闭蓝牙扫描，成功返回true，否则返回false。 |

**示例**

```TypeScript
let result : boolean = bluetooth.stopBluetoothDiscovery();
```
