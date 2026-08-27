# TimePicker属性/事件

除支持通用属性外，还支持以下属性：除支持通用事件外，还支持以下事件：

**继承/实现关系：** TimePickerAttribute extends CommonMethod<TimePickerAttribute>

**起始版本：** 8

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## dateTimeOptions

```TypeScript
dateTimeOptions(value: DateTimeOptions)
```

设置时分秒是否显示前导0。'2-digit'适用于需要统一格式显示的场景（如表格、报表），'numeric'适用于更简洁的显示需求。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [DateTimeOptions](arkts-arkui-datetimeoptions-t.md) | 是 | 设置时分秒是否显示前导0。 默认值： hour: 24小时制默认为"2-digit"，设置hour是否按照2位数字显示，如果实际数值小于10，则会补充前导0并显示，即为"0X"； 12小时制默认为"numeric"，即没有前导0。 minute: 默认为"2-digit"，设置minute是否按照2位数字显示，如果实际数值小于10，则会补充前导0并显示，即为"0X"。 second: 默认为"2-digit"，设置second是否按照2位数字显示，如果实际数值小于10，则会补充前导0并显示，即为"0X"。 当hour、minute、second的值设置为undefined时，显示效果与其默认值规则一致。 |

## dateTimeOptions

```TypeScript
dateTimeOptions(timeFormat: Optional<DateTimeOptions>)
```

