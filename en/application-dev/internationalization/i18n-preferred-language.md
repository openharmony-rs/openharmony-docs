# Preferred Language

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @yliupy-->
<!--Designer: @sunyaozu-->
<!--Tester: @lpw_work-->
<!--Adviser: @Brilliantry_Rui-->

## Use Cases

Multi-language users usually set the system language to one language (for example, Chinese) and the language of a specific application to another language (for example, English). When application resources are loaded on the UI, it is expected that the resources be displayed in the language set for the application. To address this issue, you can set a preferred language in locale settings so that resources are loaded in the preferred language when the application is launched. Currently, only one preferred language can be set for an application.

## How to Develop

For details about how to use related APIs, see [getAppPreferredLanguage](../reference/apis-localization-kit/js-apis-i18n.md#getapppreferredlanguage9).

1. Obtain the preferred language of the application.
   ```ts
   import { i18n } from '@kit.LocalizationKit';

   let appPreferredLanguage: string = i18n.System.getAppPreferredLanguage(); // Obtain the preferred language of the application.
   ```
   
2. Set the preferred language of the application. After the preferred language of the application is set to the target language, the application UI is switched to the target language. The setting is subject only to the application. It does not affect the system language settings.
   ```ts
   import { i18n } from '@kit.LocalizationKit';
   import { BusinessError } from '@kit.BasicServicesKit';

   try {
     i18n.System.setAppPreferredLanguage('zh-Hans'); // Set the preferred language of the application to zh-Hans.
   } catch (error) {
     let err: BusinessError = error as BusinessError;
     console.error(`call System.setAppPreferredLanguage failed, error code: ${err.code}, message: ${err.message}.`);
   }
   ```

3. Clear the preferred language of the application. If the preferred language is set to **default**, the application's language will be the same as the system language, and the setting will take effect upon application restarting.
   ```ts
   import { i18n } from '@kit.LocalizationKit';
   import { BusinessError } from '@kit.BasicServicesKit';

   try {  
     i18n.System.setAppPreferredLanguage ('default'); // Clear the preferred language of the application.
   } catch(error) {
     let err: BusinessError = error as BusinessError;
     console.error(`call System.setAppPreferredLanguage failed, error code: ${err.code}, message: ${err.message}.`);
   }
   ```
