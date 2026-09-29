# SingleLocationRequest

```TypeScript
export interface SingleLocationRequest
```

Configuring parameters in single location requests.

**Since:** 12

<!--Device-geoLocationManager-export interface SingleLocationRequest--><!--Device-geoLocationManager-export interface SingleLocationRequest-End-->

**System capability:** SystemCapability.Location.Location.Core

## Modules to Import

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
```

## locatingPriority

```TypeScript
locatingPriority: LocatingPriority
```

Priority of the location request.

**Type:** [LocatingPriority](arkts-location-geolocationmanager-locatingpriority-e.md)

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-SingleLocationRequest-locatingPriority: LocatingPriority--><!--Device-SingleLocationRequest-locatingPriority: LocatingPriority-End-->

**System capability:** SystemCapability.Location.Location.Core

## locatingTimeoutMs

```TypeScript
locatingTimeoutMs: number
```

Timeout of a single location request, in milliseconds.

**Type:** number

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-SingleLocationRequest-locatingTimeoutMs: int--><!--Device-SingleLocationRequest-locatingTimeoutMs: int-End-->

**System capability:** SystemCapability.Location.Location.Core

## needPoi

```TypeScript
needPoi?: boolean
```

Indicates whether to obtain POI information near the current location.

**Type:** boolean

**Since:** 19

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 19.

<!--Device-SingleLocationRequest-needPoi?: boolean--><!--Device-SingleLocationRequest-needPoi?: boolean-End-->

**System capability:** SystemCapability.Location.Location.Core
