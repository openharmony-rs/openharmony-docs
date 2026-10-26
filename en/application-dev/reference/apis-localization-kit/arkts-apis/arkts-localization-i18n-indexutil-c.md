# IndexUtil

```TypeScript
export class IndexUtil
```

Provides index management capabilities, such as obtaining the locale index list and text index values.

**Since:** 8

<!--Device-i18n-export class IndexUtil--><!--Device-i18n-export class IndexUtil-End-->

**System capability:** SystemCapability.Global.I18n

## Modules to Import

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## addLocale

```TypeScript
addLocale(locale: string): void
```

Adds the index list of a new locale to the index list of the current locale to form a composite list.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-IndexUtil-addLocale(locale: string): void--><!--Device-IndexUtil-addLocale(locale: string): void-End-->

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| locale | string | Yes | [System locale](../../../internationalization/i18n-locale-culture.md#how-it-works), which consists of the language, script, and country/region. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let indexUtil: i18n.IndexUtil = i18n.getInstance('zh-CN');
indexUtil.addLocale('en-US');
```

## getBilingualIndex

```TypeScript
getBilingualIndex(text: string): string
```

Obtains the bilingual index of the text object.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-IndexUtil-getBilingualIndex(text: string): string--><!--Device-IndexUtil-getBilingualIndex(text: string): string-End-->

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| text | string | Yes | Input text. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Bilingual index of the text object. Returns '#' if no proper index is found or text is empty. |

## getBilingualIndexList

```TypeScript
getBilingualIndexList(mode?: BilingualIndexMode): Array<string>
```

Obtains the bilingual index list of the current locale.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-IndexUtil-getBilingualIndexList(mode?: BilingualIndexMode): Array<string>--><!--Device-IndexUtil-getBilingualIndexList(mode?: BilingualIndexMode): Array<string>-End-->

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [BilingualIndexMode](arkts-localization-i18n-bilingualindexmode-e.md) | No | Bilingual index mode, defaults to FULL. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;string&gt; | Bilingual index list. The first element is '#', followed by local index list and English index list. |

## getIndex

```TypeScript
getIndex(text: string): string
```

Obtains the index of the **text** object.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-IndexUtil-getIndex(text: string): string--><!--Device-IndexUtil-getIndex(text: string): string-End-->

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| text | string | Yes | Input text. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Index of the **text** object. If no proper index is found, an empty string is returned. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let indexUtil: i18n.IndexUtil = i18n.getInstance('zh-CN');
let index: string = indexUtil.getIndex('hi'); // index = 'H'
```

## getIndexList

```TypeScript
getIndexList(): Array<string>
```

Obtains the index list of the current locale.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-IndexUtil-getIndexList(): Array<string>--><!--Device-IndexUtil-getIndexList(): Array<string>-End-->

**System capability:** SystemCapability.Global.I18n

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;string&gt; | Index list of the current locale. The first and last elements are **...**. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let indexUtil: i18n.IndexUtil = i18n.getInstance('zh-CN');
// indexList = [ '...', 'A', 'B', 'C', 'D', 'E', 'F', 'G', 'H', 'I', 'J', 'K', 'L', 'M', 'N',
// 'O', 'P', 'Q', 'R', 'S', 'T', 'U', 'V', 'W', 'X', 'Y', 'Z', '...' ]
let indexList: Array<string> = indexUtil.getIndexList();
```

## isBilingualIndexSupported

```TypeScript
static isBilingualIndexSupported(locale: Intl.Locale): boolean
```

Checks whether the specified locale supports bilingual index.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-IndexUtil-static isBilingualIndexSupported(locale: Intl.Locale): boolean--><!--Device-IndexUtil-static isBilingualIndexSupported(locale: Intl.Locale): boolean-End-->

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| locale | [Intl.Locale](arkts-localization-intl-locale-c.md) | Yes | Locale to check, in BCP 47 format (e.g., "zh-CN"). |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | true if bilingual index is supported, false otherwise. |
