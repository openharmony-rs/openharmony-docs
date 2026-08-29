# TextClock属性/事件

除支持[通用属性](arkts-arkui-commonmethod-c.md)外，还支持以下属性。除支持[通用事件](arkts-arkui-commonmethod-c.md)外，还支持以下事件。

**继承/实现关系：** TextClockAttribute extends CommonMethod<TextClockAttribute>

**起始版本：** 8

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## contentModifier

```TypeScript
contentModifier(modifier: ContentModifier<TextClockConfiguration>)
```

定制TextClock内容区的方法。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| modifier | [ContentModifier](arkts-arkui-contentmodifier-i.md)&lt;[TextClockConfiguration](arkts-arkui-textclockconfiguration-i.md)&gt; | 是 | 在TextClock组件上，定制内容区的方法。 modifier： 内容修改器，开发者需要自定义class实现ContentModifier接口。 |

## dateTimeOptions

```TypeScript
dateTimeOptions(dateTimeOptions: Optional<DateTimeOptions>)
```

设置小时是否显示前导0。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dateTimeOptions | [Optional](arkts-arkui-optional-t.md)&lt;DateTimeOptions&gt; | 是 | 设置小时是否显示前导0，只支持设置hour参数，参数值为{hour: "2-digit"}时表示显示前导0，参数值为{hour: "numeric"}时表示不显示前导0。 默认值：undefined，默认状态下，24小时制显示前导0，12小时制不显示前导0。 |

## fontColor

```TypeScript
fontColor(value: ResourceColor)
```

设置字体颜色。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 字体颜色。 Wearable设备上默认值：'#c5ffffff'，其他设备默认值：'#e6182431' |

## fontFamily

```TypeScript
fontFamily(value: ResourceStr)
```

设置字体列表。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | 是 | 字体列表。默认字体'HarmonyOS Sans'。 应用当前支持'HarmonyOS Sans'字体和[注册自定义字体](../arkts-apis/arkts-font.md)。 卡片当前仅支持'HarmonyOS Sans'字体。 |

## fontFeature

```TypeScript
fontFeature(value: string)
```

设置文字特性效果，比如数字等宽的特性。格式为：normal \| \&lt;feature-tag-value\&gt;\&lt;feature-tag-value\&gt;的格式为：\&lt;string\&gt; \[ \&lt;integer\&gt; \| on \| off ]\&lt;feature-tag-value\&gt;的个数可以有多个，中间用','隔开。例如，使用等宽时钟数字的输入格式为："ss01" on。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string | 是 | 文字特性效果，用于设置文字的OpenType特性。格式为：normal \|  &lt;feature-tag-value&gt;，其中 &lt;feature-tag-value&gt;格式为： &lt;string&gt; [ &lt;integer&gt; \ | on \| off ]。可设置多个特性，中间用','隔开。例如，使用等宽时钟数字的格式为：'"ss01" on'。 |

## fontSize

```TypeScript
fontSize(value: Length)
```

设置字体大小。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | 是 | 字体大小。fontSize为number类型时，使用fp单位。 字体默认大小16fp。不支持设置百分比字符串，传入百分比字符串时使用默认值。 |

## fontStyle

```TypeScript
fontStyle(value: FontStyle)
```

设置字体样式。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | FontStyle | 是 | 字体样式。 默认值：FontStyle.Normal，表示标准的字体样式（非斜体）。 |

## fontWeight

```TypeScript
fontWeight(value: number | FontWeight | string)
```

设置文本的字体粗细，设置过大可能会导致不同字体下的文字出现截断。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| FontWeight \| string | 是 | 文本的字体粗细，number类型取值范围为[100, 900]，取值间隔为100，取值越大，字体越粗。number类型取值范围外的默认 值为400。string类型支持：number类型取值的字符串形式（如400），以及枚举值'lighter'（对应300）、'regular'（对应400）、'medium'（对应500）、'bold'（对应700）、'bolder'（对应900），分别对应FontWeight中相应的枚举值。 默认值：FontWeight.Normal |

## format

```TypeScript
format(value: ResourceStr)
```

