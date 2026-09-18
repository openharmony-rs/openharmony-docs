# getCalendar

## Modules to Import

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## getCalendar

```TypeScript
export function getCalendar(locale: string, type?: string): Calendar
```

Obtains the **Calendar** object for the specified locale and calendar type.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| locale | string | Yes | [Locale ID](../../../internationalization/i18n-locale-culture.md#how-it-works), which consists of the language, script, and country/region, for example, **zh-Hans-CN**. |
| type | string | No | Calendar. The value can be buddhist, chinese, coptic, ethiopic, hebrew, gregory, indian,  islamic_civil, islamic_tbla, islamic_umalqura, japanese,  or persian. The default value is the default calendar of the locale. For details about the meanings and application scenarios of different values, see [Calendar Setting](../../../internationalization/i18n-calendar.md). |

**Return value:**

| Type | Description |
| --- | --- |
| [Calendar](arkts-localization-i18n-calendar-c.md) | **Calendar** object. |

**Examples**

```TypeScript
let calendar: i18n.Calendar = i18n.getCalendar('zh-Hans', 'chinese'); // Obtain the Calendar object for the Chinese lunar calendar.
```
