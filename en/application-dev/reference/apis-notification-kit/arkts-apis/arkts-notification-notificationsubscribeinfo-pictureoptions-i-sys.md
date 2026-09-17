# PictureOptions (System API)

Describes the image options of the live notification.

**Since:** 26.0.0

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## preparseLiveViewPicList

```TypeScript
preparseLiveViewPicList?: string[]
```

Subscribes to the image information in **extraInfo** of [NotificationLiveViewContent](arkts-notification-notificationcontent-notificationliveviewcontent-i-sys.md) in a common live notification. The input parameter is the **Key** of the image file name that needs to be parsed into the pixelMap format in **extraInfo**.<br>When the application publishes a common live notification, the parsed image information is called back to the subscriber through [onConsume](arkts-notification-notificationsubscriber-notificationsubscriber-i-sys.md#onconsume) and stored in **pictureInfo** of **NotificationLiveViewContent**.

**Type:** string[]

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.
