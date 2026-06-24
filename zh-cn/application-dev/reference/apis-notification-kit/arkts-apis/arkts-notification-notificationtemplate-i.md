# NotificationTemplate

通知模板。

> **说明：**
>
> 提供预定义模板支持。允许应用开发者使用系统预定义的通知模板，只需提供模板名称和相应的数据，系统会自动渲染出符合规范的通知样式。
> > 使用场景：当前仅支持上传下载场景。

**起始版本：** 8

**系统能力：** SystemCapability.Notification.Notification

## data

```TypeScript
data: Record<string, Object>
```

模板数据。

- title: 表示下载标题。必填字段，值为字符串类型。
- fileName: 表示下载文件名。必填字段，值为字符串类型。
- progressValue: 表示下载进度，值为数值类型。

**类型：** Record<string, Object>

**起始版本：** 8

**系统能力：** SystemCapability.Notification.Notification

## name

```TypeScript
name: string
```

模板名称。当前仅支持表示下载进度的进度条通知模板，取值为'downloadTemplate'。

**类型：** string

**起始版本：** 8

**系统能力：** SystemCapability.Notification.Notification

