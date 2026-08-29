# SymbolGlyph属性/事件

支持[通用属性](arkts-arkui-commonmethod-c.md)，不支持文本通用属性，仅支持以下特有属性。支持[通用事件](arkts-arkui-commonmethod-c.md)。

**继承/实现关系：** SymbolGlyphAttribute extends CommonMethod\<SymbolGlyphAttribute>

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## effectStrategy

```TypeScript
effectStrategy(value: SymbolEffectStrategy)
```

设置SymbolGlyph组件动效策略。未通过该接口设置时，默认动效策略为SymbolEffectStrategy.NONE。

> **说明：**
> 
> - 从API version 12开始，该接口支持在attributeModifier中调用。
> 
> - 动效属性，仅支持使用effectStrategy属性或单个symbolEffect属性，不支持多种动效属性混合使用。
> 
> - 本接口仅支持NONE、SCALE、HIERARCHICAL三种预置动效类型，设置后动效自动播放。如需使用更丰富的动效类型（如出现、消失、弹跳、替换、脉冲动效等）或控制动效的播放状态和触发时机，请使用
> [symbolEffect](#symboleffect)接口。两者不可同时使
> 用，详见[symbolEffect](#symboleffect)接口说明。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [SymbolEffectStrategy](arkts-arkui-symboleffectstrategy-e.md) | 是 | SymbolGlyph组件动效策略。 |

## fontColor

```TypeScript
fontColor(value: Array<ResourceColor>)
```

设置SymbolGlyph组件字体颜色。

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
| value | Array&lt;[ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)&gt; | 是 | SymbolGlyph组件字体颜色。 当value为undefined时，使用图标的默认颜色，默认颜色跟随主题。 不同渲染策略下颜色设置效果不同，详见[SymbolRenderingStrategy](arkts-arkui-symbolrenderingstrategy-e.md)枚举说明。 |

## fontColor

```TypeScript
fontColor(value: Array<ResourceColor | ColorMetrics> | undefined)
```

设置SymbolGlyph组件的字体颜色，相比[fontColor](#fontcolor)接口，本接口支持传入 [ColorMetrics](../arkts-apis/arkts-arkui-graphics-colormetrics-c.md)类型参数。

> **说明：**
> 
> 该接口支持在attributeModifier中调用。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Array&lt;[ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) \| ColorMetrics&gt; \ | undefined | 是 |  |

## fontSize

```TypeScript
fontSize(value: number | string | Resource)
```

设置SymbolGlyph组件字体大小。设置string类型时，支持number类型取值的字符串形式，可以附带单位，例如"10"、"10fp"。组件的图标显示大小由fontSize控制，设置width或height后，其他通用属性仅对组件的占位大小生效。未通过该接口设置时，默认字体大小为16fp。

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
| value | number \| string \| Resource | 是 | SymbolGlyph组件字体大小。 取值范围：[0, +∞) 单位：[fp](../arkts-apis/arkts-arkui-length-t.md) 不支持设置百分比字符串。 |

## fontWeight

```TypeScript
fontWeight(value: number | FontWeight | string)
```

设置SymbolGlyph组件字体粗细。未通过该接口设置时，默认字体粗细为FontWeight.Normal（正常粗细，对应数值400）。sys.symbol.ohos_lungs图标不支持设置fontWeight。

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
| value | number \| FontWeight \| string | 是 | SymbolGlyph组件字体粗细。 number类型取值[100, 900]，取值间隔为100，默认为400，取值越大，字体越粗。string类型仅支持number类型取值的字符串形式，例如“400”，以及“bold”、“bolder”、“ lighter”、“regular”、“medium”，分别对应FontWeight中相应的枚举值。设置过大可能会在不同字体下有截断。传入超出取值范围或不符合间隔要求的值时取默认值。 |

## fontWeight

```TypeScript
fontWeight(value: number | FontWeight | ResourceStr, fontWeightConfigs?: FontWeightConfigs)
```

设置SymbolGlyph组件图标小符号的粗细，支持通过FontWeightConfigs配置是否开启可变字重调节（启用后可设置非100整数倍的精细字重值，如220、660）、是否开启随设备的字体粗细级别自动更新字重（启用后组件字 重随系统字体粗细设置自动调整）。未通过该接口设置时，默认字体粗细为FontWeight.Normal（正常粗细，对应数值400）。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| FontWeight \| [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | 是 | SymbolGlyph组件图标小符号的粗细。 number类型取值[100, 900]，取值间隔为100，默认为400，取值越大，字体越粗。string类型仅支持number类型取值的字符串形式，例如“400”，以及“bold”、“bolder”、“ lighter”、“regular”、“medium”，分别对应FontWeight中相应的枚举值。设置过大可能会在不同字体下有截断。 传入超出取值范围的值时取默认值。传入不符合间隔要求的值时，若设置fontWeightConfigs的enableVariableFontWeight为true，使用传入值；若设置为false，使用默认值。 |
| fontWeightConfigs | [FontWeightConfigs](../arkts-apis/arkts-arkui-fontweightconfigs-i.md) | 否 | 字体粗细配置。当需要启用可变字重调节（设置非100整数倍的精细字重值如220、660）或跟随设备字体粗细级别自动更新字重时传入此 参数。默认值继承[FontWeightConfigs](../arkts-apis/arkts-arkui-fontweightconfigs-i.md)。 |

## maxFontScale

```TypeScript
maxFontScale(scale: Optional<number|Resource>)
```

设置SymbolGlyph组件最大的字体缩放倍数。适用于需要防止图标在用户字体缩放设置过大时超出布局容器或破坏界面一致性的场景，例如限制图标在小尺寸容器中的最大显示尺寸。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scale | [Optional](arkts-arkui-optional-t.md)&lt;number \| Resource&gt; | 是 | SymbolGlyph组件最大的字体缩放倍数。 取值范围：[1, +∞)    **说明：** 设置的值小于1时，按值为1处理。 |

## minFontScale

```TypeScript
minFontScale(scale: Optional<number|Resource>)
```

设置SymbolGlyph组件最小的字体缩放倍数。适用于需要防止图标在用户字体缩放设置过小时变得不可识别的场景，例如确保图标在任意系统字体设置下仍保持最小可读尺寸。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scale | [Optional](arkts-arkui-optional-t.md)&lt;number \| Resource&gt; | 是 | SymbolGlyph组件最小的字体缩放倍数。 取值范围：[0, 1] 设置为0，缩放最小。    **说明：** 设置的值小于0时，按值为0处理。设置的值大于1，按值为1处理。异常值默认不生效。 |

## renderingStrategy

```TypeScript
renderingStrategy(value: SymbolRenderingStrategy)
```

设置SymbolGlyph组件渲染策略。未通过该接口设置时，默认渲染策略为SymbolRenderingStrategy.SINGLE。

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
| value | [SymbolRenderingStrategy](arkts-arkui-symbolrenderingstrategy-e.md) | 是 | SymbolGlyph组件渲染策略。 |

## shaderStyle

```TypeScript
shaderStyle(shader: Array<ShaderStyle | undefined> | ShaderStyle)
```

设置SymbolGlyph组件的渐变色效果。可以显示为径向渐变[RadialGradientStyle](../arkts-apis/arkts-arkui-radialgradientstyle-c.md)或线性渐变[LinearGradientStyle](../arkts-apis/arkts-arkui-lineargradientstyle-c.md)或纯色 [ColorShaderStyle](../arkts-apis/arkts-arkui-colorshaderstyle-c.md)，shaderStyle的优先级高于 [fontColor](#fontcolor)和AI识别，纯色建议使用 [fontColor](#fontcolor)。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| shader | Array&lt;[ShaderStyle](../arkts-apis/arkts-arkui-shaderstyle-c.md) \| undefined&gt; \ | [ShaderStyle](../arkts-apis/arkts-arkui-shaderstyle-c.md) | 是 | 径向渐变或线性渐变或纯色。 传入ShaderStyle时，覆盖所有层；传入数组时，数据项是ShaderStyle，则应用该层；数组项是undefined，则该层使用SymbolGlyph默认颜色，未设置的层也应用默认颜色。根据传入的参数区分处 理径向渐变[RadialGradientStyle](../arkts-apis/arkts-arkui-radialgradientstyle-c.md)或线性渐变[LinearGradientStyle](../arkts-apis/arkts-arkui-lineargradientstyle-c.md)或纯色 [ColorShaderStyle](../arkts-apis/arkts-arkui-colorshaderstyle-c.md)，最终设置到SymbolGlyph组件上显示为渐变色效果。    **说明：** 中心点请按百分比使用。如果使用的是非百分比（例如10PX），效果等同于设置1000%。 半径建议使用百分比。 百分比是基于图标大小的百分比，建议取值范围[0, 1)。 |

## symbolEffect

```TypeScript
symbolEffect(symbolEffect: SymbolEffect, isActive?: boolean)
```

设置SymbolGlyph组件动效策略及播放状态。未通过该接口设置时，默认动效为SymbolEffect对象，默认播放状态为false。

> **说明：**
> 
> 动效属性，仅支持使用effectStrategy属性或单个symbolEffect属性，不支持多种动效属性混合使用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| symbolEffect | [SymbolEffect](arkts-arkui-symboleffect-c.md) | 是 | SymbolGlyph组件动效策略。 |
| isActive | boolean | 否 | SymbolGlyph组件动效播放状态。 true表示播放，false表示不播放。 |

## symbolEffect

```TypeScript
symbolEffect(symbolEffect: SymbolEffect, triggerValue?: number)
```

设置SymbolGlyph组件动效策略及播放触发器。未通过该接口设置时，默认动效为SymbolEffect对象，默认触发器值为-1。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| symbolEffect | [SymbolEffect](arkts-arkui-symboleffect-c.md) | 是 | SymbolGlyph组件动效策略。 |
| triggerValue | number | 否 | SymbolGlyph组件动效播放触发器，在数值变更时触发动效。 如果首次不希望触发动效，设置-1。 |

## symbolShadow

```TypeScript
symbolShadow(shadow: Optional<ShadowOptions>)
```

设置SymbolGlyph组件的阴影效果。未通过该接口设置时，默认阴影效果为{radius：0,color：Color.Black,offsetX：0,offsetY：0}。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本20开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| shadow | [Optional](arkts-arkui-optional-t.md)&lt;[ShadowOptions](arkts-arkui-shadowoptions-i.md)&gt; | 是 | SymbolGlyph组件的阴影效果。 单位：[vp](../arkts-apis/arkts-arkui-length-t.md) 不支持fill、type属性和color中的ColoringStrategy枚举值。 |
