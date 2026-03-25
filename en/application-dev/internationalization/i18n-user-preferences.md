# User Preferences

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @yliupy-->
<!--Designer: @sunyaozu-->
<!--Tester: @lpw_work-->
<!--Adviser: @Brilliantry_Rui-->

## Use Cases

In addition to system locales and preferred application languages, the system also allows for user preference settings. The user preferences currently supported include local digit usage and 12/24-hour time format. User preference settings are saved to system locales and application preferred languages as part of the internationalization feature.

## How to Develop

The development procedure is as follows. For details about how to use related APIs, see [System](../reference/apis-localization-kit/js-apis-i18n.md#system9).

1. Import the related modules.

   <!-- @[import_module](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/International/Internationalization/entry/src/main/ets/i18napplication/LanguagePreferenceSetting.ets) -->
   
   ``` TypeScript
   import { i18n } from '@kit.LocalizationKit';
   import { BusinessError, commonEventManager } from '@kit.BasicServicesKit';
   ```

2. Application scenario.
- Obtain user preferences.

   <!-- @[get_user_preference](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/International/Internationalization/entry/src/main/ets/i18napplication/LanguagePreferenceSetting.ets) -->
   
   ``` TypeScript
   // Check whether use of local digits is enabled.
   let usingLocalDigit: boolean = i18n.System.getUsingLocalDigit();
   
   // Check whether use of the 24-hour time format is enabled.
   let is24HourClock: boolean = i18n.System.is24HourClock();
   
   // Subscribe to COMMON_EVENT_TIME_CHANGED events to detect system time format changes.
   let timeSubscriber: commonEventManager.CommonEventSubscriber; // Used to save the created subscriber object for subsequent subscription and unsubscription.
   let timeSubscribeInfo: commonEventManager.CommonEventSubscribeInfo = {
     events: [commonEventManager.Support.COMMON_EVENT_TIME_CHANGED]
   };
   // Create a subscriber.
   commonEventManager.createSubscriber(timeSubscribeInfo)
     .then((commonEventSubscriber: commonEventManager.CommonEventSubscriber) => {
       console.info('CreateSubscriber');
       timeSubscriber = commonEventSubscriber;
       commonEventManager.subscribe(timeSubscriber, (err, data) => {
         if (err) {
           console.error(`Failed to subscribe common event. error code: ${err.code}, message: ${err.message}.`);
           return;
         }
         // Distinguish between system time and system time format changes.
         if (data.data != undefined && data.data == '24HourChange') {
           console.info('The subscribed event has occurred.'); // The system time format has changed.
         }
       })
     })
     .catch((err: BusinessError) => {
       console.error(`CreateSubscriber failed, code is ${err.code}, message is ${err.message}`);
     });
   ```

<!--Del-->
- Enable use of local digits.

   ``` TypeScript
   try {
     i18n.System.setUsingLocalDigit(true); // Enable use of local digits.
   } catch (error) {
     let err: BusinessError = error as BusinessError;
     console.error(`call System.setUsingLocalDigit failed, error code: ${err.code}, message: ${err.message}.`);
   }
   ```

- Enable use of the 24-hour time format.

   ``` TypeScript
   try {
     i18n.System.set24HourClock (true); // Set the system time to the 24-hour clock.
   } catch (error) {
     let err: BusinessError = error as BusinessError;
     console.error(`call System.set24HourClock failed, error code: ${err.code}, message: ${err.message}.`);
   }
   ```
<!--DelEnd-->
