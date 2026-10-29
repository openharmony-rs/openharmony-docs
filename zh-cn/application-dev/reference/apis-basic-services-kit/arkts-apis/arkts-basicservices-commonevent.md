# @ohos.commonEvent(公共事件模块)

本模块提供了公共事件的能力，包括公共事件的权限列表，发布公共事件，订阅或取消订阅公共事件，获取或修改公共事件结果代码、结果数据等。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [commonEventManager](arkts-basicservices-commoneventmanager.md)

<!--Device-unnamed-declare namespace commonEvent--><!--Device-unnamed-declare namespace commonEvent-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## 导入模块

```TypeScript
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [createSubscriber](arkts-basicservices-commonevent-createsubscriber-depr-f.md#createsubscriber-1) | 以回调形式创建订阅者。 |
| [createSubscriber](arkts-basicservices-commonevent-createsubscriber-depr-f.md#createsubscriber-2) | 以Promise形式创建订阅者。 |
| [publish](arkts-basicservices-commonevent-publish-depr-f.md#publish-1) | 以回调形式发布公共事件。 |
| [publish](arkts-basicservices-commonevent-publish-depr-f.md#publish-2) | 以回调形式发布公共事件。 |
| [subscribe](arkts-basicservices-commonevent-subscribe-depr-f.md#subscribe) | 以回调形式订阅公共事件。 |
| [unsubscribe](arkts-basicservices-commonevent-unsubscribe-depr-f.md#unsubscribe) | 以回调形式取消订阅公共事件。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [publishAsUser](arkts-basicservices-commonevent-publishasuser-depr-f-sys.md#publishasuser-1) | 以回调的形式向指定用户发布公共事件。 |
| [publishAsUser](arkts-basicservices-commonevent-publishasuser-depr-f-sys.md#publishasuser-2) | 以回调形式向指定用户发布公共事件并指定发布信息。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [Support](arkts-basicservices-commonevent-support-depr-e.md) | [系统公共事件](../../../basic-services/common-event/common-event-glossary.md#system-common-event系统公共事件)是指由系统服务或系统应用发布的事件，订阅这些系统公共事件需要相应的权限。发布或订阅这些事件需要使用如下链接中的枚举定义。 |
