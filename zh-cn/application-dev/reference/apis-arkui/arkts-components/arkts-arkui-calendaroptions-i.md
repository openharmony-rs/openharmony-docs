# CalendarOptions

日历选择器组件的参数说明。

## start和end设置规则 > 日期异常场景说明： > - start日期晚于end日期：start日期、end日期都设置无效，选中日期为默认值 > - 选中日期早于start日期：选中日期为start日期 > - 选中日期晚于end日期：选中日期为end日期 > - start日期晚于当前系统日期，选中日期未设置：选中日期为start日期 > - end日期早于当前系统日期，选中日期未设置：选中日期为end日期 > - 日期格式不符合规范，如`1999-13-32`：start日期或end日期设置无效，选中日期取默认值

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

<!--Device-unnamed-declare interface CalendarOptions--><!--Device-unnamed-declare interface CalendarOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## disabledDateRange

```TypeScript
disabledDateRange?: DateRange[]
```

设置禁用日期区间。不传此参数时不禁用任何日期。 > **说明：** > > 1. 若日期区间内的开始日期或结束日期未设置或设置为异常值，则该日期区间无效。 > 2. 若在日期区间内，结束日期早于开始日期，则该日期区间无效。 > 3. 当在入口区选定某日期，通过上下箭头调整日期进行增加或减少操作时，若遇到禁用日期，系统将自动跳过整个禁用区间。

**类型：** DateRange[]

**起始版本：** 19

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为19。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-CalendarOptions-disabledDateRange?: DateRange[]--><!--Device-CalendarOptions-disabledDateRange?: DateRange[]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## end

```TypeScript
end?: Date
```

设置结束日期。 > 默认值：Date('5000-12-31') > 取值范围：[Date('0001-01-01'), Date('5000-12-31')] > **说明：** 若start日期晚于end日期，则start日期、end日期都设置无效，选中日期为默认值。 > 详见[start和end设置规则](#CalendarOptions)。

**类型：** Date

**默认值：** Date('5000-12-31')

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CalendarOptions-end?: Date--><!--Device-CalendarOptions-end?: Date-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## hintRadius

```TypeScript
hintRadius?: number | Resource
```

设置日期选中态底板样式。 > 取值范围：[0.0, 16.0] > 单位：vp > 默认值：16.0，即底板样式为圆形。 > **说明：** > > 当hintRadius为0.0时表示底板样式为直角矩形；当hintRadius为(0.0, 16.0)时，底板样式为圆角矩形；当hintRadius为16.0时， > 底板样式为圆形；当hintRadius为负数或大于16.0时，恢复为默认值16.0。

**类型：** number \| Resource

**默认值：** 16.0

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CalendarOptions-hintRadius?: number | Resource--><!--Device-CalendarOptions-hintRadius?: number | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selected

```TypeScript
selected?: Date
```

设置选中项的日期。当需要预设选中日期时传入此参数，不需要预设时使用当前系统日期。选中的日期未设置或日期格式不符合规范则为默认值。选中日期与 start、end参数的配合关系见[start和end设置规则](#CalendarOptions)。 > 默认值：当前系统日期。 > 取值范围：[Date('0001-01-01'), Date('5000-12-31')]

**类型：** Date

**默认值：** current system date

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CalendarOptions-selected?: Date--><!--Device-CalendarOptions-selected?: Date-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## start

```TypeScript
start?: Date
```

设置开始日期。 > 默认值：Date('0001-01-01') > 取值范围：[Date('0001-01-01'), Date('5000-12-31')] > **说明：** 若start日期晚于end日期，则start日期、end日期都设置无效，选中日期为默认值。 > 详见[start和end设置规则](#CalendarOptions)。

**类型：** Date

**默认值：** Date('0001-01-01')

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CalendarOptions-start?: Date--><!--Device-CalendarOptions-start?: Date-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

