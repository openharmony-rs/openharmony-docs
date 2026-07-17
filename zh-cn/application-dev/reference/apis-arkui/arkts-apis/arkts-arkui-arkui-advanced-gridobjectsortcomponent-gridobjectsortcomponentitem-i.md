# GridObjectSortComponentItem

网格对象排序组件的组件数据配置信息。

**起始版本：** 11

<!--Device-unnamed-export interface GridObjectSortComponentItem--><!--Device-unnamed-export interface GridObjectSortComponentItem-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { GridObjectSortComponentType, GridObjectSortComponentOptions, GridObjectSortComponent, GridObjectSortComponentItem } from '@kit.ArkUI';
```

## id

```TypeScript
id: number | string
```

数据id序号，不可重复。

默认值：空字符串。

**类型：** number | string

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GridObjectSortComponentItem-id: number | string--><!--Device-GridObjectSortComponentItem-id: number | string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## order

```TypeScript
order: number
```

顺序序号。

取值范围：大于等于0。

默认值：0

**类型：** number

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GridObjectSortComponentItem-order: number--><!--Device-GridObjectSortComponentItem-order: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selected

```TypeScript
selected: boolean
```

是否已经被添加，已添加：true，未添加：false。

**类型：** boolean

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GridObjectSortComponentItem-selected: boolean--><!--Device-GridObjectSortComponentItem-selected: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## symbolStyle

```TypeScript
symbolStyle?: SymbolGlyphModifier
```

GridObjectSortComponentType类型为IMAGE_TEXT时，需要传入Symbol图标资源。配置优先级高于url。

**类型：** SymbolGlyphModifier

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-GridObjectSortComponentItem-symbolStyle?: SymbolGlyphModifier--><!--Device-GridObjectSortComponentItem-symbolStyle?: SymbolGlyphModifier-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## text

```TypeScript
text: ResourceStr
```

显示文本信息。

**类型：** ResourceStr

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GridObjectSortComponentItem-text: ResourceStr--><!--Device-GridObjectSortComponentItem-text: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## url

```TypeScript
url?: ResourceStr
```

GridObjectSortComponentType类型为IMAGE_TEXT时，需要传入图片地址。

**类型：** ResourceStr

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GridObjectSortComponentItem-url?: ResourceStr--><!--Device-GridObjectSortComponentItem-url?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

