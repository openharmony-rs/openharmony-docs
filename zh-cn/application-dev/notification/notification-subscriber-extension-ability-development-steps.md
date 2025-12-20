# 通知订阅扩展能力开发步骤
<!--Kit: Notification Kit-->
<!--Subsystem: Notification-->
<!--Owner: @cheerful_ricky-->
<!--Designer: @dongqingran-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->
## 接口说明
| 接口名     | 描述 | 说明|
| ----- |---------|----------|
| onDestroy(): void| 通知订阅扩展被销毁时的回调。 |具体使用方法详见[NotificationSubscriberExtensionAbility](../reference/apis-notification-kit/js-apis-notificationSubscriberExtensionAbility.md#ondestroy)中该接口说明。|
| onReceiveMessage(): void| 当系统收到通知时回调。 |具体使用方法详见[NotificationSubscriberExtensionAbility](../reference/apis-notification-kit/js-apis-notificationSubscriberExtensionAbility.md#onreceivemessage)中该接口说明。|
| onCancelMessages(): void| 取消通知时的回调。 |具体使用方法详见[NotificationSubscriberExtensionAbility](../reference/apis-notification-kit/js-apis-notificationSubscriberExtensionAbility.md#oncancelmessages)中该接口说明。|

## 前提条件
申请ohos.permission.SUBSCRIBE_NOTIFICATION权限。

## 开发步骤

开发者在实现[NotificationSubscriberExtensionAbility](../reference/apis-notification-kit/js-apis-notificationSubscriberExtensionAbility.md)提供方时，需在[DevEco Studio](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/ide-tools-overview)工程中新建一个NotificationSubscriberExtensionAbility。具体步骤如下。

1. 在entry/src/main/ets/创建目录notificationsubscriberextability。

2. 在entry/src/main/ets/notificationsubscriberextability目录下创建NotificationSubscriberExtAbility.ets，其内容如下。
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
3. 连接穿戴设备，使用[蓝牙模块](../connectivity/connectivity-kit-intro.md#蓝牙简介)接口获取地址，然后通过[subscribe](../reference/apis-notification-kit/js-apis-notificationExtensionSubscription.md#notificationextensionsubscriptionsubscribe)/[unsubscribe](../reference/apis-notification-kit/js-apis-notificationExtensionSubscription.md#notificationextensionsubscriptionunsubscribe)接口订阅或取消订阅通知。

4. 实现[NotificationSubscriberExtensionAbility](../reference/apis-notification-kit/js-apis-notificationSubscriberExtensionAbility.md)后，还需要在合适的时机调用[OpenSubscriptionSettings](../reference/apis-notification-kit/js-apis-notificationExtensionSubscription.md#notificationextensionsubscriptionopensubscriptionsettings)接口，打开通知扩展订阅设置页面，引导用户授予获取本机通知的权限，该页面以半模态弹窗显示。建议在设备管理页面提供一个通知授权的按钮，用户点击按钮则调用[OpenSubscriptionSettings](../reference/apis-notification-kit/js-apis-notificationExtensionSubscription.md#notificationextensionsubscriptionopensubscriptionsettings)接口。

5. 在应用的module.json5文件中配置extensionAbilities。
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
6. 在应用的string.json文件中添加
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

## 传统蓝牙连接示例

1. 示例仅为传统蓝牙连接示例，开发者也可选用低功耗蓝牙连接方式。
2. 用户收到消息后,假如蓝牙连接是无效的,则建立蓝牙连接。
3. 假如蓝牙连接已经存在,则直接使用这个连接发送消息。
4. 如果使用该连接发送消息失败,则重新建立连接,如果连接能建立成功则发送消息。
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
注意：请勿频繁建立链接，可能会影响功能。