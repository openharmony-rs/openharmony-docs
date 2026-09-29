# Character

```TypeScript
export class Character
```

Provides the API for accessing unicode character properties. For example, determine whether a character is a number.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [Unicode](arkts-localization-i18n-unicode-c.md)

<!--Device-i18n-export class Character--><!--Device-i18n-export class Character-End-->

**System capability:** SystemCapability.Global.I18n

## Modules to Import

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## getType

```TypeScript
getType(ch: string): string
```

Obtains the type of the input character.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getType](arkts-localization-i18n-unicode-c.md#gettype)

<!--Device-Character-getType(ch: string): string--><!--Device-Character-getType(ch: string): string-End-->

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ch | string | Yes | Input character. If the input is a string, only the type of the first character is checked. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Type of the input character. |

## isDigit

```TypeScript
isDigit(ch: string): boolean
```

Checks whether the input character is a digit.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [isDigit](arkts-localization-i18n-unicode-c.md#isdigit)

<!--Device-Character-isDigit(ch: string): boolean--><!--Device-Character-isDigit(ch: string): boolean-End-->

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ch | string | Yes | Input character. If the input is a string, only the type of the first character is checked. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | **true** if the input character is a digit, and **false** otherwise. |

## isIdeograph

```TypeScript
isIdeograph(ch: string): boolean
```

Checks whether the input character is an ideographic character.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [isIdeograph](arkts-localization-i18n-unicode-c.md#isideograph)

<!--Device-Character-isIdeograph(ch: string): boolean--><!--Device-Character-isIdeograph(ch: string): boolean-End-->

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ch | string | Yes | Input character. If the input is a string, only the type of the first character is checked. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | **true** if the input character an ideographic character, and **false** otherwise. |

## isLetter

```TypeScript
isLetter(ch: string): boolean
```

Checks whether the input character is a letter.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [isLetter](arkts-localization-i18n-unicode-c.md#isletter)

<!--Device-Character-isLetter(ch: string): boolean--><!--Device-Character-isLetter(ch: string): boolean-End-->

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ch | string | Yes | Input character. If the input is a string, only the type of the first character is checked. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | **true** if the input character a letter, and **false** otherwise. |

## isLowerCase

```TypeScript
isLowerCase(ch: string): boolean
```

Checks whether the input character is a lowercase letter.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [isLowerCase](arkts-localization-i18n-unicode-c.md#islowercase)

<!--Device-Character-isLowerCase(ch: string): boolean--><!--Device-Character-isLowerCase(ch: string): boolean-End-->

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ch | string | Yes | Input character. If the input is a string, only the type of the first character is checked. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | **true** if the input character a lowercase letter, and **false** otherwise. |

## isRTL

```TypeScript
isRTL(ch: string): boolean
```

Checks whether the input character is of the right to left (RTL) language.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [isRTL](arkts-localization-i18n-unicode-c.md#isrtl)

<!--Device-Character-isRTL(ch: string): boolean--><!--Device-Character-isRTL(ch: string): boolean-End-->

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ch | string | Yes | Input character. If the input is a string, only the type of the first character is checked. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | **true** if the input character is of the RTL language, and **false** otherwise. |

## isSpaceChar

```TypeScript
isSpaceChar(ch: string): boolean
```

Checks whether the input character is a space.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [isSpaceChar](arkts-localization-i18n-unicode-c.md#isspacechar)

<!--Device-Character-isSpaceChar(ch: string): boolean--><!--Device-Character-isSpaceChar(ch: string): boolean-End-->

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ch | string | Yes | Input character. If the input is a string, only the type of the first character is checked. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | **true** if the input character is a space, and **false** otherwise. |

## isUpperCase

```TypeScript
isUpperCase(ch: string): boolean
```

Checks whether the input character is an uppercase letter.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [isUpperCase](arkts-localization-i18n-unicode-c.md#isuppercase)

<!--Device-Character-isUpperCase(ch: string): boolean--><!--Device-Character-isUpperCase(ch: string): boolean-End-->

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ch | string | Yes | Input character. If the input is a string, only the type of the first character is checked. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | **true** if the input character an uppercase letter, and **false** otherwise. |

## isWhitespace

```TypeScript
isWhitespace(ch: string): boolean
```

Checks whether the input character is a whitespace.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [isWhitespace](arkts-localization-i18n-unicode-c.md#iswhitespace)

<!--Device-Character-isWhitespace(ch: string): boolean--><!--Device-Character-isWhitespace(ch: string): boolean-End-->

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ch | string | Yes | Input character. If the input is a string, only the type of the first character is checked. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | **true** if the input character is a white space, and **false** otherwise. |
