# ScanResult

```TypeScript
interface ScanResult
```

Describes the contents of the scan results.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [ScanResult](arkts-connectivity-bluetoothmanager-scanresult-i.md)

<!--Device-bluetooth-interface ScanResult--><!--Device-bluetooth-interface ScanResult-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## Modules to Import

```TypeScript
import { bluetooth } from '@kit.ConnectivityKit';
```

## data

```TypeScript
data: ArrayBuffer
```

The raw data of broadcast packet

**Type:** ArrayBuffer

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [data](arkts-connectivity-bluetoothmanager-scanresult-i.md#data)

<!--Device-ScanResult-data: ArrayBuffer--><!--Device-ScanResult-data: ArrayBuffer-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## deviceId

```TypeScript
deviceId: string
```

Address of the scanned device

**Type:** string

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [deviceId](arkts-connectivity-bluetoothmanager-scanresult-i.md#deviceid)

<!--Device-ScanResult-deviceId: string--><!--Device-ScanResult-deviceId: string-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## rssi

```TypeScript
rssi: number
```

RSSI of the remote device

**Type:** number

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [rssi](arkts-connectivity-bluetoothmanager-scanresult-i.md#rssi)

<!--Device-ScanResult-rssi: number--><!--Device-ScanResult-rssi: number-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core
