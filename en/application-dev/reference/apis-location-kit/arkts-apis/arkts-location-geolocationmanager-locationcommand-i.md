# LocationCommand

```TypeScript
export interface LocationCommand
```

Location subsystem command structure.

**Since:** 9

<!--Device-geoLocationManager-export interface LocationCommand--><!--Device-geoLocationManager-export interface LocationCommand-End-->

**System capability:** SystemCapability.Location.Location.Core

## Modules to Import

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
```

## command

```TypeScript
command: string
```

Sent command content.

**Type:** string

**Since:** 9

<!--Device-LocationCommand-command: string--><!--Device-LocationCommand-command: string-End-->

**System capability:** SystemCapability.Location.Location.Core

## scenario

```TypeScript
scenario: LocationRequestScenario
```

Information about the scenario where the command is sent.

**Type:** [LocationRequestScenario](arkts-location-geolocationmanager-locationrequestscenario-e.md)

**Since:** 9

<!--Device-LocationCommand-scenario: LocationRequestScenario--><!--Device-LocationCommand-scenario: LocationRequestScenario-End-->

**System capability:** SystemCapability.Location.Location.Core
