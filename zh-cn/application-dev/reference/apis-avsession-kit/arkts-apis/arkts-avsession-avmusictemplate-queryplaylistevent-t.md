# QueryPlaylistEvent

```TypeScript
type QueryPlaylistEvent = (pageIndex: int, sort: Sort) => Promise<PageMediaEntity>
```

播放列表查询事件。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-avMusicTemplate-type QueryPlaylistEvent = (pageIndex: int, sort: Sort) => Promise<PageMediaEntity>--><!--Device-avMusicTemplate-type QueryPlaylistEvent = (pageIndex: int, sort: Sort) => Promise<PageMediaEntity>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pageIndex | int | 是 | 页面的索引。 |
| sort | [Sort](arkts-avsession-avmusictemplate-sort-e.md) | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[PageMediaEntity](arkts-avsession-avmusictemplate-pagemediaentity-i.md)&gt; | Promise对象，返回查询的播放列表的分页对象。 |

