# ScanOptions

```TypeScript
interface ScanOptions
```

Represents the scan options.

**Since:** 26.0.0

<!--Device-scan-interface ScanOptions--><!--Device-scan-interface ScanOptions-End-->

**System capability:** SystemCapability.Communication.NearLink.Base

## Modules to Import

```TypeScript
import { scan } from '@kit.ConnectivityKit';
```

## duration

```TypeScript
duration?: number
```

Scan duration, in seconds. The value range is The value should be an integer.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ScanOptions-duration?: int--><!--Device-ScanOptions-duration?: int-End-->

**System capability:** SystemCapability.Communication.NearLink.Base

## scanMode

```TypeScript
scanMode?: ScanMode
```

Scan mode. The default value is **'SCAN_MODE_LOW_POWER'**.

**Type:** [ScanMode](arkts-connectivity-scan-scanmode-e.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ScanOptions-scanMode?: ScanMode--><!--Device-ScanOptions-scanMode?: ScanMode-End-->

**System capability:** SystemCapability.Communication.NearLink.Base
