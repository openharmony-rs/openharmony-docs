# @ohos.multimodalAwareness.carAwareness(Car awareness)

This module provides car awareness capabilities, including spatial motion interaction, real-time weather recognition, and refueling status recognition.

**Since:** 26.0.1

<!--Device-unnamed-declare namespace carAwareness--><!--Device-unnamed-declare namespace carAwareness-End-->

**System capability:** SystemCapability.MultimodalAwareness.CarAwareness

## Modules to Import

```TypeScript
import { carAwareness } from '@kit.MultimodalAwarenessKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getAllCapabilityList](arkts-multimodalawareness-carawareness-getallcapabilitylist-f.md#getallcapabilitylist) | Obtains the list of all car awareness capabilities supported by the current device. |
| [offRealTimeWeather](arkts-multimodalawareness-carawareness-offrealtimeweather-f.md#offrealtimeweather) | Unsubscribes from real-time weather results. |
| [offRefueling](arkts-multimodalawareness-carawareness-offrefueling-f.md#offrefueling) | Unsubscribes from the refueling status result. |
| [offSpatialMotion](arkts-multimodalawareness-carawareness-offspatialmotion-f.md#offspatialmotion) | Unsubscribes from spatial motion results. |
| [onRealTimeWeather](arkts-multimodalawareness-carawareness-onrealtimeweather-f.md#onrealtimeweather) | Subscribes to real-time weather awareness results. If the device does not support this capability, error code 34000002 is thrown. You can obtain the supported capabilities by calling the getAllCapabilityList method. The data is returned asynchronously through the callback. |
| [onRefueling](arkts-multimodalawareness-carawareness-onrefueling-f.md#onrefueling) | Subscribes to the refueling status awareness result. If the device does not support this capability, error code 34000002 is thrown. You can obtain the supported capabilities by calling the getAllCapabilityList method. The data is returned asynchronously through the callback. |
| [onSpatialMotion](arkts-multimodalawareness-carawareness-onspatialmotion-f.md#onspatialmotion) | Subscribes to spatial motion awareness results. If the device does not support this capability, error code 34000002 is thrown. You can obtain the supported capabilities by calling the getAllCapabilityList method. The data is returned asynchronously through the callback. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [getCarAwareness](arkts-multimodalawareness-carawareness-getcarawareness-f-sys.md#getcarawareness) | Obtains the car awareness result of the specified type once. |
| [offCarAwareness](arkts-multimodalawareness-carawareness-offcarawareness-f-sys.md#offcarawareness) | Unsubscribes from the specific car awareness capability result. |
| [onCarAwareness](arkts-multimodalawareness-carawareness-oncarawareness-f-sys.md#oncarawareness) | Subscribes to car awareness results. If the device does not support the capability, error code 34000002 is thrown. You can obtain the supported capabilities by calling the getAllCapabilityList method. The data is returned asynchronously through the callback. |
| [updateSpatialActionEnableStatus](arkts-multimodalawareness-carawareness-updatespatialactionenablestatus-f-sys.md#updatespatialactionenablestatus) | Updates the start/stop status of spatial action awareness. |
| [updateSpatialActionZone](arkts-multimodalawareness-carawareness-updatespatialactionzone-f-sys.md#updatespatialactionzone) | Updates the voice zone information for spatial action awareness. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [RealTimeWeatherInfo](arkts-multimodalawareness-carawareness-realtimeweatherinfo-i.md) | Interface for real-time weather response info. |
| [RefuelingInfo](arkts-multimodalawareness-carawareness-refuelinginfo-i.md) | Interface for refueling response info. |
| [SpatialMotionInfo](arkts-multimodalawareness-carawareness-spatialmotioninfo-i.md) | Interface for spatial motion response info. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [CarAwarenessInfo](arkts-multimodalawareness-carawareness-carawarenessinfo-i-sys.md) | Interface for general car awareness response info. |
| [CarAwarenessOptions](arkts-multimodalawareness-carawareness-carawarenessoptions-i-sys.md) | Interface for car awareness subscription options. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [Capability](arkts-multimodalawareness-carawareness-capability-e.md) | Enumerates the capability types supported by car awareness. |

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [Capability](arkts-multimodalawareness-carawareness-capability-e-sys.md) | Enumerates the capability types supported by car awareness. |
<!--DelEnd-->
