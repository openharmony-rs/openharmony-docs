# StepCounterResponse

```TypeScript
export interface StepCounterResponse
```

Defines a response object of the callback function invoked when the step counter sensor data changes, including the accumulated step count recorded after the step counter sensor is restarted.

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [PedometerResponse](arkts-sensorservice-sensor-pedometerresponse-i.md)

**Required permissions:** ohos.permission.ACTIVITY_MOTION

<!--Device-unnamed-export interface StepCounterResponse--><!--Device-unnamed-export interface StepCounterResponse-End-->

**System capability:** SystemCapability.Sensors.Sensor.Lite

## Modules to Import

```TypeScript
import { Sensor, AccelerometerResponse, BarometerResponse, CompassResponse, DeviceOrientationResponse, GetOnBodyStateOptions, GyroscopeResponse, HeartRateResponse, LightResponse, OnBodyStateResponse, ProximityResponse, StepCounterResponse, SubscribeBarometerOptions, SubscribeCompassOptions, SubscribeDeviceOrientationOptions, SubscribeGyroscopeOptions, SubscribeHeartRateOptions, SubscribeLightOptions, SubscribeOnBodyStateOptions, SubscribeProximityOptions, SubscribeStepCounterOptions, subscribeAccelerometerOptions } from '@kit.SensorServiceKit';
```

## steps

```TypeScript
steps: number
```

Number of counted steps after the sensor is restarted. Value range: an integer greater than or equal to 0. The value is the actually reported physical quantity. The step count restarts from 0 after the sensor is restarted.

**Type:** number

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [steps](arkts-sensorservice-sensor-pedometerresponse-i.md#steps)

**Required permissions:** ohos.permission.ACTIVITY_MOTION

**Model restriction:** This API can be used only in the FA model.

<!--Device-StepCounterResponse-steps: number--><!--Device-StepCounterResponse-steps: number-End-->

**System capability:** SystemCapability.Sensors.Sensor.Lite
