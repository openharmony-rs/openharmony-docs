# @system.notification (Notification)
<!--Kit: Notification Kit-->
<!--Subsystem: Notification-->
<!--Owner: @HuYueRong-->
<!--Designer: @wangsen1994-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=1ded46b3f2c6157598c112b16f192beb1f37cf1d translatedAt=2026-10-08T02:35:40.742Z pushedAt=2026-10-08T10:04:15.829Z -->

> **NOTE**
> - The APIs of this module are no longer maintained since API version 7. You are advised to use [@ohos.notification (Notification)](js-apis-notification.md).
> 
> - The initial APIs of this module are supported since API version 3. Newly added APIs will be marked with a superscript to indicate their earliest API version.


## Modules to Import


```ts
import notification from '@system.notification';
```

## ActionResult

**System capability**: SystemCapability.Notification.Notification

| Name       | Type                                          | Mandatory| Description                     |
| ----------- | ---------------------------------------------- | ---- | ------------------------- |
| bundleName  | string                                          | Yes  | Name of the application bundle to which the notification will be redirected after being tapped.                 |
| abilityName  | string                                          | Yes  | Name of the application ability to which the notification will be redirected after being tapped.|
| uri         | string                                          | No  | URI of the page to be redirected to.             |


## ShowNotificationOptions

**System capability**: SystemCapability.Notification.Notification

| Name         | Type                                          | Mandatory| Description                       |
| ------------- | ---------------------------------------------- | ---- | ------------------------- |
| contentTitle  | string                                          | No  | Notification title.                 |
| contentText   | string                                          | No   | [Notification content](../../notification/notification-glossary.md#notification-content).                  |
| clickAction<sup>(deprecated)</sup>   | [ActionResult](#actionresult)                                    | No  | Action triggered when the notification is tapped.<br>This API is deprecated since API version 7.    |


## notification.show

show(options?: ShowNotificationOptions): void

Displays a notification.

**System capability**: SystemCapability.Notification.Notification

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| options | [ShowNotificationOptions](#shownotificationoptions) | No | Options for displaying the notification, including the notification title, notification content, and the action triggered when the notification is tapped. |

**Example**
```ts
let notificationObj: notification = {
  show() {
    notification.show({
      contentTitle: 'title info',
      contentText: 'text',
      clickAction: {
        bundleName: 'com.example.testapp',
        abilityName: 'notificationDemo',
        uri: '/path/to/notification'
      }
    });
  }
}
```