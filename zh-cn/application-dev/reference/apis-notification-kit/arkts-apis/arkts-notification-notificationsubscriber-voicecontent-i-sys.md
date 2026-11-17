# VoiceContent（系统接口）

```TypeScript
export interface VoiceContent
```

通知语音播报内容。

**起始版本：** 26.0.0

<!--Device-unnamed-export interface VoiceContent--><!--Device-unnamed-export interface VoiceContent-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## textContent

```TypeScript
readonly textContent?: string
```

文本语音播报内容。中国境内（香港特别行政区、澳门特别行政区、中国台湾除外）播报内容为智能化播报内容。从API版本26.1.0开始，支持中国境内之外地区通知语音播报，播报内容固定为应用名+通知正文。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-VoiceContent-readonly textContent?: string--><!--Device-VoiceContent-readonly textContent?: string-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。
