# 请求通知授权

<!--Kit: Notification Kit-->
<!--Subsystem: Notification-->
<!--Owner: @peixu-->
<!--Designer: @dongqingran; @wulong158-->
<!--Tester: @wanghong1997-->
<!--Adviser: @fang-jinxu-->

应用需要获取用户授权才能发送通知。在通知发布前调用[requestEnableNotification()](../reference/apis-notification-kit/js-apis-notificationManager.md#notificationmanagerrequestenablenotification10-1)接口，弹窗让用户选择是否允许发送通知。当用户拒绝授权后，将无法通过该接口再次拉起弹窗。如果应用需要向用户再次申请通知授权，则可以使用[openNotificationSettings](../reference/apis-notification-kit/js-apis-notificationManager.md#notificationmanageropennotificationsettings13)接口拉起通知管理半模态弹窗。

## 接口说明

接口详情参见[API参考](../reference/apis-notification-kit/js-apis-notificationManager.md)。

**表1** 通知授权接口功能介绍

| **接口名**  | **描述** |
| -------- | -------- |
| isNotificationEnabled():Promise\<boolean\>       | 查询通知是否授权。  |
| requestEnableNotification(context: UIAbilityContext): Promise\<void\> | 请求发送通知的许可，第一次调用会弹窗让用户选择。     |
| openNotificationSettings(context: UIAbilityContext): Promise\<void\>  | 拉起通知管理弹窗。|


## 开发步骤

1. 导入NotificationManager模块。

   <!-- @[request_enable_notification_header](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Notification/Notification/entry/src/main/ets/pages/RequestEnableNotification.ets) -->

2. 拉起通知弹窗，向用户请求通知授权。

    可通过requestEnableNotification的错误码判断用户是否授权。若返回的错误码为1600004，即为拒绝授权。

    <!-- @[request_enable_notification_permission](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Notification/Notification/entry/src/main/ets/pages/RequestEnableNotification.ets) -->

3. （可选）拉起通知管理半模态弹窗，向用户再次申请通知授权。

    <!-- @[reapply_notify_auth_halfmodal](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Notification/Notification/entry/src/main/ets/pages/RequestEnableNotification.ets) -->



