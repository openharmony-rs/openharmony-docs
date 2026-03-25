# Character Processing

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @yliupy-->
<!--Designer: @sunyaozu-->
<!--Tester: @lpw_work-->
<!--Adviser: @Brilliantry_Rui-->

## Use Cases

Character rules vary greatly in different languages. Character processing ensures that texts are processed with similar logic under different language rules.

## How to Develop


1. Import the related modules.

   <!-- @[import_module](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/International/Internationalization/entry/src/main/ets/i18napplication/CharacterProcessing.ets) -->
   
   ``` TypeScript
   import { i18n } from '@kit.LocalizationKit';
   ```

2. Application scenario.

- Character attributes: used to determine the character type, for example, digit, letter, or space, and check whether a character is of the right-to-left (RTL) language or whether a character is an ideographic character (for example, Chinese, Japanese, or Korean). You can implement this feature by using APIs of the Unicode class. For example, you can use [isDigit](../reference/apis-localization-kit/js-apis-i18n.md#isdigit9). The following is an example of the code:

  <!-- @[identify_character_type](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/International/Internationalization/entry/src/main/ets/i18napplication/CharacterProcessing.ets) -->
  
  ``` TypeScript
  // Check whether the input character is a digit.
  let isDigit = i18n.Unicode.isDigit('1'); // isDigit = true
  
  // Check whether a character is of the RTL language.
  let isRTL = i18n.Unicode.isRTL('a'); // isRTL = false
  
  // Check whether a character is an ideographic character.
  let isIdeograph = i18n.Unicode.isIdeograph('Hua'); // isIdeograph = true
  
  // Obtain the character type.
  let unicodeType = i18n.Unicode.getType('a'); // unicodeType = 'U_LOWERCASE_LETTER'
  ```

- Transliteration: refers to the process of converting text represented by one writing system or alphabet into text represented by another writing system or alphabet with the same pronunciation. It is distinct from translation. You can use the [transform](../reference/apis-localization-kit/js-apis-i18n.md#transform9) API of the Transliterator class to implement transliteration. The following is an example of the code:

  > **NOTE**
  >
  > This module enables the conversion of Chinese characters into pinyin. Nevertheless, when the Chinese text includes polyphonic characters, there may be instances where some of these characters fail to be converted into pinyin with the accurate pronunciation.

  <!-- @[get_transliteration](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/International/Internationalization/entry/src/main/ets/i18napplication/CharacterProcessing.ets) -->
  
  ``` TypeScript
  // Transliterate the text into the Latn format.
  let transliterator: i18n.Transliterator = i18n.Transliterator.getInstance('Any-Latn');
  let translatedText = transliterator.transform('China'); // translatedText = 'zhōng guó'
  
  // Chinese transliteration and tone removal
  let toneLessTransliterator: i18n.Transliterator = i18n.Transliterator.getInstance('Any-Latn;Latin-Ascii');
  let toneLessTranslatedText = toneLessTransliterator.transform('China'); // toneLessTranslatedText = 'zhong guo'
  
  // Chinese surname pronunciation
  let nameTransliterator: i18n.Transliterator = i18n.Transliterator.getInstance('Han-Latin/Names');
  let nameTranslatedText = nameTransliterator.transform('Teacher Shan'); // nameTranslatedText = 'shàn lǎo shī'
  
  // Obtain the list of available transliterator IDs.
  let ids = i18n.Transliterator.getAvailableIDs(); // ids = ['ASCII-Latin', 'Accents-Any', ...]
  ```

- Text Normalization: normalizes text according to the specified paradigm. The text normalization mode can be NFC, NFD, NFKC, or NFKD. For details, see [Unicode Normalization Forms](https://www.unicode.org/reports/tr15/#Norm_Forms). You can use the [normalize](../reference/apis-localization-kit/js-apis-i18n.md#normalize10) API of the Normalizer class to normalize text. The following is an example of the code:

  <!-- @[character_normalization](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/International/Internationalization/entry/src/main/ets/i18napplication/CharacterProcessing.ets) -->
  
  ``` TypeScript
  // Normalize the text in NFC mode.
  let normalizer: i18n.Normalizer = i18n.Normalizer.getInstance(i18n.NormalizerMode.NFC);
  let normalizedText = normalizer.normalize('\u1E9B\u0323'); // normalizedText = 'ẛ̣'
  ```

- Line Break Point Acquisition: You can use APIs of the [BreakIterator](../reference/apis-localization-kit/js-apis-i18n.md#breakiterator8) class to obtain the line break points of the text for the specified locale. The following is an example of the code:

  <!-- @[set_text_line_break_settings](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/International/Internationalization/entry/src/main/ets/i18napplication/CharacterProcessing.ets) -->
  
  ``` TypeScript
  // Create a BreakIterator object, which is used to calculate the positions of line breaks based on the rules of the specified locale.
  let iterator: i18n.BreakIterator  = i18n.getLineInstance('en-GB');
  
  // Set the text to be processed.
  iterator.setLineBreakText('Apple is my favorite fruit.');
  
  // Move the BreakIterator object to the beginning of the text.
  let firstPos = iterator.first(); // firstPos = 0
  
  // Move the BreakIterator object backward by two line break points. nextPos indicates the position after movement. If BreakIterator is moved out of the text length range, -1 is returned.
  let nextPos = iterator.next(2); // nextPos = 9
  
  // Obtain the position of the BreakIterator object in the text.
  let currentPos = iterator.current(); // currentPos = 9
  
  // Check whether a certain position is a line break point.
  let isBoundary = iterator.isBoundary(9); // isBoundary = true
  
  // Obtain the text processed by BreakIterator.
  let breakText = iterator.getLineBreakText(); // breakText = 'Apple is my favorite fruit.'
  ```
  

- File Path Mirroring: localizes file paths for an RTL language, so as to achieve file path mirroring effect in that language. You can use the [getUnicodeWrappedFilePath](../reference/apis-localization-kit/js-apis-i18n.md#getunicodewrappedfilepath20) API of the I18NUtil class to implement file path mirroring. The following is an example of the code:

  <!-- @[get_unicode_wrapped_file_path](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/International/Internationalization/entry/src/main/ets/i18napplication/CharacterProcessing.ets) -->
  
  ``` TypeScript
  let mirrorPath = '';
  let unMirrorPath = '';
  
  // Perform file path mirroring if mirrorPath is passed.
  let path = 'data/out/tmp';
  
  try {
    let delimiter = '/';
    let locale: Intl.Locale = new Intl.Locale('ar');
    // mirrorPath = 'tmp/out/data/'
    mirrorPath = i18n.I18NUtil.getUnicodeWrappedFilePath(path, delimiter, locale);
    
    // Skip file path mirroring if unMirrorPath is passed.
    let localeZh: Intl.Locale = new Intl.Locale('zh');
    // unMirrorPath = '/data/out/tmp'
    unMirrorPath = i18n.I18NUtil.getUnicodeWrappedFilePath(path, delimiter, localeZh);
  } catch (error) {
    console.error(`call I18NUtil.getUnicodeWrappedFilePath failed, error code: ${error.code}, message: ${error.message}.`);
  }
  ```

<!--RP1--><!--RP1End-->
