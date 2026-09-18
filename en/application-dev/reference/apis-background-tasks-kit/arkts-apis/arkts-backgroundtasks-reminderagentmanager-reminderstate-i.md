# ReminderState

Defines the agent-powered reminder state information, for which notifications are triggered in the following scenarios:

1. When a user taps a button on an agent-powered reminder notification,
a notification specifying the tapped button type is sent to the application if it is running. If the application is not running, the notification will not be received.
2. Since the above scenario cannot guarantee that the application receives the notification,
all callbacks associated with user-tapped button types under the application are returned to the application when it registers a new callback function. State information is retained for a maximum of 30 days. Cached state information is cleared when the application registers a new callback function or has not registered any callback function for more than 30 days.

**Since:** 23

**System capability:** SystemCapability.Notification.ReminderAgent

## Modules to Import

```TypeScript
import { reminderAgentManager } from '@kit.BackgroundTasksKit';
```

## buttonType

```TypeScript
buttonType: ActionButtonType
```

Button type.

**Type:** [ActionButtonType](arkts-backgroundtasks-reminderagentmanager-actionbuttontype-e.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Notification.ReminderAgent

## isMessageResent

```TypeScript
isMessageResent: boolean
```

Whether a message is sent repeatedly.

- **false**: The message is sent for the first time. Applicable scenarios: The application is running when the  
user taps a button on the agent-powered reminder notification; the application is not running when the user taps the button, and the application registers a new callback function afterward.  
- **true**: The message is sent repeatedly. Applicable scenario: The application is running and registers a new  
callback function after the user taps a button on the agent-powered reminder notification.

**Type:** boolean

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Notification.ReminderAgent

## reminderId

```TypeScript
reminderId: number
```

Reminder ID. The value range is all integers.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Notification.ReminderAgent
