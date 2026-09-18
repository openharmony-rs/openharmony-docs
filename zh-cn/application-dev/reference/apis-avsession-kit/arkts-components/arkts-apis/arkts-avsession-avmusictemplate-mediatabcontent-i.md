# MediaTabContent

媒体标签页内容的定义。继承自[OperResult](arkts-avsession-avmusictemplate-operresult-i.md)。

@extends OperResult @interface MediaTabContent

**继承/实现关系：** MediaTabContent extends [OperResult](arkts-avsession-avmusictemplate-operresult-i.md)

**起始版本：** 23

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## 导入模块

```TypeScript
import { avMusicTemplate } from '@kit.AVSessionKit';
```

## compilations

```TypeScript
compilations: Compilation[]
```

页面内容的合集数组。

**类型：** [Compilation](arkts-avsession-avmusictemplate-compilation-i.md)[]

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## tabId

```TypeScript
tabId: string
```

标签页的ID。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate
