# QueryMediaEntityByKeywordEvent

```TypeScript
type QueryMediaEntityByKeywordEvent = (keyword: string, searchType: EntityType,
    pageIndex: number) => Promise<PageMediaEntity>
```

The query media entity by keyword event.

@typedef { function } QueryMediaEntityByKeywordEvent

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| keyword | string | Yes | keyword |
| searchType | [EntityType](arkts-avsession-avmusictemplate-entitytype-e.md) | Yes | search type |
| pageIndex | number | Yes | page index |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[PageMediaEntity](arkts-avsession-avmusictemplate-pagemediaentity-i.md)&gt; | (PageMediaEntity) returned through promise |
