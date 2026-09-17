# AutoCapitalizationMode

Enumerates automatic capitalization modes. This only provides API capabilities; the specific implementation depends on the input method application.

**Since:** 20

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## NONE

```TypeScript
NONE = 0
```

Default state; automatic capitalization is disabled.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## WORDS

```TypeScript
WORDS = 1
```

Automatic capitalization is applied per word: The first character of each word is capitalized, others are lowercase.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## SENTENCES

```TypeScript
SENTENCES = 2
```

Automatic capitalization is applied per sentence: The first character of each sentence is capitalized, others are lowercase.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## ALL_CHARACTERS

```TypeScript
ALL_CHARACTERS = 3
```

Automatic capitalization applied to all characters.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
