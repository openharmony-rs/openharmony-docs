# NotificationActionButton

<!--Kit: Notification Kit-->
<!--Subsystem: Notification-->
<!--Owner: @HuYueRong-->
<!--Designer: @dongqingran-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=50e734d278c25dbb71273705da516c218b3754a1 translatedAt=2026-06-29T02:36:13.739Z pushedAt=2026-06-30T10:57:36.996Z -->

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
| extras    | { [key: string]: any }                          | No  | Yes  | Extended information of the button. The default value is empty.              |
| userInput<sup>8+</sup> | [NotificationUserInput](js-apis-inner-notification-notificationUserInput.md) | No | Yes | User input object. This parameter is left empty by default. ID entered by a subscriber.         |