# 发布文本类型通知

<!--Kit: Notification Kit-->
<!--Subsystem: Notification-->
<!--Owner: @peixu-->
<!--Designer: @dongqingran; @wulong158-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->

文本类型通知主要应用于发送短信息、提示信息等，支持普通文本类型和多行文本类型。

**表1** 基础类型通知中的内容分类

| 类型                             | 描述          |
| ------------------------------- | ------------- |
| NOTIFICATION_CONTENT_BASIC_TEXT | 普通文本类型。 |
| NOTIFICATION_CONTENT_MULTILINE  | 多行文本类型。 |

## 接口说明

通知发布接口说明详见下表，通知发布的详情可通过入参[NotificationRequest](../reference/apis-notification-kit/js-apis-inner-notification-notificationRequest.md#notificationrequest-1)来进行指定，可以包括通知内容、通知ID、通知的通道类型和通知发布时间等信息。

| **接口名** | **描述** |
| -------- | -------- |
| publish(request:&nbsp;NotificationRequest,&nbsp;callback:&nbsp;AsyncCallback&lt;void&gt;):&nbsp;void | 发布通知。                 |


## 开发步骤

1. 导入模块。

   <!-- @[publish_notification_header](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Notification/EventNotification/entry/src/main/ets/pages/PublishNotification.ets) -->

2. 构造NotificationRequest对象，并发布通知。
   - 普通文本类型通知由标题、文本内容和附加信息三个字段组成。详情请参考[NotificationBasicContent](../reference/apis-notification-kit/js-apis-inner-notification-notificationContent.md#notificationbasiccontent)。

     <!-- @[pub_plaintext_req_notify](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Notification/EventNotification/entry/src/main/ets/pages/PublishNotification.ets) -->
    
   - 多行文本类型通知继承了普通文本类型的字段，同时新增了多行文本内容、内容概要和通知展开时的标题。详情请参考[NotificationMultiLineContent](../reference/apis-notification-kit/js-apis-inner-notification-notificationContent.md#notificationmultilinecontent)。

     <!-- @[pub_multi_line_req_notify](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Notification/EventNotification/entry/src/main/ets/pages/PublishNotification.ets) -->
    