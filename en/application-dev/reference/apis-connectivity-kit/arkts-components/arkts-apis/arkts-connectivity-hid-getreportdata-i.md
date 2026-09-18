# GetReportData

Describe the GET_REPORT data is received from remote host.

@typedef GetReportData

**Since:** 23

**System capability:** SystemCapability.Communication.Bluetooth.Core

## Modules to Import

```TypeScript
import { hid } from '@kit.ConnectivityKit';
```

## bufferSize

```TypeScript
bufferSize: number
```

bufferSize of GET_REPORT data, maximum number of octets to transfer during data phase.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.Bluetooth.Core

## id

```TypeScript
id: number
```

id of GET_REPORT data.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.Bluetooth.Core

## type

```TypeScript
type: ReportType
```

reportType of GET_REPORT data.

**Type:** [ReportType](arkts-connectivity-hid-reporttype-e.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.Bluetooth.Core
