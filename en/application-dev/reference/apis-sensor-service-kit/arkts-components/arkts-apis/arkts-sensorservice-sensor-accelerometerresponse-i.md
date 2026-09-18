# AccelerometerResponse

Describes the acceleration sensor data. It extends from [Response](arkts-sensorservice-sensor-response-i.md).

**Inheritance/Implementation:** AccelerometerResponse extends [Response](arkts-sensorservice-sensor-response-i.md)

**Since:** 8

**System capability:** SystemCapability.Sensors.Sensor

## Modules to Import

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## x

```TypeScript
x: number
```

Acceleration along the x-axis of the device, in m/s?. The value is equal to the reported physical quantity.

**Type:** number

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Sensors.Sensor

## y

```TypeScript
y: number
```

Acceleration along the y-axis of the device, in m/s?. The value is equal to the reported physical quantity.

**Type:** number

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Sensors.Sensor

## z

```TypeScript
z: number
```

Acceleration along the z-axis of the device, in m/s?. The value is equal to the reported physical quantity.

**Type:** number

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Sensors.Sensor
