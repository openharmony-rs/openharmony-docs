# RichEditorSymbolSpanStyle

组件SymbolSpan样式信息。

**起始版本：** 11

<!--Device-unnamed-declare interface RichEditorSymbolSpanStyle--><!--Device-unnamed-declare interface RichEditorSymbolSpanStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## effectStrategy

```TypeScript
effectStrategy?: SymbolEffectStrategy
```

设置SymbolSpan组件动效策略。

默认值：SymbolEffectStrategy.NONE。

**类型：** SymbolEffectStrategy

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorSymbolSpanStyle-effectStrategy?: SymbolEffectStrategy--><!--Device-RichEditorSymbolSpanStyle-effectStrategy?: SymbolEffectStrategy-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontColor

```TypeScript
fontColor?: Array<ResourceColor>
```

设置SymbolSpan组件颜色。

默认值：不同渲染策略下默认值不同。

**类型：** Array&lt;ResourceColor&gt;

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorSymbolSpanStyle-fontColor?: Array<ResourceColor>--><!--Device-RichEditorSymbolSpanStyle-fontColor?: Array<ResourceColor>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontSize

```TypeScript
fontSize?: number | string | Resource
```

设置SymbolSpan组件大小，默认单位为fp。

number类型取值范围：(0, +∞)，设置为0时显示默认字体大小。

默认值：跟随主题。

**类型：** number \| string \| Resource

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorSymbolSpanStyle-fontSize?: number | string | Resource--><!--Device-RichEditorSymbolSpanStyle-fontSize?: number | string | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontWeight

```TypeScript
fontWeight?: number | FontWeight | string
```

设置SymbolSpan组件粗细。

number类型取值[100,900]，取值间隔为100，默认为400，取值越大，字体越粗。

string类型仅支持number类型取值的字符串形式，例如“400”，以及“bold”、“bolder”、“lighter”、“regular” 、“medium”分别对应FontWeight中相应的枚举值。

默认值：FontWeight.Normal。

**类型：** number \| FontWeight \| string

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorSymbolSpanStyle-fontWeight?: number | FontWeight | string--><!--Device-RichEditorSymbolSpanStyle-fontWeight?: number | FontWeight | string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## renderingStrategy

```TypeScript
renderingStrategy?: SymbolRenderingStrategy
```

设置SymbolSpan组件渲染策略。

默认值：SymbolRenderingStrategy.SINGLE。

**类型：** SymbolRenderingStrategy

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorSymbolSpanStyle-renderingStrategy?: SymbolRenderingStrategy--><!--Device-RichEditorSymbolSpanStyle-renderingStrategy?: SymbolRenderingStrategy-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

