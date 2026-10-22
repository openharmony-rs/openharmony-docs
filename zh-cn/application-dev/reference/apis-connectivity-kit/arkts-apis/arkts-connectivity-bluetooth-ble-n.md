# BLE（蓝牙）

```TypeScript
namespace BLE
```

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [BLE](arkts-connectivity-bluetoothmanager-ble-n.md)

<!--Device-bluetooth-namespace BLE--><!--Device-bluetooth-namespace BLE-End-->

**系统能力：** SystemCapability.Communication.Bluetooth.Core

## 导入模块

```TypeScript
import { bluetooth } from '@kit.ConnectivityKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [createGattClientDevice](arkts-connectivity-ble-creategattclientdevice-f.md#creategattclientdevice-1) | 创建一个可使用的GattClientDevice实例。 |
| [createGattServer](arkts-connectivity-ble-creategattserver-f.md#creategattserver-1) | 创建一个可使用的GattServer实例。 |
| [getConnectedBLEDevices](arkts-connectivity-ble-getconnectedbledevices-f.md#getconnectedbledevices-1) | 获取和当前设备连接的BLE设备。 |
| [off('BLEDeviceFind')](arkts-connectivity-ble-off-f.md#offbledevicefind) | 取消订阅BLE设备发现上报事件。 |
| [on('BLEDeviceFind')](arkts-connectivity-ble-on-f.md#onbledevicefind) | 订阅BLE设备发现上报事件。 |
| [startBLEScan](arkts-connectivity-ble-startblescan-f.md#startblescan-1) | 发起BLE扫描流程。 |
| [stopBLEScan](arkts-connectivity-ble-stopblescan-f.md#stopblescan-1) | 停止BLE扫描流程。 |
