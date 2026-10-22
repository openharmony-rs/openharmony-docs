# BLE

```TypeScript
namespace BLE
```

Provides methods to operate or manage Bluetooth.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [BLE](arkts-connectivity-bluetoothmanager-ble-n.md)

<!--Device-bluetooth-namespace BLE--><!--Device-bluetooth-namespace BLE-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## Modules to Import

```TypeScript
import { bluetooth } from '@kit.ConnectivityKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [createGattClientDevice](arkts-connectivity-ble-creategattclientdevice-f.md#creategattclientdevice-1) | create a JavaScript Gatt client device instance. |
| [createGattServer](arkts-connectivity-ble-creategattserver-f.md#creategattserver-1) | create a JavaScript Gatt server instance. |
| [getConnectedBLEDevices](arkts-connectivity-ble-getconnectedbledevices-f.md#getconnectedbledevices-1) | Obtains the list of devices in the connected status. |
| [off('BLEDeviceFind')](arkts-connectivity-ble-off-f.md#offbledevicefind) | Unsubscribe BLE scan result. |
| [on('BLEDeviceFind')](arkts-connectivity-ble-on-f.md#onbledevicefind) | Subscribe BLE scan result. |
| [startBLEScan](arkts-connectivity-ble-startblescan-f.md#startblescan-1) | Starts scanning for specified BLE devices with filters. |
| [stopBLEScan](arkts-connectivity-ble-stopblescan-f.md#stopblescan-1) | Stops BLE scanning. |
