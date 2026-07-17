# PageMediaEntity

标签页媒体的定义。继承自[OperResult](arkts-avsession-avmusictemplate-operresult-i.md)。

**继承/实现关系：** PageMediaEntity extends [OperResult](arkts-avsession-avmusictemplate-operresult-i.md)

**起始版本：** 23

<!--Device-avMusicTemplate-interface PageMediaEntity extends OperResult--><!--Device-avMusicTemplate-interface PageMediaEntity extends OperResult-End-->

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

**类型：** MediaEntity[]

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PageMediaEntity-elements: MediaEntity[]--><!--Device-PageMediaEntity-elements: MediaEntity[]-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## episodeRange

```TypeScript
episodeRange?: EpisodeRange
```

剧集区间。

**类型：** EpisodeRange

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PageMediaEntity-episodeRange?: EpisodeRange--><!--Device-PageMediaEntity-episodeRange?: EpisodeRange-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## hasMoreData

```TypeScript
hasMoreData: boolean
```

是否有下一页。true表示有，false表示没有。无默认值。

**类型：** boolean

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PageMediaEntity-hasMoreData: boolean--><!--Device-PageMediaEntity-hasMoreData: boolean-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## memberMediaType

```TypeScript
memberMediaType: EntityType
```

媒体资源类型。

**类型：** EntityType

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PageMediaEntity-memberMediaType: EntityType--><!--Device-PageMediaEntity-memberMediaType: EntityType-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## pageIndex

```TypeScript
pageIndex: number
```

分页查询页码。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PageMediaEntity-pageIndex: int--><!--Device-PageMediaEntity-pageIndex: int-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## pageSize

```TypeScript
pageSize: number
```

页面的大小。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PageMediaEntity-pageSize: int--><!--Device-PageMediaEntity-pageSize: int-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## sort

```TypeScript
sort?: Sort
```

数据排序。

**类型：** Sort

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PageMediaEntity-sort?: Sort--><!--Device-PageMediaEntity-sort?: Sort-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## totalSize

```TypeScript
totalSize: number
```

数据总大小。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PageMediaEntity-totalSize: int--><!--Device-PageMediaEntity-totalSize: int-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

