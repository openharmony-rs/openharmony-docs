# OnBodyStateResponse

Specifies whether the device that houses the sensor is worn.

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [WearDetectionResponse](arkts-sensorservice-sensor-weardetectionresponse-i.md)

**System capability:** SystemCapability.Sensors.Sensor.Lite

## Modules to Import

```TypeScript
import { Sensor, AccelerometerResponse, BarometerResponse, CompassResponse, DeviceOrientationResponse, GetOnBodyStateOptions, GyroscopeResponse, HeartRateResponse, LightResponse, OnBodyStateResponse, ProximityResponse, StepCounterResponse, SubscribeBarometerOptions, SubscribeCompassOptions, SubscribeDeviceOrientationOptions, SubscribeGyroscopeOptions, SubscribeHeartRateOptions, SubscribeLightOptions, SubscribeOnBodyStateOptions, SubscribeProximityOptions, SubscribeStepCounterOptions, subscribeAccelerometerOptions } from '@kit.SensorServiceKit';
```

## value

```TypeScript
value: boolean
```

Boolean value indicating whether the device is worn. The value **true** indicates that the device is worn, and the value **false** indicates the opposite.

**Type:** boolean

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [value](arkts-sensorservice-sensor-weardetectionresponse-i.md#value)

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Sensors.Sensor.Lite
