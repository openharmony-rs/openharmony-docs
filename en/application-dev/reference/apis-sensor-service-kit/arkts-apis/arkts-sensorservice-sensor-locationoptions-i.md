# LocationOptions

```TypeScript
interface LocationOptions
```

Indicates the geographical location, which is used to pass the longitude, latitude, and altitude information for calculating the geomagnetic field.

**Since:** 8

<!--Device-sensor-interface LocationOptions--><!--Device-sensor-interface LocationOptions-End-->

**System capability:** SystemCapability.Sensors.Sensor

## Modules to Import

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## altitude

```TypeScript
altitude: number
```

Altitude. Unit: m

**Type:** number

**Since:** 8

<!--Device-LocationOptions-altitude: double--><!--Device-LocationOptions-altitude: double-End-->

**System capability:** SystemCapability.Sensors.Sensor

## latitude

```TypeScript
latitude: number
```

Latitude. Value range: [-90, 90]. Unit: degree

**Type:** number

**Since:** 8

<!--Device-LocationOptions-latitude: double--><!--Device-LocationOptions-latitude: double-End-->

**System capability:** SystemCapability.Sensors.Sensor

## longitude

```TypeScript
longitude: number
```

Longitude. Value range: [-180, 180]. Unit: degree

**Type:** number

**Since:** 8

<!--Device-LocationOptions-longitude: double--><!--Device-LocationOptions-longitude: double-End-->

**System capability:** SystemCapability.Sensors.Sensor