设置时分秒是否显示前导0。与[dateTimeOptions&lt;sup&gt;12+&lt;/sup&gt;](#datetimeoptions)相比， timeFormat参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| timeFormat | [Optional](arkts-arkui-optional-t.md)&lt;[DateTimeOptions](arkts-arkui-datetimeoptions-t.md)&gt; | 是 | 设置时分秒是否显示前导0，目前只支持设置hour、minute和second参数。 默认值： hour: 24小时制默认为"2-digit"，设置hour是否按照2位数字显示，如果实际数值小于10，则会补充前导0并显示，即为"0X"； 12小时制默认为"numeric"，即没有前导0。 minute: 默认为"2-digit"，设置minute是否按照2位数字显示，如果实际数值小于10，则会补充前导0并显示，即为"0X"。 second: 默认为"2-digit"，设置second是否按照2位数字显示，如果实际数值小于10，则会补充前导0并显示，即为"0X"。 当hour、minute、second的值设置为undefined时，显示效果与其默认值规则一致。 |

## digitalCrownSensitivity

```TypeScript
digitalCrownSensitivity(sensitivity: Optional<CrownSensitivity>)
```

设置表冠灵敏度。高灵敏度适用于需要快速调整时间的场景，低灵敏度适用于需要精确调整时间的场景。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sensitivity | [Optional](arkts-arkui-optional-t.md)&lt;[CrownSensitivity](../arkts-apis/arkts-arkui-crownsensitivity-e.md)&gt; | 是 | 表冠响应灵敏度。 默认值：CrownSensitivity.MEDIUM，表示响应速度适中。 |

## disappearTextStyle

```TypeScript
disappearTextStyle(value: PickerTextStyle)
```

设置边缘项（以选中项为基准向上或向下的第二项）的文本颜色、字号、字体粗细。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [PickerTextStyle](arkts-arkui-pickertextstyle-i.md) | 是 | 边缘项（以选中项为基准向上或向下的第二项）的文本颜色、字号和字体粗细。 默认值： {color: '#ff182431', font: {size: '14fp', weight: FontWeight.Regular } } |

## disappearTextStyle

```TypeScript
disappearTextStyle(style: Optional<PickerTextStyle>)
```

设置边缘项（以选中项为基准向上或向下的第二项）的文本颜色、字号、字体粗细。与 [disappearTextStyle&lt;sup&gt;10+&lt;/sup&gt;](#disappeartextstyle)相比， style参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-optional-t.md)&lt;[PickerTextStyle](arkts-arkui-pickertextstyle-i.md)&gt; | 是 | 边缘项的文本颜色、字号、字体粗细。 默认值： {color: '#ff182431', font: {size: '14fp', weight: FontWeight.Regular } } 当style的值为undefined时，使用默认值。 |

## enableCascade

```TypeScript
enableCascade(enabled: boolean)
```

设置上午和下午的标识是否根据小时数自动切换， 仅在[useMilitaryTime](#usemilitarytime)设置为false时生效。 自动切换适用于闹钟、日程等注重操作效率和流畅体验的日常消费场景，手动切换适用于医疗、法律等对时间精确性要求严苛、不容歧义的场景。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | 上午和下午的标识是否根据小时数自动切换，仅在useMilitaryTime设置为false时生效。    - true：自动切换。当enabled设置为true时，仅在loop参数同时为true时生效。    - false：不自动切换。上午/下午标识需手动选择，不会根据小时数自动调整。    默认值：false |

## enableHapticFeedback

```TypeScript
enableHapticFeedback(enable: boolean)
```

设置是否开启触控反馈。开启触控反馈时，需要在工程的src/main/module.json5文件的"module"内配置requestPermissions字段开启振动权限，配置如下：

> **说明：**
> 
> 从API version 18开始，该接口支持在attributeModifier中调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 设置是否开启触控反馈。    - true：开启触控反馈。    - false：不开启触控反馈。    默认值：true 设置为true后，若系统硬件不支持振动功能，则不会产生振动反馈。 |

## enableHapticFeedback

```TypeScript
enableHapticFeedback(enable: Optional<boolean>)
```

设置是否开启触控反馈。 与[enableHapticFeedback&lt;sup&gt;12+&lt;/sup&gt;](#enablehapticfeedback)相比， enable参数新增了对undefined类型的支持。开启触控反馈时，需要在工程的src/main/module.json5文件的"module"内配置requestPermissions字段开启振动权限，配置如下：

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 设置是否开启触控反馈。    - true：开启触控反馈。    - false：不开启触控反馈。    默认值：true 当enable的值为undefined时，使用默认值。 设置为true后，若系统硬件不支持振动功能，则不会产生振动反馈。 |

## loop

```TypeScript
loop(value: boolean)
```

设置是否启用循环模式。循环模式适用于需要连续滚动选择时间的场景，非循环模式适用于固定时间范围的限制场景。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 是否启用循环模式。    - true：启用循环模式。    - false：不启用循环模式。    默认值：true    **说明：** 设置了start或end且为非默认值的场景下，loop不生效。 |

## loop

```TypeScript
loop(isLoop: Optional<boolean>)
```

设置是否启用循环模式。与[loop&lt;sup&gt;11+&lt;/sup&gt;](#loop)相比， isLoop参数新增了对undefined类型的支持。

> **说明：**
> 
> 设置了start或end且为非默认值的场景下，loop不生效。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isLoop | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 是否启用循环模式。    - true：启用循环模式。    - false：不启用循环模式。    默认值：true 当isLoop的值为undefined时，使用默认值。 |

## onChange

```TypeScript
onChange(callback: (value: TimePickerResult) => void)
```

滑动TimePicker后，时间选项归位至选中项位置时，触发该回调。不能通过双向绑定的状态变量触发。适用于需要在用户确认时间选择后执行保存、 更新UI等操作的场景。回调会在滑动动画结束后触发，如果需要快速获取索引值变化， 建议使用[onEnterSelectedArea](#onenterselectedarea)接口。需要注意的是， 当[enableCascade](#enablecascade)设置为true时，由于上午/下午列与小时列存在联动关系， 该回调的行为可能不符合预期，不建议在此场景下使用。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (value: TimePickerResult) = & gt; void | 是 | Time in 24-hour format. |

## onChange

```TypeScript
onChange(callback: Optional<OnTimePickerChangeCallback>)
```

滑动TimePicker后，时间选项归位至选中项位置时，触发该回调。不能通过双向绑定的状态变量触发。 与onChange相比， callback参数新增了对undefined类型的支持。回调会在滑动动画结束后触发，如果需要快速获取索引值变化， 建议使用[onEnterSelectedArea](#onenterselectedarea)接口。需要注意的是， 当[enableCascade](#enablecascade)设置为true时，由于上午/下午列与小时列存在联动关系， 该回调的行为可能不符合预期，不建议在此场景下使用。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Optional](arkts-arkui-optional-t.md)&lt;[OnTimePickerChangeCallback](arkts-arkui-ontimepickerchangecallback-t.md)&gt; | 是 | 选择时间时触发该回调。 当callback的值为undefined时，不使用回调函数。 |

## onEnterSelectedArea

```TypeScript
onEnterSelectedArea(callback: Callback<TimePickerResult>)
```

滑动TimePicker过程中，选项进入分割线区域内，触发该回调。适用于需要在滑动过程中实时更新UI、实时验证时间范围等需要快速响应的场景。 与onChange相比，该回调触发时机更早，适合需要即时反馈的场景。与onChange事件的差别在于， 该事件的触发时机早于onChange事件， 当滑动列的滑动距离超过选中项高度的一半时，选项已经进入分割线区域内，会触发该事件。 当[enableCascade](#enablecascade)设置为true时， 由于上午/下午列与小时列存在联动关系（即上午/下午标识会根据小时数自动调整），不建议使用该回调。 该回调标识的是滑动过程中选项进入分割线区域内的节点，而联动变化的选项并不涉及滑动，因此，回调的返回值中，仅当前滑动列的值会正常变化， 其余未滑动列的值保持不变。

> **说明：**
> 
> 该接口不支持在attributeModifier中调用。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;[TimePickerResult](arkts-arkui-timepickerresult-i.md)&gt; | 是 | 滑动TimePicker过程中，选项进入分割线区域时触发的回调。 |

## selectedTextStyle

```TypeScript
selectedTextStyle(value: PickerTextStyle)
```

设置选中项的文本颜色、字号和字体粗细。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [PickerTextStyle](arkts-arkui-pickertextstyle-i.md) | 是 | 选中项的文本颜色、字号、字体粗细。 默认值： {color: '#ff007dff', font: {size: '20fp', weight: FontWeight.Medium } } |

## selectedTextStyle

```TypeScript
selectedTextStyle(style: Optional<PickerTextStyle>)
```

设置选中项的文本颜色、字号及字体粗细。与 [selectedTextStyle&lt;sup&gt;10+&lt;/sup&gt;](#selectedtextstyle)相比， style参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-optional-t.md)&lt;[PickerTextStyle](arkts-arkui-pickertextstyle-i.md)&gt; | 是 | 选中项的文本颜色、字号、字体粗细。 默认值： {color: '#ff007dff', font: {size: '20fp', weight: FontWeight.Medium } } 当style的值为undefined时，使用默认值。 |

## textStyle

```TypeScript
textStyle(value: PickerTextStyle)
```

设置待选项（以选中项为基准向上或向下的第一项）的文本颜色、字号、字体粗细。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [PickerTextStyle](arkts-arkui-pickertextstyle-i.md) | 是 | 待选项的文本颜色、字号、字体粗细。 默认值： {color: '#ff182431', font: {size: '16fp', weight: FontWeight.Regular } } |

## textStyle

```TypeScript
textStyle(style: Optional<PickerTextStyle>)
```

设置待选项（以选中项为基准向上或向下的第一项）的文本颜色、字号、字体粗细。与 [textStyle&lt;sup&gt;10+&lt;/sup&gt;](#textstyle)相比， style参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-optional-t.md)&lt;[PickerTextStyle](arkts-arkui-pickertextstyle-i.md)&gt; | 是 | 待选项的文本颜色、字号、字体粗细。 默认值： {color: '#ff182431', font: {size: '16fp', weight: FontWeight.Regular } } 当style的值为undefined时，使用默认值。 |

## useMilitaryTime

```TypeScript
useMilitaryTime(value: boolean)
```

设置时间是否以24小时制展示，未通过该接口设置时，默认跟随系统设置展示。24小时制适用于精确的时间记录和调度场景，12小时制适用于日常闹钟设置等 更直观的时间显示需求。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 时间是否以24小时制展示。    - true：时间以24小时制展示。    - false：时间以12小时制展示。 |

## useMilitaryTime

```TypeScript
useMilitaryTime(isMilitaryTime: Optional<boolean>)
```

设置展示时间是否为24小时制，未通过该接口设置时，默认跟随系统设置展示。 与[useMilitaryTime](#usemilitarytime)相比， isMilitaryTime参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isMilitaryTime | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 展示时间是否为24小时制。    - true：展示时间为24小时制。    - false：展示时间为12小时制。    当isMilitaryTime的值为undefined时，跟随系统设置。 |
