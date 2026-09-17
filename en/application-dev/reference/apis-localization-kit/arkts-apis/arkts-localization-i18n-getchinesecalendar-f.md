# getChineseCalendar

## Modules to Import

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## getChineseCalendar

```TypeScript
export function getChineseCalendar(locale?: Intl.Locale): ChineseCalendar
```

Obtains the ChineseCalendar object for the specified locale.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| locale | [Intl.Locale](arkts-localization-intl-locale-c.md) | No | Locale object. The default value is the current system locale. |

**Return value:**

| Type | Description |
| --- | --- |
| [ChineseCalendar](arkts-localization-i18n-chinesecalendar-c.md) | ChineseCalendar object. |

**Examples**

```TypeScript
let locale: Intl.Locale = i18n.System.getSystemLocaleInstance();
let calendar: i18n.ChineseCalendar = i18n.getChineseCalendar(locale);
```
