# GyroscopeResponse

```TypeScript
interface GyroscopeResponse extends Response
```

Describes the gyroscope sensor data. It extends from [Response](arkts-sensorservice-sensor-response-i.md).

**Atomic service API**: This API can be used in atomic services since API version 11.

**Inheritance/Implementation:** GyroscopeResponse extends [Response](arkts-sensorservice-sensor-response-i.md)

**Since:** 8

<!--Device-sensor-interface GyroscopeResponse extends Response--><!--Device-sensor-interface GyroscopeResponse extends Response-End-->

**System capability:** SystemCapability.Sensors.Sensor

## Modules to Import

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## x

```TypeScript
x: number
```

Rotational angular velocity of the x-axis. in rad/s. The value is equal to the reported physical quantity.

**Type:** number

**Since:** 8

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-GyroscopeResponse-x: double--><!--Device-GyroscopeResponse-x: double-End-->

**System capability:** SystemCapability.Sensors.Sensor

## y

```TypeScript
y: number
```

Rotational angular velocity of the y-axis. in rad/s. The value is equal to the reported physical quantity.

**Type:** number

**Since:** 8

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-GyroscopeResponse-y: double--><!--Device-GyroscopeResponse-y: double-End-->

**System capability:** SystemCapability.Sensors.Sensor

## z

```TypeScript
z: number
```

Rotational angular velocity of the z-axis. in rad/s. The value is equal to the reported physical quantity.

**Type:** number

**Since:** 8

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-GyroscopeResponse-z: double--><!--Device-GyroscopeResponse-z: double-End-->

**System capability:** SystemCapability.Sensors.Sensor
