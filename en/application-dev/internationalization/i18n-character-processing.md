# Character Processing

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @yliupy-->
<!--Designer: @sunyaozu-->
<!--Tester: @lpw_work-->
<!--Adviser: @Brilliantry_Rui-->

## Use Cases

Character rules vary greatly in different languages, and it is usually difficult to extract expected information from the corresponding text. Character processing makes it possible to process text with similar logic under different language rules.

## How to Develop


### Character Type Identification Using Character Attributes

Character attributes are used to determine the character type, for example, digit, letter, or space, and check whether a character is of the right-to-left (RTL) language or whether a character is an ideographic character (for example, Chinese, Japanese, or Korean).

You can implement character type identification by using the [isDigit](../reference/apis-localization-kit/js-apis-i18n.md#isdigit9) API of the **Unicode** class. The sample code is as follows:

```ts
// Import the i18n module.
import { i18n } from '@kit.LocalizationKit';

// Check whether the input character is a digit.
let isDigit: boolean = i18n.Unicode.isDigit('1'); // isDigit = true

// Check whether a character is of the RTL language.
let isRTL: boolean = i18n.Unicode.isRTL('a'); // isRTL = false

// Check whether a character is an ideographic character.
let isIdeograph: boolean = i18n.Unicode.isIdeograph ('华'); // isIdeograph = true

// Obtain the character type.
let unicodeType: string = i18n.Unicode.getType('a'); // unicodeType = 'U_LOWERCASE_LETTER'
```


### Transliteration

Transliteration refers to the process of converting text represented by one writing system or alphabet into text represented by another writing system or alphabet with the same pronunciation. It is distinct from translation. You can implement transliteration by using the [transform](../reference/apis-localization-kit/js-apis-i18n.md#transform9) API of the **Transliterator** class. The sample code is as follows:

> **NOTE**
> This module enables the conversion of Chinese characters into pinyin. Nevertheless, when the Chinese text includes polyphonic characters, there may be instances where some of these characters fail to be converted into pinyin with the accurate pronunciation.

```ts
// Import the i18n module.
import { i18n } from '@kit.LocalizationKit';

// Transliterate the text into the Latn format.
let transliterator: i18n.Transliterator = i18n.Transliterator.getInstance('Any-Latn');
let text: string = '中国'
let translatedText: string = transliterator.transform(text); // translatedText = 'zhōng guó'

// Chinese transliteration and tone removal
let toneLessTransliterator: i18n.Transliterator = i18n.Transliterator.getInstance('Any-Latn;Latin-Ascii');
translatedText = toneLessTransliterator.transform ('中国'); // translatedText ='zhong guo'

// Chinese surname pronunciation
let nameTransliterator: i18n.Transliterator = i18n.Transliterator.getInstance('Han-Latin/Names');
translatedText = nameTransliterator.transform('单老师'); // translatedText = 'shàn lǎo shī'
translatedText = nameTransliterator.transform('长孙无忌'); // translatedText = 'zhǎng sūn wú jì'

// Obtain the list of available transliterator IDs.
let ids: string[] = i18n.Transliterator.getAvailableIDs(); // ids = ['ASCII-Latin', 'Accents-Any', ...]
```


### Text Normalization

Text normalization means to the normalize text according to the specified paradigm. The text normalization mode can be NFC, NFD, NFKC, or NFKD. For details, see [Unicode Normalization Forms](https://www.unicode.org/reports/tr15/#Norm_Forms). You can implement text normalization by using the [normalize](../reference/apis-localization-kit/js-apis-i18n.md#normalize10) API of the **Normalizer** class. The sample code is as follows:

```ts
// Import the i18n module.
import { i18n } from '@kit.LocalizationKit';

// Normalize the text in NFC mode.
let normalizer: i18n.Normalizer = i18n.Normalizer.getInstance(i18n.NormalizerMode.NFC);
let normalizedText: string = normalizer.normalize('\u1E9B\u0323'); // normalizedText = 'ẛ̣'
```


### Line Break Point Acquisition

You can use APIs of the [BreakIterator](../reference/apis-localization-kit/js-apis-i18n.md#breakiterator8) class to obtain line break points of the text for the specified locale. The sample code is as follows:

```ts
// Import the i18n module.
import { i18n } from '@kit.LocalizationKit';

// Create a BreakIterator object, which is used to calculate the positions of line breaks based on the rules of the specified locale.
let iterator: i18n.BreakIterator  = i18n.getLineInstance('en-GB');

// Set the text to be processed.
iterator.setLineBreakText('Apple is my favorite fruit.');

// Move the BreakIterator object to the beginning of the text.
let firstPos: number = iterator.first(); // firstPos = 0

// Move the BreakIterator object backward by two line break points. nextPos indicates the position after movement. If BreakIterator is moved out of the text length range, -1 is returned.
let nextPos: number = iterator.next(2); // nextPos = 9

// Obtain the position of the BreakIterator object in the text.
let currentPos: number = iterator.current(); // currentPos = 9

// Check whether a certain position is a line break point.
let isBoundary: boolean = iterator.isBoundary(9); // isBoundary = true

// Obtain the text processed by BreakIterator.
let breakText: string = iterator.getLineBreakText(); // breakText = 'Apple is my favorite fruit.'
```

### File Path Mirroring

File path mirroring means to localize file paths for an RTL language, so as to achieve file path mirroring effect in that language. You can implement file path mirroring by using the [getUnicodeWrappedFilePath](../reference/apis-localization-kit/js-apis-i18n.md#getunicodewrappedfilepath20) API of the **I18NUtil** class. The sample code is as follows:

```ts
// Import the i18n module.
import { i18n } from '@kit.LocalizationKit';

try {
  // Perform file path mirroring if mirrorPath is passed.
  let path: string = 'data/out/tmp';
  let delimiter: string = '/';
  let locale: Intl.Locale = new Intl.Locale('ar');
  // mirrorPath = 'tmp/out/data/'
  let mirrorPath: string = i18n.I18NUtil.getUnicodeWrappedFilePath(path, delimiter, locale);

  // Skip file path mirroring if unMirrorPath is passed.
  let localeZh: Intl.Locale = new Intl.Locale('zh');
  // unMirrorPath = '/data/out/tmp'
  let unMirrorPath: string = i18n.I18NUtil.getUnicodeWrappedFilePath(path, delimiter, localeZh);
} catch (error) {
  console.error(`call I18NUtil.getUnicodeWrappedFilePath failed, error code: ${error.code}, message: ${error.message}.`);
}
```
<!--RP1--><!--RP1End-->
<!--no_check-->