# BarometerResponse

```TypeScript
interface BarometerResponse extends Response
```

Describes the barometer sensor data. It extends from [Response](arkts-sensorservice-sensor-response-i.md).

**Inheritance/Implementation:** BarometerResponse extends [Response](arkts-sensorservice-sensor-response-i.md)

**Since:** 8

<!--Device-sensor-interface BarometerResponse extends Response--><!--Device-sensor-interface BarometerResponse extends Response-End-->

**System capability:** SystemCapability.Sensors.Sensor

## Modules to Import

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## pressure

```TypeScript
pressure: number
```

Atmospheric pressure, in hPa.

**Type:** number

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-BarometerResponse-pressure: double--><!--Device-BarometerResponse-pressure: double-End-->

**System capability:** SystemCapability.Sensors.Sensor
