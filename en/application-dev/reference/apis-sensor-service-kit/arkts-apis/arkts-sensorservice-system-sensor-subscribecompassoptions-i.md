# SubscribeCompassOptions

```TypeScript
export interface SubscribeCompassOptions
```

Sets the parameters for subscribing to the compass sensor, including the callback function.

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [ORIENTATION](arkts-sensorservice-sensor-sensorid-e.md#orientation)

<!--Device-unnamed-export interface SubscribeCompassOptions--><!--Device-unnamed-export interface SubscribeCompassOptions-End-->

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

**Model restriction:** This API can be used only in the FA model.

<!--Device-SubscribeCompassOptions-fail?: (data: string, code: number) => void--><!--Device-SubscribeCompassOptions-fail?: (data: string, code: number) => void-End-->

**System capability:** SystemCapability.Sensors.Sensor.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | string | Yes |  |
| code | number | Yes |  |

## success

```TypeScript
success: (data: CompassResponse) => void
```

Callback invoked when the compass sensor data changes. The callback parameter is a **CompassResponse** object.

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [on](arkts-sensorservice-sensor-on-f.md)

**Model restriction:** This API can be used only in the FA model.

<!--Device-SubscribeCompassOptions-success: (data: CompassResponse) => void--><!--Device-SubscribeCompassOptions-success: (data: CompassResponse) => void-End-->

**System capability:** SystemCapability.Sensors.Sensor.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | [CompassResponse](arkts-sensorservice-system-sensor-compassresponse-i.md) | Yes |  |
