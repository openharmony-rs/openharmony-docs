# GeoAddress

```TypeScript
export interface GeoAddress
```

Data struct describes geographic locations.

**Since:** 9

<!--Device-geoLocationManager-export interface GeoAddress--><!--Device-geoLocationManager-export interface GeoAddress-End-->

**System capability:** SystemCapability.Location.Location.Geocoder

## Modules to Import

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
```

## addressUrl

```TypeScript
addressUrl?: string
```

Indicates website URL.

**Type:** string

**Since:** 9

<!--Device-GeoAddress-addressUrl?: string--><!--Device-GeoAddress-addressUrl?: string-End-->

**System capability:** SystemCapability.Location.Location.Geocoder

## administrativeArea

```TypeScript
administrativeArea?: string
```

Indicates administrative region name.

**Type:** string

**Since:** 9

<!--Device-GeoAddress-administrativeArea?: string--><!--Device-GeoAddress-administrativeArea?: string-End-->

**System capability:** SystemCapability.Location.Location.Geocoder

## countryCode

```TypeScript
countryCode?: string
```

Indicates country code.

**Type:** string

**Since:** 9

<!--Device-GeoAddress-countryCode?: string--><!--Device-GeoAddress-countryCode?: string-End-->

**System capability:** SystemCapability.Location.Location.Geocoder

## countryName

```TypeScript
countryName?: string
```

Indicates country name.

**Type:** string

**Since:** 9

<!--Device-GeoAddress-countryName?: string--><!--Device-GeoAddress-countryName?: string-End-->

**System capability:** SystemCapability.Location.Location.Geocoder

## descriptions

```TypeScript
descriptions?: Array<string>
```

Indicates additional information.

**Type:** Array&lt;string&gt;

**Since:** 9

<!--Device-GeoAddress-descriptions?: Array<string>--><!--Device-GeoAddress-descriptions?: Array<string>-End-->

**System capability:** SystemCapability.Location.Location.Geocoder

## descriptionsSize

```TypeScript
descriptionsSize?: number
```

Indicates the amount of additional descriptive information.

**Type:** number

**Since:** 9

<!--Device-GeoAddress-descriptionsSize?: int--><!--Device-GeoAddress-descriptionsSize?: int-End-->

**System capability:** SystemCapability.Location.Location.Geocoder

## latitude

```TypeScript
latitude?: number
```

Indicates latitude information. A positive value indicates north latitude, and a negative value indicates south latitude.

**Type:** number

**Since:** 9

<!--Device-GeoAddress-latitude?: double--><!--Device-GeoAddress-latitude?: double-End-->

**System capability:** SystemCapability.Location.Location.Geocoder

## locale

```TypeScript
locale?: string
```

Indicates language used for the location description. zh indicates Chinese, and en indicates English.

**Type:** string

**Since:** 9

<!--Device-GeoAddress-locale?: string--><!--Device-GeoAddress-locale?: string-End-->

**System capability:** SystemCapability.Location.Location.Geocoder

## locality

```TypeScript
locality?: string
```

Indicates locality information.

**Type:** string

**Since:** 9

<!--Device-GeoAddress-locality?: string--><!--Device-GeoAddress-locality?: string-End-->

**System capability:** SystemCapability.Location.Location.Geocoder

## longitude

```TypeScript
longitude?: number
```

Indicates longitude information. A positive value indicates east longitude , and a negative value indicates west longitude.

**Type:** number

**Since:** 9

<!--Device-GeoAddress-longitude?: double--><!--Device-GeoAddress-longitude?: double-End-->

**System capability:** SystemCapability.Location.Location.Geocoder

## phoneNumber

```TypeScript
phoneNumber?: string
```

Indicates phone number.

**Type:** string

**Since:** 9

<!--Device-GeoAddress-phoneNumber?: string--><!--Device-GeoAddress-phoneNumber?: string-End-->

**System capability:** SystemCapability.Location.Location.Geocoder

## placeName

```TypeScript
placeName?: string
```

Indicates detailed address information.

**Type:** string

**Since:** 9

<!--Device-GeoAddress-placeName?: string--><!--Device-GeoAddress-placeName?: string-End-->

**System capability:** SystemCapability.Location.Location.Geocoder

## postalCode

```TypeScript
postalCode?: string
```

Indicates postal code.

**Type:** string

**Since:** 9

<!--Device-GeoAddress-postalCode?: string--><!--Device-GeoAddress-postalCode?: string-End-->

**System capability:** SystemCapability.Location.Location.Geocoder

## premises

```TypeScript
premises?: string
```

Indicates house information.

**Type:** string

**Since:** 9

<!--Device-GeoAddress-premises?: string--><!--Device-GeoAddress-premises?: string-End-->

**System capability:** SystemCapability.Location.Location.Geocoder

## roadName

```TypeScript
roadName?: string
```

Indicates road name.

**Type:** string

**Since:** 9

<!--Device-GeoAddress-roadName?: string--><!--Device-GeoAddress-roadName?: string-End-->

**System capability:** SystemCapability.Location.Location.Geocoder

## subAdministrativeArea

```TypeScript
subAdministrativeArea?: string
```

Indicates sub-administrative region name.

**Type:** string

**Since:** 9

<!--Device-GeoAddress-subAdministrativeArea?: string--><!--Device-GeoAddress-subAdministrativeArea?: string-End-->

**System capability:** SystemCapability.Location.Location.Geocoder

## subLocality

```TypeScript
subLocality?: string
```

Indicates sub-locality information.

**Type:** string

**Since:** 9

<!--Device-GeoAddress-subLocality?: string--><!--Device-GeoAddress-subLocality?: string-End-->

**System capability:** SystemCapability.Location.Location.Geocoder

## subRoadName

```TypeScript
subRoadName?: string
```

Indicates auxiliary road information.

**Type:** string

**Since:** 9

<!--Device-GeoAddress-subRoadName?: string--><!--Device-GeoAddress-subRoadName?: string-End-->

**System capability:** SystemCapability.Location.Location.Geocoder
