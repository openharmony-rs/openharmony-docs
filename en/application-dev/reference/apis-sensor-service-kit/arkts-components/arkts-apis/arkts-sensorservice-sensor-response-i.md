# Response

```TypeScript
interface Response
```

Defines the base class for the timestamp and accuracy information of sensor data. All sensor response types inherit from this class.

**Atomic service API**: This API can be used in atomic services since API version 11.

**Since:** 8

<!--Device-sensor-interface Response--><!--Device-sensor-interface Response-End-->

**System capability:** SystemCapability.Sensors.Sensor

## Modules to Import

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## accuracy

```TypeScript
accuracy: SensorAccuracy
```

Accuracy of the sensor data, indicating the reliability of the reported data.

**Type:** [SensorAccuracy](arkts-sensorservice-sensor-sensoraccuracy-e.md)

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-Response-accuracy: SensorAccuracy--><!--Device-Response-accuracy: SensorAccuracy-End-->

**System capability:** SystemCapability.Sensors.Sensor

## timestamp

```TypeScript
timestamp: number
```

Timestamp when the sensor reports data. Time from device startup to data reporting, in nanoseconds.

**Type:** number

**Since:** 8

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-Response-timestamp: long--><!--Device-Response-timestamp: long-End-->

**System capability:** SystemCapability.Sensors.Sensor
