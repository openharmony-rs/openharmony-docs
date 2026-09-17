# NotificationBasicContent

Describes the basic text notification, which is used to display the title and body content. It serves as the basic content structure for other notification types. Other notification types (such as long text, multi-line text, picture, and live view) inherit this API and extend their own specific fields on this basis.

**Since:** 7

**System capability:** SystemCapability.Notification.Notification

## additionalText

```TypeScript
additionalText?: string
```

Additional notification content, which supplements the notification content and is not displayed in the notification center. It defaults to empty. The size does not exceed 3072 bytes, and the excess part will be truncated.

**Type:** string

**Since:** 7

**System capability:** SystemCapability.Notification.Notification

## lockscreenPicture

```TypeScript
lockscreenPicture?: image.PixelMap
```

Picture displayed on the lock screen. This parameter is left empty by default. Currently, only the live view notification is supported. The total number of the icon pixel bytes cannot exceed 192 KB (which is obtained through getPixelBytesNumber). The recommended icon size is 128 x 128 pixels. The display effect depends on the device capability and notification center UI style.

**Type:** [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)

**Since:** 12

**System capability:** SystemCapability.Notification.Notification

## text

```TypeScript
text: string
```

Notification body content, displayed below the title. It cannot be an empty string. The size does not exceed 3072 bytes, and the excess part will be truncated.

**Type:** string

**Since:** 7

**System capability:** SystemCapability.Notification.Notification

## title

```TypeScript
title: string
```

Notification title, displayed at the top of the notification. It cannot be an empty string. The size does not exceed 1024 bytes, and the excess part will be truncated.

**Type:** string

**Since:** 7

**System capability:** SystemCapability.Notification.Notification
