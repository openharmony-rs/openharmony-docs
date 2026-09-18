# DistanceMeasurementResponse (System API)

Interface for distance measurement result @interface DistanceMeasurementResponse

**Since:** 23

**System capability:** SystemCapability.MultimodalAwareness.DistanceMeasurement

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { spatialAwareness } from '@kit.MultimodalAwarenessKit';
```

## confidence

```TypeScript
confidence: float
```

indicates confidence of distance measurement

**Type:** float

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MultimodalAwareness.DistanceMeasurement

**System API:** This is a system API.

## deviceId

```TypeScript
deviceId: string
```

indicates the ID of the remote ranging device

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MultimodalAwareness.DistanceMeasurement

**System API:** This is a system API.

## distance

```TypeScript
distance: float
```

indicates distance result

**Type:** float

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MultimodalAwareness.DistanceMeasurement

**System API:** This is a system API.

## rank

```TypeScript
rank: DistanceRank
```

indicates distance rank

**Type:** [DistanceRank](arkts-multimodalawareness-spatialawareness-distancerank-e-sys.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MultimodalAwareness.DistanceMeasurement

**System API:** This is a system API.
