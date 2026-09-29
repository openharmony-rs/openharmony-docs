# OnBodyStateResponse

```TypeScript
export interface OnBodyStateResponse
```

Defines a response object of the device wearing status, including the data indicating whether the device is worn.

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [WearDetectionResponse](arkts-sensorservice-sensor-weardetectionresponse-i.md)

<!--Device-unnamed-export interface OnBodyStateResponse--><!--Device-unnamed-export interface OnBodyStateResponse-End-->

**System capability:** SystemCapability.Sensors.Sensor.Lite

## Modules to Import

```TypeScript
import { Sensor, AccelerometerResponse, BarometerResponse, CompassResponse, DeviceOrientationResponse, GetOnBodyStateOptions, GyroscopeResponse, HeartRateResponse, LightResponse, OnBodyStateResponse, ProximityResponse, StepCounterResponse, SubscribeBarometerOptions, SubscribeCompassOptions, SubscribeDeviceOrientationOptions, SubscribeGyroscopeOptions, SubscribeHeartRateOptions, SubscribeLightOptions, SubscribeOnBodyStateOptions, SubscribeProximityOptions, SubscribeStepCounterOptions, subscribeAccelerometerOptions } from '@kit.SensorServiceKit';
```

## value

```TypeScript
value: boolean
```

Whether the device is worn The value **true** indicates that the device is worn, and the value **false** indicates that the device is not worn.

**Type:** boolean

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [value](arkts-sensorservice-sensor-weardetectionresponse-i.md#value)

**Model restriction:** This API can be used only in the FA model.

<!--Device-OnBodyStateResponse-value: boolean--><!--Device-OnBodyStateResponse-value: boolean-End-->

**System capability:** SystemCapability.Sensors.Sensor.Lite
