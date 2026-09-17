# getLineInstance

## Modules to Import

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## getLineInstance

```TypeScript
export function getLineInstance(locale: string): BreakIterator
```

Obtains a **BreakIterator** object. The **BreakIterator** object maintains an internal break iterator that can be used to access various line break points.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| locale | string | Yes | [System locale](../../../internationalization/i18n-locale-culture.md#how-it-works), which consists of the language, script, and country/region. The generated [BreakIterator](arkts-localization-i18n-breakiterator-c.md) object calculates the positions of line breaks based on the rules of the specified locale. |

**Return value:**

| Type | Description |
| --- | --- |
| [BreakIterator](arkts-localization-i18n-breakiterator-c.md) | **BreakIterator** object. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let iterator: i18n.BreakIterator = i18n.getLineInstance('en');
```
