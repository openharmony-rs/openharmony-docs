# getFirstPreferredLanguage

## Modules to Import

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## getFirstPreferredLanguage

```TypeScript
export function getFirstPreferredLanguage(): string
```

Obtains the first language in the preferred language list.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getFirstPreferredLanguage](arkts-localization-i18n-system-c.md#getfirstpreferredlanguage)

**System capability:** SystemCapability.Global.I18n

**Return value:**

| Type | Description |
| --- | --- |
| string | First language in the preferred language list. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let firstPreferredLanguage: string = i18n.getFirstPreferredLanguage();
```
