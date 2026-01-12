# Developing the ExtensionAbility for Notification Subscription
<!--Kit: Notification Kit-->
<!--Subsystem: Notification-->
<!--Owner: @cheerful_ricky-->
<!--Designer: @dongqingran-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->
## Available APIs
| API    | Description| Reference|
| ----- |---------|----------|
| onDestroy(): void| Callback to be invoked when the notification subscription extension is destroyed.|For details, see the API description in [NotificationSubscriberExtensionAbility](../reference/apis-notification-kit/js-apis-notificationSubscriberExtensionAbility.md#ondestroy).|
| onReceiveMessage(): void| Callback to be invoked when the system receives a notification.|For details, see the API description in [NotificationSubscriberExtensionAbility](../reference/apis-notification-kit/js-apis-notificationSubscriberExtensionAbility.md#onreceivemessage).|
| onCancelMessages(): void| Callback to be invoked when notifications are canceled.|For details, see the API description in [NotificationSubscriberExtensionAbility](../reference/apis-notification-kit/js-apis-notificationSubscriberExtensionAbility.md#oncancelmessages).|

## Prerequisites
You have requested the ohos.permission.SUBSCRIBE_NOTIFICATION permission.

## How to Develop

To implement a provider for [NotificationSubscriberExtensionAbility](../reference/apis-notification-kit/js-apis-notificationSubscriberExtensionAbility.md), you need to create a **NotificationSubscriberExtensionAbility** in [DevEco Studio](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-tools-overview) project. The procedure is as follows:

1. Create the **entry/src/main/ets/notificationsubscriberextability** directory.

2. Create the **NotificationSubscriberExtAbility.ets** file in the **entry/src/main/ets/notificationsubscriberextability** directory. The file content is as follows:
   <!--@[huidiao_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Notification-Kit/ThirdpartyWerableDemo/entry/src/main/ets/extensionability/NotificationSubscriberExtAbility.ets)-->
   
   ``` TypeScript
   import { hilog } from '@kit.PerformanceAnalysisKit';
   import { notificationExtensionSubscription, NotificationSubscriberExtensionAbility } from '@kit.NotificationKit';
   // ...
   const DOMAIN = 0x0000;
   
   export default class NotificationSubscriberExtAbility extends NotificationSubscriberExtensionAbility {
     // ...
     onDestroy(): void {
       hilog.info(DOMAIN, 'testTag', 'onDestroy');
       // ...
     }
     // ...
     onReceiveMessage(notificationInfo: notificationExtensionSubscription.NotificationInfo): void {
       hilog.info(DOMAIN, 'testTag', `on receive message ${JSON.stringify(notificationInfo)}`)
       // ...
     }
     // ...
     onCancelMessages(hashCodes: Array<string>): void {
       hilog.info(DOMAIN, 'testTag', `on cancel message ${JSON.stringify(hashCodes)}`)
       // ...
     }
     // ...
   }
   ```
3. Connect to the wearable, obtain the address using the API of [Bluetooth module](../connectivity/connectivity-kit-intro.md#bluetooth), and then subscribe to or unsubscribe from notifications through the [subscribe](../reference/apis-notification-kit/js-apis-notificationExtensionSubscription.md#notificationextensionsubscriptionsubscribe)/[unsubscribe](../reference/apis-notification-kit/js-apis-notificationExtensionSubscription.md#notificationextensionsubscriptionunsubscribe) API.

4. After implementing [NotificationSubscriberExtensionAbility](../reference/apis-notification-kit/js-apis-notificationSubscriberExtensionAbility.md), call the [OpenSubscriptionSettings](../reference/apis-notification-kit/js-apis-notificationExtensionSubscription.md#notificationextensionsubscriptionopensubscriptionsettings) API at an appropriate time to open the notification subscription settings screen and guide the user to grant the permission for obtaining notifications from the device. This screen is displayed as a semi-modal dialog box. It is recommended that you provide a notification authorization button on the device management screen. When the user taps the button, the [OpenSubscriptionSettings](../reference/apis-notification-kit/js-apis-notificationExtensionSubscription.md#notificationextensionsubscriptionopensubscriptionsettings) API is called.

5. Configure ExtensionAbilities in the **module.json5** file of the application.
   <!--@[quick_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Notification-Kit/ThirdpartyWerableDemo/entry/src/main/module.json5)-->
   
   ``` JSON5
   {
     "name": "NotificationSubscriberExtAbility",
     "srcEntry": "./ets/extensionability/NotificationSubscriberExtAbility.ets",
     "type": "notificationSubscriber",
     "description": "$string:NotificationSubscriberExtAbility_desc",
     "icon": "$media:layered_image",
     "label": "$string:NotificationSubscriberExtAbility_label",
     "exported": true
   }
   ```
6. Add the following content to the **string.json** file of the application:
   ```json
     {
       "name": "NotificationSubscriberExtAbility_desc",
       "value": "description"
     },
     {
       "name": "NotificationSubscriberExtAbility_label",
       "value": "ThirdPartyWearableApp"
     }
   ```

## Sample Code for Classic Bluetooth

1. The following uses classic Bluetooth as an example. You can use BLE for connection as required.
2. After receiving the message, the user establishes a Bluetooth connection if the connection is invalid.
3. If the Bluetooth connection already exists, the user directly send the message via Bluetooth.
4. If the message fails to be sent, the user will re-establish the connection and resume sending it once the connection is successfully established.
   <!--@[quick_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Notification-Kit/ThirdpartyWerableDemo/entry/src/main/ets/extensionability/NotificationSubscriberExtAbility.ets)-->
   
   ``` TypeScript
   import { hilog } from '@kit.PerformanceAnalysisKit';
   import { notificationExtensionSubscription, NotificationSubscriberExtensionAbility } from '@kit.NotificationKit';
   import SppClientManager from '../utils/SppClientManager'
   
   const DOMAIN = 0x0000;
   
   export default class NotificationSubscriberExtAbility extends NotificationSubscriberExtensionAbility {
     private sppClientManager: SppClientManager | undefined;
   
     onDestroy(): void {
       hilog.info(DOMAIN, 'testTag', 'onDestroy');
       this.sppClientManager!.stopConnect();
     }
   
     //Called back when a notification is published.
     onReceiveMessage(notificationInfo: notificationExtensionSubscription.NotificationInfo): void {
       hilog.info(DOMAIN, 'testTag', `on receive message ${JSON.stringify(notificationInfo)}`)
       notificationExtensionSubscription.getSubscribeInfo()
         .then(info => {
           if (this.sppClientManager == undefined) {
             this.sppClientManager = new SppClientManager(info[0].addr);
           }
           if (this.sppClientManager.isConnect()) {
             this.sendPublishWithRetry(notificationInfo);
           } else {
             this.sppClientManager.startConnect()
             setTimeout(() => {
               this.sendPublishWithRetry(notificationInfo);
             }, 3000)
           }
         })
     }
   
     // Sends a publish notification and retries once upon failure.
     private sendPublishWithRetry(notificationInfo: notificationExtensionSubscription.NotificationInfo) {
       try {
         this.sppClientManager!.sendNotificationData(notificationInfo);
       } catch (err) {
         hilog.error(DOMAIN, 'testTag', `send failed, errCode ${err.code}, errorMessage ${err.message}, and retry one times`);
         this.sppClientManager!.startConnect();
         setTimeout(() => {
           this.sppClientManager!.sendNotificationData(notificationInfo);
         }, 3000);
       }
     }
   
     //Called back when notifications is cancelled.
     onCancelMessages(hashCodes: Array<string>): void {
       hilog.info(DOMAIN, 'testTag', `on cancel message ${JSON.stringify(hashCodes)}`)
       notificationExtensionSubscription.getSubscribeInfo()
         .then(info => {
           if (this.sppClientManager == undefined) {
             this.sppClientManager = new SppClientManager(info[0].addr);
           }
           if (this.sppClientManager.isConnect()) {
             this.sendCancelWithRetry(hashCodes);
           } else {
             this.sppClientManager.startConnect()
             setTimeout(() => {
               this.sendCancelWithRetry(hashCodes);
             }, 3000)
           }
         })
     }
   
     // Retries a cancel operation if it fails.
     private sendCancelWithRetry(hashCodes: string[]) {
       try {
         this.sppClientManager!.sendCancelNotificationData(hashCodes);
       } catch (err) {
         hilog.error(DOMAIN, 'testTag', `send failed, errCode ${err.code}, errorMessage ${err.message}, and retry one times`);
         this.sppClientManager!.startConnect();
         setTimeout(() => {
           this.sppClientManager!.sendCancelNotificationData(hashCodes);
         }, 3000);
       }
     }
   }
   ```
Note: Do not frequently establish connections. Otherwise, the functionality may be affected.
