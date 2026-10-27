# DatePickerComponentResult

```TypeScript
export declare class DatePickerComponentResult
```

DatePickerComponentResult定义日期时间选择器的选择结果，包含用户选择的年、月、日、时、分、秒信息，用于在onChange和onScrollStop回调中传递选择的具体日期时间值。

说明当[enableHideYear](arkts-arkui-arkui-advanced-datepickercomponent-dateoptions-c.md)为**true**时，如果用户选择了"----"。[year](arkts-arkui-arkui-advanced-datepickercomponent-datepickercomponentresult-c.md)不返回，如果选择了具体的年份，则[year](arkts-arkui-arkui-advanced-datepickercomponent-datepickercomponentresult-c.md)为选择的年份。在农历模式下，返回的是年月日。和day为农历值，在公历模式下，返回值为公历值。当[enableHideYear](arkts-arkui-arkui-advanced-datepickercomponent-dateoptions-c.md)为**false**时，固定年、月、日以返回公历值。

**起始版本：** 26.0.0

<!--Device-unnamed-export declare class DatePickerComponentResult--><!--Device-unnamed-export declare class DatePickerComponentResult-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { DatePickerComponent, DatePickerComponentOptions, DisplayMode, DateMode, TimeFormat, DatePickerComponentResult } from '@kit.ArkUI';
```

## day

```TypeScript
day?: number
```

所选日期的日。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

<!--Device-DatePickerComponentResult-day?: int--><!--Device-DatePickerComponentResult-day?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## hour

```TypeScript
hour?: number
```

所选时间的小时部分。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

<!--Device-DatePickerComponentResult-hour?: int--><!--Device-DatePickerComponentResult-hour?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## minute

```TypeScript
minute?: number
```

所选时间的分钟部分。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

<!--Device-DatePickerComponentResult-minute?: int--><!--Device-DatePickerComponentResult-minute?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## month

```TypeScript
month?: number
```

所选日期的月份索引，从0开始，0表示1月，11表示12月。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

<!--Device-DatePickerComponentResult-month?: int--><!--Device-DatePickerComponentResult-month?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## second

```TypeScript
second?: number
```

所选时间的秒部分。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

<!--Device-DatePickerComponentResult-second?: int--><!--Device-DatePickerComponentResult-second?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## year

```TypeScript
year?: number
```

所选日期的年份。当[enableHideYear](arkts-arkui-arkui-advanced-datepickercomponent-dateoptions-c.md)为**true**且用户选择"----"时，不返回年份；当选择了特定年份，值是选择的年份。取值限定为整数。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

<!--Device-DatePickerComponentResult-year?: int--><!--Device-DatePickerComponentResult-year?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
