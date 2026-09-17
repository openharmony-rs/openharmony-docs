# QueryMediaEntityParam

查询媒体实例参数的定义。

@interface QueryMediaEntityParam

**起始版本：** 23

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## 导入模块

```TypeScript
import { avMusicTemplate } from '@kit.AVSessionKit';
```

## entityId

```TypeScript
entityId: string
```

媒体实例的ID。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## episodeRange

```TypeScript
episodeRange?: EpisodeRange
```

要查询的剧集区间。

**类型：** [EpisodeRange](arkts-avsession-avmusictemplate-episoderange-i.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## pageIndex

```TypeScript
pageIndex: number
```

分页查询页码。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## sort

```TypeScript
sort?: Sort
```

查询到的列表数据排序。

**类型：** [Sort](arkts-avsession-avmusictemplate-sort-e.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## subEntityType

```TypeScript
subEntityType?: EntityType
```

子节点的媒体资源类型。

**类型：** [EntityType](arkts-avsession-avmusictemplate-entitytype-e.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## type

```TypeScript
type: EntityType
```

媒体资源类型。

**类型：** [EntityType](arkts-avsession-avmusictemplate-entitytype-e.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate
