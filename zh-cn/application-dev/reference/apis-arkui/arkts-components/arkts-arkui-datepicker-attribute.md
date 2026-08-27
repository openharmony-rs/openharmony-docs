# DatePicker属性/事件

除支持通用属性外，还支持以下属性：除支持通用事件外，还支持以下事件：@extends CommonMethod [since 8 - 10] @extends CommonMethod&lt;DatePickerAttribute&gt; [since 11]

**继承/实现关系：** DatePickerAttribute extends CommonMethod<DatePickerAttribute>

**起始版本：** 8

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## canLoop

```TypeScript
canLoop(isLoop: Optional<boolean>)
```

设置是否可循环滚动。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isLoop | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 是否可循环滚动。    - true：可循环滚动，年份随着月份的循环滚动进行联动加减，月份随着日的循环滚动进行联动加减。    - false：非循环滚动，年、月、日到达本列的顶部或底部时停止滚动，年、月、日之间保持独立，不进行联动加减。    默认值：true 当isLoop的值为undefined时，使用默认值。    **说明：** 设置了[start](arkts-arkui-datepickeroptions-i.md)或[end](arkts-arkui-datepickeroptions-i.md)且为非默认值的场景下，canLoop不生效。 这是因为设置了日期范围限制后，循环滚动可能导致日期超出有效范围，为确保日期选择的准确性，强制使用非循环模式。 |

## digitalCrownSensitivity

```TypeScript
digitalCrownSensitivity(sensitivity: Optional<CrownSensitivity>)
```

设置表冠灵敏度。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sensitivity | [Optional](arkts-arkui-optional-t.md)&lt;[CrownSensitivity](../arkts-apis/arkts-arkui-crownsensitivity-e.md)&gt; | 是 | 表冠响应灵敏度。 默认值：CrownSensitivity.MEDIUM，响应速度适中。 |

## disappearTextStyle

```TypeScript
disappearTextStyle(value: PickerTextStyle)
```

设置边缘项（以选中项为基准向上或向下的第二项）的文本样式。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [PickerTextStyle](arkts-arkui-pickertextstyle-i.md) | 是 | 边缘项的文本颜色、字号、字体粗细。 默认值： {color: '#ff182431', font: {size: '14fp', weight: FontWeight.Regular } } |

## disappearTextStyle

```TypeScript
disappearTextStyle(style: Optional<PickerTextStyle>)
```

设置边缘项（以选中项为基准向上或向下的第二项）的文本样式。与 [disappearTextStyle&lt;sup&gt;10+&lt;/sup&gt;](#disappeartextstyle)相比， style参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-optional-t.md)&lt;[PickerTextStyle](arkts-arkui-pickertextstyle-i.md)&gt; | 是 | 边缘项的文本颜色、字号、字体粗细。 默认值： {color: '#ff182431', font: {size: '14fp', weight: FontWeight.Regular } } 当style的值为undefined时，使用默认值。 |

## enableHapticFeedback

```TypeScript
enableHapticFeedback(enable: Optional<boolean>)
```

设置是否开启触控反馈。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 设置是否开启触控反馈。    - true：开启触控反馈。    - false：不开启触控反馈。    默认值：true 设置为true后，其生效情况取决于系统的硬件是否支持。 当enable的值为undefined时，使用默认值。 |

## lunar

```TypeScript
lunar(value: boolean)
```

设置日期是否显示为农历。

> **说明：**
> 
> 仅在简体中文和繁体中文语言环境下生效，其他语言环境下设置该属性无效果。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 日期是否显示为农历。    - true：显示为农历。    - false：不显示为农历。    默认值：false |

## lunar

```TypeScript
lunar(isLunar: Optional<boolean>)
```

设置日期是否显示为农历。与[lunar](#lunar)相比， isLunar参数新增了对undefined类型的支持。

> **说明：**
> 
> 仅在简体中文和繁体中文语言环境下生效，其他语言环境下设置该属性无效果。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isLunar | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 日期是否显示为农历。    - true：显示为农历。    - false：不显示为农历。    默认值：false 当isLunar的值为undefined时，使用默认值。 |

## onChange

```TypeScript
onChange(callback: (value: DatePickerResult) => void)
```

滑动DatePicker文本内容后，选项完全归位至选中项位置时，触发该回调。不能通过双向绑定的状态变量触发。从API version 8开始支持，从API version 10开始废弃，建议使用 [onDateChange](#ondatechange)替代。

**起始版本：** 8

**废弃版本：** 10

**替代接口：** [onDateChange](#ondatechange)(callback: Callback&lt;Date&gt;)

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (value: DatePickerResult) = & gt; void | 是 | 返回选中的时间，包含年、月、日字段。 |

## onDateChange

```TypeScript
onDateChange(callback: Callback<Date>)
```

滑动DatePicker文本内容后，选项完全归位至选中项位置时，触发该回调。归位是指滚动动画结束、选项稳定停靠在选中位置。不 能通过双向绑定的状态变量触发，可以响应用户的滑动操作。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback & lt;Date & gt; | 是 | 返回选中的时间，年、月、日为选中的日期，时、分取决于当前系统时间的时、分，秒恒为00。 适用于需要在用户确认日期选择后获取选中日期、更新界面或执行业务逻辑的场景。<br>**起始版本：** 18 |

## onDateChange

```TypeScript
onDateChange(callback: Optional<Callback<Date>>)
```

滑动DatePicker文本内容后，选项完全归位至选中项位置时，触发该回调。不能通过双向绑定的状态变量触发。与 [onDateChange&lt;sup&gt;10+&lt;/sup&gt;](#ondatechange)相比， callback参数新增了对undefined类型的支持。

> **说明：**
> 
> 从API version 20开始，该接口支持在attributeModifier中调用。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Optional](arkts-arkui-optional-t.md)&lt;Callback&lt;Date&gt;&gt; | 是 | 返回选中的时间，年、月、日为选中的日期，时、分取决于当前系统时间的时、分，秒恒为00。 适用于需要在用户确认日期选择后获取选中日期、更新界面或执行业务逻辑的场景。 当callback的值为undefined时，不使用回调函数。 |

## selectedTextStyle

```TypeScript
selectedTextStyle(value: PickerTextStyle)
```

设置选中项的文本样式。

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

设置选中项的文本样式。 与[selectedTextStyle&lt;sup&gt;10+&lt;/sup&gt;](#selectedtextstyle)相比， style参数新增了对undefined类型的支持。

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

设置待选项（以选中项为基准向上或向下的第一项）的文本样式。

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

设置待选项（以选中项为基准向上或向下的第一项）的文本样式。与 [textStyle&lt;sup&gt;10+&lt;/sup&gt;](#textstyle)相比， style参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-optional-t.md)&lt;[PickerTextStyle](arkts-arkui-pickertextstyle-i.md)&gt; | 是 | 待选项的文本颜色、字号、字体粗细。 默认值： {color: '#ff182431', font: {size: '16fp', weight: FontWeight.Regular } } 当style的值为undefined时，使用默认值。 |
