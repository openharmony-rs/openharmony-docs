# HallResponse

```TypeScript
interface HallResponse extends Response
```

Describes the Hall effect sensor data. It extends from [Response](arkts-sensorservice-sensor-response-i.md).

**Inheritance/Implementation:** HallResponse extends [Response](arkts-sensorservice-sensor-response-i.md)

**Since:** 8

<!--Device-sensor-interface HallResponse extends Response--><!--Device-sensor-interface HallResponse extends Response-End-->

**System capability:** SystemCapability.Sensors.Sensor

## Modules to Import

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## status

```TypeScript
status: number
```

Hall effect status, indicating whether there is a magnetic force around the device. The value **0** indicates there is no magnetic force, and the Hall effect is off. A value greater than 0 indicates there is magnetic force, and the Hall effect is on.

**Type:** number

**Since:** 8

<!--Device-HallResponse-status: double--><!--Device-HallResponse-status: double-End-->

**System capability:** SystemCapability.Sensors.Sensor
