# RichEditorSymbolSpanStyleResult

后端返回的SymbolSpan样式信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare interface RichEditorSymbolSpanStyleResult--><!--Device-unnamed-export declare interface RichEditorSymbolSpanStyleResult-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## effectStrategy

```TypeScript
effectStrategy: SymbolEffectStrategy
```

SymbolSpan组件动效策略。 默认值：SymbolEffectStrategy.NONE。

**类型：** [SymbolEffectStrategy](../arkts-components/arkts-arkui-symboleffectstrategy-e.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorSymbolSpanStyleResult-effectStrategy: SymbolEffectStrategy--><!--Device-RichEditorSymbolSpanStyleResult-effectStrategy: SymbolEffectStrategy-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontColor

```TypeScript
fontColor: Array<ResourceColor>
```

SymbolSpan组件颜色。 默认值：不同渲染策略下默认值不同。

**类型：** Array&lt;[ResourceColor](arkts-arkui-resourcecolor-t.md)&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorSymbolSpanStyleResult-fontColor: Array<ResourceColor>--><!--Device-RichEditorSymbolSpanStyleResult-fontColor: Array<ResourceColor>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontSize

```TypeScript
fontSize: double | string | Resource
```

SymbolSpan组件大小，默认单位为fp。 默认值：跟随主题。

**类型：** double \| string \| [Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-resource-i.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorSymbolSpanStyleResult-fontSize: double | string | Resource--><!--Device-RichEditorSymbolSpanStyleResult-fontSize: double | string | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontWeight

```TypeScript
fontWeight: int | FontWeight | string
```

SymbolSpan组件粗细。 number类型取值[100,900]，取值间隔为100，默认为400，取值越大，字体越粗。 string类型仅支持number类型取值的字符串形式，例如“400”，以及“bold”、“bolder”、“lighter”、“regular” 、“medium”分别对应FontWeight中相应的枚举值。 默认值：FontWeight.Normal。

**类型：** int \| [FontWeight](arkts-arkui-fontweight-e.md) \| string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorSymbolSpanStyleResult-fontWeight: int | FontWeight | string--><!--Device-RichEditorSymbolSpanStyleResult-fontWeight: int | FontWeight | string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## renderingStrategy

```TypeScript
renderingStrategy: SymbolRenderingStrategy
```

SymbolSpan组件渲染策略。 默认值：SymbolRenderingStrategy.SINGLE。

**类型：** [SymbolRenderingStrategy](../arkts-components/arkts-arkui-symbolrenderingstrategy-e.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorSymbolSpanStyleResult-renderingStrategy: SymbolRenderingStrategy--><!--Device-RichEditorSymbolSpanStyleResult-renderingStrategy: SymbolRenderingStrategy-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

