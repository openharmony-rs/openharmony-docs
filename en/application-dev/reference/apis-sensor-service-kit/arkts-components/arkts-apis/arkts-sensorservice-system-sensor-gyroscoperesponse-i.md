# GyroscopeResponse

```TypeScript
export interface GyroscopeResponse
```

Defines a response object of the callback function after the gyroscope sensor data changes, including the rotational velocity data of the device on the x, y, and z axes.

**Since:** 6

**Deprecated since:** 8

**Substitutes:** [GyroscopeResponse](arkts-sensorservice-sensor-gyroscoperesponse-i.md)

**Required permissions:** ohos.permission.GYROSCOPE

<!--Device-unnamed-export interface GyroscopeResponse--><!--Device-unnamed-export interface GyroscopeResponse-End-->

**System capability:** SystemCapability.Sensors.Sensor.Lite

## Modules to Import

```TypeScript
import { Sensor, AccelerometerResponse, BarometerResponse, CompassResponse, DeviceOrientationResponse, GetOnBodyStateOptions, GyroscopeResponse, HeartRateResponse, LightResponse, OnBodyStateResponse, ProximityResponse, StepCounterResponse, SubscribeBarometerOptions, SubscribeCompassOptions, SubscribeDeviceOrientationOptions, SubscribeGyroscopeOptions, SubscribeHeartRateOptions, SubscribeLightOptions, SubscribeOnBodyStateOptions, SubscribeProximityOptions, SubscribeStepCounterOptions, subscribeAccelerometerOptions } from '@kit.SensorServiceKit';
```

## x

```TypeScript
x: number
```

Rotation angular velocity of the X axis, in rad/s. Value range: The value is the actually reported physical quantity, which is determined by the hardware sensor.

**Type:** number

**Since:** 6

**Deprecated since:** 8

**Substitutes:** [x](arkts-sensorservice-sensor-gyroscoperesponse-i.md#x)

**Required permissions:** ohos.permission.GYROSCOPE

**Model restriction:** This API can be used only in the FA model.

<!--Device-GyroscopeResponse-x: number--><!--Device-GyroscopeResponse-x: number-End-->

**System capability:** SystemCapability.Sensors.Sensor.Lite

## y

```TypeScript
y: number
```

Rotation angular velocity of the Y axis, in rad/s. Value range: The value is the actually reported physical quantity, which is determined by the hardware sensor.

**Type:** number

**Since:** 6

**Deprecated since:** 8

**Substitutes:** [y](arkts-sensorservice-sensor-gyroscoperesponse-i.md#y)

**Required permissions:** ohos.permission.GYROSCOPE

**Model restriction:** This API can be used only in the FA model.

<!--Device-GyroscopeResponse-y: number--><!--Device-GyroscopeResponse-y: number-End-->

**System capability:** SystemCapability.Sensors.Sensor.Lite

## z

```TypeScript
z: number
```

Rotation angular velocity of the Z axis, in rad/s. Value range: The value is the actually reported physical quantity, which is determined by the hardware sensor.

**Type:** number

**Since:** 6

**Deprecated since:** 8

**Substitutes:** [z](arkts-sensorservice-sensor-gyroscoperesponse-i.md#z)

**Required permissions:** ohos.permission.GYROSCOPE

**Model restriction:** This API can be used only in the FA model.

<!--Device-GyroscopeResponse-z: number--><!--Device-GyroscopeResponse-z: number-End-->

**System capability:** SystemCapability.Sensors.Sensor.Lite
