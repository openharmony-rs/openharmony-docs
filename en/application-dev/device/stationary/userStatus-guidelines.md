# User Status Awareness Development

<!--Kit: Multimodal Awareness Kit-->
<!--Subsystem: MultimodalAwareness-->
<!--Owner: @dilligencer-->
<!--Designer: @zou_ye-->
<!--Tester: @judan-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=a1815a6960f035b2f960cbb3747e78fb7c1af4a8 translatedAt=2026-06-15T08:12:58.089Z pushedAt=2026-06-16T13:35:15.586Z -->

The UserStatus module, designed for user status awareness, empowers the system to perceive specific conditions of the operator, such as determining their age group.

For detailed API description, refer to [@ohos.multimodalAwareness.userStatus (User Status Awareness)](../../reference/apis-multimodalawareness-kit/js-apis-awareness-userStatus.md).

> **NOTE**
> 
> The initial APIs of this module are supported since API version 20 and deprecated since API version 24.

## How to Develop

### When to Use

An application can invoke the UserStatus module when it needs to obtain the age group of users. This way, the application can determine, for example, whether the individual interacting with the device is a child or an adult.

The APIs of this module are supported since API version 20.

### Available APIs

| API                                                      | Description                                  |
| ------------------------------------------------------------ | -------------------------------------- |
| on(type:'userAgeGroupDetected',callback:Callback&lt;UserClassification&gt;):void; | Enables the age group detection function. This API returns the result through a callback.|
| off(type: 'userAgeGroupDetected', callback?: Callback&lt;UserClassification&gt;): void; | Disables the age group detection function.                  |

### Constraints

 - If the device does not support the age group detection function, error code 801 is returned.

<!--RP1--> <!--RP1End-->

### Development Procedure

1. Import the related modules.

   <!-- @[import_the_user_status_module](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Stationary/UserStatus/entry/src/main/ets/pages/Index.ets) -->

   ```ts
   import { userStatus } from '@kit.MultimodalAwarenessKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   ```

2. Define the callback function used to listen for the age group detection result changes.

   <!-- @[user_status_parameter](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Stationary/UserStatus/entry/src/main/ets/pages/Index.ets) -->

   ```ts
   let callback : Callback<userStatus.UserClassification> = (data : userStatus.UserClassification) => {
     console.info('callback succeeded, ageGroup:' + data.ageGroup + ", confidence:" + data.confidence);
   };
   ```

3. Enable the age group detection function.

   <!-- @[user_status_subscribe](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Stationary/UserStatus/entry/src/main/ets/pages/Index.ets) -->

   ```ts
   try {
      userStatus.on('userAgeGroupDetected', callback);  
      console.info("on succeeded");
   } catch (err) {
      let error = err as BusinessError;
      console.error("Failed on and err code is " + error.code);
   }
   ```

4. Disable the age group detection function.

   <!-- @[user_status_unsubscribe](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Stationary/UserStatus/entry/src/main/ets/pages/Index.ets) -->

   ```ts
   try {
      userStatus.off('userAgeGroupDetected');
      console.info("off succeeded");
   } catch (err) {
      let error = err as BusinessError;
      console.error("Failed off and err code is " + error.code);
   }
   ```