# CachedGnssLocationsRequest

```TypeScript
export interface CachedGnssLocationsRequest
```

Parameters for requesting to report cache location information.

**Since:** 9

<!--Device-geoLocationManager-export interface CachedGnssLocationsRequest--><!--Device-geoLocationManager-export interface CachedGnssLocationsRequest-End-->

**System capability:** SystemCapability.Location.Location.Gnss

## Modules to Import

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
```

## reportingPeriodSec

```TypeScript
reportingPeriodSec: number
```

GNSS cache location report period.

**Type:** number

**Since:** 9

<!--Device-CachedGnssLocationsRequest-reportingPeriodSec: int--><!--Device-CachedGnssLocationsRequest-reportingPeriodSec: int-End-->

**System capability:** SystemCapability.Location.Location.Gnss

## wakeUpCacheQueueFull

```TypeScript
wakeUpCacheQueueFull: boolean
```

Indicates whether to wake up the listener when the GNSS cache location queue is full.

**Type:** boolean

**Since:** 9

<!--Device-CachedGnssLocationsRequest-wakeUpCacheQueueFull: boolean--><!--Device-CachedGnssLocationsRequest-wakeUpCacheQueueFull: boolean-End-->

**System capability:** SystemCapability.Location.Location.Gnss
