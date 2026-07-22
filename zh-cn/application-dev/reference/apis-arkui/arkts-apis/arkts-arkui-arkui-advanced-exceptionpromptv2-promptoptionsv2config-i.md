# PromptOptionsV2Config

PromptOptionsV2Config定义用于构造PromptOptionsV2对象的配置信息接口。

**起始版本：** 26.0.0

<!--Device-unnamed-export interface PromptOptionsV2Config--><!--Device-unnamed-export interface PromptOptionsV2Config-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { MarginTypeV2, PromptOptionsV2, ExceptionPromptV2, PromptOptionsV2Config } from '@kit.ArkUI';
```

## actionText

```TypeScript
actionText?: ResourceStr
```

指定当前异常提示的右侧图标按钮的文字内容。

默认不设置或设置为undefined，文字内容不显示。

**类型：** ResourceStr

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-PromptOptionsV2Config-actionText?: ResourceStr--><!--Device-PromptOptionsV2Config-actionText?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
icon?: ResourceStr
```

指定当前异常提示的异常图标样式。

默认不设置或设置为undefined，不显示异常图标。

**类型：** ResourceStr

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-PromptOptionsV2Config-icon?: ResourceStr--><!--Device-PromptOptionsV2Config-icon?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isShown

```TypeScript
isShown?: boolean
```

指定当前异常提示的显隐状态。

true：显示状态。

false：隐藏状态。

默认值：false

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-PromptOptionsV2Config-isShown?: boolean--><!--Device-PromptOptionsV2Config-isShown?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## marginTop

```TypeScript
marginTop: Dimension
```

指定当前异常提示的距离顶部的位置。

**类型：** Dimension

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-PromptOptionsV2Config-marginTop: Dimension--><!--Device-PromptOptionsV2Config-marginTop: Dimension-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## marginType

```TypeScript
marginType: MarginTypeV2
```

指定当前异常提示的边距样式。

**类型：** MarginTypeV2

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-PromptOptionsV2Config-marginType: MarginTypeV2--><!--Device-PromptOptionsV2Config-marginType: MarginTypeV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## symbolStyle

```TypeScript
symbolStyle?: SymbolGlyphModifier
```

指定当前异常提示的异常Symbol图标样式，优先级大于icon。

默认不设置或设置为undefined，Symbol图标不显示。

**类型：** SymbolGlyphModifier

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-PromptOptionsV2Config-symbolStyle?: SymbolGlyphModifier--><!--Device-PromptOptionsV2Config-symbolStyle?: SymbolGlyphModifier-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## tip

```TypeScript
tip?: ResourceStr
```

指定当前异常提示的文字提示内容。

支持自定义资源，或如下四种状态文字系统资源。

1. 无网络状态：显示网络未连接，引用$r('sys.string.ohos_network_not_connected')。2. 网络差状态：显示网络连接不稳定，请点击重试，引用$r('sys.string.ohos_network_connected_unstable')。3. 连不上服务器状态：显示无法连接到服务器，请点击重试，引用$r('sys.string.ohos_unstable_connect_server')。4. 有网但是获取不到位置状态：显示无法获取位置，请点击重试，引用$r('sys.string.ohos_custom_network_tips_left')。

默认不设置或设置为undefined，文字提示内容不显示。

**类型：** ResourceStr

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-PromptOptionsV2Config-tip?: ResourceStr--><!--Device-PromptOptionsV2Config-tip?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

