# ScanOptions

```TypeScript
interface ScanOptions
```

Describes the parameters for scan.

**Since:** 10

<!--Device-ble-interface ScanOptions--><!--Device-ble-interface ScanOptions-End-->

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

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ScanOptions-dutyMode?: ScanDuty--><!--Device-ScanOptions-dutyMode?: ScanDuty-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## interval

```TypeScript
interval?: number
```

Time of delay for reporting the scan result

**Type:** number

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ScanOptions-interval?: int--><!--Device-ScanOptions-interval?: int-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## isExtended

```TypeScript
isExtended?: boolean
```

Indicates whether the scan is extended, default is `false`

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-ScanOptions-isExtended?: boolean--><!--Device-ScanOptions-isExtended?: boolean-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## matchMode

```TypeScript
matchMode?: MatchMode
```

Match mode for Bluetooth LE scan filters hardware match

**Type:** [MatchMode](arkts-connectivity-ble-matchmode-e.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ScanOptions-matchMode?: MatchMode--><!--Device-ScanOptions-matchMode?: MatchMode-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## phyType

```TypeScript
phyType?: PhyType
```

Physical Layer used during scan.

**Type:** [PhyType](arkts-connectivity-ble-phytype-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ScanOptions-phyType?: PhyType--><!--Device-ScanOptions-phyType?: PhyType-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## reportMode

```TypeScript
reportMode?: ScanReportMode
```

Report mode used during scan.

**Type:** [ScanReportMode](arkts-connectivity-ble-scanreportmode-e.md)

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 15.

<!--Device-ScanOptions-reportMode?: ScanReportMode--><!--Device-ScanOptions-reportMode?: ScanReportMode-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core
