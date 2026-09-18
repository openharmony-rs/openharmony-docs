# ZoneOffsetTransition

Provides the API for obtaining a timezone transition information.

**Since:** 20

**System capability:** SystemCapability.Global.I18n

## Modules to Import

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## getMilliseconds

```TypeScript
public getMilliseconds(): number
```

Obtains the timestamp of the time zone transition point.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Global.I18n

**Return value:**

| Type | Description |
| --- | --- |
| number | Timestamp of the time zone transition point. It is measured as the number of milliseconds from 00:00:00 on January 1, 1970 (UTC) to the time zone transition point, for example, 1762074000000. If the [raw offset](arkts-localization-i18n-timezone-c.md#getrawoffset) remains unchanged and DST is not used, **0** is returned. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let timeZone: i18n.TimeZone = i18n.getTimeZone('America/Tijuana');
let zoneRules: i18n.ZoneRules = timeZone.getZoneRules();
let date = new Date(2025, 4, 13);
let zoneOffsetTransition: i18n.ZoneOffsetTransition =
    zoneRules.nextTransition(date.getTime()); // Obtain the nextTransition object for time zone transition after May 13, 2025.
zoneOffsetTransition.getMilliseconds(); // Timestamp of the transition point: 1762074000000
```

## getOffsetAfter

```TypeScript
public getOffsetAfter(): number
```

Obtains the offset after the time zone transition.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Global.I18n

**Return value:**

| Type | Description |
| --- | --- |
| number | Post-transition offset, that is, the time difference between the post-transition time and UTC, measured in ms. For example, **-28800000** indicates that the time after the transition is 28800000 ms (8 hours) later than UTC. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let timeZone: i18n.TimeZone = i18n.getTimeZone('America/Tijuana');
let zoneRules: i18n.ZoneRules = timeZone.getZoneRules();
let date = new Date(2025, 4, 13);
let zoneOffsetTransition: i18n.ZoneOffsetTransition =
    zoneRules.nextTransition(date.getTime()); // Obtain the nextTransition object for time zone transition after May 13, 2025.
zoneOffsetTransition.getOffsetAfter(); // Post-transition offset: -28800000
```

## getOffsetBefore

```TypeScript
public getOffsetBefore(): number
```

Obtains the offset before the time zone transition.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Global.I18n

**Return value:**

| Type | Description |
| --- | --- |
| number | Pre-transition offset, that is, the time difference between the pre-transition time and UTC, measured in ms. For example, **-25200000** indicates that the pre-transition time is 25200000 ms (7 hours) slower than UTC. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let timeZone: i18n.TimeZone = i18n.getTimeZone('America/Tijuana');
let zoneRules: i18n.ZoneRules = timeZone.getZoneRules();
let date = new Date(2025, 4, 13);
let zoneOffsetTransition: i18n.ZoneOffsetTransition =
    zoneRules.nextTransition(date.getTime()); // Obtain the nextTransition object for time zone transition after May 13, 2025.
zoneOffsetTransition.getOffsetBefore(); // Pre-transition offset: -25200000
```
