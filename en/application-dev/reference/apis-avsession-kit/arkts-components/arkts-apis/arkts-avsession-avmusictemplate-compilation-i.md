# Compilation

```TypeScript
interface Compilation extends OperResult
```

The definition of compilation.

@extends OperResult @interface Compilation

**Inheritance/Implementation:** Compilation extends [OperResult](arkts-avsession-avmusictemplate-operresult-i.md)

**Since:** 23

<!--Device-avMusicTemplate-interface Compilation extends OperResult--><!--Device-avMusicTemplate-interface Compilation extends OperResult-End-->

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## Modules to Import

```TypeScript
import { avMusicTemplate } from '@kit.AVSessionKit';
```

## hasMoreData

```TypeScript
hasMoreData: boolean
```

Having more compilation data

**Type:** boolean

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-Compilation-hasMoreData: boolean--><!--Device-Compilation-hasMoreData: boolean-End-->

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## id

```TypeScript
id: string
```

Unique ID of the compilation

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-Compilation-id: string--><!--Device-Compilation-id: string-End-->

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## memberMediaType

```TypeScript
memberMediaType: EntityType
```

Media type of the compilation

**Type:** [EntityType](arkts-avsession-avmusictemplate-entitytype-e.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-Compilation-memberMediaType: EntityType--><!--Device-Compilation-memberMediaType: EntityType-End-->

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## title

```TypeScript
title: string
```

Title of the compilation

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-Compilation-title: string--><!--Device-Compilation-title: string-End-->

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## topElements

```TypeScript
topElements: MediaEntity[]
```

Content of the compilation

**Type:** [MediaEntity](arkts-avsession-avmusictemplate-mediaentity-i.md)[]

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-Compilation-topElements: MediaEntity[]--><!--Device-Compilation-topElements: MediaEntity[]-End-->

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## totalSize

```TypeScript
totalSize: number
```

Total size of the compilation

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-Compilation-totalSize: int--><!--Device-Compilation-totalSize: int-End-->

**System capability:** SystemCapability.Multimedia.AVSession.AVMusicTemplate
