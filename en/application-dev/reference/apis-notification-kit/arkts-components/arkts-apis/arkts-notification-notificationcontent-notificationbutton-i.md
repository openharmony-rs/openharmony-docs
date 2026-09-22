# NotificationButton

```TypeScript
export interface NotificationButton
```

Describes the notification button, which is used to display an interactive button in the live view.

> **NOTE:** 
> 
> The actual display effect depends on the device capabilities and the notification center UI style.

**Since:** 11

**System capability:** SystemCapability.Notification.Notification

## icons

```TypeScript
icons?: Array<image.PixelMap>
```

List of button icons, corresponding one-to-one with **names**, with each icon displayed on its corresponding button. A maximum of 3 icons is supported. The total bytes of icon pixels does not exceed 192 KB (the total bytes of icon pixels is obtained through getPixelBytesNumber). It is recommended that the icon pixel dimensions be 128 x 128. The value defaults to empty. This parameter is mutually exclusive with **iconsResource**; only one of them can be used.

**Type:** Array&lt;[image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)&gt;

**Since:** 11

**System capability:** SystemCapability.Notification.Notification

## iconsResource

```TypeScript
iconsResource?: Array<Resource>
```

List of button icon resources, corresponding one-to-one with **names** via Resource references. A maximum of 3 resources is supported. The value defaults to empty. This parameter is mutually exclusive with **icons**; only one of them can be used.

**Type:** Array&lt;[Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-resource-i.md)&gt;

**Since:** 12

**System capability:** SystemCapability.Notification.Notification

## names

```TypeScript
names?: Array<string>
```

List of button names. Each name corresponds to the text displayed on a notification button. A maximum of 3 buttons is supported. The size of each name does not exceed 202 bytes, and the excess part will be truncated. The value defaults to empty.

**Type:** Array&lt;string&gt;

**Since:** 11

**System capability:** SystemCapability.Notification.Notification
