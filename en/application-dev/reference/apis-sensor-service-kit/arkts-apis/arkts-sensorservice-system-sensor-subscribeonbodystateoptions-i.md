# SubscribeOnBodyStateOptions

```TypeScript
export interface SubscribeOnBodyStateOptions
```

Sets the parameters for subscribing to the device wearing status, including the callback function. The wearing status can be worn or not worn.

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [WEAR_DETECTION](arkts-sensorservice-sensor-sensorid-e.md#wear_detection)

<!--Device-unnamed-export interface SubscribeOnBodyStateOptions--><!--Device-unnamed-export interface SubscribeOnBodyStateOptions-End-->

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

<!--Device-SubscribeOnBodyStateOptions-fail?: (data: string, code: number) => void--><!--Device-SubscribeOnBodyStateOptions-fail?: (data: string, code: number) => void-End-->

**System capability:** SystemCapability.Sensors.Sensor.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | string | Yes |  |
| code | number | Yes |  |

## success

```TypeScript
success: (data: OnBodyStateResponse) => void
```

Callback invoked when the wearing state of the device that houses the sensor is successfully obtained. The callback parameter is an **OnBodyStateResponse** object.

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [on](arkts-sensorservice-sensor-on-f.md)

**Model restriction:** This API can be used only in the FA model.

<!--Device-SubscribeOnBodyStateOptions-success: (data: OnBodyStateResponse) => void--><!--Device-SubscribeOnBodyStateOptions-success: (data: OnBodyStateResponse) => void-End-->

**System capability:** SystemCapability.Sensors.Sensor.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | [OnBodyStateResponse](arkts-sensorservice-system-sensor-onbodystateresponse-i.md) | Yes |  |
