# SubscribeGyroscopeOptions

```TypeScript
export interface SubscribeGyroscopeOptions
```

Defines the parameters for subscribing to the gyroscope sensor, including the callback frequency and callback function.

**Since:** 6

**Deprecated since:** 8

**Substitutes:** [GYROSCOPE](arkts-sensorservice-sensor-sensorid-e.md#gyroscope)

**Required permissions:** ohos.permission.GYROSCOPE

<!--Device-unnamed-export interface SubscribeGyroscopeOptions--><!--Device-unnamed-export interface SubscribeGyroscopeOptions-End-->

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

**Since:** 6

**Deprecated since:** 8

**Substitutes:** [on](arkts-sensorservice-sensor-on-f.md)

**Required permissions:** ohos.permission.GYROSCOPE

**Model restriction:** This API can be used only in the FA model.

<!--Device-SubscribeGyroscopeOptions-fail?: (data: string, code: number) => void--><!--Device-SubscribeGyroscopeOptions-fail?: (data: string, code: number) => void-End-->

**System capability:** SystemCapability.Sensors.Sensor.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | string | Yes |  |
| code | number | Yes |  |

## success

```TypeScript
success: (data: GyroscopeResponse) => void
```

Callback invoked when the gyroscope sensor data changes. The callback parameter is a **GyroscopeResponse** object.

**Since:** 6

**Deprecated since:** 8

**Substitutes:** [on](arkts-sensorservice-sensor-on-f.md)

**Required permissions:** ohos.permission.GYROSCOPE

**Model restriction:** This API can be used only in the FA model.

<!--Device-SubscribeGyroscopeOptions-success: (data: GyroscopeResponse) => void--><!--Device-SubscribeGyroscopeOptions-success: (data: GyroscopeResponse) => void-End-->

**System capability:** SystemCapability.Sensors.Sensor.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | [GyroscopeResponse](arkts-sensorservice-system-sensor-gyroscoperesponse-i.md) | Yes |  |

## interval

```TypeScript
interval: string
```

Interval at which the callback is invoked to return the gyroscope sensor data.

Default value: **'normal'**

Possible values:

- **'game'**: called at an interval of 20 ms, which is applicable to gaming scenarios.  
- **'ui'**: called at an interval of 60 ms, which is applicable to UI updating scenarios.  
- **'normal'**: called at an interval of 200 ms, which is applicable to power-saving scenarios.

**Type:** string

**Since:** 6

**Deprecated since:** 8

**Substitutes:** [interval](arkts-sensorservice-sensor-options-i.md#interval)

**Required permissions:** ohos.permission.GYROSCOPE

**Model restriction:** This API can be used only in the FA model.

<!--Device-SubscribeGyroscopeOptions-interval: string--><!--Device-SubscribeGyroscopeOptions-interval: string-End-->

**System capability:** SystemCapability.Sensors.Sensor.Lite
