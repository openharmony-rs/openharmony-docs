# getTimeZone

## Modules to Import

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## getTimeZone

```TypeScript
export function getTimeZone(zoneID?: string): TimeZone
```

Obtains the **TimeZone** object corresponding to the specified time zone ID.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| zoneID | string | No | Time zone ID. The default value is the system time zone. |

**Return value:**

| Type | Description |
| --- | --- |
| [TimeZone](arkts-localization-i18n-timezone-c.md) | **TimeZone** object corresponding to the time zone ID. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let timezone: i18n.TimeZone = i18n.getTimeZone('Asia/Shanghai');
```
