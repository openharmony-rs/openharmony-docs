# CompassResponse

```TypeScript
export interface CompassResponse
```

Callback function response object after the compass data changes, including the degree of the direction that the device faces.

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [OrientationResponse](arkts-sensorservice-sensor-orientationresponse-i.md)

<!--Device-unnamed-export interface CompassResponse--><!--Device-unnamed-export interface CompassResponse-End-->

**System capability:** SystemCapability.Sensors.Sensor.Lite

## Modules to Import

```TypeScript
import { Sensor, AccelerometerResponse, BarometerResponse, CompassResponse, DeviceOrientationResponse, GetOnBodyStateOptions, GyroscopeResponse, HeartRateResponse, LightResponse, OnBodyStateResponse, ProximityResponse, StepCounterResponse, SubscribeBarometerOptions, SubscribeCompassOptions, SubscribeDeviceOrientationOptions, SubscribeGyroscopeOptions, SubscribeHeartRateOptions, SubscribeLightOptions, SubscribeOnBodyStateOptions, SubscribeProximityOptions, SubscribeStepCounterOptions, subscribeAccelerometerOptions } from '@kit.SensorServiceKit';
```

## direction

```TypeScript
direction: number
```

Direction of the device, in degrees. The value range is [0, 360). The value **0** indicates north. The value is equal to the reported physical quantity.

**Type:** number

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [alpha](arkts-sensorservice-sensor-orientationresponse-i.md#alpha)

**Model restriction:** This API can be used only in the FA model.

<!--Device-CompassResponse-direction: number--><!--Device-CompassResponse-direction: number-End-->

**System capability:** SystemCapability.Sensors.Sensor.Lite
