# ReportDialogCommandEvent

```TypeScript
type ReportDialogCommandEvent = (type: DialogControlType, buttonInfo: DialogInfo) => void
```

The report dialog command event.

@typedef { function } ReportDialogCommandEvent

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [DialogControlType](arkts-avsession-avmusictemplate-dialogcontroltype-t.md) | Yes | [type](arkts-avsession-avmusictemplate-querymediaentityparam-i.md) |
| buttonInfo | [DialogInfo](arkts-avsession-avmusictemplate-dialoginfo-i.md) | Yes | button info |
