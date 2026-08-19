# DatePickerComponentResult

DatePickerComponentResult定义日期时间选择器的选择结果，包含用户选择的年、月、日、时、分、秒信息，用于在onChange和onScrollStop回调中 传递选择的具体日期时间值。

**起始版本：** 26.0.0

<!--Device-unnamed-export declare class DatePickerComponentResult--><!--Device-unnamed-export declare class DatePickerComponentResult-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { DatePickerComponent, DatePickerComponentOptions, DisplayMode, DateMode, TimeFormat, DatePickerComponentResult } from '@kit.ArkUI';
```

## day

```TypeScript
day?: int
```

所选日期的日。

**类型：** int

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-DatePickerComponentResult-day?: int--><!--Device-DatePickerComponentResult-day?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## hour

```TypeScript
hour?: int
```

所选时间的小时部分。

**类型：** int

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-DatePickerComponentResult-hour?: int--><!--Device-DatePickerComponentResult-hour?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## minute

```TypeScript
minute?: int
```

所选时间的分钟部分。

**类型：** int

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-DatePickerComponentResult-minute?: int--><!--Device-DatePickerComponentResult-minute?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## month

```TypeScript
month?: int
```

所选日期的月份索引，从0开始，0表示1月，11表示12月。

**类型：** int

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-DatePickerComponentResult-month?: int--><!--Device-DatePickerComponentResult-month?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## second

```TypeScript
second?: int
```

所选时间的秒部分。

**类型：** int

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-DatePickerComponentResult-second?: int--><!--Device-DatePickerComponentResult-second?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## year

```TypeScript
year?: int
```

所选日期的年份。

**类型：** int

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-DatePickerComponentResult-year?: int--><!--Device-DatePickerComponentResult-year?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

