# AccelerometerResponse

```TypeScript
export interface AccelerometerResponse
```

Callback invoked when the acceleration sensor data changes. The callback returns the acceleration data of the device on the x, y, and z axes.

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [AccelerometerResponse](arkts-sensorservice-sensor-accelerometerresponse-i.md)

**Required permissions:** ohos.permission.ACCELEROMETER

<!--Device-unnamed-export interface AccelerometerResponse--><!--Device-unnamed-export interface AccelerometerResponse-End-->

**System capability:** SystemCapability.Sensors.Sensor.Lite

## Modules to Import

```TypeScript
import { Sensor, AccelerometerResponse, BarometerResponse, CompassResponse, DeviceOrientationResponse, GetOnBodyStateOptions, GyroscopeResponse, HeartRateResponse, LightResponse, OnBodyStateResponse, ProximityResponse, StepCounterResponse, SubscribeBarometerOptions, SubscribeCompassOptions, SubscribeDeviceOrientationOptions, SubscribeGyroscopeOptions, SubscribeHeartRateOptions, SubscribeLightOptions, SubscribeOnBodyStateOptions, SubscribeProximityOptions, SubscribeStepCounterOptions, subscribeAccelerometerOptions } from '@kit.SensorServiceKit';
```

## x

```TypeScript
x: number
```

Acceleration along the x-axis of the device, in m/s². Value range: The value is the actually reported physical quantity, which is determined by the hardware sensor.

**Type:** number

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [x](arkts-sensorservice-sensor-accelerometerresponse-i.md#x)

**Required permissions:** ohos.permission.ACCELEROMETER

**Model restriction:** This API can be used only in the FA model.

<!--Device-AccelerometerResponse-x: number--><!--Device-AccelerometerResponse-x: number-End-->

**System capability:** SystemCapability.Sensors.Sensor.Lite

## y

```TypeScript
y: number
```

Acceleration along the y-axis of the device, in m/s². Value range: The value is the actually reported physical quantity, which is determined by the hardware sensor.

**Type:** number

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [y](arkts-sensorservice-sensor-accelerometerresponse-i.md#y)

**Required permissions:** ohos.permission.ACCELEROMETER

**Model restriction:** This API can be used only in the FA model.

<!--Device-AccelerometerResponse-y: number--><!--Device-AccelerometerResponse-y: number-End-->

**System capability:** SystemCapability.Sensors.Sensor.Lite

## z

```TypeScript
z: number
```

Acceleration along the z-axis of the device, in m/s². Value range: The value is the actually reported physical quantity, which is determined by the hardware sensor. The acceleration along the z-axis is about 9.8 m/s² (gravity acceleration) when the device is still.

**Type:** number

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [z](arkts-sensorservice-sensor-accelerometerresponse-i.md#z)

**Required permissions:** ohos.permission.ACCELEROMETER

**Model restriction:** This API can be used only in the FA model.

<!--Device-AccelerometerResponse-z: number--><!--Device-AccelerometerResponse-z: number-End-->

**System capability:** SystemCapability.Sensors.Sensor.Lite
