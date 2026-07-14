# TimePicker属性/事件

除支持[通用属性](./common)外，还支持以下属性：

除支持[通用事件](./common)外，还支持以下事件：

**继承/实现关系：** TimePickerAttribute extends [CommonMethod<TimePickerAttribute>](CommonMethod<TimePickerAttribute>)

**起始版本：** 8

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## dateTimeOptions

```TypeScript
dateTimeOptions(value: DateTimeOptions)
```

设置时分秒是否显示前导0。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | DateTimeOptions | 是 | 设置时分秒是否显示前导0。默认值：<br/>hour: 24小时制默认为"2-digit"，设置hour是否按照2位数字显示，如果实际数值小于10，则会补充前导0并显示，即为"0X"；12小时制默认为"numeric"，即没有前导0。minute: 默认为"2-digit"，设置minute是否按照2位数字显示，如果实际数值小于10，则会补充前导0并显示，即为"0X"。second: 默认为"2-digit"，设置second是否按照2位数字显示，如果实际数值小于10，则会补充前导0并显示，即为"0X"。当hour、minute、second的值设置为undefined时，显示效果与其默认值规则一致。 |

## dateTimeOptions

```TypeScript
dateTimeOptions(timeFormat: Optional<DateTimeOptions>)
```

设置时分秒是否显示前导0。与[dateTimeOptions<sup>12+</sup>](TimePickerAttribute#dateTimeOptions(value:
DateTimeOptions))相比，timeFormat参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| timeFormat | Optional&lt;DateTimeOptions&gt; | 是 | 设置时分秒是否显示前导0，目前只支持设置hour、minute和second参数。默认值：<br/>hour: 24小时制默认为"2-digit"，设置hour是否按照2位数字显示，如果实际数值小于10，则会补充前导0并显示，即为"0X"；12小时制默认为"numeric"，即没有前导0。minute: 默认为"2-digit"，设置minute是否按照2位数字显示，如果实际数值小于10，则会补充前导0并显示，即为"0X"。second: 默认为"2-digit"，设置second是否按照2位数字显示，如果实际数值小于10，则会补充前导0并显示，即为"0X"。<br/> 当hour、minute、second的值设置为undefined时，显示效果与其默认值规则一致。 |

## digitalCrownSensitivity

```TypeScript
digitalCrownSensitivity(sensitivity: Optional<CrownSensitivity>)
```

设置表冠灵敏度。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sensitivity | Optional&lt;CrownSensitivity&gt; | 是 | 表冠响应灵敏度。<br/>默认值：CrownSensitivity.MEDIUM，表示响应速度适中。 |

## disappearTextStyle

```TypeScript
disappearTextStyle(value: PickerTextStyle)
```

设置边缘项（以选中项为基准向上或向下的第二项）的文本颜色、字号、字体粗细。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | PickerTextStyle | 是 | 边缘项的文本颜色、字号和字体粗细。默认值：{ color: '#ff182431', font: { size: '14fp', weight: FontWeight.Regular } } |

## disappearTextStyle

```TypeScript
disappearTextStyle(style: Optional<PickerTextStyle>)
```

设置边缘项（以选中项为基准向上或向下的第二项）的文本颜色、字号、字体粗细。与
[disappearTextStyle<sup>10+</sup>](TimePickerAttribute#disappearTextStyle(value: PickerTextStyle))相比，
style参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | Optional&lt;PickerTextStyle&gt; | 是 | 边缘项的文本颜色、字号、字体粗细。默认值：{ color: '#ff182431', font: { size: '14fp', weight: FontWeight.Regular } }当style的值为undefined时，使用默认值。 |

## enableCascade

```TypeScript
enableCascade(enabled: boolean)
```

设置上午和下午的标识是否根据小时数自动切换，仅在[useMilitaryTime](TimePickerAttribute#useMilitaryTime(value:
boolean))设置为false时生效。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | 上午和下午的标识是否根据小时数自动切换，仅在useMilitaryTime设置为false时生效。- true：自动切换。- false：不自动切换。默认值：false当enabled设置为true时，仅在loop参数同时为true时生效。 |

## enableHapticFeedback

```TypeScript
enableHapticFeedback(enable: boolean)
```

设置是否支持触控反馈。

开启触控反馈时，需要在工程的src/main/module.json5文件的"module"内配置requestPermissions字段开启振动权限。

> **说明：**
>
> 从API version 18开始，该接口支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 设置是否开启触控反馈。- true：开启触控反馈。- false：不开启触控反馈。默认值：true<br/>设置为true后，其生效情况取决于系统的硬件是否支持。 |

## enableHapticFeedback

```TypeScript
enableHapticFeedback(enable: Optional<boolean>)
```

设置是否支持触控反馈。与[enableHapticFeedback<sup>12+</sup>](TimePickerAttribute#enableHapticFeedback(enable:
boolean))相比，enable参数新增了对undefined类型的支持。

开启触控反馈时，需要在工程的src/main/module.json5文件的"module"内配置requestPermissions字段开启振动权限。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | Optional&lt;boolean&gt; | 是 | 设置是否开启触控反馈。- true：开启触控反馈。- false：不开启触控反馈。默认值：true<br/>当enable的值为undefined时，使用默认值。设置为true后，其生效情况取决于系统的硬件是否支持。 |

## loop

```TypeScript
loop(value: boolean)
```

设置是否启用循环模式。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 是否启用循环模式。<br/>- true：启用循环模式。<br/>- false：不启用循环模式。<br/>默认值：true |

