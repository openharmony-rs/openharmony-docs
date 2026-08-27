# NotificationSlot

描述通知渠道，不同通知渠道对应的通知提醒方式不同。

**起始版本：** 7

**系统能力：** SystemCapability.Notification.Notification

## badgeFlag

```TypeScript
badgeFlag?: boolean
```

是否显示角标。默认值为true。  
- true：显示角标。  
- false：不显示角标。

**类型：** boolean

**起始版本：** 7

**系统能力：** SystemCapability.Notification.Notification

## bypassDnd

```TypeScript
bypassDnd?: boolean
```

是否在系统中绕过免打扰模式。默认值为false。  
- true：绕过免打扰模式，免打扰模式下仍会提醒。  
- false：不绕过免打扰模式，免打扰模式下不提醒。

**类型：** boolean

**起始版本：** 7

**系统能力：** SystemCapability.Notification.Notification

## desc

```TypeScript
desc?: string
```

通知渠道描述信息。大小不超过243字节，超出部分会被截断。

**类型：** string

**起始版本：** 7

**系统能力：** SystemCapability.Notification.Notification

## enabled

```TypeScript
readonly enabled?: boolean
```

是否允许发布此通知渠道类型的通知。  
- true：允许发布通知。  
- false：禁止发布通知。

**类型：** boolean

**起始版本：** 9

**系统能力：** SystemCapability.Notification.Notification

## level

```TypeScript
level?: notification.SlotLevel
```

通知级别。

**类型：** notification.SlotLevel

**起始版本：** 7

**废弃版本：** 20

**替代接口：** [notificationLevel](#notificationlevel)

**系统能力：** SystemCapability.Notification.Notification

## lightColor

```TypeScript
lightColor?: number
```

通知灯颜色。预留能力，暂不支持。

**类型：** number

**起始版本：** 7

**系统能力：** SystemCapability.Notification.Notification

## lightEnabled

```TypeScript
lightEnabled?: boolean
```

是否闪灯。默认值为false。  
- true：闪灯。  
- false：不闪灯。

**类型：** boolean

**起始版本：** 7

**系统能力：** SystemCapability.Notification.Notification

## lockscreenVisibility

```TypeScript
lockscreenVisibility?: number
```

在锁定屏幕上显示通知的模式。预留能力，暂不支持。

**类型：** number

**起始版本：** 7

**系统能力：** SystemCapability.Notification.Notification

## notificationLevel

```TypeScript
notificationLevel?: notificationManager.SlotLevel
```

通知级别，用于描述该渠道类型通知的显示优先级和提醒强度。

**类型：** notificationManager.SlotLevel

**起始版本：** 20

**系统能力：** SystemCapability.Notification.Notification

## notificationType

```TypeScript
notificationType?: notificationManager.SlotType
```

渠道类型。不同渠道类型的通知提醒方式不同。

**类型：** notificationManager.SlotType

**起始版本：** 11

**系统能力：** SystemCapability.Notification.Notification

## sound

```TypeScript
sound?: string
```

该渠道的通知的自定义铃声文件名。该文件放在resources/rawfile目录下，支持m4a、aac、mp3、ogg、wav、flac、amr等格式。大小不超过243字节，超出部分会被截断。

**类型：** string

**起始版本：** 7

**系统能力：** SystemCapability.Notification.Notification

## type

```TypeScript
type?: notification.SlotType
```

渠道类型。

**类型：** notification.SlotType

**起始版本：** 7

**废弃版本：** 11

**替代接口：** [notificationType](#notificationtype)

**系统能力：** SystemCapability.Notification.Notification

## vibrationEnabled

```TypeScript
vibrationEnabled?: boolean
```

是否可振动。默认值为false。  
- true：可振动。  
- false：不可振动。

**类型：** boolean

**起始版本：** 7

**系统能力：** SystemCapability.Notification.Notification

## vibrationValues

```TypeScript
vibrationValues?: Array<number>
```

通知振动样式。预留能力，暂不支持。

**类型：** Array&lt;number&gt;

**起始版本：** 7

**系统能力：** SystemCapability.Notification.Notification
