# CalendarPicker
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @luoying_ace_admin-->
<!--Designer: @weixin_52725220-->
<!--Tester: @xiong0104-->
<!--Adviser: @HelloCrease-->

日历选择器组件，提供下拉日历弹窗，可以让用户选择日期。

>  **说明：**
>
> 该组件从API version 10开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。

## 子组件

无

## 接口

CalendarPicker(options?: CalendarOptions)

日历选择器。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**设备行为差异：** 该接口在Wearable设备上使用时，应用程序运行异常，异常信息中提示接口未定义，在其他设备中可正常调用。

**参数：** 

| 参数名  | 类型                                        | 必填 | 说明                       |
| ------- | ------------------------------------------- | ---- | -------------------------- |
| options | [CalendarOptions](#calendaroptions对象说明) | 否   | 配置日历选择器组件的参数。 |

## 属性

除支持[通用属性](ts-component-general-attributes.md)外，还支持以下属性：

### edgeAlign

edgeAlign(alignType: CalendarAlign, offset?: Offset)

设置选择器与入口组件的对齐方式。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**设备行为差异：** 该接口在Wearable设备上使用时，应用程序运行异常，异常信息中提示接口未定义，在其他设备中可正常调用。

**参数：** 

| 参数名    | 类型                                    | 必填 | 说明                                                         |
| --------- | --------------------------------------- | ---- | ------------------------------------------------------------ |
| alignType | [CalendarAlign](#calendaralign枚举说明) | 是   | 对齐方式的类型。<br/>默认值：CalendarAlign.END                 |
| offset    | [Offset](ts-types.md#offset)            | 否   | 按照对齐方式对齐后，选择器相对入口组件的偏移量。<br/>默认值：{dx: 0, dy: 0} |

### edgeAlign<sup>18+</sup>

edgeAlign(alignType: Optional\<CalendarAlign>, offset?: Offset)

设置选择器与入口组件的对齐方式。与[edgeAlign](#edgealign)相比，alignType参数新增了对undefined类型的支持。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**设备行为差异：** 该接口在Wearable设备上使用时，应用程序运行异常，异常信息中提示接口未定义，在其他设备中可正常调用。

**参数：** 

| 参数名    | 类型                                                         | 必填 | 说明                                                         |
| --------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| alignType | [Optional](ts-universal-attributes-custom-property.md#optionalt12)\<[CalendarAlign](#calendaralign枚举说明)> | 是   | 对齐方式的类型。<br/>默认值：CalendarAlign.END<br/>当alignType的值为undefined时，使用默认值。 |
| offset    | [Offset](ts-types.md#offset)                                 | 否   | 按照对齐方式对齐后，选择器相对入口组件的偏移量。<br/>默认值：{dx: 0, dy: 0} |

### textStyle

textStyle(value: PickerTextStyle)

入口区的文本颜色、字号、字体粗细。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**设备行为差异：** 该接口在Wearable设备上使用时，应用程序运行异常，异常信息中提示接口未定义，在其他设备中可正常调用。

**参数：** 

| 参数名 | 类型                                                         | 必填 | 说明                                                         |
| ------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| value  | [PickerTextStyle](ts-picker-common.md#pickertextstyle对象说明) | 是   | 设置入口区的文本颜色、字号、字体粗细。<br/>默认值：<br/>{<br/>color: '#ff182431',<br/>font: {<br/>size: '16fp', <br/>weight: FontWeight.Regular<br/>}<br/>} |

### textStyle<sup>18+</sup>

textStyle(style: Optional\<PickerTextStyle>)

入口区的文本颜色、字号、字体粗细。与[textStyle](#textstyle)相比，style参数新增了对undefined类型的支持。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**设备行为差异：** 该接口在Wearable设备上使用时，应用程序运行异常，异常信息中提示接口未定义，在其他设备中可正常调用。

**参数：** 

| 参数名 | 类型                                                         | 必填 | 说明                                                         |
| ------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| style  | [Optional](ts-universal-attributes-custom-property.md#optionalt12)\<[PickerTextStyle](ts-picker-common.md#pickertextstyle对象说明)> | 是   | 设置入口区的文本颜色、字号、字体粗细。<br/>默认值：<br/>{<br/>color: '#ff182431',<br/>font: {<br/>size: '16fp', <br/>weight: FontWeight.Regular<br/>}<br/>}<br/>当style的值为undefined时，使用默认值。 |

### markToday<sup>19+</sup>

markToday(enabled: boolean)

设置日历选择器中系统当前日期是否保持高亮显示。

**原子化服务API：** 从API version 19开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**设备行为差异：** 该接口在Wearable设备上使用时，应用程序运行异常，异常信息中提示接口未定义，在其他设备中可正常调用。

**参数：** 

| 参数名 | 类型                                                         | 必填 | 说明                                                         |
| ------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| enabled  | boolean | 是   | 设置日历选择器中系统当前日期是否保持高亮显示。<br/>- true：系统当前日期在日历选择器内保持高亮显示。<br/>- false：系统当前日期在日历选择器内不保持高亮显示。<br/>默认值：false |

## 事件

除支持[通用事件](ts-component-general-events.md)，还支持以下事件：

### onChange

onChange(callback: Callback\<Date>)

选择日期时触发该事件。不能通过双向绑定的状态变量触发。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**设备行为差异：** 该接口在Wearable设备上使用时，应用程序运行异常，异常信息中提示接口未定义，在其他设备中可正常调用。

**参数：** 

| 参数名 | 类型 | 必填 | 说明           |
| ------ | ---- | ---- | -------------- |
| callback | [Callback](ts-types.md#callback12)\<Date> | 是   | 选中的日期值。 |

### onChange<sup>18+</sup>

onChange(callback: Optional\<Callback\<Date>>)

选择日期时触发该事件。不能通过双向绑定的状态变量触发。与[onChange](#onchange)相比，callback参数新增了对undefined类型的支持。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**设备行为差异：** 该接口在Wearable设备上使用时，应用程序运行异常，异常信息中提示接口未定义，在其他设备中可正常调用。

**参数：** 

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| callback | [Optional](ts-universal-attributes-custom-property.md#optionalt12)\<[Callback](ts-types.md#callback12)\<Date>> | 是   | 选中的日期值。<br>当callback的值为undefined时，不使用回调函数。 |

##  CalendarOptions对象说明

日历选择器组件的参数说明。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**设备行为差异：** 该接口在Wearable设备上使用时，应用程序运行异常，异常信息中提示接口未定义，在其他设备中可正常调用。

| 名称      | 类型       | 只读 | 可选        | 说明                            |
| ----------- | ---------- | ------| --------------------------------- | --------------------------------- |
| hintRadius | number \| [Resource](ts-types.md#resource) | 否   | 是    | 描述日期选中态底板样式。<br />取值范围：[0.0, 16.0]<br />单位：vp<br/>默认值：16.0，即底板样式为圆形。<br />**说明：**<br />当hintRadius为0.0时表示底板样式为直角矩形；当hintRadius为(0.0, 16.0)时，底板样式为圆角矩形；当hintRadius为负数或大于16.0时，恢复成默认值16.0。<br />**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。 |
| selected | Date | 否   | 是    | 设置选中项的日期。选中的日期未设置或日期格式不符合规范则为默认值。<br/>默认值：当前系统日期。<br/>取值范围：\[Date('0001-01-01'), Date('5000-12-31')]<br />**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。 |
| start<sup>18+</sup> | Date | 否   | 是    | 设置开始日期。<br/>默认值：Date('0001-01-01')<br/>取值范围：\[Date('0001-01-01'), Date('5000-12-31')]<br />**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。 |
| end<sup>18+</sup> | Date | 否   | 是    | 设置结束日期。<br/>默认值：Date('5000-12-31')<br/>取值范围：\[Date('0001-01-01'), Date('5000-12-31')]<br />**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。 |
| disabledDateRange<sup>19+</sup> | [DateRange](ts-picker-common.md#daterange19对象说明)[] | 否   | 是    | 设置禁用日期区间。<br/>**说明：**<br />1. 若日期区间内的开始日期或结束日期未设置或设置为异常值，则该日期区间无效。<br/>2. 若在日期区间内，结束日期早于开始日期，则该日期区间无效。<br/>3. 当在入口区选定某日期，通过上下箭头调整日期进行增加或减少操作时，若遇到禁用日期，系统将自动跳过整个禁用区间。<br/>**原子化服务API：** 从API version 19开始，该接口支持在原子化服务中使用。 |

**start和end设置规则：**

| 场景   | 说明  |
| -------- |  ------------------------------------------------------------ |
| start日期晚于end日期    | start日期、end日期都设置无效，选中日期为默认值  |
| 选中日期早于start日期    | 选中日期为start日期  |
| 选中日期晚于end日期    | 选中日期为end日期  |
| start日期晚于当前系统日期，选中日期未设置    | 选中日期为start日期  |
| end日期早于当前系统日期，选中日期未设置    | 选中日期为end日期  |
| 日期格式不符合规范，如‘1999-13-32’ | start日期或end日期设置无效，选中日期取默认值  |

## CalendarAlign枚举说明

对齐方式类型。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**设备行为差异：** 该接口在Wearable设备上使用时，应用程序运行异常，异常信息中提示接口未定义，在其他设备中可正常调用。

| 名称   | 值 | 说明                     |
| ------ | - | ------------------------ |
| START  | 0 | 设置选择器与入口组件的对齐方式为左对齐。   |
| CENTER | 1 | 设置选择器与入口组件的对齐方式为居中对齐。 |
| END    | 2 | 设置选择器与入口组件的对齐方式为右对齐。   |

## 示例
### 示例1（设置下拉日历弹窗）

该示例实现了日历选择器组件，提供下拉日历弹窗。

```ts
// xxx.ets
@Entry
@Component
struct CalendarPickerExample {
  private selectedDate: Date = new Date('2024-03-05');

  build() {
    Column() {
      Column() {
        CalendarPicker({ hintRadius: 10, selected: this.selectedDate })
          .edgeAlign(CalendarAlign.END)
          .textStyle({ color: "#ff182431", font: { size: 20, weight: FontWeight.Normal } })
          .margin(10)
          .onChange((value) => {
            console.info(`CalendarPicker onChange: ${value.toString()}`);
          })
      }.alignItems(HorizontalAlign.End).width("100%")

      Text('日历日期选择器').fontSize(30)
    }.width('100%').margin({ top: 350 })
  }
}
```

![CalendarPicker](figures/CalendarPicker.gif)

### 示例2（设置开始日期和结束日期）

该示例通过start和end设置日历选择器的开始日期和结束日期。

```ts
// xxx.ets
@Entry
@Component
struct CalendarPickerExample {
  private selectedDate: Date = new Date('2025-01-15');
  private startDate: Date = new Date('2025-01-05');
  private endDate: Date = new Date('2025-01-25');

  build() {
    Column() {
      Column() {
        CalendarPicker({ hintRadius: 10, selected: this.selectedDate, start: this.startDate, end: this.endDate })
          .edgeAlign(CalendarAlign.END)
          .textStyle({ color: "#ff182431", font: { size: 20, weight: FontWeight.Normal } })
          .margin(10)
          .onChange((value) => {
            console.info(`CalendarPicker onChange: ${value.toString()}`);
          })
      }.alignItems(HorizontalAlign.End).width("100%")
    }.width('100%').margin({ top: 350 })
  }
}
```

![CalendarPicker](figures/calendar_picker_start_end.jpg)

### 示例3（设置日历选择器在系统当前日期时，保持高亮显示和禁用日期区间）

该示例通过[markToday](#marktoday19)设置日历选择器在系统当前日期时，开启保持高亮显示，同时，通过[disabledDateRange](#calendaroptions对象说明)设置日历选择器的禁用日期区间。

```ts
// xxx.ets
@Entry
@Component
struct CalendarPickerExample {
  private disabledDateRange: DateRange[] = [
    { start: new Date('2025-01-01'), end: new Date('2025-01-02') },
    { start: new Date('2025-01-09'), end: new Date('2025-01-10') },
    { start: new Date('2025-01-15'), end: new Date('2025-01-16') },
    { start: new Date('2025-01-19'), end: new Date('2025-01-19') },
    { start: new Date('2025-01-22'), end: new Date('2025-01-25') }
  ];

  build() {
    Column() {
      CalendarPicker({ disabledDateRange: this.disabledDateRange })
        .margin(10)
        .markToday(true)
        .onChange((value) => {
          console.info(`CalendarPicker onChange: ${value.toString()}`);
        })
    }.alignItems(HorizontalAlign.End).width('100%')
  }
}
```

![CalendarPicker](figures/calendar_picker_mark_disabled.gif)
