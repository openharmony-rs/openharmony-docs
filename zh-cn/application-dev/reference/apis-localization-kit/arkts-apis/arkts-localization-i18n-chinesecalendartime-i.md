# ChineseCalendarTime

农历时间对象。

**起始版本：** 26.0.0

<!--Device-i18n-export interface ChineseCalendarTime--><!--Device-i18n-export interface ChineseCalendarTime-End-->

**系统能力：** SystemCapability.Global.I18n

## 导入模块

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## cyclicalYear

```TypeScript
cyclicalYear: number
```

农历的干支年。

取值范围：[1, 60]。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChineseCalendarTime-cyclicalYear: int--><!--Device-ChineseCalendarTime-cyclicalYear: int-End-->

**系统能力：** SystemCapability.Global.I18n

## date

```TypeScript
date: number
```

农历的日。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChineseCalendarTime-date: int--><!--Device-ChineseCalendarTime-date: int-End-->

**系统能力：** SystemCapability.Global.I18n

## gregorianYear

```TypeScript
gregorianYear: number
```

公历的年。

取值范围：[1900, 2100]。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChineseCalendarTime-gregorianYear: int--><!--Device-ChineseCalendarTime-gregorianYear: int-End-->

**系统能力：** SystemCapability.Global.I18n

## hour

```TypeScript
hour?: number
```

农历的时。默认值：0。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChineseCalendarTime-hour?: int--><!--Device-ChineseCalendarTime-hour?: int-End-->

**系统能力：** SystemCapability.Global.I18n

## isLeapMonth

```TypeScript
isLeapMonth?: boolean
```

是否是闰月。默认值：false。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChineseCalendarTime-isLeapMonth?: boolean--><!--Device-ChineseCalendarTime-isLeapMonth?: boolean-End-->

**系统能力：** SystemCapability.Global.I18n

## minute

```TypeScript
minute?: number
```

农历的分。默认值：0。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChineseCalendarTime-minute?: int--><!--Device-ChineseCalendarTime-minute?: int-End-->

**系统能力：** SystemCapability.Global.I18n

## month

```TypeScript
month: number
```

农历的月。

**说明：**

月份从0开始计数，0表示一月。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChineseCalendarTime-month: int--><!--Device-ChineseCalendarTime-month: int-End-->

**系统能力：** SystemCapability.Global.I18n

## second

```TypeScript
second?: number
```

农历的秒。默认值：0。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChineseCalendarTime-second?: int--><!--Device-ChineseCalendarTime-second?: int-End-->

**系统能力：** SystemCapability.Global.I18n

