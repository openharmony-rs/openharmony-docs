# ReverseGeoCodeRequest

```TypeScript
export interface ReverseGeoCodeRequest
```

Configuring parameters in reverse geocode requests.

**Since:** 9

<!--Device-geoLocationManager-export interface ReverseGeoCodeRequest--><!--Device-geoLocationManager-export interface ReverseGeoCodeRequest-End-->

**System capability:** SystemCapability.Location.Location.Geocoder

## Modules to Import

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
```

## country

```TypeScript
country?: string
```

Indicates the country information.

**Type:** string

**Since:** 12

<!--Device-ReverseGeoCodeRequest-country?: string--><!--Device-ReverseGeoCodeRequest-country?: string-End-->

**System capability:** SystemCapability.Location.Location.Geocoder

## latitude

```TypeScript
latitude: number
```

Latitude for reverse geocoding query.

**Type:** number

**Since:** 9

<!--Device-ReverseGeoCodeRequest-latitude: double--><!--Device-ReverseGeoCodeRequest-latitude: double-End-->

**System capability:** SystemCapability.Location.Location.Geocoder

## locale

```TypeScript
locale?: string
```

Indicates the language area information.

**Type:** string

**Since:** 9

<!--Device-ReverseGeoCodeRequest-locale?: string--><!--Device-ReverseGeoCodeRequest-locale?: string-End-->

**System capability:** SystemCapability.Location.Location.Geocoder

## longitude

```TypeScript
longitude: number
```

Longitude for reverse geocoding query.

**Type:** number

**Since:** 9

<!--Device-ReverseGeoCodeRequest-longitude: double--><!--Device-ReverseGeoCodeRequest-longitude: double-End-->

**System capability:** SystemCapability.Location.Location.Geocoder

## maxItems

```TypeScript
maxItems?: number
```

Indicates the maximum number of addresses returned by reverse geocoding query.

**Type:** number

**Since:** 9

<!--Device-ReverseGeoCodeRequest-maxItems?: int--><!--Device-ReverseGeoCodeRequest-maxItems?: int-End-->

**System capability:** SystemCapability.Location.Location.Geocoder
