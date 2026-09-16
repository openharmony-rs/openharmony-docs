# TimePicker

TimePicker是用于滑动选择时间的组件，支持12/24小时制、多种时间格式（小时/分钟/秒）、循环滚动、样式定制和时间范围限制等功能。适用于日程安排、时间预约、任务管理等需要用户选择时间的场景，能够提升用户体验，减少输入错误，并可快速集成到应用中。

> **说明：** > > - 该组件从API version 8开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。 > > - 该组件不建议开发者在动效过程中修改属性数据。 > > - 最大显示行数在横、竖屏模式下存在差异。竖屏时默认为5行，横屏时依赖系统配置，未配置时默认显示为3行。 > 可通过如下参数查看具体配置值$r('sys.float.ohos_id_picker_show_count_landscape')。

>

## 子组件 > > 该组件为基础组件，不建议包含子组件。

## TimePicker

```TypeScript
TimePicker(options?: TimePickerOptions)
```

创建滑动选择器，默认使用24小时的时间区间。适用于日程安排、闹钟设置、时间记录等需要选择时间的场景。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [TimePickerOptions](arkts-arkui-timepickeroptions-i.md) | 否 | 配置时间选择组件的参数。当需要自定义初始选中时间、时间格式、时间范围等配置时传入此参数，不传入时使用默认配置（初始选中时间为当前系统时间，时间格式默认为小时和分钟，时间范围默认为00:00-23:59（默认结束时间为23:59:59））。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [TimePickerDialogOptions](arkts-arkui-timepickerdialogoptions-i.md) | 时间选择器弹窗选项。 |
| [TimePickerOptions](arkts-arkui-timepickeroptions-i.md) | 时间选择器组件的参数说明。 |
| [TimePickerResult](arkts-arkui-timepickerresult-i.md) | 返回选中的时间结果，hour取值0-23，与展示制式无关。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [DateTimeOptions](arkts-arkui-datetimeoptions-t.md) | 时间、日期格式化时可设置的配置项。 |
| [OnTimePickerChangeCallback](arkts-arkui-ontimepickerchangecallback-t.md) | 选择时间时触发该事件。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [TimePickerFormat](arkts-arkui-timepickerformat-e.md) | 时间选择器的数据格式。 |

## 示例

```TypeScript
### 示例1（设置文本样式）

该示例通过配置[disappearTextStyle](#disappeartextstyle10)、[textStyle](#textstyle10)和[selectedTextStyle](#selectedtextstyle10)实现文本选择器中的文本样式。


```

```TypeScript
### 示例2（切换小时制）

该示例通过配置useMilitaryTime实现12小时制、24小时制的切换。


```

```TypeScript
### 示例3（设置时间格式）

该示例使用format和dateTimeOptions设置TimePicker时间格式。


```

```TypeScript
### 示例4（设置循环滚动）

该示例通过配置[loop](#loop11)设置TimePicker是否循环滚动。


```

```TypeScript
### 示例5（设置时间选择组件的起始时间）

该示例设置TimePicker的起始时间。


```

```TypeScript
### 示例6（设置时间选择组件的结束时间）

该示例设置TimePicker的结束时间。


```

```TypeScript
### 示例7（设置上午/下午跟随时间联动）

该示例通过配置[enableCascade](#enablecascade18)、[loop](#loop11)实现12小时制时上午/下午跟随时间联动。

从API version 18开始，新增enableCascade接口。
```
