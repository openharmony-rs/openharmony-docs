# CalendarAccount

日历账户信息。

**起始版本：** 10

<!--Device-calendarManager-interface CalendarAccount--><!--Device-calendarManager-interface CalendarAccount-End-->

**系统能力：** SystemCapability.Applications.CalendarData

## 导入模块

```TypeScript
import { calendarManager } from '@kit.CalendarKit';
```

## displayName

```TypeScript
displayName?: string
```

账户显示在日历应用上的名称（面向用户）。不填时，默认为空字符串，长度限制为[0,64]字符，长度超限制会导致日历应用上账户名显示不全，被截断。

**类型：** string

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CalendarAccount-displayName?: string--><!--Device-CalendarAccount-displayName?: string-End-->

**系统能力：** SystemCapability.Applications.CalendarData

## name

```TypeScript
readonly name: string
```

账户名称（面向开发者），长度建议为[0,5000]字符。

**类型：** string

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CalendarAccount-readonly name: string--><!--Device-CalendarAccount-readonly name: string-End-->

**系统能力：** SystemCapability.Applications.CalendarData

## type

```TypeScript
type: CalendarType
```

账户类型。

**类型：** CalendarType

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CalendarAccount-type: CalendarType--><!--Device-CalendarAccount-type: CalendarType-End-->

**系统能力：** SystemCapability.Applications.CalendarData

