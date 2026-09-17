# createGattServer

## 导入模块

```TypeScript
import { bluetoothManager } from '@kit.ConnectivityKit';
```

## createGattServer

```TypeScript
function createGattServer(): GattServer
```

创建一个可使用的GattServer实例。

从API version 9开始支持，从API version 10开始废弃。

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [createGattServer](arkts-connectivity-ble-creategattserver-f.md)

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [GattServer](arkts-connectivity-ble-gattserver-i.md) | server端类，使用server端方法之前需要创建该类的实例进行操作。 |

**示例**

```TypeScript
let gattServer: bluetoothManager.GattServer  = bluetoothManager.BLE.createGattServer();
```
