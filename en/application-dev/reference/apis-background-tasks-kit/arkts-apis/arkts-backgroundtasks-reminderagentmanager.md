# @ohos.reminderAgentManager(Agent-powered Reminder)

The **reminderAgentManager** module provides APIs related to agent-powered reminders. When your application is frozen or exits, the application's scheduled notification capability will be taken over by a system service running in the background. You can use the APIs to create scheduled reminders for countdown timers, calendar events, and alarm clocks. For details, see [Agent-powered Reminder](../../../task-management/agent-powered-reminder.md).

**Since:** 9

**System capability:** SystemCapability.Notification.ReminderAgent

## Modules to Import

```TypeScript
import { reminderAgentManager } from '@kit.BackgroundTasksKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [addExcludeDate](arkts-backgroundtasks-reminderagentmanager-addexcludedate-f.md) | Adds a non-reminder date for a recurring calendar reminder with a specific ID. For example, configure a daily reminder to skip notifications on Tuesdays. This API uses a promise to return the result. |
| [addNotificationSlot](arkts-backgroundtasks-reminderagentmanager-addnotificationslot-f.md) | Adds a notification slot. This API uses an asynchronous callback to return the result. |
| [addNotificationSlot](arkts-backgroundtasks-reminderagentmanager-addnotificationslot-f.md) | Adds a notification slot. This API uses a promise to return the result. |
| [cancelAllReminders](arkts-backgroundtasks-reminderagentmanager-cancelallreminders-f.md) | Cancels all reminders set by the current application. This API uses an asynchronous callback to return the result. |
| [cancelAllReminders](arkts-backgroundtasks-reminderagentmanager-cancelallreminders-f.md) | Cancels all reminders set by the current application. This API uses a promise to return the result. |
| [cancelReminder](arkts-backgroundtasks-reminderagentmanager-cancelreminder-f.md) | Cancels a reminder published. This API uses an asynchronous callback to return the result. |
| [cancelReminder](arkts-backgroundtasks-reminderagentmanager-cancelreminder-f.md) | Cancels a reminder published. This API uses a promise to return the result. |
| [cancelReminderOnDisplay](arkts-backgroundtasks-reminderagentmanager-cancelreminderondisplay-f.md) | Cancels the notification card displayed in the notification center with the agent reminder data retained. For example, for a daily repeating reminder, calling this API removes the card from the notification center, but the reminder will be triggered again the next day according to its schedule. |
| [deleteExcludeDates](arkts-backgroundtasks-reminderagentmanager-deleteexcludedates-f.md) | Deletes all non-reminder dates for a recurring calendar reminder with a specific ID. This API uses a promise to return the result. |
| [getAllValidReminders](arkts-backgroundtasks-reminderagentmanager-getallvalidreminders-f.md) | Obtains all [valid (not yet expired) reminders](../../../task-management/agent-powered-reminder.md#constraints) set by the current application. This API uses a promise to return the result. To call this API, you need to request the ohos.permission.PUBLISH_AGENT_REMINDER permission. |
| [getExcludeDates](arkts-backgroundtasks-reminderagentmanager-getexcludedates-f.md) | Obtains all non-reminder dates for a recurring calendar reminder with a specific ID. This API uses a promise to return the result. |
| [getValidReminders](arkts-backgroundtasks-reminderagentmanager-getvalidreminders-f.md) | Obtains all [valid (not yet expired) reminders](../../../task-management/agent-powered-reminder.md#constraints) set by the current application. This API uses an asynchronous callback to return the result. |
| [getValidReminders](arkts-backgroundtasks-reminderagentmanager-getvalidreminders-f.md) | Obtains all [valid (not yet expired) reminders](../../../task-management/agent-powered-reminder.md#constraints) set by the current application. This API uses a promise to return the result. |
| [publishReminder](arkts-backgroundtasks-reminderagentmanager-publishreminder-f.md) | Publishes a reminder. This API uses an asynchronous callback to return the result. |
| [publishReminder](arkts-backgroundtasks-reminderagentmanager-publishreminder-f.md) | Publishes a reminder. This API uses a promise to return the result. |
| [removeNotificationSlot](arkts-backgroundtasks-reminderagentmanager-removenotificationslot-f.md) | Removes a specified notification slot. This API uses an asynchronous callback to return the result. |
| [removeNotificationSlot](arkts-backgroundtasks-reminderagentmanager-removenotificationslot-f.md) | Removes a specified notification slot. This API uses a promise to return the result. |
| [subscribeReminderState](arkts-backgroundtasks-reminderagentmanager-subscribereminderstate-f.md) | Subscribes to agent-powered reminder state changes. This API uses a promise to return the result. |
| [unsubscribeReminderState](arkts-backgroundtasks-reminderagentmanager-unsubscribereminderstate-f.md) | Unsubscribes from agent-powered reminder state changes. This API uses a promise to return the result. |
| [updateReminder](arkts-backgroundtasks-reminderagentmanager-updatereminder-f.md) | Updates the agent-powered reminder with the specified ID. This API uses a promise to return the result. Only [valid (not yet expired) reminders](../../../task-management/agent-powered-reminder.md#constraints) that are not displayed in the notification panel can be updated. |

### Interfaces

| Name | Description |
| --- | --- |
| [ActionButton](arkts-backgroundtasks-reminderagentmanager-actionbutton-i.md) | Describes the button displayed for a reminder. |
| [LocalDateTime](arkts-backgroundtasks-reminderagentmanager-localdatetime-i.md) | Defines the time information for a calendar reminder. |
| [MaxScreenWantAgent](arkts-backgroundtasks-reminderagentmanager-maxscreenwantagent-i.md) | Describes the information about the ability that is started automatically and displayed in full-screen mode when a reminder is displayed in the notification center. This API is reserved. |
| [NotificationRequestProxy](arkts-backgroundtasks-reminderagentmanager-notificationrequestproxy-i.md) | Notification request proxy. |
| [ReminderInfo](arkts-backgroundtasks-reminderagentmanager-reminderinfo-i.md) | Defines the reminder information. |
| [ReminderRequest](arkts-backgroundtasks-reminderagentmanager-reminderrequest-i.md) | Defines the request for publishing a reminder. |
| [ReminderRequestAlarm](arkts-backgroundtasks-reminderagentmanager-reminderrequestalarm-i.md) | ReminderRequestAlarm extends ReminderRequest |
| [ReminderRequestCalendar](arkts-backgroundtasks-reminderagentmanager-reminderrequestcalendar-i.md) | ReminderRequestCalendar extends ReminderRequest |
| [ReminderRequestTimer](arkts-backgroundtasks-reminderagentmanager-reminderrequesttimer-i.md) | ReminderRequestTimer extends ReminderRequest |
| [ReminderState](arkts-backgroundtasks-reminderagentmanager-reminderstate-i.md) | Defines the agent-powered reminder state information, for which notifications are triggered in the following scenarios: |
| [WantAgent](arkts-backgroundtasks-reminderagentmanager-wantagent-i.md) | Defines the information about the redirected-to ability. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [ActionButton](arkts-backgroundtasks-reminderagentmanager-actionbutton-i-sys.md) | Describes the button displayed for a reminder. |
| [DataShareUpdate](arkts-backgroundtasks-reminderagentmanager-datashareupdate-i-sys.md) | Defines the parameter information used to update the database. |
| [ReminderRequest](arkts-backgroundtasks-reminderagentmanager-reminderrequest-i-sys.md) | Defines the request for publishing a reminder. |
| [ReminderRequestCalendar](arkts-backgroundtasks-reminderagentmanager-reminderrequestcalendar-i-sys.md) | ReminderRequestCalendar extends ReminderRequest |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [ActionButtonType](arkts-backgroundtasks-reminderagentmanager-actionbuttontype-e.md) | Enumerates the types of buttons displayed for a reminder. |
| [ReminderType](arkts-backgroundtasks-reminderagentmanager-remindertype-e.md) | Enumerates the reminder types. |
| [RingChannel](arkts-backgroundtasks-reminderagentmanager-ringchannel-e.md) | Enumerates the audio playback channels for the custom prompt tone. |
| [TimeZoneType](arkts-backgroundtasks-reminderagentmanager-timezonetype-e.md) | Enumerates the time zone types. When the time zone is changed, the reminder time is recalculated based on the new time zone. |

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [ActionButtonType](arkts-backgroundtasks-reminderagentmanager-actionbuttontype-e-sys.md) | Enumerates the types of buttons displayed for a reminder. |
<!--DelEnd-->
