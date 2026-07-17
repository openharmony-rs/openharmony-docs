# NotificationIconButton（系统接口）

描述系统通知按钮。

**起始版本：** 18

<!--Device-unnamed-export interface NotificationIconButton--><!--Device-unnamed-export interface NotificationIconButton-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## hidePanel

```TypeScript
hidePanel?: boolean
```

点击按钮时，是否隐藏通知中心。默认为false。

- true：是。  
- false：否。

**类型：** boolean

**起始版本：** 18

<!--Device-NotificationIconButton-hidePanel?: boolean--><!--Device-NotificationIconButton-hidePanel?: boolean-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## iconResource

```TypeScript
iconResource: IconType
```

按钮的背景图。

**类型：** IconType

**起始版本：** 18

<!--Device-NotificationIconButton-iconResource: IconType--><!--Device-NotificationIconButton-iconResource: IconType-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## name

```TypeScript
name: string
```

按钮标识，用于区分同一通知的多个不同按钮。字符串长度不超过202字节，超出部分会被截断。不可为空字符串。

**类型：** string

**起始版本：** 18

<!--Device-NotificationIconButton-name: string--><!--Device-NotificationIconButton-name: string-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## text

```TypeScript
text?: string
```

按钮展示的信息。默认为空。字符串长度不超过202字节，超出部分会被截断。

**类型：** string

**起始版本：** 18

<!--Device-NotificationIconButton-text?: string--><!--Device-NotificationIconButton-text?: string-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

