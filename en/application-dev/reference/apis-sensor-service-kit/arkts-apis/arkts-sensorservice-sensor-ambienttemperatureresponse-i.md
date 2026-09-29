# AmbientTemperatureResponse

```TypeScript
interface AmbientTemperatureResponse extends Response
```

Describes the ambient temperature sensor data. It extends from [Response](arkts-sensorservice-sensor-response-i.md).

**Inheritance/Implementation:** AmbientTemperatureResponse extends [Response](arkts-sensorservice-sensor-response-i.md)

**Since:** 8

<!--Device-sensor-interface AmbientTemperatureResponse extends Response--><!--Device-sensor-interface AmbientTemperatureResponse extends Response-End-->

**System capability:** SystemCapability.Sensors.Sensor

## Modules to Import

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## temperature

```TypeScript
temperature: number
```

Ambient temperature, in °C.

**Type:** number

**Since:** 8

<!--Device-AmbientTemperatureResponse-temperature: double--><!--Device-AmbientTemperatureResponse-temperature: double-End-->

**System capability:** SystemCapability.Sensors.Sensor
