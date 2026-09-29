# BarometerResponse

```TypeScript
export interface BarometerResponse
```

Defines a response object of the callback function after the barometric pressure sensor data is changed, including the atmospheric pressure value.

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [BarometerResponse](arkts-sensorservice-sensor-barometerresponse-i.md)

<!--Device-unnamed-export interface BarometerResponse--><!--Device-unnamed-export interface BarometerResponse-End-->

**System capability:** SystemCapability.Sensors.Sensor.Lite

## Modules to Import

```TypeScript
import { Sensor, AccelerometerResponse, BarometerResponse, CompassResponse, DeviceOrientationResponse, GetOnBodyStateOptions, GyroscopeResponse, HeartRateResponse, LightResponse, OnBodyStateResponse, ProximityResponse, StepCounterResponse, SubscribeBarometerOptions, SubscribeCompassOptions, SubscribeDeviceOrientationOptions, SubscribeGyroscopeOptions, SubscribeHeartRateOptions, SubscribeLightOptions, SubscribeOnBodyStateOptions, SubscribeProximityOptions, SubscribeStepCounterOptions, subscribeAccelerometerOptions } from '@kit.SensorServiceKit';
```

## pressure

```TypeScript
pressure: number
```

Atmospheric pressure, in Pa. Value range: The value is the actually reported physical quantity, which is determined by the hardware sensor. The standard atmospheric pressure is about 101,325 Pa.

**Type:** number

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [pressure](arkts-sensorservice-sensor-barometerresponse-i.md#pressure)

**Model restriction:** This API can be used only in the FA model.

<!--Device-BarometerResponse-pressure: number--><!--Device-BarometerResponse-pressure: number-End-->

**System capability:** SystemCapability.Sensors.Sensor.Lite
