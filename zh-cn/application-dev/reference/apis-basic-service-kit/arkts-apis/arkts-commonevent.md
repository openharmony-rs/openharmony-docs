# @ohos.commonEvent

本模块提供了公共事件的能力，包括公共事件的权限列表，发布公共事件，订阅或取消订阅公共事件，获取或修改公共事件结果代码、结果数据等。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [commonEventManager:commonEventManager](arkts-commoneventmanager.md)

<!--Device-unnamed-declare namespace commonEvent--><!--Device-unnamed-declare namespace commonEvent-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [createSubscriber](arkts-basicservices-commonevent-createsubscriber-depr-f.md#createsubscriber) | 以回调形式创建订阅者。 |
| [createSubscriber](arkts-basicservices-commonevent-createsubscriber-depr-f.md#createsubscriber-1) | 以Promise形式创建订阅者。 |
| [publish](arkts-basicservices-commonevent-publish-depr-f.md#publish) | 发布公共事件（回调形式）。 |
| [publish](arkts-basicservices-commonevent-publish-depr-f.md#publish-1) | 以回调的形式发布公共事件。 |
| [subscribe](arkts-basicservices-commonevent-subscribe-depr-f.md#subscribe) | 以回调形式订阅公共事件。 |
| [unsubscribe](arkts-basicservices-commonevent-unsubscribe-depr-f.md#unsubscribe) | 以回调形式取消订阅公共事件。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [publishAsUser](arkts-basicservices-commonevent-publishasuser-depr-f-sys.md#publishasuser) | 以回调的形式向指定用户发布公共事件。 |
| [publishAsUser](arkts-basicservices-commonevent-publishasuser-depr-f-sys.md#publishasuser-1) | 以回调形式向指定用户发布公共事件并指定发布信息。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [Support](arkts-basicservices-commonevent-support-depr-e.md) | 系统公共事件是指由系统服务或系统应用发布的事件，订阅这些系统公共事件需要特定的权限。 |

