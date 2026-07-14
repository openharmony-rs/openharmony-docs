# Motion Awareness Development

<!--Kit: Multimodal Awareness Kit-->
<!--Subsystem: MultimodalAwareness-->
<!--Owner: @dilligencer-->
<!--Designer: @zou_ye-->
<!--Tester: @judan-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=45bd746ae860f1fef969073ffaa0af763a0251fa translatedAt=2026-06-29T06:19:48.370Z pushedAt=2026-06-30T03:15:35.109Z -->

## When to Use

An application can call the motion module to identify user actions, for example, whether the user is operating the device screen with the left hand or the right hand.

For detailed API introduction, refer to [@ohos.multimodalAwareness.motion (Motion Awareness)](../../reference/apis-multimodalawareness-kit/js-apis-awareness-motion.md).

Operating hand status query is supported since API version 15. Holding hand status query is supported since API version 20.

## Operating Hand Status Query

### Available APIs

| API                                                      | Description                                  |
| ------------------------------------------------------------ | -------------------------------------- |
| on(type:'operatingHandChanged',callback:Callback&lt;OperatingHandStatus&gt;):void; | Subscribes to operating hand change events. This API uses a callback to return the result.|
| off(type: 'operatingHandChanged', callback?: Callback&lt;OperatingHandStatus&gt;): void; | Unsubscribes from operating hand change events.                  |
| getRecentOperatingHandStatus(): OperatingHandStatus;         | Obtains the latest operating hand status.                |

### Required Permissions

To use the motion module to obtain the operating hand, you need to request the **ohos.permission.ACTIVITY_MOTION** or **ohos.permission.DETECT_GESTURE** permission. For details, see [Declaring Permissions](../../security/AccessToken/declare-permissions.md).

  ```JSON5
  "requestPermissions":[
      {
        "name" : "ohos.permission.ACTIVITY_MOTION",
        // Configure reason and usedScene as needed.
        "reason" : "", // Used for application release verification.
        "usedScene" : {
           "abilities" : [
              "" // Name of the ability that uses this permission.
           ],
           "when" : "" // Time when the permission is used.
        },
      },
      {
        "name" : "ohos.permission.DETECT_GESTURE"
      }
    ]
  ```

### Constraints

 - If the device does not support the age group detection function, error code 801 is returned.

 - Knuckle operations are not categorized as hand operations.

 - Multi-finger operations are not supported in window rotation scenarios.

 - The effective range does not include the area within 8 mm from the screen edge.

 - Result is reported after the first subscription or operating hand switchover and the operation is triggered for several consecutive times.

 - Touch response is not supported within 8 mm from the edges of the screen.

### How to Develop

1. Import the related modules.

   <!-- @[import_the_motion_module](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Stationary/Motion/entry/src/main/ets/pages/Index.ets) -->

   ``` TypeScript
   import { motion } from '@kit.MultimodalAwarenessKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   ```

2. Define a callback to receive operating hand change results.

   <!-- @[motion_subscribe_operating_parameter](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Stationary/Motion/entry/src/main/ets/pages/Index.ets) -->

   ```ts
   let callback:Callback<motion.OperatingHandStatus> = (data:motion.OperatingHandStatus) => {
     console.info('callback succeeded' + data);
   };
   ```

3. Subscribe to operating hand change results.

   <!-- @[motion_subscribe_operating](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Stationary/Motion/entry/src/main/ets/pages/Index.ets) -->

   ```ts
   try {
      motion.on('operatingHandChanged', callback);
      console.info("on succeeded");
   } catch (err) {
      let error = err as BusinessError;
      console.error("Failed on and err code is " + error.code);
   }
   ```

4. Unsubscribe from operating hand change events.

   <!-- @[motion_unsubscribe_operating](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Stationary/Motion/entry/src/main/ets/pages/Index.ets) -->

   ```ts
   try {
      motion.off('operatingHandChanged');
      console.info("off succeeded");
   } catch (err) {
      let error = err as BusinessError;
      console.error("Failed off and err code is " + error.code);
   }
   ```

