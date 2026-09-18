# BluetoothScanResult

Describes the contents of the bluetooth scan results.

**Since:** 16

**System capability:** SystemCapability.Location.Location.Core

## Modules to Import

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
```

## connectable

```TypeScript
connectable: boolean
```

Connectable of the scanned device

**Type:** boolean

**Since:** 16

**System capability:** SystemCapability.Location.Location.Core

## data

```TypeScript
data?: ArrayBuffer
```

The raw data of broadcast packet

**Type:** ArrayBuffer

**Since:** 16

**System capability:** SystemCapability.Location.Location.Core

## deviceId

```TypeScript
deviceId: string
```

Address of the scanned device

**Type:** string

**Since:** 16

**System capability:** SystemCapability.Location.Location.Core

## deviceName

```TypeScript
deviceName: string
```

The local name of the scanned device

**Type:** string

**Since:** 16

**System capability:** SystemCapability.Location.Location.Core

## rssi

```TypeScript
rssi: number
```

RSSI of the scanned device

**Type:** number

**Since:** 16

**System capability:** SystemCapability.Location.Location.Core
