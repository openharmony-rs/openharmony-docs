# Transliterator

Provides text transliteration capabilities, such as obtaining the supported language IDs and transliterating text.

**Since:** 9

**System capability:** SystemCapability.Global.I18n

## Modules to Import

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## getAvailableIDs

```TypeScript
static getAvailableIDs(): string[]
```

Obtains a list of IDs supported by the **Transliterator** object.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

**Return value:**

| Type | Description |
| --- | --- |
| string[] | List of IDs supported by the **Transliterator** object. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

// A total number of 742 IDs are supported. Each ID is in *source*-*destination* format. For example, in **ids = ['Han-Latin','Latin-ASCII', 'Amharic-Latin/BGN','Accents-Any', ...]**, **Han-Latin** indicates conversion from Chinese to Latin, and **Amharic-Latin** indicates conversion from Amharic to Latin.
// For more information, see ISO-15924.
let ids: string[] = i18n.Transliterator.getAvailableIDs();
```

## getInstance

```TypeScript
static getInstance(id: string): Transliterator
```

Creates a **Transliterator** object based on the specified ID.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | string | Yes | ID supported by the **Transliterator** object. |

**Return value:**

| Type | Description |
| --- | --- |
| [Transliterator](arkts-localization-i18n-transliterator-c.md) | **Transliterator** object. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let transliterator: i18n.Transliterator = i18n.Transliterator.getInstance('Any-Latn');
```

## transform

```TypeScript
transform(text: string): string
```

Converts the input text from the source format to the target format.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| text | string | Yes | Input text. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Text after conversion. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let transliterator: i18n.Transliterator = i18n.Transliterator.getInstance('Any-Latn');
let wordArray: string[] = ['China', 'Germany', 'US', 'France"]
for (let i = 0; i < wordArray.length; i++) {
  let transliterateLatn: string =
    transliterator.transform(wordArray[i]); // transliterateLatn: 'zhōng guó', 'dé guó', 'měi guó', 'fǎ guó'
}

// Chinese transliteration and tone removal
transliterator = i18n.Transliterator.getInstance('Any-Latn;Latin-Ascii');
let transliterateAscii: string = transliterator.transform ('China'); // transliterateAscii = 'zhong guo'

// Chinese surname pronunciation
transliterator = i18n.Transliterator.getInstance('Han-Latin/Names');
let transliterateNames: string = transliterator.transform('Teacher Shan'); // transliterateNames = 'shàn lǎo shī'
transliterateNames = transliterator.transform('Long Sun No Taboo'); // transliterateNames = 'zhǎng sūn wú jì'
```
