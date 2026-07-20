# NotificationActionButton

NotificationActionButton模块定义了通知中显示的操作按钮，用于在[NotificationRequest](arkts-notification-notificationrequest-notificationrequest-i.md)中添加交互式操作按钮，让用户通过点击按钮触发WantAgent动作。当开发者需要在通知中提供交互式操作按钮（如"回复"、"标记已读"等）时使用此模块。

> **说明：**  
>  
> 本模块首批接口从API version 7开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

**起始版本：** 7

<!--Device-unnamed-export interface NotificationActionButton--><!--Device-unnamed-export interface NotificationActionButton-End-->

**系统能力：** SystemCapability.Notification.Notification

## extras

```TypeScript
extras?: { [key: string]: any }
```

按钮扩展信息。默认为空。

**类型：** { [key: string]: any }

**起始版本：** 7

<!--Device-NotificationActionButton-extras?: { [key: string]: any }--><!--Device-NotificationActionButton-extras?: { [key: string]: any }-End-->

**系统能力：** SystemCapability.Notification.Notification

## title

```TypeScript
title: string
```

按钮标题，显示在通知的操作按钮上。字符串长度不超过202字节，超出部分会被截断。不可为空字符串。

**类型：** string

**起始版本：** 7

<!--Device-NotificationActionButton-title: string--><!--Device-NotificationActionButton-title: string-End-->

**系统能力：** SystemCapability.Notification.Notification

## userInput

```TypeScript
userInput?: NotificationUserInput
```

用户输入对象实例，默认为空。表示用户输入时的标识。

**类型：** NotificationUserInput

**起始版本：** 8

<!--Device-NotificationActionButton-userInput?: NotificationUserInput--><!--Device-NotificationActionButton-userInput?: NotificationUserInput-End-->

**系统能力：** SystemCapability.Notification.Notification

## wantAgent

```TypeScript
wantAgent: WantAgent
```

点击按钮时触发的WantAgent，封装了应用的行为意图。用户点击按钮后，系统将按WantAgent指定的方式执行动作（如跳转至指定UIAbility或发送公共事件）。

**类型：** WantAgent

**起始版本：** 7

<!--Device-NotificationActionButton-wantAgent: WantAgent--><!--Device-NotificationActionButton-wantAgent: WantAgent-End-->

**系统能力：** SystemCapability.Notification.Notification

