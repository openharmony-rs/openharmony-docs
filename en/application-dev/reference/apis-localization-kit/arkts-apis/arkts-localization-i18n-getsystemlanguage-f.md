# getSystemLanguage

## Modules to Import

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## getSystemLanguage

```TypeScript
export function getSystemLanguage(): string
```

Obtains the system language.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getSystemLanguage](arkts-localization-i18n-system-c.md#getsystemlanguage)

**System capability:** SystemCapability.Global.I18n

**Return value:**

| Type | Description |
| --- | --- |
| string | System language ID. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let systemLanguage: string = i18n.getSystemLanguage();
```
