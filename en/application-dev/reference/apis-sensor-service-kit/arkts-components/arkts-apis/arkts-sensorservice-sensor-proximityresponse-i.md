# ProximityResponse

```TypeScript
interface ProximityResponse extends Response
```

Describes the proximity sensor data. It extends from [Response](arkts-sensorservice-sensor-response-i.md).

**Inheritance/Implementation:** ProximityResponse extends [Response](arkts-sensorservice-sensor-response-i.md)

**Since:** 8

<!--Device-sensor-interface ProximityResponse extends Response--><!--Device-sensor-interface ProximityResponse extends Response-End-->

**System capability:** SystemCapability.Sensors.Sensor

## Modules to Import

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## distance

```TypeScript
distance: number
```

Proximity between the visible object and the device monitor. Value range: **0** indicates that the object is close to the device, and a value greater than 0 indicates that the object is far away from the device.

**Type:** number

**Since:** 8

<!--Device-ProximityResponse-distance: double--><!--Device-ProximityResponse-distance: double-End-->

**System capability:** SystemCapability.Sensors.Sensor
