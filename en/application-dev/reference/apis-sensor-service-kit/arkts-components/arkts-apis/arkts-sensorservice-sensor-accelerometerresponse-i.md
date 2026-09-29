# AccelerometerResponse

```TypeScript
interface AccelerometerResponse extends Response
```

Describes the acceleration sensor data. It extends from [Response](arkts-sensorservice-sensor-response-i.md).

**Atomic service API**: This API can be used in atomic services since API version 11.

**Inheritance/Implementation:** AccelerometerResponse extends [Response](arkts-sensorservice-sensor-response-i.md)

**Since:** 8

<!--Device-sensor-interface AccelerometerResponse extends Response--><!--Device-sensor-interface AccelerometerResponse extends Response-End-->

**System capability:** SystemCapability.Sensors.Sensor

## Modules to Import

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## x

```TypeScript
x: number
```

Acceleration along the x-axis of the device, in m/s². The value is equal to the reported physical quantity.

**Type:** number

**Since:** 8

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-AccelerometerResponse-x: double--><!--Device-AccelerometerResponse-x: double-End-->

**System capability:** SystemCapability.Sensors.Sensor

## y

```TypeScript
y: number
```

Acceleration along the y-axis of the device, in m/s². The value is equal to the reported physical quantity.

**Type:** number

**Since:** 8

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-AccelerometerResponse-y: double--><!--Device-AccelerometerResponse-y: double-End-->

**System capability:** SystemCapability.Sensors.Sensor

## z

```TypeScript
z: number
```

Acceleration along the z-axis of the device, in m/s². The value is equal to the reported physical quantity.

**Type:** number

**Since:** 8

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-AccelerometerResponse-z: double--><!--Device-AccelerometerResponse-z: double-End-->

**System capability:** SystemCapability.Sensors.Sensor
