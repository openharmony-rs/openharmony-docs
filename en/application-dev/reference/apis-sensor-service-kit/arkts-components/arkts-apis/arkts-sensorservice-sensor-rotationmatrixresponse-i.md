# RotationMatrixResponse

```TypeScript
interface RotationMatrixResponse
```

Response object for setting the rotation matrix, which describes the calculation results of the rotation matrix and tilt matrix.

**Since:** 8

<!--Device-sensor-interface RotationMatrixResponse--><!--Device-sensor-interface RotationMatrixResponse-End-->

**System capability:** SystemCapability.Sensors.Sensor

## Modules to Import

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## inclination

```TypeScript
inclination: Array<number>
```

Tilt matrix, which is a one-dimensional array with a length of 9 and indicates the geomagnetic tilt transformation matrix.

**Type:** Array&lt;number&gt;

**Since:** 8

<!--Device-RotationMatrixResponse-inclination: Array<double>--><!--Device-RotationMatrixResponse-inclination: Array<double>-End-->

**System capability:** SystemCapability.Sensors.Sensor

## rotation

```TypeScript
rotation: Array<number>
```

Rotation matrix, which is a one-dimensional array with a length of 9, indicating the rotation status of the device in three-dimensional space.

**Type:** Array&lt;number&gt;

**Since:** 8

<!--Device-RotationMatrixResponse-rotation: Array<double>--><!--Device-RotationMatrixResponse-rotation: Array<double>-End-->

**System capability:** SystemCapability.Sensors.Sensor
