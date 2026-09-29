# HeartRateResponse

```TypeScript
export interface HeartRateResponse
```

Defines a response object of the callback function after the heart rate sensor data is changed, including the heart rate value.

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [HeartRateResponse](arkts-sensorservice-sensor-heartrateresponse-i.md)

**Required permissions:** ohos.permission.READ_HEALTH_DATA

<!--Device-unnamed-export interface HeartRateResponse--><!--Device-unnamed-export interface HeartRateResponse-End-->

**System capability:** SystemCapability.Sensors.Sensor.Lite

## Modules to Import

```TypeScript
import { Sensor, AccelerometerResponse, BarometerResponse, CompassResponse, DeviceOrientationResponse, GetOnBodyStateOptions, GyroscopeResponse, HeartRateResponse, LightResponse, OnBodyStateResponse, ProximityResponse, StepCounterResponse, SubscribeBarometerOptions, SubscribeCompassOptions, SubscribeDeviceOrientationOptions, SubscribeGyroscopeOptions, SubscribeHeartRateOptions, SubscribeLightOptions, SubscribeOnBodyStateOptions, SubscribeProximityOptions, SubscribeStepCounterOptions, subscribeAccelerometerOptions } from '@kit.SensorServiceKit';
```

## heartRate

```TypeScript
heartRate: number
```

Heart rate, in bpm. Value range: The value is the actually reported physical quantity, which is determined by the hardware sensor. The resting heart rate of a normal adult ranges from 60 to 100 bpm.

**Type:** number

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [heartRate](arkts-sensorservice-sensor-heartrateresponse-i.md#heartrate)

**Required permissions:** ohos.permission.READ_HEALTH_DATA

**Model restriction:** This API can be used only in the FA model.

<!--Device-HeartRateResponse-heartRate: number--><!--Device-HeartRateResponse-heartRate: number-End-->

**System capability:** SystemCapability.Sensors.Sensor.Lite
