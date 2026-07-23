# CalendarPicker属性/事件

除支持[通用属性](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持以下属性：

除支持[通用事件](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)，还支持以下事件：

**继承/实现关系：** CalendarPickerAttribute extends [CommonMethod<CalendarPickerAttribute>]

**起始版本：** 10

<!--Device-unnamed-declare class CalendarPickerAttribute extends CommonMethod<CalendarPickerAttribute>--><!--Device-unnamed-declare class CalendarPickerAttribute extends CommonMethod<CalendarPickerAttribute>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## edgeAlign

```TypeScript
edgeAlign(alignType: CalendarAlign, offset?: Offset)
```

设置选择器与入口组件的对齐方式。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CalendarPickerAttribute-edgeAlign(alignType: CalendarAlign, offset?: Offset): CalendarPickerAttribute--><!--Device-CalendarPickerAttribute-edgeAlign(alignType: CalendarAlign, offset?: Offset): CalendarPickerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| alignType | [CalendarAlign](arkts-arkui-calendaralign-e.md) | 是 | 对齐方式的类型。<br/>默认值：CalendarAlign.END |
| offset | [Offset](../arkts-apis/arkts-arkui-componentutils-offset-i.md) | 否 | 按照对齐方式对齐后，选择器相对入口组件的偏移量。<br/>默认值：{dx: 0, dy: 0} |

## edgeAlign

```TypeScript
edgeAlign(alignType: Optional<CalendarAlign>, offset?: Offset)
```

设置选择器与入口组件的对齐方式。与[edgeAlign](CalendarPickerAttribute#edgeAlign(alignType: CalendarAlign, offset?: Offset))相比，alignType参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CalendarPickerAttribute-edgeAlign(alignType: Optional<CalendarAlign>, offset?: Offset): CalendarPickerAttribute--><!--Device-CalendarPickerAttribute-edgeAlign(alignType: Optional<CalendarAlign>, offset?: Offset): CalendarPickerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| alignType | [Optional](arkts-arkui-optional-t.md)&lt;CalendarAlign&gt; | 是 | 对齐方式的类型。默认值：CalendarAlign.END<br/>当alignType的值为undefined时，使用默认值。 |
| offset | [Offset](../arkts-apis/arkts-arkui-componentutils-offset-i.md) | 否 | 按照对齐方式对齐后，选择器相对入口组件的偏移量。<br/>默认值：{dx: 0, dy: 0} |

## markToday

```TypeScript
markToday(enabled: boolean)
```

设置日历选择器中系统当前日期是否保持高亮显示。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-CalendarPickerAttribute-markToday(enabled: boolean): CalendarPickerAttribute--><!--Device-CalendarPickerAttribute-markToday(enabled: boolean): CalendarPickerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | 设置日历选择器中系统当前日期是否保持高亮显示。   - true：系统当前日期在日历选择器内保持高亮显示。<br/>- false：系统当前日期在日历选择器内不保持高亮显示。<br/>默认值：false |

## onChange

```TypeScript
onChange(callback: Callback<Date>)
```

选择日期时触发该事件。不能通过双向绑定的状态变量触发。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CalendarPickerAttribute-onChange(callback: Callback<Date>): CalendarPickerAttribute--><!--Device-CalendarPickerAttribute-onChange(callback: Callback<Date>): CalendarPickerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Date&gt; | 是 | 选中的日期值。<br>**起始版本：** 18 |

## onChange

```TypeScript
onChange(callback: Optional<Callback<Date>>)
```

选择日期时触发该事件。不能通过双向绑定的状态变量触发。与[onChange](CalendarPickerAttribute#onChange(callback: Callback<Date>))相比，callback参数新增了对undefined类型的支持。
> **说明：**  
>  
> 从API version 20开始，该接口支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier)中调用。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CalendarPickerAttribute-onChange(callback: Optional<Callback<Date>>): CalendarPickerAttribute--><!--Device-CalendarPickerAttribute-onChange(callback: Optional<Callback<Date>>): CalendarPickerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Optional](arkts-arkui-optional-t.md)&lt;Callback&lt;Date&gt;&gt; | 是 | 选中的日期值。<br>当callback的值为undefined时，不使用回调函数。 |

## textStyle

```TypeScript
textStyle(value: PickerTextStyle)
```

入口区的文本颜色、字号、字体粗细。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CalendarPickerAttribute-textStyle(value: PickerTextStyle): CalendarPickerAttribute--><!--Device-CalendarPickerAttribute-textStyle(value: PickerTextStyle): CalendarPickerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [PickerTextStyle](arkts-arkui-pickertextstyle-i.md) | 是 | 设置入口区的文本颜色、字号、字体粗细。默认值：<br/>{<br/>color: '#ff182431',<br/>font: {<br/>size:'16fp', <br/>weight: FontWeight.Regular<br/>}<br/>} |

## textStyle

```TypeScript
textStyle(style: Optional<PickerTextStyle>)
```

入口区的文本颜色、字号、字体粗细。与[textStyle](CalendarPickerAttribute#textStyle(value: PickerTextStyle))相比，style参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CalendarPickerAttribute-textStyle(style: Optional<PickerTextStyle>): CalendarPickerAttribute--><!--Device-CalendarPickerAttribute-textStyle(style: Optional<PickerTextStyle>): CalendarPickerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-optional-t.md)&lt;PickerTextStyle&gt; | 是 | 设置入口区的文本颜色、字号、字体粗细。默认值：<br/>{<br/>color: '#ff182431',<br/>font: {<br/>size: '16fp', <br/>weight: FontWeight.Regular<br/>}<br/>}当style的值为undefined时，使用默认值。 |

