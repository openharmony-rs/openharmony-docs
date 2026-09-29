# CurrentLocationRequest

```TypeScript
export interface CurrentLocationRequest
```

Configuring parameters in current location requests.

**Since:** 9

<!--Device-geoLocationManager-export interface CurrentLocationRequest--><!--Device-geoLocationManager-export interface CurrentLocationRequest-End-->

**System capability:** SystemCapability.Location.Location.Core

## Modules to Import

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
```

## maxAccuracy

```TypeScript
maxAccuracy?: number
```

Accuracy requirements for reporting locations.

**Type:** number

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-CurrentLocationRequest-maxAccuracy?: double--><!--Device-CurrentLocationRequest-maxAccuracy?: double-End-->

**System capability:** SystemCapability.Location.Location.Core

## priority

```TypeScript
priority?: LocationRequestPriority
```

Priority of the location request.

**Type:** [LocationRequestPriority](arkts-location-geolocationmanager-locationrequestpriority-e.md)

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-CurrentLocationRequest-priority?: LocationRequestPriority--><!--Device-CurrentLocationRequest-priority?: LocationRequestPriority-End-->

**System capability:** SystemCapability.Location.Location.Core

## scenario

```TypeScript
scenario?: LocationRequestScenario
```

User scenario of the location request.

**Type:** [LocationRequestScenario](arkts-location-geolocationmanager-locationrequestscenario-e.md)

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-CurrentLocationRequest-scenario?: LocationRequestScenario--><!--Device-CurrentLocationRequest-scenario?: LocationRequestScenario-End-->

**System capability:** SystemCapability.Location.Location.Core

## timeoutMs

```TypeScript
timeoutMs?: number
```

Timeout interval of a single location request.

**Type:** number

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-CurrentLocationRequest-timeoutMs?: int--><!--Device-CurrentLocationRequest-timeoutMs?: int-End-->

**System capability:** SystemCapability.Location.Location.Core
