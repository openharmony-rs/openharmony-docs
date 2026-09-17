# BLE

Provides methods to operate or manage Bluetooth.

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [ble/ble](arkts-connectivity-bluetooth-ble.md)

**System capability:** SystemCapability.Communication.Bluetooth.Core

## Modules to Import

```TypeScript
import { bluetoothManager } from '@kit.ConnectivityKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [createGattServer](arkts-connectivity-ble-creategattserver-f.md) | create a JavaScript Gatt server instance. |
| [createGattClientDevice](arkts-connectivity-ble-creategattclientdevice-f.md) | create a JavaScript Gatt client device instance. |
| [getConnectedBLEDevices](arkts-connectivity-ble-getconnectedbledevices-f.md) | Obtains the list of devices in the connected status. On API 10 and above, the permission required by this interface is changed from USE_BLUETOOTH to ACCESS_BLUETOOTH. |
| [startBLEScan](arkts-connectivity-ble-startblescan-f.md) | Starts scanning for specified BLE devices with filters. On API 10 and above, the permission required by this interface is changed from DISCOVER_BLUETOOTH and MANAGE_BLUETOOTH and LOCATION to ACCESS_BLUETOOTH. |
| [stopBLEScan](arkts-connectivity-ble-stopblescan-f.md) | Stops BLE scanning. On API 10 and above, the permission required by this interface is changed from DISCOVER_BLUETOOTH to ACCESS_BLUETOOTH. |
| [on](arkts-connectivity-ble-on-f.md#onbledevicefind) | Subscribe BLE scan result. On API 10 and above, the permission required by this interface is changed from USE_BLUETOOTH to ACCESS_BLUETOOTH. |
| [off](arkts-connectivity-ble-off-f.md#offbledevicefind) | Unsubscribe BLE scan result. On API 10 and above, the permission required by this interface is changed from USE_BLUETOOTH to ACCESS_BLUETOOTH. |
