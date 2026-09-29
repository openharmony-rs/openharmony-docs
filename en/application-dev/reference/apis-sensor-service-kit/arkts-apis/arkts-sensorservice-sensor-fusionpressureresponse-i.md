# FusionPressureResponse

```TypeScript
interface FusionPressureResponse extends Response
```

Describes the fusion pressure sensor data. It extends from [Response](arkts-sensorservice-sensor-response-i.md).

**Inheritance/Implementation:** FusionPressureResponse extends [Response](arkts-sensorservice-sensor-response-i.md)

**Since:** 22

<!--Device-sensor-interface FusionPressureResponse extends Response--><!--Device-sensor-interface FusionPressureResponse extends Response-End-->

**System capability:** SystemCapability.Sensors.Sensor

## Modules to Import

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## fusionPressure

```TypeScript
fusionPressure: number
```

Fused pressure, indicating the percentage of the pressure value applied to the fused pressure sensor, in percentage.

**Type:** number

**Since:** 22

<!--Device-FusionPressureResponse-fusionPressure: double--><!--Device-FusionPressureResponse-fusionPressure: double-End-->

**System capability:** SystemCapability.Sensors.Sensor
