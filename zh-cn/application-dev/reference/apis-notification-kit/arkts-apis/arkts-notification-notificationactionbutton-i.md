# NotificationActionButton

描述通知中显示的操作按钮。

**起始版本：** 7

**系统能力：** SystemCapability.Notification.Notification

## extras

```TypeScript
extras?: { [key: string]: any }
```

按钮扩展信息。预留能力，暂未支持。

**类型：** { [key: string]: any }

**起始版本：** 7

**系统能力：** SystemCapability.Notification.Notification

## title

```TypeScript
title: string
```

按钮标题。字符串长度不超过200字节，超出部分会被截断；也不可为空字符串。

**类型：** string

**起始版本：** 7

**系统能力：** SystemCapability.Notification.Notification

## userInput

```TypeScript
userInput?: NotificationUserInput
```

用户输入对象实例，默认为空。表示用户输入时的标识。

**类型：** NotificationUserInput

**起始版本：** 8

**系统能力：** SystemCapability.Notification.Notification

## wantAgent

```TypeScript
wantAgent: WantAgent
```

点击按钮时触发的WantAgent。

**类型：** WantAgent

**起始版本：** 7

**系统能力：** SystemCapability.Notification.Notification

