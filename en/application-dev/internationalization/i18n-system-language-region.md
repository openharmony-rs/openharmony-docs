# System Language and Region

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @yliupy-->
<!--Designer: @sunyaozu-->
<!--Tester: @lpw_work-->
<!--Adviser: @Brilliantry_Rui-->

## How It Works

You can add multiple languages in the **Language & region** area in **Settings**. The list formed by multiple languages is called a language list, and the first language in the list is called the system language. Locales are divided based on the locale ID.

When you set or switch the system language, the system checks whether the [extended parameter](i18n-locale-culture.md) matches the system language. If they do not match, the system deletes the extended parameter. For example, if the current system language is **ar** and the local numeral system is **arab**, the local numeral system will be changed to **mymr** once you switch the system language to **my**. If you switch the language to Chinese, the Arabic numeral system is used because local numerals are not supported. Meanwhile, the extended parameter associated with the numeral system is removed.

Since API version 21, you can also use the **param get persist.global.language** command of the [param tool](../tools/param-tool.md#get) to obtain the system language.

## How to Develop

For details about how to use related APIs, see [System](../reference/apis-localization-kit/js-apis-i18n.md#system9).

1. Obtain the system language, region, and locale.
   ```ts
   import { i18n } from '@kit.LocalizationKit';
   import { BusinessError, commonEventManager } from '@kit.BasicServicesKit';

   // Obtain the system language.
   let systemLanguage: string = i18n.System.getSystemLanguage();  // systemLanguage indicates the current system language.

   // Obtain the system region.
   let systemRegion: string = i18n.System.getSystemRegion();  // systemRegion indicates the current system region.

   // Obtain the system locale.
   let systemLocale: Intl.Locale = i18n.System.getSystemLocaleInstance(); // systemLocale indicates the current system locale.

   // Subscribe to system language, region, or locale changes through the common event COMMON_EVENT_LOCALE_CHANGED.
   let subscriber: commonEventManager.CommonEventSubscriber; // Used to save the created subscriber object for subsequent subscription and unsubscription.
   let subscribeInfo: commonEventManager.CommonEventSubscribeInfo = {
     events: [commonEventManager.Support.COMMON_EVENT_LOCALE_CHANGED]
   };
   // Create a subscriber.
   commonEventManager.createSubscriber(subscribeInfo)
     .then((commonEventSubscriber: commonEventManager.CommonEventSubscriber) => {
       console.info("CreateSubscriber");
       subscriber = commonEventSubscriber;
       commonEventManager.subscribe(subscriber, (err, data) => {
         if (err) {
           console.error(`Failed to subscribe common event. error code: ${err.code}, message: ${err.message}.`);
           return;
         }
         console.info("The subscribed event has occurred."); // The system language, region, or locale has changed.
       })
     })
     .catch((err: BusinessError) => {
       console.error(`CreateSubscriber failed, code is ${err.code}, message is ${err.message}`);
     });
   ```

<!--Del-->
2. Set the system language and region.
   ```ts
   import { i18n } from '@kit.LocalizationKit';
   import { BusinessError } from '@kit.BasicServicesKit';

   // Set the current system language to zh-Hans.
   try {
     i18n.System.setSystemLanguage('zh-Hans');
   } catch (error) {
     let err: BusinessError = error as BusinessError;
     console.error(`call System.setSystemLanguage failed, error code: ${err.code}, message: ${err.message}.`);
   }

   // Set the current system region to CN.
   try {
     i18n.System.setSystemRegion('CN');
   } catch (error) {
     let err: BusinessError = error as BusinessError;
     console.error(`call System.setSystemRegion failed, error code: ${err.code}, message: ${err.message}.`);
   }
   ```
<!--DelEnd-->
