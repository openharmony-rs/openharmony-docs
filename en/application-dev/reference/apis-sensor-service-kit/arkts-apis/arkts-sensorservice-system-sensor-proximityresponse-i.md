# ProximityResponse

```TypeScript
export interface ProximityResponse
```

Callback function response object after the proximity sensor data changes, including the distance between a visible object and the device screen.

**Device behavior differences**: This API can be called on wearables and lite wearables, but has no effect on other device types.

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [ProximityResponse](arkts-sensorservice-sensor-proximityresponse-i.md)

<!--Device-unnamed-export interface ProximityResponse--><!--Device-unnamed-export interface ProximityResponse-End-->

**System capability:** SystemCapability.Sensors.Sensor.Lite

## Modules to Import

```TypeScript
import { Sensor, AccelerometerResponse, BarometerResponse, CompassResponse, DeviceOrientationResponse, GetOnBodyStateOptions, GyroscopeResponse, HeartRateResponse, LightResponse, OnBodyStateResponse, ProximityResponse, StepCounterResponse, SubscribeBarometerOptions, SubscribeCompassOptions, SubscribeDeviceOrientationOptions, SubscribeGyroscopeOptions, SubscribeHeartRateOptions, SubscribeLightOptions, SubscribeOnBodyStateOptions, SubscribeProximityOptions, SubscribeStepCounterOptions, subscribeAccelerometerOptions } from '@kit.SensorServiceKit';
```

## distance

```TypeScript
distance: number
```

Distance between a visible object and the device screen. Value range: **0** indicates that the object is close to the screen (near state), and a value greater than 0 indicates that the object is far away from the screen (far state). The specific value of the far state is determined by the hardware sensor.

**Type:** number

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [distance](arkts-sensorservice-sensor-proximityresponse-i.md#distance)

**Model restriction:** This API can be used only in the FA model.

<!--Device-ProximityResponse-distance: number--><!--Device-ProximityResponse-distance: number-End-->

**System capability:** SystemCapability.Sensors.Sensor.Lite
