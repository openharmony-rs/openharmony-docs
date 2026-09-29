# SarResponse (System API)

```TypeScript
interface SarResponse extends Response
```

Describes the SAR sensor data. It extends from [Response](arkts-sensorservice-sensor-response-i.md). This method is used to represent the response data reported by the SAR sensor, including the SAR information.

**Inheritance/Implementation:** SarResponse extends [Response](arkts-sensorservice-sensor-response-i.md)

**Since:** 10

<!--Device-sensor-interface SarResponse extends Response--><!--Device-sensor-interface SarResponse extends Response-End-->

**System capability:** SystemCapability.Sensors.Sensor

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## absorptionRatio

```TypeScript
absorptionRatio: number
```

Absorption ratio, in W/kg. Value range: The value is the actually reported physical quantity, which is determined by the hardware sensor.

**Type:** number

**Since:** 10

<!--Device-SarResponse-absorptionRatio: double--><!--Device-SarResponse-absorptionRatio: double-End-->

**System capability:** SystemCapability.Sensors.Sensor

**System API:** This is a system API.
