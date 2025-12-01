# Agent-powered Reminder (ArkTS)

<!--Kit: Background Tasks Kit-->
<!--Subsystem: Resourceschedule-->
<!--Owner: @cheng-shichang-->
<!--Designer: @zhouben25-->
<!--Tester: @leetestnady-->
<!--Adviser: @Brilliantry_Rui-->

## Introduction

When an application is backgrounded or closed, the system can still send scheduled notifications on behalf of the application.  Currently, the following reminder types are supported: timer, calendar, and alarm.<!--RP1--><!--RP1End-->

## Constraints

<!--RP3--><!--RP3End-->

<!--RP2-->
- **Maximum reminders**: 30 for regular applications, 10,000 for system applications, and 12,000 total for the system.
<!--RP2End-->

> **NOTE**
>
> - When the reminder time arrives, the notification center displays the relevant reminder. The reminder remains active and unexpired unless the user touches the CLOSE button, at which point the reminder becomes expired.
>
> - For a recurring reminder (for example, a daily reminder), the reminder is always valid regardless of whether the user touches the CLOSE button.

- **Redirection limit**: The application that is redirected to upon a click on the notification must be the application that requested the agent-powered reminder.

## Relationship with Other Kits
- When the preset time arrives, notifications created by Notification Kit will be displayed in the notification center. For details about notification styles, see [Notification Style](../notification/notification-overview.md#notification-style).

## Emulator Support

This capability is supported by the Emulator since API version 20.

## Available APIs

The table below uses promise as an example to describe the APIs used for developing agent-powered reminders. For details about more APIs and their usage, see [reminderAgentManager](../reference/apis-backgroundtasks-kit/js-apis-reminderAgentManager.md).

**Table 1** Main APIs for agent-powered reminders
| API| Description|
| -------- | -------- |
| publishReminder(reminderReq: ReminderRequest): Promise&lt;number&gt; | Publishes a reminder.|
| cancelReminder(reminderId: number): Promise&lt;void&gt; | Cancels a reminder published.|
| getValidReminders(): Promise&lt;Array&lt;ReminderRequest&gt;&gt; | Obtains all [valid (not yet expired) reminders](#constraints) set by the current application.|
| cancelAllReminders(): Promise&lt;void&gt; | Cancels all reminders set by the current application.|
| addNotificationSlot(slot: NotificationSlot): Promise&lt;void&gt; | Adds a notification slot.|
| removeNotificationSlot(slotType: notification.SlotType): Promise&lt;void&gt; | Removes a notification slot.|


## How to Develop

<!--RP4--><!--RP4End-->

### Requesting Permissions

Declare the ohos.permission.PUBLISH_AGENT_REMINDER permission. For details, see [Declaring Permissions](../security/AccessToken/declare-permissions.md).

### Requesting Notification Authorization

[Request notification authorization](../notification/notification-enable.md). Agent-powered reminders can be used only after being authorized by the user.

### Developing Functionalities

1. Import the modules.
   
   ```ts
   import { reminderAgentManager } from '@kit.BackgroundTasksKit';
   import { notificationManager } from '@kit.NotificationKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   ```

2. Define a reminder. You can define the following types of reminders based on project requirements.

   - Timer
     
      <!-- [timer_reminder](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/BasicFeature/TaskManagement/ReminderAgentManager/entry/src/main/ets/pages/timer/Timer.ets) -->
      
      ``` TypeScript
      let timer: reminderAgent.ReminderRequestTimer = {
        reminderType: reminderAgent.ReminderType.REMINDER_TYPE_TIMER,  // The reminder type is timer.
        ringDuration: Constant.REMINDER_DURATION,
        title: context.resourceManager.getStringSync($r('app.string.timer').id),  // Reminder title. The value in the "app.string.timer" resource file is "timer".
        content: context.resourceManager.getStringSync($r('app.string.countdown_close').id),  // Reminder content. The value in the "app.string.countdown_close" resource file is "timer ended".
        wantAgent: {  // // Information about the target UIAbility that is displayed after the reminder notification is touched.
          pkgName: 'com.example.reminderagentmanager',
          abilityName: 'EntryAbility'
        },
        notificationId: 100, // Notification ID used by the reminder. If there are reminders with the same notification ID, the later one will overwrite the earlier one.
        slotType: notificationManager.SlotType.CONTENT_INFORMATION,  // Type of the slot used by the reminder.
        triggerTimeInSeconds: this.countdownTime
      };
      ```

   - Calendar
     
      <!-- [calendar_reminder](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/BasicFeature/TaskManagement/ReminderAgentManager/entry/src/main/ets/util/CalendarReminder.ets) -->
      
      ``` TypeScript
      let calendar: reminderAgent.ReminderRequestCalendar = {
        reminderType: reminderAgent.ReminderType.REMINDER_TYPE_CALENDAR,  // The reminder type is calendar.
        dateTime: {  // Reminder time.
          year: date.getFullYear(),
          month: date.getUTCMonth() + 1,
          day: date.getDate(),
          hour: date.getHours(),
          minute: date.getMinutes(),
        },
        actionButton:  // Set the button type and title displayed for the reminder in the notification panel.
        [{
          title: context.resourceManager.getStringSync($r('app.string.calendar_close').id),  // The value in the "app.string.calendar_close" resource file is "disable calendar reminder".
          type: reminderAgent.ActionButtonType.ACTION_BUTTON_TYPE_CLOSE
        }],
        // Information about the target UIAbility that is displayed after the reminder notification is touched.
        wantAgent: { pkgName: 'com.example.reminderagentmanager', abilityName: 'EntryAbility' },
        ringDuration: Constant.REMINDER_DURATION,  // Ringing duration, in seconds.
        title: context.resourceManager.getStringSync($r('app.string.calendar').id),  // Reminder title. The value in the "app.string.calendar" resource file is "calendar".
        content: context.resourceManager.getStringSync($r('app.string.calendar_reach').id),  // Reminder content. The value in the "app.string.calendar_reach" resource file is "calendar reminder time is up".
        slotType: notificationManager.SlotType.CONTENT_INFORMATION  // Type of the slot used by the reminder.
      }
      ```

   - Alarm
   
      <!-- [alarm_reminder](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/BasicFeature/TaskManagement/ReminderAgentManager/entry/src/main/ets/util/AlarmClockReminder.ets) -->
      
      ``` TypeScript
      let alarm: reminderAgent.ReminderRequestAlarm = {
        reminderType: reminderAgent.ReminderType.REMINDER_TYPE_ALARM,  // The reminder type is alarm.
        hour: time.hour,  // Hour portion of the reminder time.
        minute: time.minute,  // Minute portion of the reminder time.
        actionButton:  // Set the button type and title displayed for the reminder in the notification panel.
        [
          {
            title: context.resourceManager.getStringSync($r('app.string.alarm_clock_close').id),  // The value in the "app.string.alarm_clock_close" resource file is "disable alarm clock".
            type: reminderAgent.ActionButtonType.ACTION_BUTTON_TYPE_CLOSE
          },
          {
            title: context.resourceManager.getStringSync($r('app.string.alarm_clock_postpone').id),  // The value in the "app.string.alarm_clock_postpone" resource file is "postpone alarm clock".
            type: reminderAgent.ActionButtonType.ACTION_BUTTON_TYPE_SNOOZE
          }
        ],
        slotType: notificationManager.SlotType.CONTENT_INFORMATION,  // Type of the slot used by the reminder.
        ringDuration: Constant.REMINDER_DURATION,  // Ringing duration, in seconds.
        wantAgent: {  // Information about the target UIAbility that is displayed after the reminder notification is touched.
          pkgName: 'com.example.reminderagentmanager',
          abilityName: 'EntryAbility'
        },
        title: context.resourceManager.getStringSync($r('app.string.alarm_clock').id),  // Reminder title. The value in the "app.string.alarm_clock" resource file is "alarm clock".
        content: context.resourceManager.getStringSync($r('app.string.alarm_clock_reach').id),  // Reminder content. The value in the "app.string.alarm_clock_reach" resource file is "alarm time is up".
        snoozeTimes: 0,  // Number of reminder snooze times.
        timeInterval: 0,  // Reminder snooze interval, in seconds.
        daysOfWeek: []  // Days of a week when the reminder repeats.
      }
      ```

3. Publish the reminder. After the reminder is published, your application can use the agent-powered reminder feature.
   
   <!-- [publish_reminder](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/BasicFeature/TaskManagement/ReminderAgentManager/entry/src/main/ets/util/CalendarReminder.ets) -->
   
   ``` TypeScript
   let reminderId: number = await reminderAgent.publishReminder(
     this.calendarReminders[index].reminderRequestCalendar!);
   Logger.info(TAG, `publish reminder result: id is ${reminderId}`);
   this.calendarReminders[index].reminderId = reminderId;  // Save the ID of the published reminder.
   ```

4. Delete the reminder as required.
   
   <!-- [cancel_reminder](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/BasicFeature/TaskManagement/ReminderAgentManager/entry/src/main/ets/util/CalendarReminder.ets) -->
   
   ``` TypeScript
   Logger.info(TAG, `cancel reminder id is ${this.calendarReminders[index].reminderId}`)
   await reminderAgent.cancelReminder(this.calendarReminders[index].reminderId);
   ```

