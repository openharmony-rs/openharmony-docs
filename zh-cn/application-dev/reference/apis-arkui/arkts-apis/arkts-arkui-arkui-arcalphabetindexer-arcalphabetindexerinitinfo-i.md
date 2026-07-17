# ArcAlphabetIndexerInitInfo

定义弧形字母索引条的初始化参数。

**起始版本：** 18

<!--Device-unnamed-declare interface ArcAlphabetIndexerInitInfo--><!--Device-unnamed-declare interface ArcAlphabetIndexerInitInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## 导入模块

```TypeScript
import { ArcAlphabetIndexerAttribute, ArcAlphabetIndexer } from '@kit.ArkUI';
```

## arrayValue

```TypeScript
arrayValue: string[]
```

字母索引字符串数组，不可设置为空。

**类型：** string[]

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcAlphabetIndexerInitInfo-arrayValue: string[]--><!--Device-ArcAlphabetIndexerInitInfo-arrayValue: string[]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## selected

```TypeScript
selected: number
```

初始选中项索引值，若超出索引值范围，则取默认值0。

该参数支持[!!](../../../../ui/state-management/arkts-new-binding.md)双向绑定变量。

**类型：** number

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcAlphabetIndexerInitInfo-selected: number--><!--Device-ArcAlphabetIndexerInitInfo-selected: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

