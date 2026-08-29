# CalendarPicker属性/事件

除支持通用属性外，还支持以下属性：除支持通用事件，还支持以下事件：

**继承/实现关系：** CalendarPickerAttribute extends CommonMethod<CalendarPickerAttribute>

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## edgeAlign

```TypeScript
edgeAlign(alignType: CalendarAlign, offset?: Offset)
```

设置选择器与入口组件的对齐方式。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| alignType | [CalendarAlign](arkts-arkui-calendaralign-e.md) | 是 | 对齐方式的类型。 默认值：CalendarAlign.END |
| offset | Offset | 否 | 按照对齐方式对齐后，选择器相对入口组件的偏移量。 默认值：{dx: 0, dy: 0} 单位：vp |

## edgeAlign

```TypeScript
edgeAlign(alignType: Optional<CalendarAlign>, offset?: Offset)
```

设置选择器与入口组件的对齐方式。 与[edgeAlign](#edgealign)相比， alignType参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| alignType | [Optional](arkts-arkui-optional-t.md)&lt;[CalendarAlign](arkts-arkui-calendaralign-e.md)&gt; | 是 | 对齐方式的类型。 默认值：CalendarAlign.END 当alignType的值为undefined时，使用默认值。 |
| offset | Offset | 否 | 按照对齐方式对齐后，选择器相对入口组件的偏移量。 默认值：{dx: 0, dy: 0} 单位：vp |

## markToday

```TypeScript
markToday(enabled: boolean)
```

设置日历选择器中系统当前日期是否保持高亮显示。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | 设置日历选择器中系统当前日期是否保持高亮显示。    - true：系统当前日期在日历选择器内保持高亮显示。    - false：系统当前日期在日历选择器内不保持高亮显示。    默认值：false |

## onChange

```TypeScript
onChange(callback: Callback<Date>)
```

选择日期时触发该事件。不能通过双向绑定的状态变量触发。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback &lt;Date&gt; | 是 | 日期选择时触发的回调函数。回调参数为Date类型的选中日期值，开发者可在回调函数中获取用户选中的日 期并进行相应处理。<br>**起始版本：** 18 |

## onChange

```TypeScript
onChange(callback: Optional<Callback<Date>>)
```

选择日期时触发该事件。不能通过双向绑定的状态变量触发。 与[onChange](#onchange)相比，callback参数新增了对undefined类型的 支持。

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
| callback | [Optional](arkts-arkui-optional-t.md)&lt;Callback&lt;Date&gt;&gt; | 是 | 日期选择时触发的回调函数，回调参数为选中的日期值。 当callback的值为undefined时，不使用回调函数。 |

## textStyle

```TypeScript
textStyle(value: PickerTextStyle)
```

设置入口区的文本颜色、字号、字体粗细。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [PickerTextStyle](arkts-arkui-pickertextstyle-i.md) | 是 | 设置入口区的文本颜色、字号、字体粗细。 默认值： {color: '#ff182431', font: {size: '16fp', weight: FontWeight.Regular } } |

## textStyle

```TypeScript
textStyle(style: Optional<PickerTextStyle>)
```

设置入口区的文本颜色、字号、字体粗细。与[textStyle](#textstyle)相比， style参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-optional-t.md)&lt;[PickerTextStyle](arkts-arkui-pickertextstyle-i.md)&gt; | 是 | 设置入口区的文本颜色、字号、字体粗细。 默认值： {color: '#ff182431', font: {size: '16fp', weight: FontWeight.Regular } } 当style的值为undefined时，使用默认值。 |
