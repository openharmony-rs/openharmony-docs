# ReportTabContentEvent

```TypeScript
type ReportTabContentEvent = (tabId: string, tabContent: MediaTabContent) => void
```

标签页内容上报事件。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-avMusicTemplate-type ReportTabContentEvent = (tabId: string, tabContent: MediaTabContent) => void--><!--Device-avMusicTemplate-type ReportTabContentEvent = (tabId: string, tabContent: MediaTabContent) => void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tabId | string | 是 | 标签页的ID。 |
| tabContent | MediaTabContent | 是 | 标签页的内容。 |

