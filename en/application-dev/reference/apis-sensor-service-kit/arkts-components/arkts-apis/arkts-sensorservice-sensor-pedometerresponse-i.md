# PedometerResponse

```TypeScript
interface PedometerResponse extends Response
```

Describes the pedometer sensor data. It extends from [Response](arkts-sensorservice-sensor-response-i.md).

**Inheritance/Implementation:** PedometerResponse extends [Response](arkts-sensorservice-sensor-response-i.md)

**Since:** 8

<!--Device-sensor-interface PedometerResponse extends Response--><!--Device-sensor-interface PedometerResponse extends Response-End-->

**System capability:** SystemCapability.Sensors.Sensor

## Modules to Import

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## steps

```TypeScript
steps: number
```

Number of steps a user has walked. Unit: step

**Type:** number

**Since:** 8

<!--Device-PedometerResponse-steps: double--><!--Device-PedometerResponse-steps: double-End-->

**System capability:** SystemCapability.Sensors.Sensor
