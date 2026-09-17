# PageMediaEntity

标签页媒体的定义。继承自[OperResult](arkts-avsession-avmusictemplate-operresult-i.md)。

@extends OperResult @interface Compilation

**继承/实现关系：** PageMediaEntity extends [OperResult](arkts-avsession-avmusictemplate-operresult-i.md)

**起始版本：** 23

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## 导入模块

```TypeScript
import { avMusicTemplate } from '@kit.AVSessionKit';
```

## elements

```TypeScript
elements: MediaEntity[]
```

查询数据内容（根据类型传递相应的结构数据）。

**类型：** [MediaEntity](arkts-avsession-avmusictemplate-mediaentity-i.md)[]

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## episodeRange

```TypeScript
episodeRange?: EpisodeRange
```

剧集区间。

**类型：** [EpisodeRange](arkts-avsession-avmusictemplate-episoderange-i.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## hasMoreData

```TypeScript
hasMoreData: boolean
```

是否有下一页。true表示有，false表示没有。无默认值。

**类型：** boolean

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## memberMediaType

```TypeScript
memberMediaType: EntityType
```

媒体资源类型。

**类型：** [EntityType](arkts-avsession-avmusictemplate-entitytype-e.md)

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

## pageSize

```TypeScript
pageSize: number
```

页面的大小。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## sort

```TypeScript
sort?: Sort
```

数据排序。

**类型：** [Sort](arkts-avsession-avmusictemplate-sort-e.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## totalSize

```TypeScript
totalSize: number
```

数据总大小。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate
