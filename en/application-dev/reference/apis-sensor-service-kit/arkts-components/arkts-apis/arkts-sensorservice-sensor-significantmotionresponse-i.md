# SignificantMotionResponse

```TypeScript
interface SignificantMotionResponse extends Response
```

Describes the significant motion sensor data. It extends from [Response](arkts-sensorservice-sensor-response-i.md).

**Inheritance/Implementation:** SignificantMotionResponse extends [Response](arkts-sensorservice-sensor-response-i.md)

**Since:** 8

<!--Device-sensor-interface SignificantMotionResponse extends Response--><!--Device-sensor-interface SignificantMotionResponse extends Response-End-->

**System capability:** SystemCapability.Sensors.Sensor

## Modules to Import

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## scalar

```TypeScript
scalar: number
```

Intensity of a motion. Value range: **1** indicates that a valid motion is detected. The value **1** is reported when the device has a large motion on three physical axes (x, y, and z).

**Type:** number

**Since:** 8

<!--Device-SignificantMotionResponse-scalar: double--><!--Device-SignificantMotionResponse-scalar: double-End-->

**System capability:** SystemCapability.Sensors.Sensor
