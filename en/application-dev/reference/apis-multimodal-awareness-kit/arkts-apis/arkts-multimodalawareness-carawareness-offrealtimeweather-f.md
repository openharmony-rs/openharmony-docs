# offRealTimeWeather

## Modules to Import

```TypeScript
import { carAwareness } from '@kit.MultimodalAwarenessKit';
```

## offRealTimeWeather

```TypeScript
function offRealTimeWeather(callback?: Callback<RealTimeWeatherInfo>): void
```

Unsubscribes from real-time weather results.

**Since:** 26.0.1

**Required permissions:** ohos.permission.vehicle.MMA_WEATHER

**Model restriction:** This API can be used only in the stage model.

<!--Device-carAwareness-function offRealTimeWeather(callback?: Callback<RealTimeWeatherInfo>): void--><!--Device-carAwareness-function offRealTimeWeather(callback?: Callback<RealTimeWeatherInfo>): void-End-->

**System capability:** SystemCapability.MultimodalAwareness.CarAwareness

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[RealTimeWeatherInfo](arkts-multimodalawareness-carawareness-realtimeweatherinfo-i.md)&gt; | No | Callback for the real-time weather event. If a specific callback is passed in, only the corresponding listener is unregistered; otherwise, all listeners are unregistered. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [34000001](../errorcode-carAwareness.md#34000001-service-exception) | Service exception. |
