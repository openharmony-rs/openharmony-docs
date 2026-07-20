# NotificationBasicContent

描述普通文本通知，用于展示标题和正文内容，是其他通知类型的基础内容结构。其他通知类型（如长文本、多行文本、图片、实况窗）均继承本接口，在此基础上扩展各自特有字段。

**起始版本：** 7

<!--Device-unnamed-export interface NotificationBasicContent--><!--Device-unnamed-export interface NotificationBasicContent-End-->

**系统能力：** SystemCapability.Notification.Notification

## structuredText

```TypeScript
structuredText?: Map<string, string>
```

通知结构化字段。当前仅支持服务提醒类短信在通知中心结构化展示。默认为空。（key/value大小不超过512字节，超出部分会被截断，最多支持3对结构化数据，超出部分会被忽略。）

**类型：** Map&lt;string, string&gt;

**起始版本：** 21

<!--Device-NotificationBasicContent-structuredText?: Map<string, string>--><!--Device-NotificationBasicContent-structuredText?: Map<string, string>-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

