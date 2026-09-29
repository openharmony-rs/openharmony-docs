# ScanResult

```TypeScript
interface ScanResult
```

Describes the contents of the scan results.

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [ScanResult](arkts-connectivity-ble-scanresult-i.md)

<!--Device-bluetoothManager-interface ScanResult--><!--Device-bluetoothManager-interface ScanResult-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## Modules to Import

```TypeScript
import { bluetoothManager } from '@kit.ConnectivityKit';
```

## data

```TypeScript
data: ArrayBuffer
```

The raw data of broadcast packet

**Type:** ArrayBuffer

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [data](arkts-connectivity-ble-scanresult-i.md#data)

<!--Device-ScanResult-data: ArrayBuffer--><!--Device-ScanResult-data: ArrayBuffer-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## deviceId

```TypeScript
deviceId: string
```

Address of the scanned device

**Type:** string

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [deviceId](arkts-connectivity-ble-scanresult-i.md#deviceid)

<!--Device-ScanResult-deviceId: string--><!--Device-ScanResult-deviceId: string-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## rssi

```TypeScript
rssi: number
```

RSSI of the remote device

**Type:** number

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [rssi](arkts-connectivity-ble-scanresult-i.md#rssi)

<!--Device-ScanResult-rssi: number--><!--Device-ScanResult-rssi: number-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core