## loop

```TypeScript
loop(isLoop: Optional<boolean>)
```

设置是否启用循环模式。与[loop<sup>11+</sup>](TimePickerAttribute#loop(value: boolean))相比，
isLoop参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isLoop | Optional&lt;boolean&gt; | 是 | 是否启用循环模式。- true：启用循环模式。- false：不启用循环模式。默认值：true当isLoop的值为undefined时，使用默认值。 |

## onChange

```TypeScript
onChange(callback: (value: TimePickerResult) => void)
```

滑动TimePicker后，时间选项归位至选中项位置时，触发该回调。不能通过双向绑定的状态变量触发。

回调会在滑动动画结束后触发，如果需要快速获取索引值变化，
建议使用[onEnterSelectedArea](TimePickerAttribute#onEnterSelectedArea)接口。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (value: TimePickerResult) =&gt; void | 是 | 24小时制时间。 |

## onChange

```TypeScript
onChange(callback: Optional<OnTimePickerChangeCallback>)
```

滑动TimePicker后，时间选项归位至选中项位置时，触发该回调。不能通过双向绑定的状态变量触发。与
[onChange](TimePickerAttribute#onChange(callback: Optional<OnTimePickerChangeCallback>))相比，
callback参数新增了对undefined类型的支持。

回调会在滑动动画结束后触发，如果需要快速获取索引值变化，
建议使用[onEnterSelectedArea](TimePickerAttribute#onEnterSelectedArea)接口。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Optional&lt;OnTimePickerChangeCallback&gt; | 是 | 选择时间时触发该回调。<br/>当callback的值为undefined时，不使用回调函数。 |

## onEnterSelectedArea

```TypeScript
onEnterSelectedArea(callback: Callback<TimePickerResult>)
```

滑动TimePicker过程中，选项进入分割线区域内，触发该回调。

与[onChange](TimePickerAttribute#onChange(callback: Optional<OnTimePickerChangeCallback>))事件的差别在于，
该事件的触发时机早于[onChange](TimePickerAttribute#onChange(callback: Optional<OnTimePickerChangeCallback>))事件，
当当前滑动列滑动距离超过选中项高度的一半时，选项此时已经进入分割线区域内，会触发该事件。
当[enableCascade](TimePickerAttribute#enableCascade)设置为true时，由于上午/下午列与小时列存在联动关系，不建议使用该回调。
该回调标识的是滑动过程中选项进入分割线区域内的节点，而联动变化的选项并不涉及滑动，因此，回调的返回值中，仅当前滑动列的值会正常变化，
其余未滑动列的值保持不变。

> **说明：**
>
> 该接口不支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;TimePickerResult&gt; | 是 | 滑动TimePicker过程中，选项进入分割线区域时触发的回调。 |

## selectedTextStyle

```TypeScript
selectedTextStyle(value: PickerTextStyle)
```

设置选中项的文本颜色、字号和字体粗细。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | PickerTextStyle | 是 | 选中项的文本颜色、字号、字体粗细。默认值：{ color: '#ff007dff', font: { size: '20fp', weight: FontWeight.Medium } } |

## selectedTextStyle

```TypeScript
selectedTextStyle(style: Optional<PickerTextStyle>)
```

设置选中项的文本颜色、字号及字体粗细。与
[selectedTextStyle<sup>10+</sup>](TimePickerAttribute#selectedTextStyle(value: PickerTextStyle))相比，
style参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | Optional&lt;PickerTextStyle&gt; | 是 | 选中项的文本颜色、字号、字体粗细。默认值：{ color: '#ff007dff', font: { size: '20fp', weight: FontWeight.Medium } }当style的值为undefined时，使用默认值。 |

## textStyle

```TypeScript
textStyle(value: PickerTextStyle)
```

设置待选项（以选中项为基准向上或向下的第一项）的文本颜色、字号、字体粗细。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | PickerTextStyle | 是 | 待选项的文本颜色、字号、字体粗细。默认值：{ color: '#ff182431', font: { size: '16fp', weight: FontWeight.Regular } } |

## textStyle

```TypeScript
textStyle(style: Optional<PickerTextStyle>)
```

设置待选项（以选中项为基准向上或向下的第一项）的文本颜色、字号、字体粗细。与
[textStyle<sup>10+</sup>](TimePickerAttribute#textStyle(value: PickerTextStyle))相比，
style参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | Optional&lt;PickerTextStyle&gt; | 是 | 待选项的文本颜色、字号、字体粗细。默认值：{ color: '#ff182431', font: { size: '16fp', weight: FontWeight.Regular } }当style的值为undefined时，使用默认值。 |

## useMilitaryTime

```TypeScript
useMilitaryTime(value: boolean)
```

设置时间是否以24小时制展示，未通过该接口设置时，默认跟随系统设置展示。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 时间是否以24小时制展示。<br/>- true：时间以24小时制展示。<br/>- false：时间以12小时制展示。 |

## useMilitaryTime

```TypeScript
useMilitaryTime(isMilitaryTime: Optional<boolean>)
```

设置展示时间是否为24小时制，未通过该接口设置时，默认跟随系统设置展示。与[useMilitaryTime]
{@link TimePickerAttribute#useMilitaryTime(value: boolean)}相比，isMilitaryTime参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isMilitaryTime | Optional&lt;boolean&gt; | 是 | 展示时间是否为24小时制。- true：展示时间为24小时制。- false：展示时间为12小时制。当isMilitaryTime的值为undefined时，跟随系统设置。 |

