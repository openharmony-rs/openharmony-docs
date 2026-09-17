# NotificationCapsule

Describes the notification capsule, which is used to display the capsule form in the live view.

> **NOTE:** 
> 
> The actual display effect depends on the device capabilities and the notification center UI style.

**Since:** 11

**System capability:** SystemCapability.Notification.Notification

## backgroundColor

```TypeScript
backgroundColor?: string
```

Capsule background color. Colors in rgb, rgba, or argb format are supported. Example of rgb format color: **#ffffff**, **rgb(255, 100, 255)**. Example of rgba format color: **rgba(255, 100, 255, 0.5)**. Example of argb format color: **#ff000000**. The size does not exceed 202 bytes, and the excess part will be truncated. The value defaults to empty.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.Notification.Notification

## icon

```TypeScript
icon?: image.PixelMap
```

Capsule icon. The total bytes of the icon pixel does not exceed 192 KB (the total bytes of the icon pixel is obtained through getPixelBytesNumber). It is recommended that the icon pixel dimensions be 128 x 128.

**Type:** [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)

**Since:** 11

**System capability:** SystemCapability.Notification.Notification

## title

```TypeScript
title?: string
```

Capsule title. The size does not exceed 202 bytes, and the excess part will be truncated. The value defaults to empty.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.Notification.Notification
