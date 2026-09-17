# @ohos.multimodalAwareness.carAwareness

This module provides the capability to use car awareness

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MultimodalAwareness.CarAwareness

## Modules to Import

```TypeScript
import { carAwareness } from '@kit.MultimodalAwarenessKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getAllCapabilityList](arkts-multimodalawareness-carawareness-getallcapabilitylist-f.md) | Returns the list of all capabilities. |
| [offRealTimeWeather](arkts-multimodalawareness-carawareness-offrealtimeweather-f.md) | Disables the real-time weather awareness function. |
| [offRefueling](arkts-multimodalawareness-carawareness-offrefueling-f.md) | Disables refueling awareness. |
| [offSpatialMotion](arkts-multimodalawareness-carawareness-offspatialmotion-f.md) | Disables spatial motion awareness and subscribes to spatial motion awareness results. |
| [onRealTimeWeather](arkts-multimodalawareness-carawareness-onrealtimeweather-f.md) | Enables real-time weather awareness and subscribes to real-time weather awareness results. If the capability is not supported, no callback will be triggered. You can obtain the supported capabilities by calling the getAllCapacityList method. |
| [onRefueling](arkts-multimodalawareness-carawareness-onrefueling-f.md) | Enables refueling awareness and subscribes to refueling awareness results. If this function is not supported, no callback will be triggered. You can obtain the supported capabilities by calling the getAllCapacityList method. |
| [onSpatialMotion](arkts-multimodalawareness-carawareness-onspatialmotion-f.md) | Enables spatial motion awareness and subscribes to spatial motion awareness results. If the capability is not supported, no callback will be triggered. You can obtain the supported capabilities by calling the getAllCapacityList method. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [getCarAwareness](arkts-multimodalawareness-carawareness-getcarawareness-f-sys.md) | /** Disables vehicle awareness and subscribes to vehicle awareness results. |
| [offCarAwareness](arkts-multimodalawareness-carawareness-offcarawareness-f-sys.md) | Unsubscribes from vehicle sensing results. |
| [onCarAwareness](arkts-multimodalawareness-carawareness-oncarawareness-f-sys.md) | Enables vehicle awareness and subscribes to vehicle awareness results. If this function is not supported, no callback will be triggered. You can use the getAllCapacityList method to obtain the supported capabilities. |
| [updateSpatialActionEnableStatus](arkts-multimodalawareness-carawareness-updatespatialactionenablestatus-f-sys.md) | Updates the awareness enabling event when the app subscribes to the function. |
| [updateSpatialActionZone](arkts-multimodalawareness-carawareness-updatespatialactionzone-f-sys.md) | Updates the voice zone when the voice subscribes to the spatial point engine capability. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [RealTimeWeatherInfo](arkts-multimodalawareness-carawareness-realtimeweatherinfo-i.md) | Interface for realtime weather response info. |
| [RefuelingInfo](arkts-multimodalawareness-carawareness-refuelinginfo-i.md) | Interface for refueling response info. |
| [SpatialMotionInfo](arkts-multimodalawareness-carawareness-spatialmotioninfo-i.md) | Interface for spatial motion response info. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [CarAwarenessInfo](arkts-multimodalawareness-carawareness-carawarenessinfo-i-sys.md) | Interface for car awareness response info. |
| [CarAwarenessOptions](arkts-multimodalawareness-carawareness-carawarenessoptions-i-sys.md) | Interface for car awareness information |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [Capability](arkts-multimodalawareness-carawareness-capability-e.md) | CarAwareness Capability. |

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [Capability](arkts-multimodalawareness-carawareness-capability-e-sys.md) | CarAwareness Capability. |
<!--DelEnd-->
