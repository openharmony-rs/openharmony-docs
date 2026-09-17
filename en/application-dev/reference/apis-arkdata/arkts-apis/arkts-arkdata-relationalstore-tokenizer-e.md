# Tokenizer

Enumerates tokenizers that can be used for FTS. Use the enum name rather than the enum value.

The table creation statement varies with the tokenizer in use.

For details about the definition of **this.context** in the sample code, see the application [context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) of the stage model.

The following is an example of the table creation statement when **ICU_TOKENIZER** is used:

The following is an example of the table creation statement when **CUSTOM_TOKENIZER** is used:

The following is an example of the table creation statement when **CUSTOM_TOKENIZER** is used:

**Since:** 17

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## NONE_TOKENIZER

```TypeScript
NONE_TOKENIZER = 0
```

NONE_TOKENIZER: not use tokenizer

**Since:** 17

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## ICU_TOKENIZER

```TypeScript
ICU_TOKENIZER = 1
```

The ICU tokenizer is used, which supports Chinese and multiple languages. If the ICU tokenizer is used, you can set the language to use, for example, **zh_CN** for Chinese and **tr_TR** for Turkish. For details about the supported languages, see [ICU tokenizer](https://gitcode.com/openharmony/third_party_icu/blob/master/icu4c/source/data/lang/en.txt). For details about the language abbreviations, see [locales](https://gitcode.com/openharmony/third_party_icu/tree/master/icu4c/source/data/locales).

**Since:** 17

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## CUSTOM_TOKENIZER

```TypeScript
CUSTOM_TOKENIZER = 2
```

A custom tokenizer is used. Chinese (simplified and traditional), English, and Arabic numerals are supported. Compared with **ICU_TOKENIZER**, **CUSTOM_TOKENIZER** has advantages in tokenization accuracy and resident memory usage. The self-developed tokenizer supports two modes: default tokenization mode and short word tokenization mode (short_words). You can use the cut_mode parameter to specify the mode. If no mode is specified, the default mode is used.

**Since:** 18

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core
