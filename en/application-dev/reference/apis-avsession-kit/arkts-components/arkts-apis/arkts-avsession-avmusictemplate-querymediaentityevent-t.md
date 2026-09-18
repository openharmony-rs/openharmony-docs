# QueryMediaEntityEvent

```TypeScript
type QueryMediaEntityEvent = (params: QueryMediaEntityParam) => Promise<PageMediaEntity>
```

The query media entity event.

@typedef { function } QueryMediaEntityEvent

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| params | [QueryMediaEntityParam](arkts-avsession-avmusictemplate-querymediaentityparam-i.md) | Yes | query params |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[PageMediaEntity](arkts-avsession-avmusictemplate-pagemediaentity-i.md)&gt; | (PageMediaEntity) returned through promise |
