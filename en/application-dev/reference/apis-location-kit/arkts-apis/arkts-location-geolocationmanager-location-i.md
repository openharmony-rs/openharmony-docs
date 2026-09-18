# Location

Provides information about geographic locations.

**Since:** 9

**System capability:** SystemCapability.Location.Location.Core

## Modules to Import

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
```

## accuracy

```TypeScript
accuracy: number
```

Indicates location accuracy, in meters.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Location.Location.Core

## additions

```TypeScript
additions?: Array<string>
```

Indicates additional information.

**Type:** Array&lt;string&gt;

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Location.Location.Core

## additionSize

```TypeScript
additionSize?: number
```

Indicates the amount of additional descriptive information.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Location.Location.Core

## additionsMap

```TypeScript
additionsMap?: Map<string, string>
```

Indicates additional information map.

**Type:** Map&lt;string, string&gt;

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Location.Location.Core

## altitude

```TypeScript
altitude: number
```

Indicates location altitude, in meters.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Location.Location.Core

## altitudeAccuracy

```TypeScript
altitudeAccuracy?: number
```

Indicates vertical position accuracy in meters.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Location.Location.Core

## direction

```TypeScript
direction: number
```

Indicates direction information.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Location.Location.Core

## directionAccuracy

```TypeScript
directionAccuracy?: number
```

Indicates direction accuracy in degrees.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Location.Location.Core

## isFromMock

```TypeScript
isFromMock?: boolean
```

Indicates whether the location is mocked.

**Type:** boolean

**Since:** 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Location.Location.Core

## latitude

```TypeScript
latitude: number
```

Indicates latitude information. A positive value indicates north latitude, and a negative value indicates south latitude.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Location.Location.Core

## longitude

```TypeScript
longitude: number
```

Indicates Longitude information. A positive value indicates east longitude , and a negative value indicates west longitude.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Location.Location.Core

## poi

```TypeScript
poi?: PoiInfo
```

Indicates the poi information.

**Type:** [PoiInfo](arkts-location-geolocationmanager-poiinfo-i.md)

**Since:** 19

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Location.Location.Core

## sourceType

```TypeScript
sourceType?: LocationSourceType
```

Indicates the source of the location.

**Type:** [LocationSourceType](arkts-location-geolocationmanager-locationsourcetype-e.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Location.Location.Core

## speed

```TypeScript
speed: number
```

Indicates speed, in m/s.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Location.Location.Core

## speedAccuracy

```TypeScript
speedAccuracy?: number
```

Indicates speed accuracy in meter per seconds.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Location.Location.Core

## timeSinceBoot

```TypeScript
timeSinceBoot: number
```

Indicates location timestamp since boot.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Location.Location.Core

## timeStamp

```TypeScript
timeStamp: number
```

Indicates location timestamp in the UTC format.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Location.Location.Core

## uncertaintyOfTimeSinceBoot

```TypeScript
uncertaintyOfTimeSinceBoot?: number
```

Time uncertainty Of timeSinceBoot in nanosecond.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Location.Location.Core
