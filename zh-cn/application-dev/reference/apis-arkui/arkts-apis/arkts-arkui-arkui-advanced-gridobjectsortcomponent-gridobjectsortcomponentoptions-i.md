# GridObjectSortComponentOptions

网格对象排序组件的组件配置信息。

**起始版本：** 11

<!--Device-unnamed-export interface GridObjectSortComponentOptions--><!--Device-unnamed-export interface GridObjectSortComponentOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { GridObjectSortComponentType, GridObjectSortComponentOptions, GridObjectSortComponent, GridObjectSortComponentItem } from '@kit.ArkUI';
```

## addAreaTitle

```TypeScript
addAreaTitle?: ResourceStr
```

添加区域标题，第二个子标题。

默认值：点击添加。

**类型：** ResourceStr

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GridObjectSortComponentOptions-addAreaTitle?: ResourceStr--><!--Device-GridObjectSortComponentOptions-addAreaTitle?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## editTitle

```TypeScript
editTitle?: ResourceStr
```

编辑状态下头部标题显示。

默认值：编辑。

**类型：** ResourceStr

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GridObjectSortComponentOptions-editTitle?: ResourceStr--><!--Device-GridObjectSortComponentOptions-editTitle?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## imageSize

```TypeScript
imageSize?: number | Resource
```

图片的尺寸，单位vp。

取值范围：大于等于0。

默认值：56vp

**类型：** number | Resource

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GridObjectSortComponentOptions-imageSize?: number | Resource--><!--Device-GridObjectSortComponentOptions-imageSize?: number | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## normalTitle

```TypeScript
normalTitle?: ResourceStr
```

未编辑状态下显示的标题。

默认值：频道。

**类型：** ResourceStr

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GridObjectSortComponentOptions-normalTitle?: ResourceStr--><!--Device-GridObjectSortComponentOptions-normalTitle?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## showAreaTitle

```TypeScript
showAreaTitle?: ResourceStr
```

展示区域标题，第一个子标题。

默认值：长按拖动排序。

**类型：** ResourceStr

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GridObjectSortComponentOptions-showAreaTitle?: ResourceStr--><!--Device-GridObjectSortComponentOptions-showAreaTitle?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type?: GridObjectSortComponentType
```

组件展示形态：文字|图片+文字。

默认值：GridObjectSortComponentType.TEXT

**类型：** GridObjectSortComponentType

**默认值：** GridObjectSortComponentType.TEXT

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GridObjectSortComponentOptions-type?: GridObjectSortComponentType--><!--Device-GridObjectSortComponentOptions-type?: GridObjectSortComponentType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

