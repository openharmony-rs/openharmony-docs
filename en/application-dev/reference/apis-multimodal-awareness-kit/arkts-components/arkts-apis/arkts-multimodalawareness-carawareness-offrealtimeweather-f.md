# offRealTimeWeather

## Modules to Import

```TypeScript
import { carAwareness } from '@kit.MultimodalAwarenessKit';
```

## offRealTimeWeather

```TypeScript
function offRealTimeWeather(callback?: Callback<RealTimeWeatherInfo>): void
```

Disables the real-time weather awareness function.

**Since:** 26.0.1

**Required permissions:** ohos.permission.vehicle.MMA_WEATHER

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MultimodalAwareness.CarAwareness

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[RealTimeWeatherInfo](arkts-multimodalawareness-carawareness-realtimeweatherinfo-i.md)&gt; | No | Callback for obtaining the capability data. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [34000001](../errorcode-carAwareness.md#34000001-service-exception) | Service exception. |
