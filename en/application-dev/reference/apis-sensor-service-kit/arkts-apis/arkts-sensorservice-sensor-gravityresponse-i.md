# GravityResponse

```TypeScript
interface GravityResponse extends Response
```

Describes the gravity sensor data. It extends from [Response](arkts-sensorservice-sensor-response-i.md).

**Inheritance/Implementation:** GravityResponse extends [Response](arkts-sensorservice-sensor-response-i.md)

**Since:** 8

<!--Device-sensor-interface GravityResponse extends Response--><!--Device-sensor-interface GravityResponse extends Response-End-->

**System capability:** SystemCapability.Sensors.Sensor

## Modules to Import

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## x

```TypeScript
x: number
```

Gravity acceleration along the x-axis of the device, in m/s².

**Type:** number

**Since:** 8

<!--Device-GravityResponse-x: double--><!--Device-GravityResponse-x: double-End-->

**System capability:** SystemCapability.Sensors.Sensor

## y

```TypeScript
y: number
```

Gravity acceleration along the y-axis of the device, in m/s².

**Type:** number

**Since:** 8

<!--Device-GravityResponse-y: double--><!--Device-GravityResponse-y: double-End-->

**System capability:** SystemCapability.Sensors.Sensor

## z

```TypeScript
z: number
```

Gravity acceleration along the z-axis of the device, in m/s².

**Type:** number

**Since:** 8

<!--Device-GravityResponse-z: double--><!--Device-GravityResponse-z: double-End-->

**System capability:** SystemCapability.Sensors.Sensor
