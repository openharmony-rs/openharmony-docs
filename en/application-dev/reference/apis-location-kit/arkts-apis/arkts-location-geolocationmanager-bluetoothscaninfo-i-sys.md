# BluetoothScanInfo (System API)

```TypeScript
export interface BluetoothScanInfo
```

Describes the contents of the Bluetooth scan results.

**Since:** 10

<!--Device-geoLocationManager-export interface BluetoothScanInfo--><!--Device-geoLocationManager-export interface BluetoothScanInfo-End-->

**System capability:** SystemCapability.Location.Location.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
```

## deviceName

```TypeScript
deviceName: string
```

The local name of the device.

**Type:** string

**Since:** 10

<!--Device-BluetoothScanInfo-deviceName: string--><!--Device-BluetoothScanInfo-deviceName: string-End-->

**System capability:** SystemCapability.Location.Location.Core

**System API:** This is a system API.

## macAddress

```TypeScript
macAddress: string
```

Mac address of the scanned device.

**Type:** string

**Since:** 10

<!--Device-BluetoothScanInfo-macAddress: string--><!--Device-BluetoothScanInfo-macAddress: string-End-->

**System capability:** SystemCapability.Location.Location.Core

**System API:** This is a system API.

## rssi

```TypeScript
rssi: number
```

RSSI of the remote device.

**Type:** number

**Since:** 10

<!--Device-BluetoothScanInfo-rssi: int--><!--Device-BluetoothScanInfo-rssi: int-End-->

**System capability:** SystemCapability.Location.Location.Core

**System API:** This is a system API.

## timestamp

```TypeScript
timestamp: number
```

Time stamp.

**Type:** number

**Since:** 10

<!--Device-BluetoothScanInfo-timestamp: long--><!--Device-BluetoothScanInfo-timestamp: long-End-->

**System capability:** SystemCapability.Location.Location.Core

**System API:** This is a system API.
