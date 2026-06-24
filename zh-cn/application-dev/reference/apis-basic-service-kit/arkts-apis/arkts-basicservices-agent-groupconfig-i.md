# GroupConfig

下载任务分组配置选项。

**起始版本：** 15

**系统能力：** SystemCapability.Request.FileTransferAgent

## gauge

```TypeScript
gauge?: boolean
```

后台任务的进度通知策略。

- true，显示进度、成功、失败通知。
- false，仅显示成功、失败通知。

默认为false。

**类型：** boolean

**起始版本：** 15

**系统能力：** SystemCapability.Request.FileTransferAgent

## notification

```TypeScript
notification: Notification
```

通知栏自定义设置。默认值为`{}`

**类型：** Notification

**起始版本：** 15

**系统能力：** SystemCapability.Request.FileTransferAgent

