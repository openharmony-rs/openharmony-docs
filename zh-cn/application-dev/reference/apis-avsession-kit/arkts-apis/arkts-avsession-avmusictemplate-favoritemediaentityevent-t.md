# FavoriteMediaEntityEvent

```TypeScript
type FavoriteMediaEntityEvent = (actionType: MediaFavoriteType, mediaEntity: MediaEntity) => Promise<OperResult>
```

媒体实体收藏事件。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-avMusicTemplate-type FavoriteMediaEntityEvent = (actionType: MediaFavoriteType, mediaEntity: MediaEntity) => Promise<OperResult>--><!--Device-avMusicTemplate-type FavoriteMediaEntityEvent = (actionType: MediaFavoriteType, mediaEntity: MediaEntity) => Promise<OperResult>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| actionType | [MediaFavoriteType](arkts-avsession-avmusictemplate-mediafavoritetype-t.md) | 是 | 操作类型。 |
| mediaEntity | [MediaEntity](arkts-avsession-avmusictemplate-mediaentity-i.md) | 是 | 媒体实体。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[OperResult](arkts-avsession-avmusictemplate-operresult-i.md)&gt; | Promise对象，返回收藏媒体实体的操作结果对象。 |

