# getSystemLocale

## Modules to Import

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## getSystemLocale

```TypeScript
export function getSystemLocale(): string
```

Obtains the system locale.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getSystemLocale](arkts-localization-i18n-system-c.md#getsystemlocale)

**System capability:** SystemCapability.Global.I18n

**Return value:**

| Type | Description |
| --- | --- |
| string | System locale ID. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let locale: string = i18n.getSystemLocale();
```
