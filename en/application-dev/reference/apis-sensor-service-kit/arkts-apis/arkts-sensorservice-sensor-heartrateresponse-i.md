# HeartRateResponse

```TypeScript
interface HeartRateResponse extends Response
```

Describes the heart rate sensor data. It extends from [Response](arkts-sensorservice-sensor-response-i.md).

**Inheritance/Implementation:** HeartRateResponse extends [Response](arkts-sensorservice-sensor-response-i.md)

**Since:** 8

<!--Device-sensor-interface HeartRateResponse extends Response--><!--Device-sensor-interface HeartRateResponse extends Response-End-->

**System capability:** SystemCapability.Sensors.Sensor

## Modules to Import

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## heartRate

```TypeScript
heartRate: number
```

Heart rate of a user, in bpm.

**Type:** number

**Since:** 8

<!--Device-HeartRateResponse-heartRate: double--><!--Device-HeartRateResponse-heartRate: double-End-->

**System capability:** SystemCapability.Sensors.Sensor
