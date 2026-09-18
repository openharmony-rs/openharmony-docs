# @ohos.multimodalAwareness.spatialAwareness

This module provides the capability to subscribe to report the distance measurement result. @namespace spatialAwareness

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MultimodalAwareness.DistanceMeasurement

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { spatialAwareness } from '@kit.MultimodalAwarenessKit';
```

## Summary

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [offDistanceMeasure](arkts-multimodalawareness-spatialawareness-offdistancemeasure-f-sys.md) | Unsubscribe from distance measurement result data. |
| [offIndoorOrOutdoorIdentify](arkts-multimodalawareness-spatialawareness-offindoororoutdooridentify-f-sys.md) | Unsubscribe from the results of indoor and outdoor recognition. |
| [onDistanceMeasure](arkts-multimodalawareness-spatialawareness-ondistancemeasure-f-sys.md) | Subscribe to distance measurement result data. |
| [onIndoorOrOutdoorIdentify](arkts-multimodalawareness-spatialawareness-onindoororoutdooridentify-f-sys.md) | Subscribe to the results of indoorand outdoor identification. |
<!--DelEnd-->

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [DistanceMeasurementConfigParams](arkts-multimodalawareness-spatialawareness-distancemeasurementconfigparams-i-sys.md) | Configuration parameters for the distance measurement interface @interface DistanceMeasurementConfigParams |
| [DistanceMeasurementResponse](arkts-multimodalawareness-spatialawareness-distancemeasurementresponse-i-sys.md) | Interface for distance measurement result @interface DistanceMeasurementResponse |
| [DoorPositionResponse](arkts-multimodalawareness-spatialawareness-doorpositionresponse-i-sys.md) | Interface for indoor or outdoor identify result @interface DoorPositionResponse |
<!--DelEnd-->

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [DistanceRank](arkts-multimodalawareness-spatialawareness-distancerank-e-sys.md) | Enum for distance rank. |
| [PositionRelativeToDoor](arkts-multimodalawareness-spatialawareness-positionrelativetodoor-e-sys.md) | Enum for identification result inside and outside the door |
| [ReportingMode](arkts-multimodalawareness-spatialawareness-reportingmode-e-sys.md) | Enum for distance measurement result reporting modes. @enum { int } ReportingMode |
| [TechnologyType](arkts-multimodalawareness-spatialawareness-technologytype-e-sys.md) | Enum for distance measurement technology types. |
<!--DelEnd-->
