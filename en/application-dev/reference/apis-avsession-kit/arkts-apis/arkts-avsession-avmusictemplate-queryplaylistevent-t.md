# QueryPlaylistEvent

```TypeScript
type QueryPlaylistEvent = (pageIndex: number, sort: Sort) => Promise<PageMediaEntity>
```

The query play list event.

@typedef { function } QueryPlaylistEvent

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| pageIndex | number | Yes | page index |
| sort | [Sort](arkts-avsession-avmusictemplate-sort-e.md) | Yes | sort |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[PageMediaEntity](arkts-avsession-avmusictemplate-pagemediaentity-i.md)&gt; | (PageMediaEntity) returned through promise |
