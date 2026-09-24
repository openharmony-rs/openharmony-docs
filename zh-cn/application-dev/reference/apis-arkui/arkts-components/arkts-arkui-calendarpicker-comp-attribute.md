# CalendarPicker属性/事件

```TypeScript
declare class CalendarPickerAttribute extends CommonMethod<CalendarPickerAttribute>
```

除支持[通用属性](arkts-arkui-common-comp.md#common)外，还支持以下属性：

除支持[通用事件](arkts-arkui-common-comp.md#common)，还支持以下事件：

**继承/实现关系：** CalendarPickerAttribute extends CommonMethod<CalendarPickerAttribute>

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## edgeAlign

```TypeScript
edgeAlign(alignType: CalendarAlign, offset?: Offset)
```

设置选择器与入口组件的对齐方式。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| alignType | [CalendarAlign](arkts-arkui-calendarpicker-comp-calendaralign-e.md) | 是 | 对齐方式的类型。<br>默认值：CalendarAlign.END |
| offset | Offset | 否 | 按照对齐方式对齐后，选择器相对入口组件的偏移量。<br>默认值：{dx: 0, dy: 0} <br>单位：vp |

<a id="edgealign-1"></a>

## edgeAlign

```TypeScript
edgeAlign(alignType: Optional<CalendarAlign>, offset?: Offset)
```

设置选择器与入口组件的对齐方式。与[edgeAlign](#edgealign)相比，alignType参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| alignType | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[CalendarAlign](arkts-arkui-calendarpicker-comp-calendaralign-e.md)&gt; | 是 | 对齐方式的类型。<br>默认值：CalendarAlign.END <br>当alignType的值为undefined时，使用默认值。 |
| offset | Offset | 否 | 按照对齐方式对齐后，选择器相对入口组件的偏移量。<br>默认值：{dx: 0, dy: 0} <br>单位：vp |

## markToday

```TypeScript
markToday(enabled: boolean)
```

设置日历选择器中系统当前日期是否保持高亮显示。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | 设置日历选择器中系统当前日期是否保持高亮显示。<br>- true：系统当前日期在日历选择器内保持高亮显示。<br>- false：系统当前日期在日历选择器内不保持高亮显示。<br>默认值：false |

## onChange

```TypeScript
onChange(callback: Callback<Date>)
```

选择日期时触发该事件。不能通过双向绑定的状态变量触发。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;Date&gt; | 是 | 日期选择时触发的回调函数。回调参数为Date类型的选中日期值，开发者可在回调函数中获取用户选中的日期并进行相应处理。<br>**适用版本：** 18 |

<a id="onchange-1"></a>

## onChange

```TypeScript
onChange(callback: Optional<Callback<Date>>)
```

选择日期时触发该事件。不能通过双向绑定的状态变量触发。与[onChange](#onchange)相比，callback参数新增了对undefined类型的支持。

> **说明：** 
> 
> 从API version 20开始，该接口支持在[attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier)中调用。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;Callback&lt;Date&gt;&gt; | 是 | 日期选择时触发的回调函数，回调参数为选中的日期值。<br>当callback的值为undefined时，不使用回调函数。 |

## textStyle

```TypeScript
textStyle(value: PickerTextStyle)
```

设置入口区的文本颜色、字号、字体粗细。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [PickerTextStyle](arkts-arkui-common-comp-pickertextstyle-i.md) | 是 | 设置入口区的文本颜色、字号、字体粗细。<br>默认值：<br>{<br>color: '#ff182431', <br>font: {<br>size: '16fp', <br>weight: FontWeight.Regular <br>} <br>} |

<a id="textstyle-1"></a>

## textStyle

```TypeScript
textStyle(style: Optional<PickerTextStyle>)
```

设置入口区的文本颜色、字号、字体粗细。与[textStyle](#textstyle)相比，style参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[PickerTextStyle](arkts-arkui-common-comp-pickertextstyle-i.md)&gt; | 是 | 设置入口区的文本颜色、字号、字体粗细。<br>默认值：<br>{<br>color: '#ff182431', <br>font: {<br>size: '16fp', <br>weight: FontWeight.Regular <br>} <br>} <br>当style的值为undefined时，使用默认值。 |
