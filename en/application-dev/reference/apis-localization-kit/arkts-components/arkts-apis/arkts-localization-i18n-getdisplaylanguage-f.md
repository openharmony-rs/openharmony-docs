# getDisplayLanguage

## Modules to Import

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## getDisplayLanguage

```TypeScript
export function getDisplayLanguage(language: string, locale: string, sentenceCase?: boolean): string
```

Obtains the localized script for the specified language.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getDisplayLanguage](arkts-localization-i18n-system-c.md#getdisplaylanguage)

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| language | string | Yes | Specified language. |
| locale | string | Yes | [System locale](../../../internationalization/i18n-locale-culture.md#how-it-works), which consists of the language, script, and country/region. |
| sentenceCase | boolean | No | Whether to use sentence case to display the text. The value **true** means to display the text in title case format, and the value **false** means to display the text in the default case format of the locale. The default value is **true**. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Localized script for the specified language. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let languageName: string = i18n.getDisplayLanguage('zh', 'en-GB', true); // languageName = 'Chinese'
languageName = i18n.getDisplayLanguage('zh', 'en-GB'); // languageName = 'Chinese'
```
