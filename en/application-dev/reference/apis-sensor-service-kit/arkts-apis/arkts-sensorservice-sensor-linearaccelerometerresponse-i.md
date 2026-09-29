# LinearAccelerometerResponse

```TypeScript
interface LinearAccelerometerResponse extends Response
```

Describes the linear acceleration sensor data. It extends from [Response](arkts-sensorservice-sensor-response-i.md).

**Inheritance/Implementation:** LinearAccelerometerResponse extends [Response](arkts-sensorservice-sensor-response-i.md)

**Since:** 8

<!--Device-sensor-interface LinearAccelerometerResponse extends Response--><!--Device-sensor-interface LinearAccelerometerResponse extends Response-End-->

**System capability:** SystemCapability.Sensors.Sensor

## Modules to Import

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## x

```TypeScript
x: number
```

Linear acceleration along the x-axis of the device, excluding the gravity component, in m/s².

**Type:** number

**Since:** 8

<!--Device-LinearAccelerometerResponse-x: double--><!--Device-LinearAccelerometerResponse-x: double-End-->

**System capability:** SystemCapability.Sensors.Sensor

## y

```TypeScript
y: number
```

Linear acceleration along the y-axis of the device, excluding the gravity component, in m/s².

**Type:** number

**Since:** 8

<!--Device-LinearAccelerometerResponse-y: double--><!--Device-LinearAccelerometerResponse-y: double-End-->

**System capability:** SystemCapability.Sensors.Sensor

## z

```TypeScript
z: number
```

Linear acceleration along the z-axis of the device, excluding the gravity component, in m/s².

**Type:** number

**Since:** 8

<!--Device-LinearAccelerometerResponse-z: double--><!--Device-LinearAccelerometerResponse-z: double-End-->

**System capability:** SystemCapability.Sensors.Sensor
