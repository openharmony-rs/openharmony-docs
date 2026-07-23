# Button属性/事件

除支持[通用属性](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持以下属性：

支持[通用事件](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)。

**继承/实现关系：** ButtonAttribute extends [CommonMethod<ButtonAttribute>]

**起始版本：** 7

<!--Device-unnamed-declare class ButtonAttribute extends CommonMethod<ButtonAttribute>--><!--Device-unnamed-declare class ButtonAttribute extends CommonMethod<ButtonAttribute>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## buttonStyle

```TypeScript
buttonStyle(value: ButtonStyleMode)
```

设置Button组件的样式和重要程度。根据设置枚举值的不同，系统自动会调整按钮的背景色和文字颜色。背景色和文字颜色也支持开发者通过[backgroundColor](arkts-arkui-commonmethod-c.md#backgroundcolor)、[fontColor](ButtonAttribute#fontColor)和[role](ButtonAttribute#role)接口设置，实际显示效果以最后一次设置为准。
> **说明：**  
>  
> 从API version 12开始，该接口支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier)中调用。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

<!--Device-ButtonAttribute-buttonStyle(value: ButtonStyleMode): ButtonAttribute--><!--Device-ButtonAttribute-buttonStyle(value: ButtonStyleMode): ButtonAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ButtonStyleMode](arkts-arkui-buttonstylemode-e.md) | 是 | Button组件的样式和重要程度。<br/>默认值：ButtonStyleMode.EMPHASIZED |

## contentModifier

```TypeScript
contentModifier(modifier: ContentModifier<ButtonConfiguration>)
```

定制Button内容区的方法。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ButtonAttribute-contentModifier(modifier: ContentModifier<ButtonConfiguration>): ButtonAttribute--><!--Device-ButtonAttribute-contentModifier(modifier: ContentModifier<ButtonConfiguration>): ButtonAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| modifier | [ContentModifier](arkts-arkui-contentmodifier-i.md)&lt;ButtonConfiguration&gt; | 是 | 在Button组件上，定制内容区的方法。<br/>modifier：内容修改器，开发者需要自定义class实现ContentModifier接口。 |

## controlSize

```TypeScript
controlSize(value: ControlSize)
```

设置Button组件的尺寸。
> **说明：**  
>  
> 从API version 12开始，该接口支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier)中调用。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

<!--Device-ButtonAttribute-controlSize(value: ControlSize): ButtonAttribute--><!--Device-ButtonAttribute-controlSize(value: ControlSize): ButtonAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ControlSize](arkts-arkui-controlsize-e.md) | 是 | Button组件的尺寸。<br/>默认值：ControlSize.NORMAL |

## fontColor

```TypeScript
fontColor(value: ResourceColor)
```

设置文本显示颜色。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ButtonAttribute-fontColor(value: ResourceColor): ButtonAttribute--><!--Device-ButtonAttribute-fontColor(value: ResourceColor): ButtonAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 文本显示颜色。<br/>默认值：$r('sys.color.font_on_primary')，显示为白色字体。 |

## fontFamily

```TypeScript
fontFamily(value: string | Resource)
```

设置字体列表。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ButtonAttribute-fontFamily(value: string | Resource): ButtonAttribute--><!--Device-ButtonAttribute-fontFamily(value: string | Resource): ButtonAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string \| Resource | 是 | 字体列表。默认字体'HarmonyOS Sans'，当前支持'HarmonyOS Sans'字体和[注册自定义字体](../arkts-apis/arkts-font.md)。 |

## fontSize

```TypeScript
fontSize(value: Length)
```

设置文本显示字号。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ButtonAttribute-fontSize(value: Length): ButtonAttribute--><!--Device-ButtonAttribute-fontSize(value: Length): ButtonAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | 是 | 文本显示字号。<br/>默认值：当controlSize为ControlSize.NORMAL时，默认值为`$r('sys.float.Body_L')`。<br/>当controlSize为ControlSize.SMALL时，默认值为`$r('sys.float.Body_S')`。<br/>**说明**：设置string类型时，不支持百分比。 |

## fontStyle

```TypeScript
fontStyle(value: FontStyle)
```

