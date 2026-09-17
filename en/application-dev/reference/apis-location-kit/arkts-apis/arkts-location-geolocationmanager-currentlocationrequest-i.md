# CurrentLocationRequest

Configuring parameters in current location requests.

**Since:** 9

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

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Location.Location.Core

## priority

```TypeScript
priority?: LocationRequestPriority
```

Priority of the location request.

**Type:** [LocationRequestPriority](arkts-location-geolocationmanager-locationrequestpriority-e.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Location.Location.Core

## scenario

```TypeScript
scenario?: LocationRequestScenario
```

User scenario of the location request.

**Type:** [LocationRequestScenario](arkts-location-geolocationmanager-locationrequestscenario-e.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Location.Location.Core

## timeoutMs

```TypeScript
timeoutMs?: number
```

Timeout interval of a single location request.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Location.Location.Core
