# PageMediaEntity

```TypeScript
interface PageMediaEntity extends OperResult
```

The definition of pagination object.

@extends OperResult @interface PageMediaEntity

**Inheritance/Implementation:** PageMediaEntity extends [OperResult](arkts-avsession-avmusictemplate-operresult-i.md)

**Since:** 23

<!--Device-avMusicTemplate-interface PageMediaEntity extends OperResult--><!--Device-avMusicTemplate-interface PageMediaEntity extends OperResult-End-->

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## Modules to Import

```TypeScript
import { avMusicTemplate } from '@kit.AVSessionKit';
```

## elements

```TypeScript
elements: MediaEntity[]
```

Query data content (pass corresponding structure data according to the type).

**Type:** [MediaEntity](arkts-avsession-avmusictemplate-mediaentity-i.md)[]

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-PageMediaEntity-elements: MediaEntity[]--><!--Device-PageMediaEntity-elements: MediaEntity[]-End-->

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## episodeRange

```TypeScript
episodeRange?: EpisodeRange
```

Episode Range

**Type:** [EpisodeRange](arkts-avsession-avmusictemplate-episoderange-i.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-PageMediaEntity-episodeRange?: EpisodeRange--><!--Device-PageMediaEntity-episodeRange?: EpisodeRange-End-->

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## hasMoreData

```TypeScript
hasMoreData: boolean
```

Have next page data.

**Type:** boolean

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-PageMediaEntity-hasMoreData: boolean--><!--Device-PageMediaEntity-hasMoreData: boolean-End-->

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## memberMediaType

```TypeScript
memberMediaType: EntityType
```

Media type.

**Type:** [EntityType](arkts-avsession-avmusictemplate-entitytype-e.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-PageMediaEntity-memberMediaType: EntityType--><!--Device-PageMediaEntity-memberMediaType: EntityType-End-->

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## pageIndex

```TypeScript
pageIndex: number
```

Pagination query page number.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-PageMediaEntity-pageIndex: int--><!--Device-PageMediaEntity-pageIndex: int-End-->

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## pageSize

```TypeScript
pageSize: number
```

Size of per page.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-PageMediaEntity-pageSize: int--><!--Device-PageMediaEntity-pageSize: int-End-->

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## sort

```TypeScript
sort?: Sort
```

Data Sorting

**Type:** [Sort](arkts-avsession-avmusictemplate-sort-e.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-PageMediaEntity-sort?: Sort--><!--Device-PageMediaEntity-sort?: Sort-End-->

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## totalSize

```TypeScript
totalSize: number
```

Total size of data.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-PageMediaEntity-totalSize: int--><!--Device-PageMediaEntity-totalSize: int-End-->

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate
