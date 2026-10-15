# RealTimeWeatherInfo

```TypeScript
export interface RealTimeWeatherInfo
```

Interface for real-time weather response info.

**Since:** 26.0.1

<!--Device-carAwareness-export interface RealTimeWeatherInfo--><!--Device-carAwareness-export interface RealTimeWeatherInfo-End-->

**System capability:** SystemCapability.MultimodalAwareness.CarAwareness

## Modules to Import

```TypeScript
import { carAwareness } from '@kit.MultimodalAwarenessKit';
```

## timestamp

```TypeScript
timestamp: number
```

Timestamp of the recognition result. Unit: ms.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-RealTimeWeatherInfo-timestamp: number--><!--Device-RealTimeWeatherInfo-timestamp: number-End-->

**System capability:** SystemCapability.MultimodalAwareness.CarAwareness

## weather

```TypeScript
weather: number
```

Weather status.  
- 1: Invalid  
0: Other 1: Fog 2: Dense fog 3: Snow 4: Heavy snow 5: Rain 6: Heavy rain.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-RealTimeWeatherInfo-weather: number--><!--Device-RealTimeWeatherInfo-weather: number-End-->

**System capability:** SystemCapability.MultimodalAwareness.CarAwareness