5. Obtain the latest operating hand status.

   <!-- @[motion_get_operating](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Stationary/Motion/entry/src/main/ets/pages/Index.ets) -->

   ```ts
   try {
      let data:motion.OperatingHandStatus = motion.getRecentOperatingHandStatus();
      console.info('get succeeded' + data);
   } catch (err) {
      let error = err as BusinessError;
      console.error("Failed get and err code is " + error.code);
   }
   ```

## Holding Hand Status Query

### Available APIs

| API                                                      | Description                                  |
| ------------------------------------------------------------ | -------------------------------------- |
| on(type:'holdingHandChanged',callback:Callback&lt;HoldingHandStatus&gt;): void; | Enables listening for holding hand status changes. This API uses a callback to return the result.|
| off(type: 'holdingHandChanged', callback?: Callback&lt;HoldingHandStatus&gt;): void; | Disables listening for holding hand status changes.                  |

### Required Permissions

To use the motion module to obtain the holding hand, you need to request the **ohos.permission.DETECT_GESTURE** permission. For details, see [Declaring Permissions](../../security/AccessToken/declare-permissions.md).

  ```JSON5
  "requestPermissions":[
      {
        "name" : "ohos.permission.DETECT_GESTURE"
      }
    ]
  ```

### Constraints

 - Motion awareness is supported on some device models. If the smart reachability switch (accessible from **Settings** > **System**) is available, this function is supported. Otherwise, error code 801 will be returned.

 - The device screen must be on and unlocked.

 - The thickness of the device protective case (if any) must not exceed 3 mm.

 - You need to naturally hold the device with five fingers, while the palm area of your hand touches the device (or four fingers except the thumb and the palm area of your hand touch the device).

 - The contact area of each finger is as large as possible (at least 30 mm2 in ideal cases).

 - Wearing gloves can significantly reduce the recognition accuracy.

 - When holding the device in portrait mode, the camera must face upward.

 - Landscape holding is supported. Note that holding the device in portrait orientation when the application is displayed in landscape orientation, or holding the device in landscape orientation when the application is displayed in portrait orientation, is considered an abnormal posture. In these cases, the device is held along its long edge or short edge, respectively, and successful recognition is not guaranteed.

 - You must face the screen when holding the device.

 - Do not touch any other objects (such as the table or other body parts) at the same time when holding the device.

 - The recognition of unholding depends on the device status. The recognition may fail if the device is not static.

### How to Develop

1. Import the related modules.

   <!-- @[import_the_motion_module](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Stationary/Motion/entry/src/main/ets/pages/Index.ets) -->

   ```ts
   import { motion } from '@kit.MultimodalAwarenessKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   ```

2. Define a callback to receive the hand holding status change.

   <!-- @[motion_subscribe_holding_parameter](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Stationary/Motion/entry/src/main/ets/pages/Index.ets) -->

   ```ts
   let callback:Callback<motion.HoldingHandStatus> = (data:motion.HoldingHandStatus) => {
     console.info('callback succeeded' + data);
   };
   ```

3. Enable listening for holding hand status changes.

   <!-- @[motion_subscribe_holding](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Stationary/Motion/entry/src/main/ets/pages/Index.ets) -->

   ```ts
   try {
      motion.on('holdingHandChanged', callback);
      console.info("on succeeded");
   } catch (err) {
      let error = err as BusinessError;
      console.error("Failed on and err code is " + error.code);
   }
   ```

4. Disable listening for holding hand status changes.

   <!-- @[motion_unsubscribe_holding](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Stationary/Motion/entry/src/main/ets/pages/Index.ets) -->

   ```ts
   try {
      motion.off('holdingHandChanged');
      console.info("off succeeded");
   } catch (err) {
      let error = err as BusinessError;
      console.error("Failed off and err code is " + error.code);
   }
   ```