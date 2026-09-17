# StepCounterResponse

Callback invoked when the step counter sensor data changes.

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [PedometerResponse](arkts-sensorservice-sensor-pedometerresponse-i.md)

**Required permissions:** ohos.permission.ACTIVITY_MOTION

**System capability:** SystemCapability.Sensors.Sensor.Lite

## Modules to Import

```TypeScript
import { Sensor, AccelerometerResponse, BarometerResponse, CompassResponse, DeviceOrientationResponse, GetOnBodyStateOptions, GyroscopeResponse, HeartRateResponse, LightResponse, OnBodyStateResponse, ProximityResponse, StepCounterResponse, SubscribeBarometerOptions, SubscribeCompassOptions, SubscribeDeviceOrientationOptions, SubscribeGyroscopeOptions, SubscribeHeartRateOptions, SubscribeLightOptions, SubscribeOnBodyStateOptions, SubscribeProximityOptions, SubscribeStepCounterOptions, subscribeAccelerometerOptions } from '@kit.SensorServiceKit';
```

## steps

```TypeScript
steps: number
```

Number of counted steps after the sensor is restarted.

**Type:** number

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [steps](arkts-sensorservice-sensor-pedometerresponse-i.md#steps)

**Required permissions:** ohos.permission.ACTIVITY_MOTION

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Sensors.Sensor.Lite
