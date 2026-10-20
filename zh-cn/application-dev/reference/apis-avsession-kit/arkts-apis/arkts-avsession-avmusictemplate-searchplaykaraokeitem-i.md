# SearchPlayKaraokeItem

```TypeScript
interface SearchPlayKaraokeItem
```

搜播的音频项目的定义。

**起始版本：** 26.0.1

<!--Device-avMusicTemplate-interface SearchPlayKaraokeItem--><!--Device-avMusicTemplate-interface SearchPlayKaraokeItem-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## 导入模块

```TypeScript
import { avMusicTemplate } from '@kit.AVSessionKit';
```

## entityId

```TypeScript
entityId: string
```

音频的唯一标识。

**类型：** string

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SearchPlayKaraokeItem-entityId: string--><!--Device-SearchPlayKaraokeItem-entityId: string-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

## entityName

```TypeScript
entityName?: string
```

音频的名称。此值为空时，应用仅根据entityId查找音频。

**类型：** string

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SearchPlayKaraokeItem-entityName?: string--><!--Device-SearchPlayKaraokeItem-entityName?: string-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate
