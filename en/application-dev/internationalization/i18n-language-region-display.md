# Language and Locale Name Localization

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @yliupy-->
<!--Designer: @zw_feifei-->
<!--Tester: @lpw_work-->
<!--Adviser: @ningningW-->
<!-- md-trans-meta sourceCommit=9da32f18d9f596600b1bcf7b3e4ed4f31b219c61 translatedAt=2026-11-03T09:28:36.110Z pushedAt=2026-11-03T09:28:36.110Z nl=1 -->

## Function Description

Language and locale name localization means to localize language and locale names on the UI based on local language habits. For example, Simplified Chinese and English are used in an English environment while 简体中文 and 英文 are used in a Chinese environment.


## How to Develop

For details about the APIs, see [getDisplayCountry](../reference/apis-localization-kit/js-apis-i18n.md#getdisplaycountry9) and [getDisplayLanguage](../reference/apis-localization-kit/js-apis-i18n.md#getdisplaylanguage9).

1. Import the required module.

   <!-- @[import_module](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/International/Internationalization/entry/src/main/ets/i18napplication/NameLocalization.ets) -->

   ``` TypeScript
   import { i18n } from '@kit.LocalizationKit';
   ```

2. Usage scenarios:
- Localize language names. Retrieve a language name in different languages. The following example retrieves the German language name in Chinese:

   <!-- @[localized_language_names](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/International/Internationalization/entry/src/main/ets/i18napplication/NameLocalization.ets) -->

   ``` TypeScript
   let displayLanguage = i18n.System.getDisplayLanguage('de', 'zh-Hans-CN'); // displayLanguage = '德文'
   // language: two-letter language code, for example, zh, de, or fr.
   // locale: locale ID, for example, en-GB, en-US, or zh-Hans-CN.
   // sentenceCase: whether the first letter of the language name needs to be capitalized. The default value is true.
   ```

- Localize country/region names. Retrieve a country/region name in different languages. The following example retrieves the name of Saudi Arabia in English:

   <!-- @[localized_country_names](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/International/Internationalization/entry/src/main/ets/i18napplication/NameLocalization.ets) -->

   ``` TypeScript
   let displayCountry = i18n.System.getDisplayCountry('SA', 'en-GB'); // displayCountry = 'Saudi Arabia'
   // country: two-letter country/region code, for example, CN, DE, or SA.
   // locale: locale ID, for example, en-GB, en-US, or zh-Hans-CN.
   // sentenceCase: whether the first letter of the country/region name needs to be capitalized. The default value is true.
   ```

<!--no_check-->
