# GridObjectSortComponentOptions

网格对象排序组件的组件配置信息。

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { GridObjectSortComponentType, GridObjectSortComponentItem, GridObjectSortComponentOptions, GridObjectSortComponent } from '@kit.ArkUI';
```

## addAreaTitle

```TypeScript
addAreaTitle?: ResourceStr
```

添加区域标题，第二个子标题。默认值：点击添加。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## editTitle

```TypeScript
editTitle?: ResourceStr
```

编辑状态下头部标题显示。默认值：编辑。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## imageSize

```TypeScript
imageSize?: number | Resource
```

图片的尺寸，单位vp。仅在type为GridObjectSortComponentType.IMAGE_TEXT时生效。设置为数值0时，普通图片按默认尺寸显示，Symbol图标的字号为0vp。取值范围：大于等于0。默认值：56vp

**类型：** number \| Resource

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## normalTitle

```TypeScript
normalTitle?: ResourceStr
```

未编辑状态下显示的标题。默认值：频道。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## showAreaTitle

```TypeScript
showAreaTitle?: ResourceStr
```

展示区域标题，第一个子标题。默认值：长按拖动排序。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type?: GridObjectSortComponentType
```

组件展示形态：文字|图片+文字。设置为GridObjectSortComponentType.IMAGE_TEXT时，需为数据项配置url或symbolStyle。默认值：GridObjectSortComponentType.TEXT

**类型：** [GridObjectSortComponentType](arkts-arkui-arkui-advanced-gridobjectsortcomponent-gridobjectsortcomponenttype-e.md)

**默认值：** GridObjectSortComponentType.TEXT

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
