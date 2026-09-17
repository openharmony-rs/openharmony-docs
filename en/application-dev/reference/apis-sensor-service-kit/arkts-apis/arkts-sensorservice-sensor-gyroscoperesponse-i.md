# GyroscopeResponse

Describes the gyroscope sensor data. It extends from [Response](arkts-sensorservice-sensor-response-i.md).

**Inheritance/Implementation:** GyroscopeResponse extends [Response](arkts-sensorservice-sensor-response-i.md)

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

Angular velocity of rotation around the x-axis of the device, in rad/s. The value is equal to the reported physical quantity.

**Type:** number

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Sensors.Sensor

## y

```TypeScript
y: number
```

Angular velocity of rotation around the y-axis of the device, in rad/s. The value is equal to the reported physical quantity.

**Type:** number

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Sensors.Sensor

## z

```TypeScript
z: number
```

Angular velocity of rotation around the z-axis of the device, in rad/s. The value is equal to the reported physical quantity.

**Type:** number

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Sensors.Sensor
