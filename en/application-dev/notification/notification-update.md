# Updating a Notification
<!--Kit: Notification Kit-->
<!--Subsystem: Notification-->
<!--Owner: @HuYueRong-->
<!--Designer: @dongqingran-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=1160b503457fd64270d561fc02b4ca184d668154 translatedAt=2026-09-29T11:12:28.677Z pushedAt=2026-09-30T09:41:58.512Z -->

Starting from API version 18, applications can update only published notifications. such as the upload/download progress and IMs.

> **NOTE**
>
> Starting from API version 26.0.1, for progress updates in data transfer scenarios such as upload and download, you are advised to use the API [`backgroundTaskManager.updateDataTransferProgress`](../reference/apis-backgroundtasks-kit/js-apis-resourceschedule-backgroundTaskManager.md#backgroundtaskmanagerupdatedatatransferprogress) provided by continuous tasks to update the notification progress, without calling `notificationManager.publish`. Before using this API, you must first request a continuous task of the data transfer type. For the development guide, see [Continuous Task (ArkTS)](../task-management/continuous-task.md).
>
> Compared with calling `notificationManager.publish`, this API offers the following advantages:
> - Flexible configuration of the reminder mode for notifications in transfer scenarios: when the progress reaches 100, you can use the `isMute` field of [ProgressInfo](../reference/apis-backgroundtasks-kit/js-apis-resourceschedule-backgroundTaskManager.md#progressinfo) to choose between silent mode and ringtone-plus-vibration reminder.
> - Binding to the continuous task lifecycle: the notification is created when the continuous task is requested and removed when it is canceled, eliminating the need to separately maintain the notification ID and cancellation logic.

## Available APIs

The following table describes the APIs for publishing and updating notifications. [Notification update](notification-glossary.md#notification-update) can be specified by carrying the **updateOnly** field in the [NotificationRequest](../reference/apis-notification-kit/js-apis-inner-notification-notificationRequest.md#notificationrequest-1) parameter. If this field is not specified, it defaults to **false**.

- When **updateOnly** is set to **true**, if a notification with the same ID exists, it will be updated. If no notification with the same ID exists, the update fails and no new notification is created.

- When **updateOnly** is set to **false**, if a notification with the same ID exists, it will be updated. If no notification with the same ID exists, a new notification is created.

| **API**| **Description**|
| -------- | -------- |
| [publish](../reference/apis-notification-kit/js-apis-notificationManager.md#notificationmanagerpublish)(request:&nbsp;NotificationRequest,&nbsp;callback:&nbsp;AsyncCallback&lt;void&gt;):&nbsp;void | Publishes an updated notification.                |


## How to Develop

The following uses the progress bar notification as an example.

1. Import modules.

   <!-- @[update_notification_header](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Notification-Kit/Notification/entry/src/main/ets/filemanager/UpdateNotification.ets) -->
   
   ``` TypeScript
   import { notificationManager } from '@kit.NotificationKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   import { hilog } from '@kit.PerformanceAnalysisKit';
   
   const TAG: string = '[PublishOperation]';
   const DOMAIN_NUMBER: number = 0xFF00;
   ```

2. Publish the progress bar notification.

   <!-- @[pub_progress_bar_notify](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Notification-Kit/Notification/entry/src/main/ets/filemanager/UpdateNotification.ets) -->
   
   ``` TypeScript
   let notificationRequest: notificationManager.NotificationRequest = {
     id: 5,
     content: {
       notificationContentType: notificationManager.ContentType.NOTIFICATION_CONTENT_BASIC_TEXT,
       normal: {
         title: 'test_title',
         text: 'test_text',
         additionalText: 'test_additionalText'
       }
     },
     // Create a progress template. The name field has a fixed value of downloadTemplate.
     template: {
       name: 'downloadTemplate',
       data: { title: 'File Title', fileName: 'music.mp4', progressValue: 50 }
     }
   };
   
   // Publish the notification.
   notificationManager.publish(notificationRequest, (err: BusinessError) => {
     if (err) {
       hilog.error(DOMAIN_NUMBER, TAG,
         `Failed to publish notification. Code is ${err.code}, message is ${err.message}`);
       return;
     }
     hilog.info(DOMAIN_NUMBER, TAG, 'Succeeded in publishing notification.');
   });
   ```

3. Update the progress bar notification using the **updateOnly** field in the [NotificationRequest](../reference/apis-notification-kit/js-apis-inner-notification-notificationRequest.md#notificationrequest-1) API.

   <!-- @[update_prog_only_notify](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Notification-Kit/Notification/entry/src/main/ets/filemanager/UpdateNotification.ets) -->
   
   ``` TypeScript
   let notificationRequest: notificationManager.NotificationRequest = {
     id: 5,
     updateOnly: true,
     content: {
       notificationContentType: notificationManager.ContentType.NOTIFICATION_CONTENT_BASIC_TEXT,
       normal: {
         title: 'test_title',
         text: 'test_text',
         additionalText: 'test_additionalText'
       }
     },
     // Create a progress template. The name field has a fixed value of downloadTemplate.
     template: {
       name: 'downloadTemplate',
       data: { title: 'File Title', fileName: 'music.mp4', progressValue: 99 }
     }
   };
   
   // Update the published notification.
   notificationManager.publish(notificationRequest, (err: BusinessError) => {
     if (err) {
       hilog.error(DOMAIN_NUMBER, TAG,
         `Failed to update notification. Code is ${err.code}, message is ${err.message}`);
       return;
     }
     hilog.info(DOMAIN_NUMBER, TAG, 'Succeeded in updating notification.');
   });
   ```
