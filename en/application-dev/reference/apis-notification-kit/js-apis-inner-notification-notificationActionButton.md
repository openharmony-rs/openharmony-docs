# NotificationActionButton
<!--Kit: Notification Kit-->
<!--Subsystem: Notification-->
<!--Owner: @HuYueRong-->
<!--Designer: @wangsen1994-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=1ded46b3f2c6157598c112b16f192beb1f37cf1d translatedAt=2026-10-08T02:16:49.501Z pushedAt=2026-10-08T09:16:40.903Z -->

The **NotificationActionButton** module defines the action buttons displayed in a notification. It is used to add interactive action buttons in [NotificationRequest](js-apis-inner-notification-notificationRequest.md#notificationrequest-1), allowing users to trigger a **WantAgent** action by tapping the button. This module is used when you need to provide interactive action buttons (such as **Reply** and **Mark as read**) in a notification.

> **NOTE**
>
> The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## NotificationActionButton

**System capability**: SystemCapability.Notification.Notification

| Name     | Type                                           | Read Only| Optional| Description                     |
| --------- | ----------------------------------------------- | --- | ---- | ------------------------- |
| title     | string                                          | No  | No  | Title of the button, displayed on the action button of the notification. The string length cannot exceed 202 bytes; the excess part will be truncated. It cannot be an empty string.                  |
| wantAgent | [WantAgent](../apis-ability-kit/js-apis-app-ability-wantAgent.md)   | No  | No  | **WantAgent** triggered when the button is tapped, which encapsulates the application's behavioral intent. After the user taps the button, the system will execute the action in the method specified by the **WantAgent** (such as navigating to a specified **UIAbility** or sending a common event). |
| extras    | { [key: string]: any }                          | No  | Yes  | Extension information of the button. The default value is empty. It is used to store custom extension data of the button. An application can add any key-value pair information as needed, such as the specific identifier and additional data of the button.              |
| userInput<sup>8+</sup> | [NotificationUserInput](js-apis-inner-notification-notificationUserInput.md) | No | Yes | User input object. This parameter is left empty by default. ID entered by a subscriber.         |
