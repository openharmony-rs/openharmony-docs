# ZoneRules

```TypeScript
export class ZoneRules
```

Queries the time zone transition rule.

**Since:** 20

<!--Device-i18n-export class ZoneRules--><!--Device-i18n-export class ZoneRules-End-->

**System capability:** SystemCapability.Global.I18n

## Modules to Import

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## nextTransition

```TypeScript
public nextTransition(date?: number): ZoneOffsetTransition
```

Obtains the **nextTransition** object for the specified time.

**Since:** 20

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 20.

<!--Device-ZoneRules-public nextTransition(date?: double): ZoneOffsetTransition--><!--Device-ZoneRules-public nextTransition(date?: double): ZoneOffsetTransition-End-->

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| date | number | No |  |

**Return value:**

| Type | Description |
| --- | --- |
| [ZoneOffsetTransition](arkts-localization-i18n-zoneoffsettransition-c.md) | **ZoneOffsetTransition** object for next transition. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

// Obtain the time zone of Tijuana.
let timeZone: i18n.TimeZone = i18n.getTimeZone('America/Tijuana');
// Obtain the time zone transition rule of Tijuana.
let zoneRules: i18n.ZoneRules = timeZone.getZoneRules();
let date = new Date(2025, 4, 13);
// Obtain the next time zone transition for Tijuana after May 13, 2025.
let zoneOffsetTransition: i18n.ZoneOffsetTransition = zoneRules.nextTransition(date.getTime());
```
