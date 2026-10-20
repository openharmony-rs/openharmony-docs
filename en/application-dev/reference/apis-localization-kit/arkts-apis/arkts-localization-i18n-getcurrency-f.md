# getCurrency

## Modules to Import

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## getCurrency

```TypeScript
export function getCurrency(locale: Intl.Locale): Currency
```

Obtains the **currency** object of the specified locale environment.

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

<!--Device-i18n-export function getCurrency(locale: Intl.Locale): Currency--><!--Device-i18n-export function getCurrency(locale: Intl.Locale): Currency-End-->

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| locale | [Intl.Locale](arkts-localization-intl-locale-c.md) | Yes | **Locale Object.** Obtains region-related parameters. |

**Return value:**

| Type | Description |
| --- | --- |
| [Currency](arkts-localization-i18n-currency-c.md) | **Currency** object. |
