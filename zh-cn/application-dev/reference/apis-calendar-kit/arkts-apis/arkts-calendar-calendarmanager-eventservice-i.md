# EventService

日程服务。

**起始版本：** 10

<!--Device-calendarManager-export interface EventService--><!--Device-calendarManager-export interface EventService-End-->

**系统能力：** SystemCapability.Applications.CalendarData

## 导入模块

```TypeScript
import { calendarManager } from '@kit.CalendarKit';
```

## description

```TypeScript
description?: string
```

服务辅助描述。长度建议为[0,5000]字符，不填时，默认为空字符串。

**类型：** string

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-EventService-description?: string--><!--Device-EventService-description?: string-End-->

**系统能力：** SystemCapability.Applications.CalendarData

## type

```TypeScript
type: ServiceType
```

服务类型。

**类型：** ServiceType

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-EventService-type: ServiceType--><!--Device-EventService-type: ServiceType-End-->

**系统能力：** SystemCapability.Applications.CalendarData

## uri

```TypeScript
uri: string
```

服务的uri，格式为DeepLink类型。可以跳转到三方应用相应界面。长度建议为[0,5000]字符。

**类型：** string

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-EventService-uri: string--><!--Device-EventService-uri: string-End-->

**系统能力：** SystemCapability.Applications.CalendarData

