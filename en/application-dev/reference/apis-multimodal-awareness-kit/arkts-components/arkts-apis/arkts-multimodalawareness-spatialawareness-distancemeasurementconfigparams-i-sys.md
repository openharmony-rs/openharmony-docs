# DistanceMeasurementConfigParams (System API)

```TypeScript
export interface DistanceMeasurementConfigParams
```

Configuration parameters for the distance measurement interface @interface DistanceMeasurementConfigParams

**Since:** 23

<!--Device-spatialAwareness-export interface DistanceMeasurementConfigParams--><!--Device-spatialAwareness-export interface DistanceMeasurementConfigParams-End-->

**System capability:** SystemCapability.MultimodalAwareness.DistanceMeasurement

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { spatialAwareness } from '@kit.MultimodalAwarenessKit';
```

## deviceList

```TypeScript
deviceList: string[]
```

distance measurement supported devices list

**Type:** string[]

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-DistanceMeasurementConfigParams-deviceList: string[]--><!--Device-DistanceMeasurementConfigParams-deviceList: string[]-End-->

**System capability:** SystemCapability.MultimodalAwareness.DistanceMeasurement

**System API:** This is a system API.

## reportFrequency

```TypeScript
reportFrequency: number
```

distance measurement result reporting frequency

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-DistanceMeasurementConfigParams-reportFrequency: int--><!--Device-DistanceMeasurementConfigParams-reportFrequency: int-End-->

**System capability:** SystemCapability.MultimodalAwareness.DistanceMeasurement

**System API:** This is a system API.

## reportMode

```TypeScript
reportMode: ReportingMode
```

distance measurement result reporting mode

**Type:** [ReportingMode](arkts-multimodalawareness-spatialawareness-reportingmode-e-sys.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-DistanceMeasurementConfigParams-reportMode: ReportingMode--><!--Device-DistanceMeasurementConfigParams-reportMode: ReportingMode-End-->

**System capability:** SystemCapability.MultimodalAwareness.DistanceMeasurement

**System API:** This is a system API.

## techType

```TypeScript
techType: TechnologyType
```

distance measurement technology type

**Type:** [TechnologyType](arkts-multimodalawareness-spatialawareness-technologytype-e-sys.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-DistanceMeasurementConfigParams-techType: TechnologyType--><!--Device-DistanceMeasurementConfigParams-techType: TechnologyType-End-->

**System capability:** SystemCapability.MultimodalAwareness.DistanceMeasurement

**System API:** This is a system API.
