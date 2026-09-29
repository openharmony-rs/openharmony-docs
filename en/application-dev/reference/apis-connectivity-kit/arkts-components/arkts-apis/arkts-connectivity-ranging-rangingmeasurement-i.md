# RangingMeasurement

```TypeScript
interface RangingMeasurement
```

Describes the measurement result.

**Since:** 26.0.0

<!--Device-ranging-interface RangingMeasurement--><!--Device-ranging-interface RangingMeasurement-End-->

**System capability:** SystemCapability.Communication.FusionConnectivity.Core

## Modules to Import

```TypeScript
import { ranging } from '@kit.ConnectivityKit';
```

## confidence

```TypeScript
confidence: RangingConfidence
```

Confidence level of measurement results.

**Type:** [RangingConfidence](arkts-connectivity-ranging-rangingconfidence-e.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-RangingMeasurement-confidence: RangingConfidence--><!--Device-RangingMeasurement-confidence: RangingConfidence-End-->

**System capability:** SystemCapability.Communication.FusionConnectivity.Core

## value

```TypeScript
value: number
```

Measurement result value. The value is expressed in centimeters.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-RangingMeasurement-value: int--><!--Device-RangingMeasurement-value: int-End-->

**System capability:** SystemCapability.Communication.FusionConnectivity.Core
