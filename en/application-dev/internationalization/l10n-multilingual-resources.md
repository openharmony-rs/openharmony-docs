# Multilingual Resource Provisioning

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @yliupy-->
<!--Designer: @zw_feifei-->
<!--Tester: @lpw_work-->
<!--Adviser: @ningningW-->
<!-- md-trans-meta sourceCommit=7058acdcfeb33326a602c42c61cad8dcf70b5b74 translatedAt=2026-11-03T09:17:02.335Z pushedAt=2026-11-03T09:17:02.335Z nl=1 -->

## Function Description

To make an application available to users in different countries and regions, localize it to meet their language and cultural requirements so that it loads and displays content in line with local conventions. Localization involves adapting language and country/region names, dates and times, numbers and units, text, images, audio, and video.

For language and country/region names, dates and times, numbers, and units, use internationalization APIs to obtain the content to display. Locale conventions may change, and the values returned by these APIs may change accordingly. Avoid further processing the returned values.

For text, images, audio, and video, create separate resource directories and configure multilingual resources. When the application runs, the system automatically selects and loads the resources that best match the device's locale.

## Using Internationalization APIs

- Calling localization APIs

  To ensure that API return values are consistent with user settings, you usually need to pass the system locale ID or system locale object to [@ohos.i18n (Internationalization-I18n)](../reference/apis-localization-kit/js-apis-i18n.md) and [@ohos.intl (Internationalization-Intl)](../reference/apis-localization-kit/js-apis-intl.md). The following examples show how to pass each type:

   <!-- @[import_module](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/International/Internationalization/entry/src/main/ets/i18napplication/NameLocalization.ets) -->

   ``` TypeScript
   import { i18n } from '@kit.LocalizationKit';
   ```

   <!-- @[system_locale_datetimeformat](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/International/Internationalization/entry/src/main/ets/i18napplication/NameLocalization.ets) -->

   ``` TypeScript
   // Obtain the system locale object.
   let locale = i18n.System.getSystemLocaleInstance();

   // If the API takes a locale ID (string), use toString() to obtain the system locale ID.
   let dateTimeFormat = new Intl.DateTimeFormat(locale.toString());

   // If the API takes an Intl.Locale object, pass the system locale object directly.
   let simpleDateTimeFormat = i18n.getSimpleDateTimeFormatBySkeleton('yMd', locale);
   ```

- Identifying the system language

  If your application needs to identify the language, avoid hard-coded comparisons of language codes. Use the following approach instead:

   <!-- @[import_module](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/International/Internationalization/entry/src/main/ets/i18napplication/NameLocalization.ets) -->

   ``` TypeScript
   import { i18n } from '@kit.LocalizationKit';
   ```

   <!-- @[best_match_locale](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/International/Internationalization/entry/src/main/ets/i18napplication/NameLocalization.ets) -->

   ``` TypeScript
   let systemLanguage = i18n.System.getSimplifiedLanguage();
   // Configure languagesList for your application. For example, if variants of Traditional Chinese do not need to be distinguished, combine 'zh-Hant-HK' and 'zh-Hant-TW' into 'zh-Hant'.
   let languagesList = ['zh-Hans', 'zh-Hant-HK', 'zh-Hant-TW'];
   let matchedLanguage = i18n.I18NUtil.getBestMatchLocale(systemLanguage, languagesList);
   switch (matchedLanguage) {
     case 'zh-Hans':
       // The system language is Simplified Chinese.
       break;
     case 'zh-Hant-HK':
       // The system language is Traditional Chinese (Hong Kong).
       break;
     case 'zh-Hant-TW':
       // The system language is Traditional Chinese (Taiwan).
       break;
     default:
       // The system language does not match any entry in languagesList.
   }
   ```

## Multilingual Resource Configuration

To ensure that the application can load content for different countries, regions, and languages, create separate resource directories to store the resources. When the application runs, the system automatically selects and loads the resources that best match the device's locale. For better localization, keep localized content separate from core functionality as much as possible and store it in resource directories.

You only need to configure the resource files and then access the resources according to your service requirements. For details about resource configuration and matching rules, see [Resource Categories and Access](../quick-start/resource-categories-and-access.md).

> **NOTE**
>
> If an application preferred language is set, the application preferentially loads resources for that language.
