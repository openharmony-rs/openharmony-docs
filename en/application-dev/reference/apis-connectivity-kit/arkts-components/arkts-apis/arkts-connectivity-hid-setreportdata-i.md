# SetReportData

```TypeScript
interface SetReportData
```

Describe the SET_REPORT data is received from remote host.

**Since:** 23

<!--Device-hid-interface SetReportData--><!--Device-hid-interface SetReportData-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## Modules to Import

```TypeScript
import { hid } from '@kit.ConnectivityKit';
```

## data

```TypeScript
data: Uint8Array
```

data of SET_REPORT data.

**Type:** Uint8Array

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-SetReportData-data: Uint8Array--><!--Device-SetReportData-data: Uint8Array-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## id

```TypeScript
id: number
```

id of SET_REPORT data.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-SetReportData-id: int--><!--Device-SetReportData-id: int-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## type

```TypeScript
type: ReportType
```

reportType of SET_REPORT data.

**Type:** [ReportType](arkts-connectivity-hid-reporttype-e.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-SetReportData-type: ReportType--><!--Device-SetReportData-type: ReportType-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core
