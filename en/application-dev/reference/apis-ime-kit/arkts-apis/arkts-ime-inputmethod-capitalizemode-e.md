# CapitalizeMode

```TypeScript
export enum CapitalizeMode
```

Enumerates the modes of capitalizing the first letter of a text. <br>

| Name | Value | Description |  
| -------- | -- | -------- |  
| NONE | 0 | No initial capitalization is performed.<br> <br>Usage scenarios: Applicable to input boxes that do not require automatic capitalization, such as password input and verification code input.|

| SENTENCES | 1 | The first letter of each sentence is capitalized.<br> <br>Usage scenarios: Applicable to ordinary text input boxes, such as chat and memo, where the first letter is automatically capitalized following punctuation marks such as a period.|

| WORDS | 2 | The first letter of each word is capitalized.<br> <br>Usage scenarios: Applicable to scenarios where the first letter of each word needs to be capitalized, such as titles and personal names.|

| CHARACTERS | 3 | Every letter is capitalized.<br> <br>Usage scenarios: Applicable to all uppercase input scenarios, such as abbreviation input (for example, the domain name part in a URL).|

**Since:** 20

<!--Device-inputMethod-export enum CapitalizeMode--><!--Device-inputMethod-export enum CapitalizeMode-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## CHARACTERS

```TypeScript
CHARACTERS
```

Capitalize each letter.

**Since:** 20

<!--Device-CapitalizeMode-CHARACTERS--><!--Device-CapitalizeMode-CHARACTERS-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## NONE

```TypeScript
NONE = 0
```

Capitalize nothing.

**Since:** 20

<!--Device-CapitalizeMode-NONE = 0--><!--Device-CapitalizeMode-NONE = 0-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## SENTENCES

```TypeScript
SENTENCES
```

Capitalize the first letter of each sentence.

**Since:** 20

<!--Device-CapitalizeMode-SENTENCES--><!--Device-CapitalizeMode-SENTENCES-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## WORDS

```TypeScript
WORDS
```

Capitalize the first letter of each word.

**Since:** 20

<!--Device-CapitalizeMode-WORDS--><!--Device-CapitalizeMode-WORDS-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework
