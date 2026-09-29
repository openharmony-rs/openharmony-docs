# OrientationResponse

```TypeScript
interface OrientationResponse extends Response
```

Describes the orientation sensor data. It extends from [Response](arkts-sensorservice-sensor-response-i.md).

**Atomic service API**: This API can be used in atomic services since API version 11.

**Inheritance/Implementation:** OrientationResponse extends [Response](arkts-sensorservice-sensor-response-i.md)

**Since:** 8

<!--Device-sensor-interface OrientationResponse extends Response--><!--Device-sensor-interface OrientationResponse extends Response-End-->

**System capability:** SystemCapability.Sensors.Sensor

## Modules to Import

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## alpha

```TypeScript
alpha: number
```

Rotation angle of the device around the z-axis, that is, the yaw angle, in degrees. The value range is [0, 360].

**Type:** number

**Since:** 8

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-OrientationResponse-alpha: double--><!--Device-OrientationResponse-alpha: double-End-->

**System capability:** SystemCapability.Sensors.Sensor

## beta

```TypeScript
beta: number
```

Rotation angle of the device around the x-axis, that is, the pitch angle, in degrees. The value range is [–180, 180].

**Type:** number

**Since:** 8

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-OrientationResponse-beta: double--><!--Device-OrientationResponse-beta: double-End-->

**System capability:** SystemCapability.Sensors.Sensor

## gamma

```TypeScript
gamma: number
```

Rotation angle of the device around the y-axis, that is, the roll angle, in degrees. The value range is [–90, 90].

**Type:** number

**Since:** 8

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-OrientationResponse-gamma: double--><!--Device-OrientationResponse-gamma: double-End-->

**System capability:** SystemCapability.Sensors.Sensor
