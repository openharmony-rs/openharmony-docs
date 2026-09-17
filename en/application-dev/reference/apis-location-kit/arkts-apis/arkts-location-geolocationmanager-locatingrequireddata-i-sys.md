# LocatingRequiredData (System API)

Describes the structure of the data required for locating.

**Since:** 10

**System capability:** SystemCapability.Location.Location.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
```

## bluetoothData

```TypeScript
bluetoothData?: BluetoothScanInfo
```

Bluetooth scan info.

**Type:** [BluetoothScanInfo](arkts-location-geolocationmanager-bluetoothscaninfo-i-sys.md)

**Since:** 10

**System capability:** SystemCapability.Location.Location.Core

**System API:** This is a system API.

## campedCellInfo

```TypeScript
campedCellInfo?: CellInfo
```

Indicates camped cell information.

**Type:** [CellInfo](arkts-location-geolocationmanager-cellinfo-i-sys.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Location.Location.Core

**System API:** This is a system API.

## neighboringCellInfo

```TypeScript
neighboringCellInfo?: CellInfo[]
```

Indicates neighboring cell information.

**Type:** [CellInfo](arkts-location-geolocationmanager-cellinfo-i-sys.md)[]

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Location.Location.Core

**System API:** This is a system API.

## slotId

```TypeScript
slotId?: number
```

Indicates the card slot index number. The value should be an integer.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Location.Location.Core

**System API:** This is a system API.

## wifiData

```TypeScript
wifiData?: WifiScanInfo
```

WiFi scan info.

**Type:** [WifiScanInfo](arkts-location-geolocationmanager-wifiscaninfo-i-sys.md)

**Since:** 10

**System capability:** SystemCapability.Location.Location.Core

**System API:** This is a system API.
