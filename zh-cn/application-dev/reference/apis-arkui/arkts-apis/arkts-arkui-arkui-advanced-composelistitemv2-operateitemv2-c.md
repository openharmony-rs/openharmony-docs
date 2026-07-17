# OperateItemV2

列表项右侧显示的元素类型。

**起始版本：** 26.0.0

<!--Device-unnamed-export declare class OperateItemV2--><!--Device-unnamed-export declare class OperateItemV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { OperateCheckV2Options, ComposeListItemV2, IconTypeV2, OperateIconV2, OperateCheckV2, OperateItemV2, OperateItemV2Options, OperateIconV2Options, OperateButtonV2, OperateButtonV2Options, ContentItemV2, ContentItemV2Options } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(options?: OperateItemV2Options)
```

OperateItemV2的构造函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-OperateItemV2-constructor(options?: OperateItemV2Options)--><!--Device-OperateItemV2-constructor(options?: OperateItemV2Options)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [OperateItemV2Options](arkts-arkui-arkui-advanced-composelistitemv2-operateitemv2options-i.md) | 否 | 列表项右侧属性配置。 |

## arrow

```TypeScript
public arrow?: OperateIconV2
```

列表项右侧元素为箭头，大小为12*24vp。

默认不设置或设置为undefined，列表项右侧箭头不显示。

**类型：** OperateIconV2

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-OperateItemV2-public arrow?: OperateIconV2--><!--Device-OperateItemV2-public arrow?: OperateIconV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## button

```TypeScript
public button?: OperateButtonV2
```

列表项右侧元素为按钮。

默认不设置或设置为undefined，列表项右侧按钮不显示。

**类型：** OperateButtonV2

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-OperateItemV2-public button?: OperateButtonV2--><!--Device-OperateItemV2-public button?: OperateButtonV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## checkbox

```TypeScript
public checkbox?: OperateCheckV2
```

列表项右侧元素为多选框，大小为24*24vp。

默认不设置或设置为undefined，列表项右侧多选框不显示。

**类型：** OperateCheckV2

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-OperateItemV2-public checkbox?: OperateCheckV2--><!--Device-OperateItemV2-public checkbox?: OperateCheckV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
public icon?: OperateIconV2
```

左侧元素的图标资源。

默认不设置或设置为undefined，表示不显示icon图标资源。

**类型：** OperateIconV2

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-OperateItemV2-public icon?: OperateIconV2--><!--Device-OperateItemV2-public icon?: OperateIconV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## image

```TypeScript
public image?: ResourceStr
```

列表项右侧元素为图片，大小为48*48vp。

默认不设置或设置为undefined，列表项右侧图片不显示。

**类型：** ResourceStr

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-OperateItemV2-public image?: ResourceStr--><!--Device-OperateItemV2-public image?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## radio

```TypeScript
public radio?: OperateCheckV2
```

列表项右侧元素为单选框，大小为24*24vp。

默认不设置或设置为undefined，列表项右侧单选框不显示。

**类型：** OperateCheckV2

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-OperateItemV2-public radio?: OperateCheckV2--><!--Device-OperateItemV2-public radio?: OperateCheckV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## subIcon

```TypeScript
public subIcon?: OperateIconV2
```

列表项右侧元素的第二个图标，大小为24*24vp。

默认不设置或设置为undefined，列表项右侧第二个图标不显示。

**类型：** OperateIconV2

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-OperateItemV2-public subIcon?: OperateIconV2--><!--Device-OperateItemV2-public subIcon?: OperateIconV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## symbolStyle

```TypeScript
public symbolStyle?: SymbolGlyphModifier
```

列表项右侧元素为Symbol图标资源，大小为48*48vp。

默认不设置或设置为undefined，列表项右侧Symbol图标不显示。

**类型：** SymbolGlyphModifier

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-OperateItemV2-public symbolStyle?: SymbolGlyphModifier--><!--Device-OperateItemV2-public symbolStyle?: SymbolGlyphModifier-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## text

```TypeScript
public text?: ResourceStr
```

列表项右侧元素为文字。

默认不设置或设置为undefined，列表项右侧文字不显示。

**类型：** ResourceStr

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-OperateItemV2-public text?: ResourceStr--><!--Device-OperateItemV2-public text?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## toggle

```TypeScript
public toggle?: OperateCheckV2
```

列表项右侧元素为开关。

默认不设置或设置为undefined，列表项右侧开关不显示。

**类型：** OperateCheckV2

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-OperateItemV2-public toggle?: OperateCheckV2--><!--Device-OperateItemV2-public toggle?: OperateCheckV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