设置文本的字体样式。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ButtonAttribute-fontStyle(value: FontStyle): ButtonAttribute--><!--Device-ButtonAttribute-fontStyle(value: FontStyle): ButtonAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [FontStyle](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-fontstyle-e.md) | 是 | 文本的字体样式。<br/>默认值：FontStyle.Normal |

## fontWeight

```TypeScript
fontWeight(value: number | FontWeight | string)
```

设置文本的字体粗细。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ButtonAttribute-fontWeight(value: number | FontWeight | string): ButtonAttribute--><!--Device-ButtonAttribute-fontWeight(value: number | FontWeight | string): ButtonAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| FontWeight \| string | 是 | 文本的字体粗细，number类型取值[100, 900]，取值间隔为100，取值越大，字体越粗。<br>默认值：500<br/>string类型仅支持number类型取值的字符串形式，例如'400'，以及'bold'、'bolder'、'lighter'、'regular'、'medium'，分别对应FontWeight中相应的枚举值。<br/>当值为异常值或非法值时，字体粗细取值为400。 |

## labelStyle

```TypeScript
labelStyle(value: LabelStyle)
```

设置Button组件label文本和字体的样式。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ButtonAttribute-labelStyle(value: LabelStyle): ButtonAttribute--><!--Device-ButtonAttribute-labelStyle(value: LabelStyle): ButtonAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [LabelStyle](arkts-arkui-labelstyle-i.md) | 是 | Button组件label文本和字体的样式。 |

## maxFontScale

```TypeScript
maxFontScale(scale: number | Resource)
```

设置文本最大的字体缩放倍数。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ButtonAttribute-maxFontScale(scale: number | Resource): ButtonAttribute--><!--Device-ButtonAttribute-maxFontScale(scale: number | Resource): ButtonAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scale | number \| Resource | 是 | 文本最大的字体缩放倍数。<br/>取值范围：[1, +∞)<br/>**说明：** <br/>设置的值小于1时，按值为1处理，异常值默认不生效。<br/>未设置最大缩放倍数时，圆形按钮最大缩放倍数为1倍，胶囊型按钮、普通按钮、圆角矩形按钮最大缩放倍数跟随系统设置。 |

## minFontScale

```TypeScript
minFontScale(scale: number | Resource)
```

设置文本最小的字体缩放倍数。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ButtonAttribute-minFontScale(scale: number | Resource): ButtonAttribute--><!--Device-ButtonAttribute-minFontScale(scale: number | Resource): ButtonAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scale | number \| Resource | 是 | 文本最小的字体缩放倍数。<br/>取值范围：[0, 1]<br/>**说明：** <br/>设置的值小于0时，按值为0处理，设置的值大于1，按值为1处理，异常值默认不生效。 |

## role

```TypeScript
role(value: ButtonRole)
```

设置Button组件的角色。根据设置枚举值的不同，系统自动会调整按钮的背景色和文字颜色。背景色和文字颜色也支持开发者通过[backgroundColor](arkts-arkui-commonmethod-c.md#backgroundcolor)、[fontColor](ButtonAttribute#fontColor)和[buttonStyle](ButtonAttribute#buttonStyle)接口设置，实际显示效果以最后一次设置为准。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-ButtonAttribute-role(value: ButtonRole): ButtonAttribute--><!--Device-ButtonAttribute-role(value: ButtonRole): ButtonAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ButtonRole](arkts-arkui-buttonrole-e.md) | 是 | 设置Button组件的角色。<br/>默认值：ButtonRole.NORMAL |

## stateEffect

```TypeScript
stateEffect(value: boolean)
```

设置是否开启按压态显示效果。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ButtonAttribute-stateEffect(value: boolean): ButtonAttribute--><!--Device-ButtonAttribute-stateEffect(value: boolean): ButtonAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 按钮按下时是否开启按压态显示效果。<br/>true：开启按压效果；false：关闭按压效果。<br/>默认值：true |

## type

```TypeScript
type(value: ButtonType)
```

设置Button样式。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ButtonAttribute-type(value: ButtonType): ButtonAttribute--><!--Device-ButtonAttribute-type(value: ButtonType): ButtonAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ButtonType](arkts-arkui-buttontype-e.md) | 是 | Button样式。<br/>API version 18及之后，ButtonType的默认值从ButtonType.Capsule变更为ButtonType.ROUNDED_RECTANGLE。 |

