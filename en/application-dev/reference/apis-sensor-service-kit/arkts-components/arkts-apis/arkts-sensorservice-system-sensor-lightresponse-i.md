# LightResponse

```TypeScript
export interface LightResponse
```

Callback invoked when the ambient light sensor data changes. The response object contains the ambient light intensity data.

**Device behavior differences**: This API can be called on wearables and lite wearables, but has no effect on other device types.

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [LightResponse](arkts-sensorservice-sensor-lightresponse-i.md)

<!--Device-unnamed-export interface LightResponse--><!--Device-unnamed-export interface LightResponse-End-->

**System capability:** SystemCapability.Sensors.Sensor.Lite

## Modules to Import

```TypeScript
import { Sensor, AccelerometerResponse, BarometerResponse, CompassResponse, DeviceOrientationResponse, GetOnBodyStateOptions, GyroscopeResponse, HeartRateResponse, LightResponse, OnBodyStateResponse, ProximityResponse, StepCounterResponse, SubscribeBarometerOptions, SubscribeCompassOptions, SubscribeDeviceOrientationOptions, SubscribeGyroscopeOptions, SubscribeHeartRateOptions, SubscribeLightOptions, SubscribeOnBodyStateOptions, SubscribeProximityOptions, SubscribeStepCounterOptions, subscribeAccelerometerOptions } from '@kit.SensorServiceKit';
```

## intensity

```TypeScript
intensity: number
```

Ambient light intensity, in lux. Value range: The value is the actually reported physical quantity, which is determined by the hardware sensor.

**Type:** number

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [intensity](arkts-sensorservice-sensor-lightresponse-i.md#intensity)

**Model restriction:** This API can be used only in the FA model.

<!--Device-LightResponse-intensity: number--><!--Device-LightResponse-intensity: number-End-->

**System capability:** SystemCapability.Sensors.Sensor.Lite
