# ScanOptions

Describes the parameters for scan.

**Since:** 10

**System capability:** SystemCapability.Communication.Bluetooth.Core

## Modules to Import

```TypeScript
import { ble } from '@kit.ConnectivityKit';
```

## dutyMode

```TypeScript
dutyMode?: ScanDuty
```

Bluetooth LE scan mode

**Type:** [ScanDuty](arkts-connectivity-ble-scanduty-e.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.Bluetooth.Core

## interval

```TypeScript
interval?: number
```

Time of delay for reporting the scan result

**Type:** number

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.Bluetooth.Core

## isExtended

```TypeScript
isExtended?: boolean
```

Indicates whether the scan is extended, default is `false`

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Communication.Bluetooth.Core

## matchMode

```TypeScript
matchMode?: MatchMode
```

Match mode for Bluetooth LE scan filters hardware match

**Type:** [MatchMode](arkts-connectivity-ble-matchmode-e.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.Bluetooth.Core

## phyType

```TypeScript
phyType?: PhyType
```

Physical Layer used during scan.

**Type:** [PhyType](arkts-connectivity-ble-phytype-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.Bluetooth.Core

## reportMode

```TypeScript
reportMode?: ScanReportMode
```

Report mode used during scan.

**Type:** [ScanReportMode](arkts-connectivity-ble-scanreportmode-e.md)

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.Communication.Bluetooth.Core
