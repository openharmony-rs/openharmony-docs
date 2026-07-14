# @ohos.commonEventManager

本模块提供了公共事件相关的能力，包括发布公共事件、订阅公共事件、以及退订公共事件。

**起始版本：** 9

**系统能力：** SystemCapability.Notification.CommonEvent

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [createSubscriber](arkts-basicservices-createsubscriber-f.md#createsubscriber-1) | 创建订阅者。使用callback异步回调。 |
| [createSubscriber](arkts-basicservices-createsubscriber-f.md#createsubscriber-2) | 创建订阅者。使用Promise异步回调。 |
| [createSubscriberSync](arkts-basicservices-createsubscribersync-f.md#createsubscribersync-1) | createSubscriber的同步接口。 |
| [publish](arkts-basicservices-publish-f.md#publish-1) | 发布公共事件。使用callback异步回调。 |
| [publish](arkts-basicservices-publish-f.md#publish-2) | 发布公共事件。使用callback异步回调。 |
| [subscribe](arkts-basicservices-subscribe-f.md#subscribe-1) | 订阅公共事件。使用callback异步回调。 |
| [subscribeToEvent](arkts-basicservices-subscribetoevent-f.md#subscribetoevent-1) | 订阅公共事件，并返回订阅成功或失败信息。使用Promise异步回调。 |
| [unsubscribe](arkts-basicservices-unsubscribe-f.md#unsubscribe-1) | 取消订阅公共事件。使用callback异步回调。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [publishAsUser](arkts-basicservices-publishasuser-f-sys.md#publishasuser-1) | 向指定用户发布公共事件。使用callback异步回调。 |
| [publishAsUser](arkts-basicservices-publishasuser-f-sys.md#publishasuser-2) | 向指定用户发布公共事件并指定发布信息。使用callback异步回调。 |
| [removeStickyCommonEvent](arkts-basicservices-removestickycommonevent-f-sys.md#removestickycommonevent-1) | 移除粘性公共事件。使用callback异步回调。 |
| [removeStickyCommonEvent](arkts-basicservices-removestickycommonevent-f-sys.md#removestickycommonevent-2) | 移除粘性公共事件。使用Promise异步回调。 |
| [setStaticSubscriberState](arkts-basicservices-setstaticsubscriberstate-f-sys.md#setstaticsubscriberstate-1) | 为当前应用设置静态订阅事件使能或去使能状态。使用callback异步回调。 |
| [setStaticSubscriberState](arkts-basicservices-setstaticsubscriberstate-f-sys.md#setstaticsubscriberstate-2) | 为当前应用设置静态订阅事件使能或去使能状态。使用Promise异步回调。 |
| [setStaticSubscriberState](arkts-basicservices-setstaticsubscriberstate-f-sys.md#setstaticsubscriberstate-3) | 为当前应用设置静态订阅事件的使能状态，并且记录事件名称。使用Promise异步回调。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [Support](arkts-basicservices-support-e.md) | 系统公共事件是指由系统服务或系统应用发布的事件，订阅这些公共事件需要特定的权限、使用相应的值。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [Support](arkts-basicservices-support-e-sys.md) | 系统公共事件是指由系统服务或系统应用发布的事件，订阅这些公共事件需要特定的权限、使用相应的值。 |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [CommonEventData](arkts-basicservices-commoneventdata-t.md) | 表示公共事件的数据。 |
| [CommonEventPublishData](arkts-basicservices-commoneventpublishdata-t.md) | 描述公共事件内容和属性。 |
| [CommonEventSubscribeInfo](arkts-basicservices-commoneventsubscribeinfo-t.md) | 用于表示订阅者的信息。 |
| [CommonEventSubscriber](arkts-basicservices-commoneventsubscriber-t.md) | 描述公共事件的订阅者。 |

