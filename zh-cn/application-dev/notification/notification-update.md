# 更新通知
<!--Kit: Notification Kit-->
<!--Subsystem: Notification-->
<!--Owner: @HuYueRong-->
<!--Designer: @dongqingran-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->

从API version 18开始，支持应用只更新已发布的通知。主要用于上传下载进度更新、IM会话消息更新等场景。

> **说明：**
>
> 从API version 26.1.0开始，对于上传下载等数据传输场景的进度更新，推荐使用长时任务提供的接口[`backgroundTaskManager.updateDataTransferProgress`](../reference/apis-backgroundtasks-kit/js-apis-resourceschedule-backgroundTaskManager.md#backgroundtaskmanagerupdatedatatransferprogress)更新通知进度，无需调用`notificationManager.publish`。使用该接口前，需先申请数据传输类型的长时任务，开发指导请参考[长时任务(ArkTS)](../task-management/continuous-task.md)。
>
> 相较于调用`notificationManager.publish`，使用该接口具有以下优势：
> - 灵活设置传输场景通知的提醒方式：进度达到100时，可通过[ProgressInfo](../reference/apis-backgroundtasks-kit/js-apis-resourceschedule-backgroundTaskManager.md#progressinfo)的isMute字段选择静音或响铃加振动提醒。
> - 与长时任务生命周期绑定：通知随长时任务申请而创建、取消而移除，无需单独维护通知ID和取消逻辑。

## 接口说明

通知发布更新接口说明详见下表，[通知更新](notification-glossary.md#notification-update通知更新)可通过入参[NotificationRequest](../reference/apis-notification-kit/js-apis-inner-notification-notificationRequest.md#notificationrequest-1)携带updateOnly字段来指定，不指定该字段默认为false。

- 当updateOnly为true时，若相同ID通知存在，则更新通知；若相同ID通知不存在，则更新失败，并且不创建新的通知。

- 当updateOnly为false时，若相同ID通知存在，则更新通知；若相同ID通知不存在，则创建通知。

| **接口名** | **描述** |
| -------- | -------- |
| [publish](../reference/apis-notification-kit/js-apis-notificationManager.md#notificationmanagerpublish)(request:&nbsp;NotificationRequest,&nbsp;callback:&nbsp;AsyncCallback&lt;void&gt;):&nbsp;void | 发布更新通知。                 |


## 开发步骤

下面以进度条通知发布更新为例。

1. 导入模块。

   <!-- @[update_notification_header](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Notification-Kit/Notification/entry/src/main/ets/filemanager/UpdateNotification.ets) -->
   
   ``` TypeScript
   import { notificationManager } from '@kit.NotificationKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   import { hilog } from '@kit.PerformanceAnalysisKit';
   
   const TAG: string = '[PublishOperation]';
   const DOMAIN_NUMBER: number = 0xFF00;
   ```

2. 发布进度条通知。

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
     // 构造进度条模板，name字段当前需要固定配置为downloadTemplate
     template: {
       name: 'downloadTemplate',
       data: { title: 'File Title', fileName: 'music.mp4', progressValue: 50 }
     }
   };
   
   // 发布通知
   notificationManager.publish(notificationRequest, (err: BusinessError) => {
     if (err) {
       hilog.error(DOMAIN_NUMBER, TAG,
         `Failed to publish notification. Code is ${err.code}, message is ${err.message}`);
       return;
     }
     hilog.info(DOMAIN_NUMBER, TAG, 'Succeeded in publishing notification.');
   });
   ```

3. 通过[NotificationRequest](../reference/apis-notification-kit/js-apis-inner-notification-notificationRequest.md#notificationrequest-1)接口携带updateOnly字段更新进度条通知。

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
     // 构造进度条模板，name字段当前需要固定配置为downloadTemplate
     template: {
       name: 'downloadTemplate',
       data: { title: 'File Title', fileName: 'music.mp4', progressValue: 99 }
     }
   };
   
   // 更新发布通知
   notificationManager.publish(notificationRequest, (err: BusinessError) => {
     if (err) {
       hilog.error(DOMAIN_NUMBER, TAG,
         `Failed to update notification. Code is ${err.code}, message is ${err.message}`);
       return;
     }
     hilog.info(DOMAIN_NUMBER, TAG, 'Succeeded in updating notification.');
   });
   ```
