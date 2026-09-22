# Unicode

```TypeScript
export class Unicode
```

Provides character attribute management capabilities, such as checking whether a character is a space, digit, or letter.

**Since:** 9

**System capability:** SystemCapability.Global.I18n

## Modules to Import

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## detectEncoding

```TypeScript
static detectEncoding(bytes: Uint8Array): EncodingInfo
```

Detects the encoding information of the input byte stream.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bytes | Uint8Array | Yes | Input byte stream. To detect the encoding of a text string, convert the text to a byte stream first while preserving its original format.<br>Byte stream to be identified and encoded |

**Return value:**

| Type | Description |
| --- | --- |
| [EncodingInfo](arkts-localization-i18n-encodinginfo-i.md) | An object containing the detected encoding name and detection confidence level. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let uint8Array = new Uint8Array([0xEF, 0xBB, 0xBF, 0xE4, 0xB8, 0xAD]);
let info = i18n.Unicode.detectEncoding(uint8Array); // info.encodingName = 'UTF-8', info.confidence = 100
```

## getType

```TypeScript
static getType(ch: string): string
```

Obtains the type of the input character.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ch | string | Yes | Input character. If the input is a string, only the type of the first character is checked.<br>**Since:** 12 |

**Return value:**

| Type | Description |
| --- | --- |
| string | Type of the input character.U_UNASSIGNED： Non-category for unassigned and non-character code points. The value can be  U_GENERAL_OTHER_TYPES： Same as **U_UNASSIGNED**.  U_UPPERCASE_LETTER： Uppercase letter.  U_LOWERCASE_LETTER： Lowercase letter.  U_TITLECASE_LETTER： Title case letter.  U_MODIFIER_LETTER： Modifier letter.  U_OTHER_LETTER： Letters other than the uppercase letter, lowercase letter, title case letter, and modifier letter.  U_NON_SPACING_MARK： Non-spacing mark, such as the accent symbol **'** and the variable symbol **#**.  U_ENCLOSING_MARK： Enclosing mark, for example, a circle or a box.  U_COMBINING_SPACING_MARK： Spacing mark, for example, the vowel symbol **[]**.  U_DECIMAL_DIGIT_NUMBER： Decimal number.  U_LETTER_NUMBER： Letter and number (including Roman numeral).  U_OTHER_NUMBER： Other numbers, which are used as encryption symbols, marker symbols, or non-Arabic numerals, such as **@**, **#**, **(1)**, and **①**.  U_SPACE_SEPARATOR： Space separator, for example, a space character, uninterrupted space character, or space character with a fixed width.  U_LINE_SEPARATOR： Line separator.  U_PARAGRAPH_SEPARATOR： Paragraph separator.  U_CONTROL_CHAR： Control character.  U_FORMAT_CHAR： Format character.  U_PRIVATE_USE_CHAR： Privately used character, for example, a company logo.  U_SURROGATE： Surrogate, which is used to represent supplementary characters in UTF-16.  U_DASH_PUNCTUATION： Dash punctuation.  U_START_PUNCTUATION： Start punctuation, for example, the left parenthesis.  U_END_PUNCTUATION： End punctuation, for example, the right parenthesis.  U_INITIAL_PUNCTUATION ： Initial punctuation, for example, the left double quotation mark or left single quotation mark.  U_FINAL_PUNCTUATION： Final punctuation, for example, the right double quotation mark or right single quotation mark.  U_CONNECTOR_PUNCTUATION： Connector punctuation.  U_OTHER_PUNCTUATION： Other punctuations.  U_MATH_SYMBOL： Mathematical symbol.  U_CURRENCY_SYMBOL： Currency symbol.  U_MODIFIER_SYMBOL： Modifier symbol.  U_OTHER_SYMBOL： Other symbols.  For details, see Unicode standard. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let unicodeType: string = i18n.Unicode.getType('a'); // unicodeType = 'U_LOWERCASE_LETTER'
```

## isDigit

```TypeScript
static isDigit(ch: string): boolean
```

Checks whether the input character is a digit.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ch | string | Yes | Input character. If the input is a string, only the type of the first character is checked.<br>**Since:** 12 |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | **true** if the input character is a digit, and **false** otherwise. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let isDigit: boolean = i18n.Unicode.isDigit('1'); // isDigit = true
```

## isIdeograph

```TypeScript
static isIdeograph(ch: string): boolean
```

Checks whether the input character is an ideographic character.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ch | string | Yes | Input character. If the input is a string, only the type of the first character is checked.<br>**Since:** 12 |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | **true** if the input character an ideographic character, and **false** otherwise. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let isIdeograph: boolean = i18n.Unicode.isIdeograph('a'); // isIdeograph = false
```

## isLetter

```TypeScript
static isLetter(ch: string): boolean
```

Checks whether the input character is a letter.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ch | string | Yes | Input character. If the input is a string, only the type of the first character is checked.<br>**Since:** 12 |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | **true** if the input character a letter, and **false** otherwise. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let isLetter: boolean = i18n.Unicode.isLetter('a'); // isLetter = true
```

## isLowerCase

```TypeScript
static isLowerCase(ch: string): boolean
```

Checks whether the input character is a lowercase letter.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ch | string | Yes | Input character. If the input is a string, only the type of the first character is checked.<br>**Since:** 12 |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | **true** if the input character a lowercase letter, and **false** otherwise. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let isLowercase: boolean = i18n.Unicode.isLowerCase('a'); // isLowercase = true
```

## isRTL

```TypeScript
static isRTL(ch: string): boolean
```

Checks whether the input character is of the right to left (RTL) language.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ch | string | Yes | Input character. If the input is a string, only the type of the first character is checked.<br>**Since:** 12 |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | **true** if the input character is of the RTL language, and **false** otherwise. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let isRtl: boolean = i18n.Unicode.isRTL('a'); // isRtl = false
```

## isSpaceChar

```TypeScript
static isSpaceChar(ch: string): boolean
```

Checks whether the input character is a space.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ch | string | Yes | Input character. If the input is a string, only the type of the first character is checked.<br>**Since:** 12 |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | **true** if the input character is a space, and **false** otherwise. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let isSpacechar: boolean = i18n.Unicode.isSpaceChar('a'); // isSpacechar = false
```

## isUpperCase

```TypeScript
static isUpperCase(ch: string): boolean
```

Checks whether the input character is an uppercase letter.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ch | string | Yes | Input character. If the input is a string, only the type of the first character is checked.<br>**Since:** 12 |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | **true** if the input character an uppercase letter, and **false** otherwise. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let isUppercase: boolean = i18n.Unicode.isUpperCase('a'); // isUppercase = false
```

## isWhitespace

```TypeScript
static isWhitespace(ch: string): boolean
```

Checks whether the input character is a whitespace.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ch | string | Yes | Input character. If the input is a string, only the type of the first character is checked.<br>**Since:** 12 |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | **true** if the input character is a white space, and **false** otherwise. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let isWhitespace: boolean = i18n.Unicode.isWhitespace('a'); // isWhitespace = false
```
