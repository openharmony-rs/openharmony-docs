# DownloadMediaEntityEvent

```TypeScript
type DownloadMediaEntityEvent = (controlType: DownloadControlType, mediaEntity: MediaEntity) => Promise<OperResult>
```

The download media entity event.

@typedef { function } DownloadMediaEntityEvent

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| controlType | [DownloadControlType](arkts-avsession-avmusictemplate-downloadcontroltype-t.md) | Yes | control type |
| mediaEntity | [MediaEntity](arkts-avsession-avmusictemplate-mediaentity-i.md) | Yes | media entity |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[OperResult](arkts-avsession-avmusictemplate-operresult-i.md)&gt; | (OperResult) returned through promise |
