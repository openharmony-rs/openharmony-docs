# Location

```TypeScript
export interface Location
```

Provides information about geographic locations.

**Since:** 9

<!--Device-geoLocationManager-export interface Location--><!--Device-geoLocationManager-export interface Location-End-->

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

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-Location-accuracy: double--><!--Device-Location-accuracy: double-End-->

**System capability:** SystemCapability.Location.Location.Core

## additions

```TypeScript
additions?: Array<string>
```

Indicates additional information.

**Type:** Array&lt;string&gt;

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-Location-additions?: Array<string>--><!--Device-Location-additions?: Array<string>-End-->

**System capability:** SystemCapability.Location.Location.Core

## additionSize

```TypeScript
additionSize?: number
```

Indicates the amount of additional descriptive information.

**Type:** number

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-Location-additionSize?: int--><!--Device-Location-additionSize?: int-End-->

**System capability:** SystemCapability.Location.Location.Core

## additionsMap

```TypeScript
additionsMap?: Map<string, string>
```

Indicates additional information map.

**Type:** Map&lt;string, string&gt;

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-Location-additionsMap?: Map<string, string>--><!--Device-Location-additionsMap?: Map<string, string>-End-->

**System capability:** SystemCapability.Location.Location.Core

## altitude

```TypeScript
altitude: number
```

Indicates location altitude, in meters.

**Type:** number

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-Location-altitude: double--><!--Device-Location-altitude: double-End-->

**System capability:** SystemCapability.Location.Location.Core

## altitudeAccuracy

```TypeScript
altitudeAccuracy?: number
```

Indicates vertical position accuracy in meters.

**Type:** number

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-Location-altitudeAccuracy?: double--><!--Device-Location-altitudeAccuracy?: double-End-->

**System capability:** SystemCapability.Location.Location.Core

## direction

```TypeScript
direction: number
```

Indicates direction information.

**Type:** number

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-Location-direction: double--><!--Device-Location-direction: double-End-->

**System capability:** SystemCapability.Location.Location.Core

## directionAccuracy

```TypeScript
directionAccuracy?: number
```

Indicates direction accuracy in degrees.

**Type:** number

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-Location-directionAccuracy?: double--><!--Device-Location-directionAccuracy?: double-End-->

**System capability:** SystemCapability.Location.Location.Core

## isFromMock

```TypeScript
isFromMock?: boolean
```

Indicates whether the location is mocked.

**Type:** boolean

**Since:** 26.0.0

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-Location-isFromMock?: boolean--><!--Device-Location-isFromMock?: boolean-End-->

**System capability:** SystemCapability.Location.Location.Core

## latitude

```TypeScript
latitude: number
```

Indicates latitude information. A positive value indicates north latitude, and a negative value indicates south latitude.

**Type:** number

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-Location-latitude: double--><!--Device-Location-latitude: double-End-->

**System capability:** SystemCapability.Location.Location.Core

## longitude

```TypeScript
longitude: number
```

Indicates Longitude information. A positive value indicates east longitude , and a negative value indicates west longitude.

**Type:** number

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-Location-longitude: double--><!--Device-Location-longitude: double-End-->

**System capability:** SystemCapability.Location.Location.Core

## poi

```TypeScript
poi?: PoiInfo
```

Indicates the poi information.

**Type:** [PoiInfo](arkts-location-geolocationmanager-poiinfo-i.md)

**Since:** 19

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 19.

<!--Device-Location-poi?: PoiInfo--><!--Device-Location-poi?: PoiInfo-End-->

**System capability:** SystemCapability.Location.Location.Core

## sourceType

```TypeScript
sourceType?: LocationSourceType
```

Indicates the source of the location.

**Type:** [LocationSourceType](arkts-location-geolocationmanager-locationsourcetype-e.md)

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-Location-sourceType?: LocationSourceType--><!--Device-Location-sourceType?: LocationSourceType-End-->

**System capability:** SystemCapability.Location.Location.Core

## speed

```TypeScript
speed: number
```

Indicates speed, in m/s.

**Type:** number

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-Location-speed: double--><!--Device-Location-speed: double-End-->

**System capability:** SystemCapability.Location.Location.Core

## speedAccuracy

```TypeScript
speedAccuracy?: number
```

Indicates speed accuracy in meter per seconds.

**Type:** number

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-Location-speedAccuracy?: double--><!--Device-Location-speedAccuracy?: double-End-->

**System capability:** SystemCapability.Location.Location.Core

## timeSinceBoot

```TypeScript
timeSinceBoot: number
```

Indicates location timestamp since boot.

**Type:** number

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-Location-timeSinceBoot: long--><!--Device-Location-timeSinceBoot: long-End-->

**System capability:** SystemCapability.Location.Location.Core

## timeStamp

```TypeScript
timeStamp: number
```

Indicates location timestamp in the UTC format.

**Type:** number

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-Location-timeStamp: long--><!--Device-Location-timeStamp: long-End-->

**System capability:** SystemCapability.Location.Location.Core

## uncertaintyOfTimeSinceBoot

```TypeScript
uncertaintyOfTimeSinceBoot?: number
```

Time uncertainty Of timeSinceBoot in nanosecond.

**Type:** number

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-Location-uncertaintyOfTimeSinceBoot?: long--><!--Device-Location-uncertaintyOfTimeSinceBoot?: long-End-->

**System capability:** SystemCapability.Location.Location.Core
