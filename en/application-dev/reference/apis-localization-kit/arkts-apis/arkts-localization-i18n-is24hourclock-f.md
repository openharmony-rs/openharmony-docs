# is24HourClock

## Modules to Import

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## is24HourClock

```TypeScript
export function is24HourClock(): boolean
```

Checks whether the 24-hour clock is used.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [is24HourClock](arkts-localization-i18n-system-c.md#is24hourclock)

**System capability:** SystemCapability.Global.I18n

**Return value:**

| Type | Description |
| --- | --- |
| boolean | **true** if the 24-hour clock is used, and **false** otherwise. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let is24HourClock: boolean = i18n.is24HourClock();
```
