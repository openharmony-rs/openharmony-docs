# SymbolSpan属性/事件

不支持[通用属性](arkts-arkui-commonmethod-c.md)，支持以下属性。不支持[通用事件](arkts-arkui-commonmethod-c.md)。

**继承/实现关系：** SymbolSpanAttribute extends CommonMethod<SymbolSpanAttribute>

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## attributeModifier

```TypeScript
attributeModifier(modifier: AttributeModifier<SymbolSpanAttribute>)
```

设置组件的动态属性。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| modifier | [AttributeModifier](arkts-arkui-attributemodifier-i.md)&lt;[SymbolSpanAttribute](arkts-arkui-symbolspan-attribute.md)&gt; | 是 | 动态设置组件的属性。 |

## effectStrategy

```TypeScript
effectStrategy(value: SymbolEffectStrategy)
```

设置SymbolSpan动效策略。未通过该接口设置时，默认动效策略为SymbolEffectStrategy.NONE。NONE表示无动效，适用于静态展示场景；SCALE表示整体缩放动效，适用于需要吸引用户注意力的场景，如按钮点击反馈；HIERARCHICAL表示层级动效，适用于需要突出图标层次感的场景。不同动效策略效果可以参考 示例1（设置渲染和动效策略）。

> **说明：**
> 
> 从API version 12开始，该接口支持在attributeModifier中调用。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [SymbolEffectStrategy](arkts-arkui-symboleffectstrategy-e.md) | 是 | SymbolSpan动效策略。 |

## fontColor

```TypeScript
fontColor(value: Array<ResourceColor>)
```

设置SymbolSpan组件颜色。未通过该接口设置时，默认颜色随[renderingStrategy](#renderingstrategy)变化，单色渲染策略（SINGLE）下默 认为单色；多色渲染策略（MULTIPLE_COLOR）和分层渲染策略（MULTIPLE_OPACITY）下默认取图标资源预设的多色配置。具体说明请参考 [SymbolRenderingStrategy](arkts-arkui-symbolrenderingstrategy-e.md)。

> **说明：**
> 
> 从API version 12开始，该接口支持在attributeModifier中调用。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Array&lt;[ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)&gt; | 是 | SymbolSpan组件颜色。具体颜色渲染模式及其说明请参考 [SymbolRenderingStrategy](arkts-arkui-symbolrenderingstrategy-e.md)。 |

## fontSize

```TypeScript
fontSize(value: number | string | Resource)
```

设置SymbolSpan组件大小。设置string类型时，支持number类型取值的字符串形式，可以附带单位，例如"10"、"10fp"。未通过该接口设置时，默认组件大小为16fp。

> **说明：**
> 
> 从API version 12开始，该接口支持在attributeModifier中调用。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| string \| Resource | 是 | SymbolSpan组件大小。 取值范围：[0, +∞) 单位：[fp](../arkts-apis/arkts-arkui-length-t.md) |

## fontWeight

```TypeScript
fontWeight(value: number | FontWeight | string)
```

设置SymbolSpan组件字体粗细。未通过该接口设置时，默认字体粗细为FontWeight.Normal（正常粗细，对应数值400）。sys.symbol.ohos_lungs图标不支持设置fontWeight。

> **说明：**
> 
> 从API version 12开始，该接口支持在attributeModifier中调用。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| FontWeight \| string | 是 | SymbolSpan组件字体粗细。 number类型取值[100, 900]，取值间隔为100，默认为400，取值越大，字体越粗。string类型仅支持number类型取值的字符串形式，例如“400”，以及“bold”、“bolder”、“ lighter”、“regular”、“medium”，分别对应FontWeight中相应的枚举值。设置过大可能会在不同字体下有截断。传入超出取值范围或不符合间隔要求的值时取默认值。 |

## fontWeight

```TypeScript
fontWeight(value: number | FontWeight | ResourceStr, fontWeightConfigs?: FontWeightConfigs)
```

设置SymbolSpan组件字体粗细，支持通过FontWeightConfigs配置是否开启可变字重调节、是否开启随设备的字体粗细级别自动更新字重。未通过该接口设置时，默认字体粗细为FontWeight.Normal（正常粗细，对 应数值400）。sys.symbol.ohos_lungs图标不支持设置fontWeight。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| FontWeight \| [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | 是 | SymbolSpan组件字体粗细。 number类型取值[100, 900]，取值间隔为100，默认为400，取值越大，字体越粗。string类型仅支持number类型取值的字符串形式，例如“400”，以及“bold”、“bolder”、“ lighter”、“regular”、“medium”，分别对应FontWeight中相应的枚举值。设置过大可能会在不同字体下有截断。 传入超出取值范围的值时取默认值。传入不符合间隔要求的值时，若设置fontWeightConfigs的enableVariableFontWeight为true，使用传入值；若设置为false，使用默认值。 |
| fontWeightConfigs | [FontWeightConfigs](../arkts-apis/arkts-arkui-fontweightconfigs-i.md) | 否 | 字体粗细配置。当需要启用可变字重调节（设置非100整数倍的精细字重值如220、660）或跟随设备字体粗细级别自动更新字重时传入此 参数。默认值继承[FontWeightConfigs](../arkts-apis/arkts-arkui-fontweightconfigs-i.md)。 |

## renderingStrategy

```TypeScript
renderingStrategy(value: SymbolRenderingStrategy)
```

设置SymbolSpan渲染策略。未通过该接口设置时，默认渲染策略为SymbolRenderingStrategy.SINGLE。SINGLE表示单色渲染，适用于需要统一颜色的图标显示场景；MULTIPLE_COLOR表示多色渲染，适用于需要展示图标多层不同颜色的场景；MULTIPLE_OPACITY表示分层渲染，适用于需要展示图标层次效果的场景。

> **说明：**
> 
> 从API version 12开始，该接口支持在attributeModifier中调用。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [SymbolRenderingStrategy](arkts-arkui-symbolrenderingstrategy-e.md) | 是 | SymbolSpan渲染策略。 |
