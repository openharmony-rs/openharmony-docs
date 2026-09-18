# CalendarConfig

Describes the calendar configuration information.

**Since:** 10

**System capability:** SystemCapability.Applications.CalendarData

## Modules to Import

```TypeScript
import { calendarManager } from '@kit.CalendarKit';
```

## color

```TypeScript
color?: number | string
```

Calendar color. If the value is a number, the value ranges from 0x000001 to 0xFFFFFF or from 0x00000001 to 0xFFFFFFFF. If the value is a string, the value contains 7 or 9 characters, for example, **#FFFFFF** or **#FFFFFFFF**. If this parameter is not set, the default value **0xFF0A59F7** is used.

**Type:** number &#124; string

**Since:** 10

**System capability:** SystemCapability.Applications.CalendarData

## enableReminder

```TypeScript
enableReminder?: boolean
```

Whether to enable the reminder for events in the calendar. The value **true** means to enable the reminder for events in the calendar, and **false** means the opposite. The default value is **true**.

**Type:** boolean

**Since:** 10

**System capability:** SystemCapability.Applications.CalendarData
