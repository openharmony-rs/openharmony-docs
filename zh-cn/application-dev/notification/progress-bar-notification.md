# 发布进度条类型通知

<!--Kit: Notification Kit-->
<!--Subsystem: Notification-->
<!--Owner: @michael_woo888-->
<!--Designer: @dongqingran; @wulong158-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->

进度条通知也是常见的通知类型，主要应用于文件下载、事务处理进度显示。当前系统提供了进度条模板，发布通知应用设置好进度条模板的属性值，如模板名、模板数据，通过通知子系统发送到通知栏显示。

目前系统模板仅支持进度条模板，通知模板[NotificationTemplate](../reference/apis-notification-kit/js-apis-inner-notification-notificationTemplate.md)中的data参数为用户自定义数据，用于显示与模块相关的数据。

## 接口说明

[`isSupportTemplate()`](../reference/apis-notification-kit/js-apis-notificationManager.md#notificationmanagerissupporttemplate)是查询模板是否支持接口，目前仅支持进度条模板。

| **接口名** | **描述** |
| -------- | -------- |
| isSupportTemplate(templateName: string): Promise\<boolean\> | 查询模板是否存在。 |


## 开发步骤

1. 导入模块。

   <!-- @[publish_notification_header](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Notification/EventNotification/entry/src/main/ets/pages/PublishNotification.ets) -->

2. 查询系统是否支持进度条模板，查询结果为支持downloadTemplate模板类通知。

   <!-- @[check_progress_template_download](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Notification/EventNotification/entry/src/main/ets/pages/PublishNotification.ets) -->
   
   > **说明：**
   > 查询系统支持进度条模板后，再进行后续的步骤操作。
   
3. 构造进度条模板对象，并发布通知。

   <!-- @[pub_progress_template_req_notify](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Notification/EventNotification/entry/src/main/ets/pages/PublishNotification.ets) -->
