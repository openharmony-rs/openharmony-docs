# ScanOptions

```TypeScript
interface ScanOptions
```

Describes the parameters for scan.

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [ScanOptions](arkts-connectivity-ble-scanoptions-i.md)

<!--Device-bluetoothManager-interface ScanOptions--><!--Device-bluetoothManager-interface ScanOptions-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## Modules to Import

```TypeScript
import { bluetoothManager } from '@kit.ConnectivityKit';
```

## dutyMode

```TypeScript
dutyMode?: ScanDuty
```

Bluetooth LE scan mode

**Type:** [ScanDuty](arkts-connectivity-bluetoothmanager-scanduty-e.md)

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [dutyMode](arkts-connectivity-ble-scanoptions-i.md#dutymode)

<!--Device-ScanOptions-dutyMode?: ScanDuty--><!--Device-ScanOptions-dutyMode?: ScanDuty-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## interval

```TypeScript
interval?: number
```

Time of delay for reporting the scan result

**Type:** number

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [interval](arkts-connectivity-ble-scanoptions-i.md#interval)

<!--Device-ScanOptions-interval?: number--><!--Device-ScanOptions-interval?: number-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## matchMode

```TypeScript
matchMode?: MatchMode
```

Match mode for Bluetooth LE scan filters hardware match

**Type:** [MatchMode](arkts-connectivity-bluetoothmanager-matchmode-e.md)

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [matchMode](arkts-connectivity-ble-scanoptions-i.md#matchmode)

<!--Device-ScanOptions-matchMode?: MatchMode--><!--Device-ScanOptions-matchMode?: MatchMode-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core
