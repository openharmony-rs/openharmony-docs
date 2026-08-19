# CalendarOptions

日历选择器组件的参数说明。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface CalendarOptions--><!--Device-unnamed-export declare interface CalendarOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## disabledDateRange

```TypeScript
disabledDateRange?: DateRange[]
```

设置禁用日期区间。 **说明：** 1. 若日期区间内的开始日期或结束日期未设置或设置为异常值，则该日期区间无效。 2. 若在日期区间内，结束日期早于开始日期，则该日期区间无效。 3. 当在入口区选定某日期，通过上下箭头调整日期进行增加或减少操作时，若遇到禁用日期，系统将自动跳过整个禁用区间。

**类型：** [DateRange](../../apis-arkui/arkts-components/arkts-arkui-daterange-i.md)[]

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CalendarOptions-disabledDateRange?: DateRange[]--><!--Device-CalendarOptions-disabledDateRange?: DateRange[]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## end

```TypeScript
end?: Date
```

设置结束日期。 默认值：Date('5000-12-31') 取值范围：[Date('0001-01-01'), Date('5000-12-31')]

**类型：** Date

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CalendarOptions-end?: Date--><!--Device-CalendarOptions-end?: Date-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## hintRadius

```TypeScript
hintRadius?: double | Resource
```

描述日期选中态底板样式。 取值范围：[0.0, 16.0] 单位：vp 默认值：16.0，即底板样式为圆形。 **说明：** 当hintRadius为0.0时表示底板样式为直角矩形；当hintRadius为(0.0, 16.0)时，底板样式为圆角矩形；当hintRadius为负数或大于16.0时，恢复为默认值16.0。

**类型：** double \| [Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-resource-i.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CalendarOptions-hintRadius?: double | Resource--><!--Device-CalendarOptions-hintRadius?: double | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selected

```TypeScript
selected?: Date
```

设置选中项的日期。选中的日期未设置或日期格式不符合规范则为默认值。 默认值：当前系统日期。 取值范围：[Date('0001-01-01'), Date('5000-12-31')]

**类型：** Date

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CalendarOptions-selected?: Date--><!--Device-CalendarOptions-selected?: Date-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## start

```TypeScript
start?: Date
```

设置开始日期。 默认值：Date('0001-01-01') 取值范围：[Date('0001-01-01'), Date('5000-12-31')]

**类型：** Date

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CalendarOptions-start?: Date--><!--Device-CalendarOptions-start?: Date-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

