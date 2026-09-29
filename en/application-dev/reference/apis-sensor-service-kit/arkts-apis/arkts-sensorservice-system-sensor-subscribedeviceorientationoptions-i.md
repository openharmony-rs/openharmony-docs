# SubscribeDeviceOrientationOptions

```TypeScript
export interface SubscribeDeviceOrientationOptions
```

Sets the parameters for subscribing to the device orientation sensor, including the callback frequency and callback function.

**Device behavior differences**: This API can be called on wearables and lite wearables, but has no effect on other device types.

**Since:** 6

**Deprecated since:** 8

**Substitutes:** [ORIENTATION](arkts-sensorservice-sensor-sensorid-e.md#orientation)

<!--Device-unnamed-export interface SubscribeDeviceOrientationOptions--><!--Device-unnamed-export interface SubscribeDeviceOrientationOptions-End-->

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

**Model restriction:** This API can be used only in the FA model.

<!--Device-SubscribeDeviceOrientationOptions-fail?: (data: string, code: number) => void--><!--Device-SubscribeDeviceOrientationOptions-fail?: (data: string, code: number) => void-End-->

**System capability:** SystemCapability.Sensors.Sensor.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | string | Yes |  |
| code | number | Yes |  |

## success

```TypeScript
success: (data: DeviceOrientationResponse) => void
```

Callback invoked when the device orientation sensor data changes. The callback parameter is a **DeviceOrientationResponse** object.

**Since:** 6

**Deprecated since:** 8

**Substitutes:** [on](arkts-sensorservice-sensor-on-f.md)

**Model restriction:** This API can be used only in the FA model.

<!--Device-SubscribeDeviceOrientationOptions-success: (data: DeviceOrientationResponse) => void--><!--Device-SubscribeDeviceOrientationOptions-success: (data: DeviceOrientationResponse) => void-End-->

**System capability:** SystemCapability.Sensors.Sensor.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | [DeviceOrientationResponse](arkts-sensorservice-system-sensor-deviceorientationresponse-i.md) | Yes |  |

## interval

```TypeScript
interval: string
```

Interval at which the callback is invoked to return the device orientation sensor data.

Default value: **'normal'**

Possible values:

- **'game'**: called at an interval of 20 ms, which is applicable to gaming scenarios.  
- **'ui'**: called at an interval of 60 ms, which is applicable to UI updating scenarios.  
- **'normal'**: called at an interval of 200 ms, which is applicable to power-saving scenarios.

**Type:** string

**Since:** 6

**Deprecated since:** 8

**Substitutes:** [interval](arkts-sensorservice-sensor-options-i.md#interval)

**Model restriction:** This API can be used only in the FA model.

<!--Device-SubscribeDeviceOrientationOptions-interval: string--><!--Device-SubscribeDeviceOrientationOptions-interval: string-End-->

**System capability:** SystemCapability.Sensors.Sensor.Lite