设置显示时间格式，如“yyyy/MM/dd”、“yyyy-MM-dd”。y：年（yyyy表示完整年份，yy表示年份后两位）M：月（若想使用01月则使用MM）d：日（若想使用01日则使用dd）E：星期（若想使用星期六则使用EEEE，若想使用周六则使用E、EE、EEE）H：小时（24小时制）h：小时（12小时制）m：分钟s：秒SS：厘秒（format中S个数&lt;3，全部按厘秒处理）SSS：毫秒（format中S个数&gt;=3，全部按毫秒处理）a：上午/下午（当设置小时制式为H时，该参数不生效）日期间隔符："年月日"、“/”、"-"、"."（可以自定义间隔符样式，字母不可以作为间隔符，汉字可以作为间隔符处理）允许自行拼接组合显示格式，即：年、月、日、星期、时、分、秒、毫秒可拆分为子元素，可自行排布组合。时间更新频率最高为一秒一次，不建议单独设置厘秒和毫秒格式。当设置无效字母时（非上述字母被认为是无效字母），该字母会被忽略。如果format全是无效字母时，显示格式跟随系统语言和系统小时制。例如系统语言为中文时，12小时制显示格式为yyyy/MM/dd aa hh:mm:ss.SSS，24 小时制显示格式为yyyy/MM/dd HH:mm:ss.SSS。若format为空字符串（""）或者undefined，则使用默认值。非卡片中默认值：12小时制：aa hh:mm:ss，24小时制：HH:mm:ss。卡片中默认值：12小时制：hh:mm，24小时制：HH:mm 。卡片中使用时，最小时间单位为分钟。如果设置格式中有秒或厘秒，则按默认值处理。以下是format输入的格式样式及对应的显示效果：  
| 输入格式 | 显示效果 | | ---------------------- | ------------------- | | yyyy年M月d日 EEEE | 2023年2月4日 星期六 | | yyyy年M月d日 | 2023年2月4日 | | M月d日 EEEE | 2月4日 星期六 | | M月d日 | 2月4日 | | MM/dd/yyyy | 02/04/2023 | | EEEE MM月dd日 | 星期六 02月04日 | | yyyy（完整年份） | 2023年 | | yy（年份后两位） | 23年 | | MM（完整月份） | 02月 | | M（月份） | 2月 | | dd（完整日期） | 04日 | | d（日期） | 4日 | | EEEE（完整星期） | 星期六 | | E、EE、EEE（简写星期） | 周六 | | yyyy年M月d日 | 2023年2月4日 | | yyyy/M/d | 2023/2/4 | | yyyy-M-d | 2023-2-4 | | yyyy.M.d | 2023.2.4 | | HH:mm:ss（时:分:秒） | 17:00:04 | | aa hh:mm:ss（时:分:秒） | 上午 5:00:04 | | hh:mm:ss（时:分:秒） | 5:00:04 | | HH:mm（时:分） | 17:00 | | aa hh:mm（时:分） | 上午 5:00 | | hh:mm（时:分） | 5:00 | | mm:ss（分:秒） | 00:04 | | mm:ss.SS（分:秒.厘秒） | 00:04.91 | | mm:ss.SSS（分:秒.毫秒） | 00:04.536 | | hh:mm:ss aa | 5:00:04 上午 | | HH | 17 |

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | 是 | 显示时间格式。<br>**起始版本：** 20 |

## onDateChange

```TypeScript
onDateChange(event: (value: number) => void)
```

提供时间变化回调，该事件回调间隔为秒。组件不可见时不回调。非卡片中使用时，该事件回调间隔为秒。卡片中使用时，该事件回调间隔为分钟。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | (value: number) =&gt; void | 是 | Unix time stamp, which is the number of seconds that have elapsed since the Unix epoch. |

## textShadow

```TypeScript
textShadow(value: ShadowOptions | Array<ShadowOptions>)
```

设置文字阴影效果。该接口支持以数组形式入参，实现多重文字阴影。不支持fill字段和智能取色模式。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ShadowOptions](arkts-arkui-shadowoptions-i.md) \| Array&lt;[ShadowOptions](arkts-arkui-shadowoptions-i.md)&gt; | 是 | 文字阴影效果。支持单个阴影对象或阴影数组实现多重阴影效果。ShadowOptions对象包含radius（模糊半径）、 color（阴影颜色）、offsetX（X轴偏移）、offsetY（Y轴偏移）等属性。 不支持fill字段，不支持智能取色模式。具体属性说明请参考[ShadowOptions对象说明](arkts-arkui-shadowoptions-i.md)。 |
