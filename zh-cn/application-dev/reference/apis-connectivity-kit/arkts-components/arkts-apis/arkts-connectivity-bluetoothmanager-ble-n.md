# BLE(蓝牙)

BLE模块提供了对蓝牙操作和管理的方法。

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [ble/ble](arkts-connectivity-bluetooth-ble.md)

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { bluetoothManager } from '@kit.ConnectivityKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [createGattServer](arkts-connectivity-ble-creategattserver-f.md) | 创建一个可使用的GattServer实例。 |
| [createGattClientDevice](arkts-connectivity-ble-creategattclientdevice-f.md) | 创建一个可使用的GattClientDevice实例。 |
| [getConnectedBLEDevices](arkts-connectivity-ble-getconnectedbledevices-f.md) | 获取和当前设备连接的BLE设备。 |
| [startBLEScan](arkts-connectivity-ble-startblescan-f.md) | 发起BLE扫描流程。 |
| [stopBLEScan](arkts-connectivity-ble-stopblescan-f.md) | 停止BLE扫描流程。 |
| [on](arkts-connectivity-ble-on-f.md#onbledevicefind) | 订阅BLE设备发现上报事件。 |
| [off](arkts-connectivity-ble-off-f.md#offbledevicefind) | 取消订阅BLE设备发现上报事件。 |
