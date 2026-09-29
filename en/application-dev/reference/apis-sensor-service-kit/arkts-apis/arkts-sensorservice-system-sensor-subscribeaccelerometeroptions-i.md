# subscribeAccelerometerOptions

```TypeScript
export interface subscribeAccelerometerOptions
```

Sets the parameters for subscribing to the acceleration sensor, including the callback frequency and callback function.

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [ACCELEROMETER](arkts-sensorservice-sensor-sensorid-e.md#accelerometer)

**Required permissions:** ohos.permission.ACCELEROMETER

<!--Device-unnamed-export interface subscribeAccelerometerOptions--><!--Device-unnamed-export interface subscribeAccelerometerOptions-End-->

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

**Required permissions:** ohos.permission.ACCELEROMETER

**Model restriction:** This API can be used only in the FA model.

<!--Device-subscribeAccelerometerOptions-fail?: (data: string, code: number) => void--><!--Device-subscribeAccelerometerOptions-fail?: (data: string, code: number) => void-End-->

**System capability:** SystemCapability.Sensors.Sensor.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | string | Yes |  |
| code | number | Yes |  |

## success

```TypeScript
success: (data: AccelerometerResponse) => void
```

Callback function invoked when the acceleration sensor data changes. The callback parameter is an **AccelerometerResponse** object.

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [on](arkts-sensorservice-sensor-on-f.md)

**Required permissions:** ohos.permission.ACCELEROMETER

**Model restriction:** This API can be used only in the FA model.

<!--Device-subscribeAccelerometerOptions-success: (data: AccelerometerResponse) => void--><!--Device-subscribeAccelerometerOptions-success: (data: AccelerometerResponse) => void-End-->

**System capability:** SystemCapability.Sensors.Sensor.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | [AccelerometerResponse](arkts-sensorservice-system-sensor-accelerometerresponse-i.md) | Yes |  |

## interval

```TypeScript
interval: string
```

Execution frequency of the callback for returning the acceleration sensor data.

Default value: **'normal'**

Possible values:

- **'game'**: called at an interval of 20 ms, which is applicable to gaming scenarios.  
- **'ui'**: called at an interval of 60 ms, which is applicable to UI updating scenarios.  
- **'normal'**: called at an interval of 200 ms, which is applicable to power-saving scenarios.

**Type:** string

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [interval](arkts-sensorservice-sensor-options-i.md#interval)

**Required permissions:** ohos.permission.ACCELEROMETER

**Model restriction:** This API can be used only in the FA model.

<!--Device-subscribeAccelerometerOptions-interval: string--><!--Device-subscribeAccelerometerOptions-interval: string-End-->

**System capability:** SystemCapability.Sensors.Sensor.Lite
