# ReportDialogCommandEvent

```TypeScript
type ReportDialogCommandEvent = (type: DialogControlType, buttonInfo: DialogInfo) => void
```

对话框命令上报事件。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-avMusicTemplate-type ReportDialogCommandEvent = (type: DialogControlType, buttonInfo: DialogInfo) => void--><!--Device-avMusicTemplate-type ReportDialogCommandEvent = (type: DialogControlType, buttonInfo: DialogInfo) => void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [DialogControlType](arkts-avsession-avmusictemplate-dialogcontroltype-t.md) | 是 |  |
| buttonInfo | [DialogInfo](arkts-avsession-avmusictemplate-dialoginfo-i.md) | 是 | 对话框信息。  |

