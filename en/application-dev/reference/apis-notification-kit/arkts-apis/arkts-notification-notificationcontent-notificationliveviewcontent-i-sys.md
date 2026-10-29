# NotificationLiveViewContent (System API)

```TypeScript
export interface NotificationLiveViewContent extends NotificationBasicContent
```

Describes the [normal live view notification](../../../notification/notification-glossary.md#normal-live-view). This API is inherited from [NotificationBasicContent](arkts-notification-notificationcontent-notificationbasiccontent-i.md).

**Inheritance/Implementation:** NotificationLiveViewContent extends [NotificationBasicContent](arkts-notification-notificationcontent-notificationbasiccontent-i.md)

**Since:** 11

<!--Device-unnamed-export interface NotificationLiveViewContent extends NotificationBasicContent--><!--Device-unnamed-export interface NotificationLiveViewContent extends NotificationBasicContent-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## extensionWantAgent

```TypeScript
extensionWantAgent?: WantAgent
```

Redirection by tapping in the auxiliary area. This parameter is left empty by default.

**Type:** [WantAgent](../../apis-ability-kit/arkts-apis/arkts-ability-wantagent-depr-t.md)

**Since:** 20

<!--Device-NotificationLiveViewContent-extensionWantAgent?: WantAgent--><!--Device-NotificationLiveViewContent-extensionWantAgent?: WantAgent-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## extraInfo

```TypeScript
extraInfo?: Record<string, Object>
```

Additional content of the [live view notification](../../../notification/notification-glossary.md#live-view-notification). Empty by default.

**Type:** Record&lt;string, Object&gt;

**Since:** 11

<!--Device-NotificationLiveViewContent-extraInfo?: Record<string, Object>--><!--Device-NotificationLiveViewContent-extraInfo?: Record<string, Object>-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## isLocalUpdateOnly

```TypeScript
isLocalUpdateOnly?: boolean
```

Whether the live view is updated only locally. The default value is **false**.

- **true**: Yes.  
- **false**: No.

**Type:** boolean

**Since:** 12

<!--Device-NotificationLiveViewContent-isLocalUpdateOnly?: boolean--><!--Device-NotificationLiveViewContent-isLocalUpdateOnly?: boolean-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## pictureInfo

```TypeScript
pictureInfo?: Record<string, Array<image.PixelMap>>
```

Extra image information of the live view. This parameter is left empty by default.

**Type:** Record&lt;string, Array&lt;[image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)&gt;&gt;

**Since:** 11

<!--Device-NotificationLiveViewContent-pictureInfo?: Record<string, Array<image.PixelMap>>--><!--Device-NotificationLiveViewContent-pictureInfo?: Record<string, Array<image.PixelMap>>-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## status

```TypeScript
status: LiveViewStatus
```

Notification status.

**Type:** [LiveViewStatus](arkts-notification-notificationcontent-liveviewstatus-e-sys.md)

**Since:** 11

<!--Device-NotificationLiveViewContent-status: LiveViewStatus--><!--Device-NotificationLiveViewContent-status: LiveViewStatus-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## version

```TypeScript
version?: number
```

Notification version number. If the version number stored in the database is **0xffffffff**, the version number is not verified when the live view is updated or ended; otherwise, the current version number must be greater than the version number stored in the database. If this parameter is left empty, the default value is **0xffffffff**.

**Type:** number

**Since:** 11

<!--Device-NotificationLiveViewContent-version?: int--><!--Device-NotificationLiveViewContent-version?: int-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.
