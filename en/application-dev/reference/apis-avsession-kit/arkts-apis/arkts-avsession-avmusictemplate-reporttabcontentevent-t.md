# ReportTabContentEvent

```TypeScript
type ReportTabContentEvent = (tabId: string, tabContent: MediaTabContent) => void
```

The report tab content event.

@typedef { function } ReportTabContentEvent

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-avMusicTemplate-type ReportTabContentEvent = (tabId: string, tabContent: MediaTabContent) => void--><!--Device-avMusicTemplate-type ReportTabContentEvent = (tabId: string, tabContent: MediaTabContent) => void-End-->

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| tabId | string | Yes | tab id |
| tabContent | [MediaTabContent](arkts-avsession-avmusictemplate-mediatabcontent-i.md) | Yes | tab content |
