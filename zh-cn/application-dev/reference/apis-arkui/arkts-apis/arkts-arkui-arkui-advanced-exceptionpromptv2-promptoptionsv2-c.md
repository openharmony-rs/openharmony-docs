# PromptOptionsV2

PromptOptionsV2用于定义异常提示组件的配置信息。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**装饰器类型：** @ObservedV2

<!--Device-unnamed-export declare class PromptOptionsV2--><!--Device-unnamed-export declare class PromptOptionsV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(config?: PromptOptionsV2Config)
```

PromptOptionsV2的构造函数。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-PromptOptionsV2-constructor(config?: PromptOptionsV2Config)--><!--Device-PromptOptionsV2-constructor(config?: PromptOptionsV2Config)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | PromptOptionsV2的配置信息。如果不传入config，则使用默认值：marginType为MarginTypeV2.DEFAULT\_\_\_ESCAPED\_UNDERSCORE\_\_\_MARGIN，marginTop为0。 |

## actionText

```TypeScript
actionText?: ResourceStr
```

指定当前异常提示的右侧图标按钮的文字内容。 默认不设置或设置为undefined，文字内容不显示。

**类型：** ResourceStr

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-PromptOptionsV2-actionText?: ResourceStr--><!--Device-PromptOptionsV2-actionText?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
icon?: ResourceStr
```

指定当前异常提示的异常图标样式。 默认不设置或设置为undefined，不显示异常图标。

**类型：** ResourceStr

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-PromptOptionsV2-icon?: ResourceStr--><!--Device-PromptOptionsV2-icon?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isShown

```TypeScript
isShown?: boolean
```

指定当前异常提示的显隐状态。 true：显示状态。 false：隐藏状态。 默认值：false

**类型：** boolean

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-PromptOptionsV2-isShown?: boolean--><!--Device-PromptOptionsV2-isShown?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## marginTop

```TypeScript
marginTop: Dimension
```

指定当前异常提示的距离顶部的位置。

**类型：** Dimension

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-PromptOptionsV2-marginTop: Dimension--><!--Device-PromptOptionsV2-marginTop: Dimension-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## marginType

```TypeScript
marginType: MarginTypeV2
```

指定当前异常提示的边距样式。

**类型：** MarginTypeV2

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-PromptOptionsV2-marginType: MarginTypeV2--><!--Device-PromptOptionsV2-marginType: MarginTypeV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## symbolStyle

```TypeScript
symbolStyle?: SymbolGlyphModifier
```

指定当前异常提示的异常Symbol图标样式，优先级大于icon。 默认不设置或设置为undefined，Symbol图标不显示。

**类型：** SymbolGlyphModifier

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-PromptOptionsV2-symbolStyle?: SymbolGlyphModifier--><!--Device-PromptOptionsV2-symbolStyle?: SymbolGlyphModifier-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## tip

```TypeScript
tip?: ResourceStr
```

指定当前异常提示的文字提示内容。 支持自定义资源，或如下四种状态文字系统资源。 1. 无网络状态：显示网络未连接，引用\$r('sys.string.ohos\_network\_not\_connected')。 2. 网络差状态：显示网络连接不稳定，请点击重试，引用\$r('sys.string.ohos\_network\_connected\_unstable')。 3. 连不上服务器状态：显示无法连接到服务器，请点击重试，引用\$r('sys.string.ohos\_unstable\_connect\_server')。 4. 有网但是获取不到位置状态：显示无法获取位置，请点击重试，引用\$r('sys.string.ohos\_custom\_network\_tips\_left')。 默认不设置或设置为undefined，文字提示内容不显示。

**类型：** ResourceStr

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-PromptOptionsV2-tip?: ResourceStr--><!--Device-PromptOptionsV2-tip?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

