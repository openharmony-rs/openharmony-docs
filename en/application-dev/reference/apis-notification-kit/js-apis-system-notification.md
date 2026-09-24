# @system.notification (Notification)
<!--Kit: Notification Kit-->
<!--Subsystem: Notification-->
<!--Owner: @HuYueRong-->
<!--Designer: @dongqingran-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=4bb0b56d7d67b2ab3ff0955bce487aba3399fade translatedAt=2026-09-22T02:37:59.787Z pushedAt=2026-09-22T08:29:58.392Z -->

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
| bundleName  | string                                          | Yes  | Name of the application bundle to which the notification will be redirected after being clicked.                 |
| abilityName  | string                                          | Yes  | Name of the application ability to which the notification will be redirected after being clicked.|
| uri         | string                                          | No  | URI of the page to be redirected to.             |


## ShowNotificationOptions

**System capability**: SystemCapability.Notification.Notification

| Name         | Type                                          | Mandatory| Description                       |
| ------------- | ---------------------------------------------- | ---- | ------------------------- |
| contentTitle  | string                                          | No  | Notification title.                 |
| contentText   | string                                          | No   | [Notification content](../../notification/notification-glossary.md#notification-content).                  |
| clickAction<sup>(deprecated)</sup>   | [ActionResult](#actionresult)                                    | No  | Action triggered when the notification is clicked.<br>This API is deprecated since API version 7.    |


## notification.show

show(options?: ShowNotificationOptions): void

Displays a notification.

**System capability**: SystemCapability.Notification.Notification

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| options | [ShowNotificationOptions](#shownotificationoptions) | No | Notification title. |

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
<!--no_check-->