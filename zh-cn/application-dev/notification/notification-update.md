# 更新通知

<!--Kit: Notification Kit-->
<!--Subsystem: Notification-->
<!--Owner: @peixu-->
<!--Designer: @dongqingran; @wulong158-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->

更新已发布的通知。主要用于上传下载进度更新、IM会话消息更新等场景。

## 接口说明

通知发布更新接口说明详见下表，通知更新可通过入参[NotificationRequest](../reference/apis-notification-kit/js-apis-inner-notification-notificationRequest.md#notificationrequest-1)携带updateOnly字段来指定，不指定该字段默认为false。

- 当updateOnly为true时，若相同ID通知存在，则更新通知；若相同ID通知不存在，则更新失败，不创建新的通知。

- 当updateOnly为false时，若相同ID通知存在，则更新通知；若相同ID通知不存在，则创建通知。

| **接口名** | **描述** |
| -------- | -------- |
| [publish](../reference/apis-notification-kit/js-apis-notificationManager.md#notificationmanagerpublish)(request:&nbsp;NotificationRequest,&nbsp;callback:&nbsp;AsyncCallback&lt;void&gt;):&nbsp;void | 发布更新通知。                 |


## 开发步骤

下面以进度条通知发布更新为例。

1. 导入模块。

   <!-- @[update_notification_header](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Notification/EventNotification/entry/src/main/ets/pages/UpdateNotification.ets) -->

2. 发布进度条通知。

   <!-- @[pub_progress_bar_notify](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Notification/EventNotification/entry/src/main/ets/pages/UpdateNotification.ets) -->

3. 通过[NotificationRequest](../reference/apis-notification-kit/js-apis-inner-notification-notificationRequest.md#notificationrequest-1)接口携带updateOnly字段更新进度条通知。

   <!-- @[update_prog_only_notify](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Notification/EventNotification/entry/src/main/ets/pages/UpdateNotification.ets) -->
