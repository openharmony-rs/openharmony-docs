# @ohos.reminderAgentManager (Agent-powered Reminder) (System API)

<!--Kit: Background Tasks Kit-->
<!--Subsystem: Resourceschedule-->
<!--Owner: @cheng-shichang-->
<!--Designer: @zhouben25-->
<!--Tester: @leetestnady-->
<!--Adviser: @Brilliantry_Rui-->

The reminderAgentManager module provides APIs related to agent-powered reminders. When your application is frozen or exits, the timing and notification functions of your application will be taken over by a system service running in the background. You can use the APIs to create scheduled reminders for countdown timers, calendar events, and alarm clocks.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - This topic describes only system APIs provided by the module. For details about its public APIs, see [@ohos.reminderAgentManager (Agent-Powered Reminders)](js-apis-reminderAgentManager.md).


## Modules to Import

```ts
import { reminderAgentManager } from '@kit.BackgroundTasksKit';
```

## ActionButtonType

Enumerates the button types.

**System capability**: SystemCapability.Notification.ReminderAgent

| Name| Value| Description|
| -------- | -------- | -------- |
| ACTION_BUTTON_TYPE_CUSTOM<sup>10+</sup>  | 2 | Custom button.|

## ActionButton

Defines the button on the reminder displayed.

**System capability**: SystemCapability.Notification.ReminderAgent

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| wantAgent<sup>10+</sup> | [WantAgent](./js-apis-reminderAgentManager.md#wantagent) | No| Yes| Information about the ability that is displayed after the button is clicked.|
| dataShareUpdate<sup>11+</sup> | [DataShareUpdate](#datashareupdate11) | No| Yes| The application database will be updated after a click on the button.|

## DataShareUpdate<sup>11+</sup>

Defines the parameter information used to update the database.<br>
The data provider needs to set the ID, read/write permissions, and basic information of the table to be shared under **proxyData** in the **module.json5** file. For details about the configuration method, see [Data Provider Application Development](../../database/share-data-by-silent-access-sys.md#data-provider-application-development).

**System capability**: SystemCapability.Notification.ReminderAgent


| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| uri | string | No| No| URI of the data, which is the unique identifier for cross-application data access.|
| equalTo | Record<string, number \| string \| boolean> | No| No| Filter criteria. Currently, only equal to is supported.|
| value | [ValueBucket](../apis-arkdata/js-apis-data-valuesBucket.md#valuesbucket) | No| No| New data.|

## ReminderRequestCalendar

Defines a reminder for a calendar event.

**System capability**: SystemCapability.Notification.ReminderAgent

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| rruleWantAgent<sup>12+</sup> | [WantAgent](./js-apis-reminderAgentManager.md#wantagent) | No| Yes| Custom reminder, which specifies the ServiceExtensionAbility to start.|

## ReminderRequest

Defines the request for publishing a reminder.

**System capability**: SystemCapability.Notification.ReminderAgent

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| notDistributed<sup>23+</sup> | boolean | No| Yes| Whether notifications are not displayed in all scenarios across devices. The default value is **false**. For details, see [NotificationRequest.notDistributed](../apis-notification-kit/js-apis-inner-notification-notificationRequest-sys.md#notificationrequest).<br> - **true**: Notifications are displayed only on the local device.<br> - **false**: Notifications are displayed on all collaborative devices.<br> **System API**: This is a system API.|
| forceDistributed<sup>23+</sup> | boolean | No| Yes| Whether notifications are forcibly displayed in all scenarios across devices. The default value is **false**. For details, see [NotificationRequest.forceDistributed](../apis-notification-kit/js-apis-inner-notification-notificationRequest-sys.md#notificationrequest).<br> - **true**: Notifications are displayed on all collaboration devices.<br> - **false**: Notifications are displayed on the applications that are on the collaborative management list.<br> **System API**: This is a system API.|
