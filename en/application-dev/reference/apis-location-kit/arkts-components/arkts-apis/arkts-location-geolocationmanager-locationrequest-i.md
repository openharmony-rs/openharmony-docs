# LocationRequest

```TypeScript
export interface LocationRequest
```

Configuring parameters in location requests.

**Since:** 9

<!--Device-geoLocationManager-export interface LocationRequest--><!--Device-geoLocationManager-export interface LocationRequest-End-->

**System capability:** SystemCapability.Location.Location.Core

## Modules to Import

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
```

## distanceInterval

```TypeScript
distanceInterval?: number
```

Location report distance interval.

**Type:** number

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-LocationRequest-distanceInterval?: double--><!--Device-LocationRequest-distanceInterval?: double-End-->

**System capability:** SystemCapability.Location.Location.Core

## maxAccuracy

```TypeScript
maxAccuracy?: number
```

Accuracy requirements for reporting locations.

**Type:** number

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-LocationRequest-maxAccuracy?: double--><!--Device-LocationRequest-maxAccuracy?: double-End-->

**System capability:** SystemCapability.Location.Location.Core

## priority

```TypeScript
priority?: LocationRequestPriority
```

Priority of the location request.

**Type:** [LocationRequestPriority](arkts-location-geolocationmanager-locationrequestpriority-e.md)

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-LocationRequest-priority?: LocationRequestPriority--><!--Device-LocationRequest-priority?: LocationRequestPriority-End-->

**System capability:** SystemCapability.Location.Location.Core

## scenario

```TypeScript
scenario?: LocationRequestScenario
```

User scenario of the location request.

**Type:** [LocationRequestScenario](arkts-location-geolocationmanager-locationrequestscenario-e.md)

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-LocationRequest-scenario?: LocationRequestScenario--><!--Device-LocationRequest-scenario?: LocationRequestScenario-End-->

**System capability:** SystemCapability.Location.Location.Core

## timeInterval

```TypeScript
timeInterval?: number
```

Location report interval.

**Type:** number

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-LocationRequest-timeInterval?: int--><!--Device-LocationRequest-timeInterval?: int-End-->

**System capability:** SystemCapability.Location.Location.Core
