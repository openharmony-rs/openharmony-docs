# ScanOptions

```TypeScript
interface ScanOptions
```

Describes the parameters for scan.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [ScanOptions](arkts-connectivity-bluetoothmanager-scanoptions-i.md)

<!--Device-bluetooth-interface ScanOptions--><!--Device-bluetooth-interface ScanOptions-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## Modules to Import

```TypeScript
import { bluetooth } from '@kit.ConnectivityKit';
```

## dutyMode

```TypeScript
dutyMode?: ScanDuty
```

Bluetooth LE scan mode

**Type:** [ScanDuty](arkts-connectivity-bluetooth-scanduty-e.md)

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [dutyMode](arkts-connectivity-bluetoothmanager-scanoptions-i.md#dutymode)

<!--Device-ScanOptions-dutyMode?: ScanDuty--><!--Device-ScanOptions-dutyMode?: ScanDuty-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## interval

```TypeScript
interval?: number
```

Time of delay for reporting the scan result

**Type:** number

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [interval](arkts-connectivity-bluetoothmanager-scanoptions-i.md#interval)

<!--Device-ScanOptions-interval?: number--><!--Device-ScanOptions-interval?: number-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## matchMode

```TypeScript
matchMode?: MatchMode
```

Match mode for Bluetooth LE scan filters hardware match

**Type:** [MatchMode](arkts-connectivity-bluetooth-matchmode-e.md)

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [matchMode](arkts-connectivity-bluetoothmanager-scanoptions-i.md#matchmode)

<!--Device-ScanOptions-matchMode?: MatchMode--><!--Device-ScanOptions-matchMode?: MatchMode-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core
