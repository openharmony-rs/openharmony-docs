# MagneticFieldResponse

```TypeScript
interface MagneticFieldResponse extends Response
```

Describes the magnetic field sensor data. It extends from [Response](arkts-sensorservice-sensor-response-i.md).

**Inheritance/Implementation:** MagneticFieldResponse extends [Response](arkts-sensorservice-sensor-response-i.md)

**Since:** 8

<!--Device-sensor-interface MagneticFieldResponse extends Response--><!--Device-sensor-interface MagneticFieldResponse extends Response-End-->

**System capability:** SystemCapability.Sensors.Sensor

## Modules to Import

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## x

```TypeScript
x: number
```

Magnetic field strength along the x-axis, in μT.

**Type:** number

**Since:** 8

<!--Device-MagneticFieldResponse-x: double--><!--Device-MagneticFieldResponse-x: double-End-->

**System capability:** SystemCapability.Sensors.Sensor

## y

```TypeScript
y: number
```

Magnetic field strength along the y-axis, in μT.

**Type:** number

**Since:** 8

<!--Device-MagneticFieldResponse-y: double--><!--Device-MagneticFieldResponse-y: double-End-->

**System capability:** SystemCapability.Sensors.Sensor

## z

```TypeScript
z: number
```

Magnetic field strength along the z-axis, in μT.

**Type:** number

**Since:** 8

<!--Device-MagneticFieldResponse-z: double--><!--Device-MagneticFieldResponse-z: double-End-->

**System capability:** SystemCapability.Sensors.Sensor
