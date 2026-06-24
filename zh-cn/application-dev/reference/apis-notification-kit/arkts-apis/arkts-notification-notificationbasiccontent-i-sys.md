# NotificationBasicContent

描述普通文本通知。

**起始版本：** 7

**系统能力：** SystemCapability.Notification.Notification

## structuredText

```TypeScript
structuredText?: Map<string, string>
```

通知结构化字段。当前仅支持服务提醒类短信在通知中心结构化展示。默认为空。（key/value大小不超过512字节，超出部分会被截断，最多支持3对结构化数据，超出部分会被忽略。）

**类型：** Map<string, string>

**起始版本：** 21

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

