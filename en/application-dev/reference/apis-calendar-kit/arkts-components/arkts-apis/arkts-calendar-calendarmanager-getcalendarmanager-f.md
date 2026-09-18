# getCalendarManager

## Modules to Import

```TypeScript
import { calendarManager } from '@kit.CalendarKit';
```

## getCalendarManager

```TypeScript
function getCalendarManager(context: Context) : CalendarManager
```

Obtains a CalendarManager object based on the context.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Applications.CalendarData

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | Yes | Application context. For details about the application context of the stage model, see Context. |

**Return value:**

| Type | Description |
| --- | --- |
| [CalendarManager](arkts-calendar-calendarmanager-calendarmanager-i.md) | CalendarManager object obtained. |

**Examples**

```TypeScript
> NOTE
> 
> For details about how to obtain an mContext object in the example, see [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).
```
