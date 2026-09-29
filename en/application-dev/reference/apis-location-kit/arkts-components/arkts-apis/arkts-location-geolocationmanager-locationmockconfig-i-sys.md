# LocationMockConfig (System API)

```TypeScript
export interface LocationMockConfig
```

Parameters for configuring the location simulation function.

**Since:** 9

<!--Device-geoLocationManager-export interface LocationMockConfig--><!--Device-geoLocationManager-export interface LocationMockConfig-End-->

**System capability:** SystemCapability.Location.Location.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
```

## locations

```TypeScript
locations: Array<Location>
```

Mock location array.

**Type:** Array&lt;[Location](arkts-location-geolocationmanager-location-i.md)&gt;

**Since:** 9

<!--Device-LocationMockConfig-locations: Array<Location>--><!--Device-LocationMockConfig-locations: Array<Location>-End-->

**System capability:** SystemCapability.Location.Location.Core

**System API:** This is a system API.

## timeInterval

```TypeScript
timeInterval: number
```

Interval for reporting simulated locations.

**Type:** number

**Since:** 9

<!--Device-LocationMockConfig-timeInterval: int--><!--Device-LocationMockConfig-timeInterval: int-End-->

**System capability:** SystemCapability.Location.Location.Core

**System API:** This is a system API.
