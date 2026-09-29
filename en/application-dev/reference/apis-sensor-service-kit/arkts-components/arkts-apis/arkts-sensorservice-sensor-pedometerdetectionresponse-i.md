# PedometerDetectionResponse

```TypeScript
interface PedometerDetectionResponse extends Response
```

Describes the pedometer detection sensor data. It extends from [Response](arkts-sensorservice-sensor-response-i.md).

**Inheritance/Implementation:** PedometerDetectionResponse extends [Response](arkts-sensorservice-sensor-response-i.md)

**Since:** 8

<!--Device-sensor-interface PedometerDetectionResponse extends Response--><!--Device-sensor-interface PedometerDetectionResponse extends Response-End-->

**System capability:** SystemCapability.Sensors.Sensor

## Modules to Import

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## scalar

```TypeScript
scalar: number
```

Pedometer detection scalar. The value can be **1** (a step counting event is detected, indicating that the user is walking) or **0** (no step counting event is detected, indicating that the user is not moving).

**Type:** number

**Since:** 8

<!--Device-PedometerDetectionResponse-scalar: double--><!--Device-PedometerDetectionResponse-scalar: double-End-->

**System capability:** SystemCapability.Sensors.Sensor
