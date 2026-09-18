# DeviceOrientationResponse

Defines a **DeviceOrientationResponse** object.

**Since:** 6

**Deprecated since:** 8

**Substitutes:** [OrientationResponse](arkts-sensorservice-sensor-orientationresponse-i.md)

**System capability:** SystemCapability.Sensors.Sensor.Lite

## Modules to Import

```TypeScript
import { Sensor, AccelerometerResponse, BarometerResponse, CompassResponse, DeviceOrientationResponse, GetOnBodyStateOptions, GyroscopeResponse, HeartRateResponse, LightResponse, OnBodyStateResponse, ProximityResponse, StepCounterResponse, SubscribeBarometerOptions, SubscribeCompassOptions, SubscribeDeviceOrientationOptions, SubscribeGyroscopeOptions, SubscribeHeartRateOptions, SubscribeLightOptions, SubscribeOnBodyStateOptions, SubscribeProximityOptions, SubscribeStepCounterOptions, subscribeAccelerometerOptions } from '@kit.SensorServiceKit';
```

## alpha

```TypeScript
alpha: number
```

Rotation angle around the Z axis when the X/Y axis of the device coincides with the X/Y axis of the earth.

**Type:** number

**Since:** 6

**Deprecated since:** 8

**Substitutes:** [alpha](arkts-sensorservice-sensor-orientationresponse-i.md#alpha)

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Sensors.Sensor.Lite

## beta

```TypeScript
beta: number
```

Rotation angle around the X axis when the Y/Z axis of the device coincides with the Y/Z axis of the earth.

**Type:** number

**Since:** 6

**Deprecated since:** 8

**Substitutes:** [beta](arkts-sensorservice-sensor-orientationresponse-i.md#beta)

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Sensors.Sensor.Lite

## gamma

```TypeScript
gamma: number
```

Rotation angle around the Y axis when the X/Z axis of the device coincides with the X/Z axis of the earth.

**Type:** number

**Since:** 6

**Deprecated since:** 8

**Substitutes:** [gamma](arkts-sensorservice-sensor-orientationresponse-i.md#gamma)

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Sensors.Sensor.Lite
