# startBluetoothDiscovery

## 导入模块

```TypeScript
import { bluetooth } from '@kit.ConnectivityKit';
```

## startBluetoothDiscovery

```TypeScript
function startBluetoothDiscovery(): boolean
```

开启蓝牙扫描，可以发现远端设备。

从API version 8开始支持，从API version 9开始废弃。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [startBluetoothDiscovery](arkts-connectivity-bluetoothmanager-startbluetoothdiscovery-f.md)

**需要权限：** ohos.permission.DISCOVER_BLUETOOTH and ohos.permission.LOCATION

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 开启蓝牙扫描，成功返回true，否则返回false。 |

**示例**

```TypeScript
let deviceId : Array<string>;
function onReceiveEvent(data : Array<string>) {
    deviceId = data;
}
bluetooth.on('bluetoothDeviceFind', onReceiveEvent);
let result : boolean = bluetooth.startBluetoothDiscovery();
```
