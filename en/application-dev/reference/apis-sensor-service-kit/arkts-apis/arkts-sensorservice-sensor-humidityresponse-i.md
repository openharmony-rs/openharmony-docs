# HumidityResponse

```TypeScript
interface HumidityResponse extends Response
```

Describes the humidity sensor data. It extends from [Response](arkts-sensorservice-sensor-response-i.md).

**Inheritance/Implementation:** HumidityResponse extends [Response](arkts-sensorservice-sensor-response-i.md)

**Since:** 8

<!--Device-sensor-interface HumidityResponse extends Response--><!--Device-sensor-interface HumidityResponse extends Response-End-->

**System capability:** SystemCapability.Sensors.Sensor

## Modules to Import

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## humidity

```TypeScript
humidity: number
```

Relative humidity of the environment, in percentage, indicating the relative humidity percentage of the environment.

**Type:** number

**Since:** 8

<!--Device-HumidityResponse-humidity: double--><!--Device-HumidityResponse-humidity: double-End-->

**System capability:** SystemCapability.Sensors.Sensor
