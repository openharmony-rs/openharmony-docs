# NotificationCapsule

描述通知胶囊，用于在实况窗中展示胶囊形态。

> **说明：**  
>  
> 实际显示效果依赖于设备能力和通知中心UI样式。

**起始版本：** 11

<!--Device-unnamed-export interface NotificationCapsule--><!--Device-unnamed-export interface NotificationCapsule-End-->

**系统能力：** SystemCapability.Notification.Notification

## capsuleButtons

```TypeScript
capsuleButtons?: Array<NotificationIconButton>
```

即时任务类实况胶囊的按钮（最多支持2个）。默认为空。

**类型：** Array&lt;NotificationIconButton&gt;

**起始版本：** 18

<!--Device-NotificationCapsule-capsuleButtons?: Array<NotificationIconButton>--><!--Device-NotificationCapsule-capsuleButtons?: Array<NotificationIconButton>-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## content

```TypeScript
content?: string
```

胶囊的拓展文本。默认为空。

**类型：** string

**起始版本：** 12

<!--Device-NotificationCapsule-content?: string--><!--Device-NotificationCapsule-content?: string-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## time

```TypeScript
time?: number
```

即时任务类实况胶囊展示时长。默认值为0。单位：秒。

**类型：** number

**起始版本：** 18

<!--Device-NotificationCapsule-time?: int--><!--Device-NotificationCapsule-time?: int-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

