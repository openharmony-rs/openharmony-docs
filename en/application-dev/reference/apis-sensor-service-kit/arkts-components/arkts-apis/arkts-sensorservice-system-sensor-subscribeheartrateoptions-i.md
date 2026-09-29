# SubscribeHeartRateOptions

```TypeScript
export interface SubscribeHeartRateOptions
```

Configures the parameters for subscribing to the heart rate sensor, including the callback function. The callback frequency of heart rate data is fixed at 5 seconds per time and cannot be configured using the interval parameter.

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [HEART_RATE](arkts-sensorservice-sensor-sensorid-e.md#heart_rate)

**Required permissions:** ohos.permission.READ_HEALTH_DATA

<!--Device-unnamed-export interface SubscribeHeartRateOptions--><!--Device-unnamed-export interface SubscribeHeartRateOptions-End-->

**System capability:** SystemCapability.Sensors.Sensor.Lite

## Modules to Import

```TypeScript
import { Sensor, AccelerometerResponse, BarometerResponse, CompassResponse, DeviceOrientationResponse, GetOnBodyStateOptions, GyroscopeResponse, HeartRateResponse, LightResponse, OnBodyStateResponse, ProximityResponse, StepCounterResponse, SubscribeBarometerOptions, SubscribeCompassOptions, SubscribeDeviceOrientationOptions, SubscribeGyroscopeOptions, SubscribeHeartRateOptions, SubscribeLightOptions, SubscribeOnBodyStateOptions, SubscribeProximityOptions, SubscribeStepCounterOptions, subscribeAccelerometerOptions } from '@kit.SensorServiceKit';
```

## fail

```TypeScript
fail?: (data: string, code: number) => void
```

Callback invoked when an API call fails. The callback parameters are **data** of the string type and **code** of the number type, where **data** indicates the error information and **code** indicates the error code. If this parameter is not specified, no callback notification is sent when the API call fails.

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [on](arkts-sensorservice-sensor-on-f.md)

**Required permissions:** ohos.permission.READ_HEALTH_DATA

**Model restriction:** This API can be used only in the FA model.

<!--Device-SubscribeHeartRateOptions-fail?: (data: string, code: number) => void--><!--Device-SubscribeHeartRateOptions-fail?: (data: string, code: number) => void-End-->

**System capability:** SystemCapability.Sensors.Sensor.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | string | Yes |  |
| code | number | Yes |  |

## success

```TypeScript
success: (data: HeartRateResponse) => void
```

Callback invoked when the heart rate sensor data changes. The callback parameter is a **HeartRateResponse** object. The callback frequency is fixed at 5 seconds.

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [on](arkts-sensorservice-sensor-on-f.md)

**Required permissions:** ohos.permission.READ_HEALTH_DATA

**Model restriction:** This API can be used only in the FA model.

<!--Device-SubscribeHeartRateOptions-success: (data: HeartRateResponse) => void--><!--Device-SubscribeHeartRateOptions-success: (data: HeartRateResponse) => void-End-->

**System capability:** SystemCapability.Sensors.Sensor.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | [HeartRateResponse](arkts-sensorservice-system-sensor-heartrateresponse-i.md) | Yes |  |
