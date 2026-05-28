# NotificationSubscribeInfo (System API)
<!--Kit: Notification Kit-->
<!--Subsystem: Notification-->
<!--Owner: @HuYueRong-->
<!--Designer: @dongqingran-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->

The **NotificationSubscribeInfo** module provides APIs for defining the information about the publisher for notification subscription.

> **NOTE**
>
> The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs provided by this module are system APIs.

## NotificationSubscribeInfo

**System capability**: SystemCapability.Notification.Notification

**System API**: This is a system API.

| Name                | Type                 | Read-Only| Optional| Description                                      |
| -------------------- | --------------------- | ---- | --- | ------------------------------------------ |
| bundleNames          | Array<string\>         | No| Yes| Bundle names of the applications whose notifications to subscribe to. If this parameter is not specified, the subscription defaults to notifications from all applications.|
| userId               | number                | No| Yes | User ID. If this parameter is not specified, the subscription defaults to notifications from the current user ID.|
| deviceType<sup>12+</sup>           | string                | No| Yes| Device type. If this parameter is not specified, the subscription defaults to notifications from the current device. The value is obtained based on [device information](../apis-basic-services-kit/js-apis-device-info.md).                                   |
| slotTypes<sup>18+</sup>   | Array<[notificationManager.SlotType](js-apis-notificationManager.md#slottype)\>| No| Yes| Types of the notification slots. If this parameter is not specified, the subscription defaults to notifications of all slot types.|
| filterLimit<sup>18+</sup>   | number| No| Yes| Notification filtering range. The default value is **0**. The options are as follows:<br>- **0**: All notifications are included in the subscription.<br>- **1**: Filter out notifications whose slot type is [SOCIAL_COMMUNICATION](js-apis-notificationManager.md#slottype) and [userInput](js-apis-inner-notification-notificationActionButton.md#notificationactionbutton-1) is empty.<br>- **2**: Filter out notifications whose slot type is [SOCIAL_COMMUNICATION](js-apis-notificationManager.md#slottype) and [userInput](js-apis-inner-notification-notificationActionButton.md#notificationactionbutton-1) is not empty.|
| voiceContentOptions   | [VoiceContentOptions](#voicecontentoptions)| No| Yes| Voice broadcast options of the notification.<br> **Since:** 26.0.0<br> **Model restriction:** This API can be used only in the stage model.|
| pictureOptions   | [PictureOptions](#pictureoptions)| No| Yes| Image options of the live notification.<br> **Since**: 26.0.0<br> **Model restriction:** This API can be used only in the stage model.|

## VoiceContentOptions

**Since:** 26.0.0

**System capability**: SystemCapability.Notification.Notification

**Model restriction:** This API can be used only in the stage model.

**System API**: This is a system API.

| Name     | Type             | Read-Only  | Optional| Description                    |
|-----------| ---------------- | -------|----- |-------------------------|
| enabled        | boolean | No| Yes| Whether to subscribe to the voice broadcast content of a notification.<br> - **true**: yes.<br> - **false**: no. The default value is **false**.|

## PictureOptions

**Since:** 26.0.0

**System capability**: SystemCapability.Notification.Notification

**Model restriction:** This API can be used only in the stage model.

**System API**: This is a system API.

| Name     | Type             | Read-Only  | Optional| Description                    |
|-----------| ---------------- | -------|----- |-------------------------|
| preparseLiveViewPicList | string[] | No| Yes| Subscribes to the image information in **extraInfo** of [NotificationLiveViewContent](js-apis-inner-notification-notificationContent-sys.md#notificationliveviewcontent11) in a common live notification. The input parameter is the **Key** of the image file name that needs to be parsed into the pixelMap format in **extraInfo**.<br>When the application publishes a common live notification, the parsed image information is called back to the subscriber through [onConsume](js-apis-inner-notification-notificationSubscriber-sys.md#onconsume) and stored in **pictureInfo** of **NotificationLiveViewContent**.|
