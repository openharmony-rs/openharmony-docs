# Publishing a Progress Notification
<!--Kit: Notification Kit-->
<!--Subsystem: Notification-->
<!--Owner: @HuYueRong-->
<!--Designer: @dongqingran-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=1160b503457fd64270d561fc02b4ca184d668154 translatedAt=2026-09-29T11:13:41.817Z pushedAt=2026-09-30T09:44:07.420Z -->

The progress notification is a commonly used notification type, mainly used to display the progress of an ongoing operation, such as file downloading. When publishing a progress notification through the notification subsystem, you can use the readily available template by specifying the related attributes, such as the template name and template data.

Currently, the system template supports only the progress bar template. The `data` parameter in the notification template [NotificationTemplate](../reference/apis-notification-kit/js-apis-inner-notification-notificationTemplate.md) is user-defined data used to display template-related data.

> **NOTE**
>
> Starting from API version 26.0.1, for progress notifications in data transfer scenarios such as upload and download, you are advised to use the API [`backgroundTaskManager.updateDataTransferProgress`](../reference/apis-backgroundtasks-kit/js-apis-resourceschedule-backgroundTaskManager.md#backgroundtaskmanagerupdatedatatransferprogress) provided by continuous tasks to update the notification progress, without calling `notificationManager.publish`. Before using this API, apply for a continuous task of the data transfer type. For details about the development guide, see [Continuous Task (ArkTS)](../task-management/continuous-task.md).
>
> Compared with calling `notificationManager.publish`, this API offers the following advantages:
> - Flexibly set the reminder mode for notifications in transfer scenarios: when the progress reaches 100%, you can use the isMute field of [ProgressInfo](../reference/apis-backgroundtasks-kit/js-apis-resourceschedule-backgroundTaskManager.md#progressinfo) to choose between silent mode or ringtone plus vibration.
> - Bound to the continuous task lifecycle: the notification is created when the continuous task is requested and removed when the task is canceled, eliminating the need to maintain the notification ID and cancellation logic separately.

## Available APIs

[`isSupportTemplate()`](../reference/apis-notification-kit/js-apis-notificationManager.md#notificationmanagerissupporttemplate) checks whether a specific notification template is supported. Currently, only the progress bar template is supported.

| Name| Description|
| -------- | -------- |
| isSupportTemplate(templateName: string): Promise\<boolean\> | Checks whether the corresponding notification template is supported. |


## How to Develop

1. Import the module.

   <!-- @[publish_notification_header](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Notification-Kit/Notification/entry/src/main/ets/filemanager/PublishNotification.ets) -->
   
   ``` TypeScript
   import { notificationManager } from '@kit.NotificationKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   import { hilog } from '@kit.PerformanceAnalysisKit';
   
   const TAG: string = '[PublishOperation]';
   const DOMAIN_NUMBER: number = 0xFF00;
   ```

2. Check whether a specific template is supported. In this example, the template of the **downloadTemplate** type is checked.

   <!-- @[check_progress_template_download](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Notification-Kit/Notification/entry/src/main/ets/filemanager/PublishNotification.ets) -->
   
   ``` TypeScript
   notificationManager.isSupportTemplate('downloadTemplate').then((data: boolean) => {
     let isSupportTemplate: boolean = data; // The value true means that the template of the downloadTemplate type is supported, and false means the opposite.
     hilog.info(DOMAIN_NUMBER, TAG,
       `Succeeded in supporting download template notification. data is ${isSupportTemplate}`);
   }).catch((err: BusinessError) => {
     hilog.error(DOMAIN_NUMBER, TAG,
       `Failed to support download template notification. Code is ${err.code}, message is ${err.message}`);
   });
   ```
   
   > **NOTE**
   > Proceed with the step below only when the specified template is supported.
   
3. Create a **NotificationRequest** object and publish a progress notification.

   <!-- @[pub_progress_template_req_notify](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Notification-Kit/Notification/entry/src/main/ets/filemanager/PublishNotification.ets) -->
   
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
       data: { title: 'File Title', fileName: 'music.mp4', progressValue: 45 }
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
