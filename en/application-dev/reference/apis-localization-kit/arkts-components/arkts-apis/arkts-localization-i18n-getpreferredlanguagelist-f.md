# getPreferredLanguageList

## Modules to Import

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## getPreferredLanguageList

```TypeScript
export function getPreferredLanguageList(): Array<string>
```

Obtains the list of preferred languages.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getPreferredLanguageList](arkts-localization-i18n-system-c.md#getpreferredlanguagelist)

**System capability:** SystemCapability.Global.I18n

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;string&gt; | List of preferred languages. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let preferredLanguageList: Array<string> = i18n.getPreferredLanguageList();
```
