# Compilation

合集的定义。继承自[OperResult](arkts-avsession-avmusictemplate-operresult-i.md)。

@extends OperResult @interface Compilation

**继承/实现关系：** Compilation extends [OperResult](arkts-avsession-avmusictemplate-operresult-i.md)

**起始版本：** 23

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## 导入模块

```TypeScript
import { avMusicTemplate } from '@kit.AVSessionKit';
```

## hasMoreData

```TypeScript
hasMoreData: boolean
```

是否有更多的合集数据。true表示有，false表示没有。无默认值。

**类型：** boolean

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## id

```TypeScript
id: string
```

合集的唯一标识。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## memberMediaType

```TypeScript
memberMediaType: EntityType
```

合集的媒体资源类型。

**类型：** [EntityType](arkts-avsession-avmusictemplate-entitytype-e.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## title

```TypeScript
title: string
```

合集的标题。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## topElements

```TypeScript
topElements: MediaEntity[]
```

合集的内容。

**类型：** [MediaEntity](arkts-avsession-avmusictemplate-mediaentity-i.md)[]

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## totalSize

```TypeScript
totalSize: number
```

合集的总个数。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate
