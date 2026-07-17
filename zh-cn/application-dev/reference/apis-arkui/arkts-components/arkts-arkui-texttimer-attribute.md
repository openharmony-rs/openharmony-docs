# TextTimer属性/事件

除支持[通用属性](../../../../reference/apis-arkui/arkui-ts/ts-component-general-attributes.md)外，还支持以下属性。

除支持[通用事件](../../../../reference/apis-arkui/arkui-ts/ts-component-general-events.md)外，还支持以下事件。

**继承/实现关系：** TextTimerAttribute extends [CommonMethod<TextTimerAttribute>](CommonMethod<TextTimerAttribute>)

**起始版本：** 8

<!--Device-unnamed-declare class TextTimerAttribute extends CommonMethod<TextTimerAttribute>--><!--Device-unnamed-declare class TextTimerAttribute extends CommonMethod<TextTimerAttribute>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## contentModifier

```TypeScript
contentModifier(modifier: ContentModifier<TextTimerConfiguration>)
```

定制TextTimer内容区的方法。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextTimerAttribute-contentModifier(modifier: ContentModifier<TextTimerConfiguration>): TextTimerAttribute--><!--Device-TextTimerAttribute-contentModifier(modifier: ContentModifier<TextTimerConfiguration>): TextTimerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| modifier | [ContentModifier](arkts-arkui-common-contentmodifier-i.md)<TextTimerConfiguration> | 是 | 在TextTimer组件上，定制内容区的方法。<br/>modifier： 内容修改器，开发者需要自定义class实现ContentModifier接口。 |

## fontColor

```TypeScript
fontColor(value: ResourceColor)
```

设置字体颜色。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-TextTimerAttribute-fontColor(value: ResourceColor): TextTimerAttribute--><!--Device-TextTimerAttribute-fontColor(value: ResourceColor): TextTimerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 字体颜色。<br/>Wearable设备上默认值为：'#c5ffffff'，显示白色。<br/>其他设备上默认值：'#e6182431'，显示黑色。 |

## fontFamily

```TypeScript
fontFamily(value: ResourceStr)
```

设置字体列表。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-TextTimerAttribute-fontFamily(value: ResourceStr): TextTimerAttribute--><!--Device-TextTimerAttribute-fontFamily(value: ResourceStr): TextTimerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | 是 | 字体列表。默认字体为'HarmonyOS Sans'。<br>应用当前支持'HarmonyOS Sans'字体和[注册自定义字体](../arkts-apis/arkts-font.md)。<br>卡片当前仅支持'HarmonyOS Sans'字体。 |

## fontSize

```TypeScript
fontSize(value: Length)
```

设置字体大小。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-TextTimerAttribute-fontSize(value: Length): TextTimerAttribute--><!--Device-TextTimerAttribute-fontSize(value: Length): TextTimerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | 是 | 字体大小。value为Length中的number类型时，单位为fp。字体大小默认为16fp。value为Length中的string类型时，设置值为非数字开头的字符串时，按0fp处理；设置值为数字开头的字符串时，如果数字后内容包含除[像素单位](../../../../reference/apis-arkui/arkui-ts/ts-pixel-units.md)外的字符（如字母、特殊符号等），则取值字符串开头的数字部分，单位为fp。例如设置值为"abc"时取值为0fp，设置值为"10vp"时取值为10vp，设置值为"10vp11abc"时取值为10fp。不支持设置百分比字符串。 |

## fontStyle

```TypeScript
fontStyle(value: FontStyle)
```

设置字体样式。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-TextTimerAttribute-fontStyle(value: FontStyle): TextTimerAttribute--><!--Device-TextTimerAttribute-fontStyle(value: FontStyle): TextTimerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [FontStyle](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-fontstyle-e.md) | 是 | 字体样式，例如斜体的字体样式。<br/>默认值：FontStyle.Normal |

## fontWeight

```TypeScript
fontWeight(value: number | FontWeight | ResourceStr)
```

设置文本的字体粗细，设置过大可能会导致不同字体下的文字出现截断。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-TextTimerAttribute-fontWeight(value: number | FontWeight | ResourceStr): TextTimerAttribute--><!--Device-TextTimerAttribute-fontWeight(value: number | FontWeight | ResourceStr): TextTimerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| FontWeight \| ResourceStr | 是 | 文本的字体粗细，number类型取值范围为[100, 900]，取值间隔为100，取值越大，字体越粗。number类型取值范围外的默认值为400。[ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)类型仅支持number类型取值的字符串形式，例如"400"，以及"bold"、"bolder"、"lighter"、"regular"、"medium"，分别对应FontWeight中相应的枚举值。<br/>默认值：FontWeight.Normal <br>从API version 20开始，支持Resource类型。<br>**起始版本：** 20 |

## format

```TypeScript
format(value: string)
```

设置自定义格式，需至少包含一个HH、mm、ss、SS中的关键字。使用yy、MM、dd等日期格式时，使用默认值。

计时器更新频率按format最小单位处理，例如：format设置为'HH:mm'时，更新频率为一分钟。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-TextTimerAttribute-format(value: string): TextTimerAttribute--><!--Device-TextTimerAttribute-format(value: string): TextTimerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string | 是 | 自定义日期显示的格式。<br/>默认值：'HH:mm:ss.SS' |

## onTimer

```TypeScript
onTimer(event: (utc: number, elapsedTime: number) => void)
```

时间文本发生变化时触发该事件。锁屏状态和应用后台状态下不会触发该事件。设置高精度的[format](TextTimerAttribute#format)（SS）时，回调间隔可能会出现波动。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-TextTimerAttribute-onTimer(event: (utc: number, elapsedTime: number) => void): TextTimerAttribute--><!--Device-TextTimerAttribute-onTimer(event: (utc: number, elapsedTime: number) => void): TextTimerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | (utc: number, elapsedTime: number) => void | 是 | utc——Linux时间戳，即自1970年1月1日起经过的时间，单位为设置格式的最小单位。<br/>elapsedTime——计时器经过的时间，单位为设置格式的最小单位。 |

## textShadow

```TypeScript
textShadow(value: ShadowOptions | Array<ShadowOptions>)
```

设置文字阴影效果。该接口支持以数组形式入参，实现多重文字阴影。不支持fill字段, 不支持智能取色模式。

> **说明：**  
>  
> 从API version 12开始，该接口支持在[attributeModifier](arkts-arkui-common-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextTimerAttribute-textShadow(value: ShadowOptions | Array<ShadowOptions>): TextTimerAttribute--><!--Device-TextTimerAttribute-textShadow(value: ShadowOptions | Array<ShadowOptions>): TextTimerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | ShadowOptions \| Array<ShadowOptions> | 是 | 文字阴影效果的参数，包括颜色、模糊半径、偏移量。 |

