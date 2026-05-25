# 代理提醒(ArkTS)

<!--Kit: Background Tasks Kit-->
<!--Subsystem: Resourceschedule-->
<!--Owner: @xufu7-->
<!--Designer: @zhouben25-->
<!--Tester: @leetestnady-->
<!--Adviser: @HelloCrease-->

## 功能介绍

应用退到后台或进程终止后，仍然有一些提醒用户的定时类通知，为满足此类功能场景，系统提供了代理提醒的能力。当应用退至后台或进程终止后，系统会代理应用做定时提醒。当前支持的提醒类型包括：倒计时、日历和闹钟。<!--RP1--><!--RP1End-->

## 约束与限制

<!--RP3--><!--RP3End-->

<!--RP2-->
- **个数限制**：一个普通应用支持最多30个有效提醒，一个系统应用支持最多10000个有效提醒。整个系统最多支持12000个有效提醒。
<!--RP2End-->

> **说明：**
>
> 当到达设置的提醒时间点时，通知中心会弹出相应提醒。若未点击提醒上的关闭/CLOSE按钮，则代理提醒是有效/未过期的；若点击了关闭/CLOSE按钮，则代理提醒过期。
>
> 当代理提醒是周期性提醒时，如设置每天提醒，无论是否点击关闭/CLOSE按钮，代理提醒都是有效的。

- **跳转限制**：点击提醒通知后跳转的应用必须是申请代理提醒的本应用。

## 与相关Kit的关系
- 当到达设置的提醒时间点后，代理提醒使用Notification Kit发布通知，通知会显示在通知中心，通知样式请参考[Notification Kit通知样式](../notification/notification-overview.md#通知样式)中的文本类型。

## 模拟器支持情况

从API version 20开始，本能力支持模拟器开发。

## 接口说明

以下是代理提醒的相关接口，下表均以Promise形式为例，更多接口及使用方式请见[后台代理提醒](../reference/apis-backgroundtasks-kit/js-apis-reminderAgentManager.md)文档。

**表1** 主要接口
| 接口名 | 描述 |
| -------- | -------- |
| publishReminder(reminderReq: ReminderRequest): Promise&lt;number&gt; | 发布后台代理提醒。 |
| cancelReminder(reminderId: number): Promise&lt;void&gt; | 取消指定id的代理提醒。 |
| getValidReminders(): Promise&lt;Array&lt;ReminderRequest&gt;&gt; | 获取当前应用设置的所有[有效（未过期）的代理提醒](#约束与限制)。 |
| cancelAllReminders(): Promise&lt;void&gt; | 取消当前应用设置的所有代理提醒。 |
| addNotificationSlot(slot: NotificationSlot): Promise&lt;void&gt; | 添加通知渠道。 |
| removeNotificationSlot(slotType: notification.SlotType): Promise&lt;void&gt; | 删除指定的通知渠道类型。 |


## 开发步骤

<!--RP4--><!--RP4End-->

### 申请权限

申请ohos.permission.PUBLISH_AGENT_REMINDER权限，配置方式请参阅[声明权限](../security/AccessToken/declare-permissions.md)。

### 请求通知授权

[请求通知授权](../notification/notification-enable.md)。获得用户授权后，才能使用代理提醒功能。

### 功能开发

1. 导入模块。

    <!-- @[reminder_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/BackGroundTasksKit/ReminderAgentManager/entry/src/main/ets/pages/timer/Timer.ets) -->
    
    ``` TypeScript
    import { notificationManager } from '@kit.NotificationKit';
    import { reminderAgentManager } from '@kit.BackgroundTasksKit';
    import { BusinessError } from '@kit.BasicServicesKit';
    ```

2. 定义目标提醒代理。开发者根据实际需要，选择定义如下类型的提醒。

   - 定义倒计时实例。
     
      <!-- @[timer_reminder](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/BackGroundTasksKit/ReminderAgentManager/entry/src/main/ets/pages/timer/Timer.ets) -->
      
      ``` TypeScript
   
      ```

   - 定义日历实例。
     
      <!-- @[calendar_reminder](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/BackGroundTasksKit/ReminderAgentManager/entry/src/main/ets/util/CalendarReminder.ets) -->
      
      ``` TypeScript
  
      ```

   - 定义闹钟实例。
   
      <!-- @[alarm_reminder](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/BackGroundTasksKit/ReminderAgentManager/entry/src/main/ets/util/AlarmClockReminder.ets) -->
      
      ``` TypeScript
  
      ```

3. 发布相应的提醒代理。代理发布后，应用即可使用后台代理提醒功能。
   
   <!-- @[publish_reminder](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/BackGroundTasksKit/ReminderAgentManager/entry/src/main/ets/util/CalendarReminder.ets) -->
   
   ``` TypeScript
   let reminderId: number = await reminderAgentManager.publishReminder(
     this.calendarReminders[index].reminderRequestCalendar!);
   Logger.info(TAG, `publish reminder result: id is ${reminderId}`);
   this.calendarReminders[index].reminderId = reminderId;  // 保存发布的提醒ID
   ```

4. 根据需要删除提醒任务。
   
   <!-- @[cancel_reminder](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/BackGroundTasksKit/ReminderAgentManager/entry/src/main/ets/util/CalendarReminder.ets) -->
   
   ``` TypeScript
   Logger.info(TAG, `cancel reminder id is ${this.calendarReminders[index].reminderId}`)
   await reminderAgentManager.cancelReminder(this.calendarReminders[index].reminderId);
   ```

## 相关实例

基于代理提醒，有以下相关实例可供参考：

- [后台代理提醒（ArkTS）（API9）](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/BackGroundTasksKit/ReminderAgentManager)

- [翻页时钟（ArkTS）（API9）](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/Solutions/Tools/FlipClock)