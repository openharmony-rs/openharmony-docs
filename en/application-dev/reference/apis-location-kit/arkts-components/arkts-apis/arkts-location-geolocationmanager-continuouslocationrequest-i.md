# ContinuousLocationRequest

```TypeScript
export interface ContinuousLocationRequest
```

Configuring parameters in continuous location requests.

**Since:** 12

<!--Device-geoLocationManager-export interface ContinuousLocationRequest--><!--Device-geoLocationManager-export interface ContinuousLocationRequest-End-->

**System capability:** SystemCapability.Location.Location.Core

## Modules to Import

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
```

## interval

```TypeScript
interval: number
```

Location report interval, in seconds.

**Type:** number

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ContinuousLocationRequest-interval: int--><!--Device-ContinuousLocationRequest-interval: int-End-->

**System capability:** SystemCapability.Location.Location.Core

## locationScenario

```TypeScript
locationScenario: UserActivityScenario | PowerConsumptionScenario
```

Location scenario. You can select a user activity scenario or power consumption scenario.

**Type:** [UserActivityScenario](arkts-location-geolocationmanager-useractivityscenario-e.md) &#124; [PowerConsumptionScenario](arkts-location-geolocationmanager-powerconsumptionscenario-e.md)

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ContinuousLocationRequest-locationScenario: UserActivityScenario | PowerConsumptionScenario--><!--Device-ContinuousLocationRequest-locationScenario: UserActivityScenario | PowerConsumptionScenario-End-->

**System capability:** SystemCapability.Location.Location.Core

## needPoi

```TypeScript
needPoi?: boolean
```

Indicates whether to obtain POI information near the current location.

**Type:** boolean

**Since:** 19

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 19.

<!--Device-ContinuousLocationRequest-needPoi?: boolean--><!--Device-ContinuousLocationRequest-needPoi?: boolean-End-->

**System capability:** SystemCapability.Location.Location.Core

## sportsType

```TypeScript
sportsType?: SportsType
```

Indicates the type of sports. This parameter is valid only when locationScenario is set to UserActivityScenario.SPORT.

**Type:** [SportsType](arkts-location-geolocationmanager-sportstype-e.md)

**Since:** 26.0.0

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 18.

<!--Device-ContinuousLocationRequest-sportsType?: SportsType--><!--Device-ContinuousLocationRequest-sportsType?: SportsType-End-->

**System capability:** SystemCapability.Location.Location.Core
