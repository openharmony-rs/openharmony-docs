# GetOnBodyStateOptions

```TypeScript
export interface GetOnBodyStateOptions
```

Sets the parameters for subscribing to the device wearing status, including the callback function. The wearing status can be worn or not worn.

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [WEAR_DETECTION](arkts-sensorservice-sensor-sensorid-e.md#wear_detection)

<!--Device-unnamed-export interface GetOnBodyStateOptions--><!--Device-unnamed-export interface GetOnBodyStateOptions-End-->

**System capability:** SystemCapability.Sensors.Sensor.Lite

## Modules to Import

```TypeScript
import { Sensor, AccelerometerResponse, BarometerResponse, CompassResponse, DeviceOrientationResponse, GetOnBodyStateOptions, GyroscopeResponse, HeartRateResponse, LightResponse, OnBodyStateResponse, ProximityResponse, StepCounterResponse, SubscribeBarometerOptions, SubscribeCompassOptions, SubscribeDeviceOrientationOptions, SubscribeGyroscopeOptions, SubscribeHeartRateOptions, SubscribeLightOptions, SubscribeOnBodyStateOptions, SubscribeProximityOptions, SubscribeStepCounterOptions, subscribeAccelerometerOptions } from '@kit.SensorServiceKit';
```

## complete

```TypeScript
complete?: () => void
```

Callback invoked when the API call is complete. This callback will be executed regardless of whether the API call succeeds or fails. If this parameter is not specified, no callback notification is sent when the API call is complete.

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [once](arkts-sensorservice-sensor-once-f.md)

**Model restriction:** This API can be used only in the FA model.

<!--Device-GetOnBodyStateOptions-complete?: () => void--><!--Device-GetOnBodyStateOptions-complete?: () => void-End-->

**System capability:** SystemCapability.Sensors.Sensor.Lite

## fail

```TypeScript
fail?: (data: string, code: number) => void
```

Callback invoked when an API call fails. The callback parameters are **data** of the string type and **code** of the number type, where **data** indicates the error information and **code** indicates the error code. If this parameter is not specified, no callback notification is sent when the API call fails.

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [once](arkts-sensorservice-sensor-once-f.md)

**Model restriction:** This API can be used only in the FA model.

<!--Device-GetOnBodyStateOptions-fail?: (data: string, code: number) => void--><!--Device-GetOnBodyStateOptions-fail?: (data: string, code: number) => void-End-->

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

Callback invoked when the API call succeeds. The callback parameter is an **OnBodyStateResponse** object.

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [once](arkts-sensorservice-sensor-once-f.md)

**Model restriction:** This API can be used only in the FA model.

<!--Device-GetOnBodyStateOptions-success: (data: OnBodyStateResponse) => void--><!--Device-GetOnBodyStateOptions-success: (data: OnBodyStateResponse) => void-End-->

**System capability:** SystemCapability.Sensors.Sensor.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | [OnBodyStateResponse](arkts-sensorservice-system-sensor-onbodystateresponse-i.md) | Yes |  |
