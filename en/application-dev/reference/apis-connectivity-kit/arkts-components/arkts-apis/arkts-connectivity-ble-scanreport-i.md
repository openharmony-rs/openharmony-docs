# ScanReport

```TypeScript
interface ScanReport
```

Describes the contents of the scan report.

**Since:** 15

<!--Device-ble-interface ScanReport--><!--Device-ble-interface ScanReport-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## Modules to Import

```TypeScript
import { ble } from '@kit.ConnectivityKit';
```

## reportType

```TypeScript
reportType: ScanReportType
```

The type of scan report

**Type:** [ScanReportType](arkts-connectivity-ble-scanreporttype-e.md)

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 15.

<!--Device-ScanReport-reportType: ScanReportType--><!--Device-ScanReport-reportType: ScanReportType-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## scanResult

```TypeScript
scanResult: Array<ScanResult>
```

Describes the contents of the scan results.

**Type:** Array&lt;[ScanResult](arkts-connectivity-ble-scanresult-i.md)&gt;

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 15.

<!--Device-ScanReport-scanResult: Array<ScanResult>--><!--Device-ScanReport-scanResult: Array<ScanResult>-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core
