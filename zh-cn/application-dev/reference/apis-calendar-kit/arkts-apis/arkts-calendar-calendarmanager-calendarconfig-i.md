# CalendarConfig

日历配置信息。

**起始版本：** 10

<!--Device-calendarManager-interface CalendarConfig--><!--Device-calendarManager-interface CalendarConfig-End-->

**系统能力：** SystemCapability.Applications.CalendarData

## 导入模块

```TypeScript
import { calendarManager } from '@kit.CalendarKit';
```

## color

```TypeScript
color?: number | string
```

设置Calendar颜色。值为number时取值范围为0x000000至0xFFFFFF或0x00000000至0xFFFFFFFF，值为string时长度为7或9，如'#FFFFFF'，'#FFFFFFFFF'。不设置时默认值为0xFF0A59F7，输入undefined或错误值时抛异常。

**类型：** number | string

**起始版本：** 10

<!--Device-CalendarConfig-color?: number | string--><!--Device-CalendarConfig-color?: number | string-End-->

**系统能力：** SystemCapability.Applications.CalendarData

## enableReminder

```TypeScript
enableReminder?: boolean
```

是否打开Calendar下所有Event提醒能力。当取值为true时，该Calendar下所有Event具备提醒能力；当取值为false时，不具备提醒能力，默认具备提醒能力。

**类型：** boolean

**起始版本：** 10

<!--Device-CalendarConfig-enableReminder?: boolean--><!--Device-CalendarConfig-enableReminder?: boolean-End-->

**系统能力：** SystemCapability.Applications.CalendarData

