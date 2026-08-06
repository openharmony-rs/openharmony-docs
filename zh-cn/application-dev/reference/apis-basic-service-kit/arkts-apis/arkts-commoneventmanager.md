# @ohos.commonEventManager

本模块提供公共事件的发布、订阅、取消订阅等能力。公共事件是一种系统级的事件通知机制，允许应用在系统状态变化 （如开机完成、电量变化、屏幕亮灭等）或业务自定义事件发生时，向订阅了该事件的应用发送通知，实现跨组件、跨 应用的信息传递。 本模块涉及的关键概念： - 无序公共事件：CES在转发公共事件时，不考虑订阅者是否接收到该事件，也不保证订阅者接收到该事件的顺序与 其订阅顺序一致。 - 有序公共事件：CES在转发公共事件时，根据订阅者设置的优先级等级，优先将公共事件发送给优先级较高的订阅 者，等待其成功接收该公共事件之后再将事件发送给优先级较低的订阅者。如果有多个订阅者具有相同的优先级， 则他们将随机接收到公共事件。 - 粘性公共事件：能够让订阅者收到在订阅前已经发送的公共事件就是粘性公共事件。普通的公共事件只能在订阅后 发送才能收到，而粘性公共事件的特殊性就是可以先发送后订阅，同时也支持先订阅后发送。发送粘性公共事件必须 是系统应用或系统服务。 **API 组合使用关系说明：** 本模块的事件通信遵循三条组合调用链：订阅流、发布流与有序事件流。其中订阅流与发布流通过事件名称关联， 发布者与订阅者无需感知对方存在。 **订阅流：创建订阅者 → 注册订阅 → 接收事件 → 取消订阅** 1. 配置订阅者信息，声明订阅的事件名称，可选设置订阅优先级、发布方权限与包名。 2. 通过\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_创建订阅者对象。 3. 通过\_\_\_INLINE\_CODE\_DESC\_USD\_1\_\_\_注册订阅，事件发布时通过回调接收\_\_\_INLINE\_CODE\_DESC\_USD\_2\_\_\_，在回调中处理事件 数据。 4. 不再需要时，通过\_\_\_INLINE\_CODE\_DESC\_USD\_3\_\_\_取消订阅。 **发布流：发布事件（可选携带数据与属性）** 1. 简单发布：通过\_\_\_INLINE\_CODE\_DESC\_USD\_4\_\_\_仅指定事件名发布事件。 2. 携带数据与属性发布：通过\_\_\_INLINE\_CODE\_DESC\_USD\_5\_\_\_配置code、data、parameters及\_\_\_INLINE\_CODE\_DESC\_USD\_6\_\_\_等属性，再调用 \_\_\_INLINE\_CODE\_DESC\_USD\_7\_\_\_发布。 **有序事件流：按优先级顺序投递 + 订阅者协作** 1. 通过\_\_\_INLINE\_CODE\_DESC\_USD\_8\_\_\_将\_\_\_INLINE\_CODE\_DESC\_USD\_9\_\_\_设为\_\_\_INLINE\_CODE\_DESC\_USD\_10\_\_\_，调用\_\_\_INLINE\_CODE\_DESC\_USD\_11\_\_\_发布有序事件，事件按订阅者优先级依 次投递。 2. 高优先级订阅者先收到事件，可在回调中通过\_\_\_INLINE\_CODE\_DESC\_USD\_12\_\_\_等方法修改code与data数据，供后续订阅者接收。 3. 处理完成后调用\_\_\_INLINE\_CODE\_DESC\_USD\_13\_\_\_，触发事件向下一优先级订阅者投递；若需中止后续投递，可调用 \_\_\_INLINE\_CODE\_DESC\_USD\_14\_\_\_标记事件为中止状态。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-unnamed-declare namespace commonEventManager--><!--Device-unnamed-declare namespace commonEventManager-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [createSubscriber](arkts-basicservices-commoneventmanager-createsubscriber-f.md#createsubscriber) | 创建订阅者。使用callback异步回调。 |
| [createSubscriber](arkts-basicservices-commoneventmanager-createsubscriber-f.md#createsubscriber-1) | 创建订阅者。使用Promise异步回调。 |
| [createSubscriberSync](arkts-basicservices-commoneventmanager-createsubscribersync-f.md#createsubscribersync) | 同步创建订阅者的接口。 |
| [publish](arkts-basicservices-commoneventmanager-publish-f.md#publish) | 发布公共事件。使用callback异步回调。 |
| [publish](arkts-basicservices-commoneventmanager-publish-f.md#publish-1) | 发布公共事件。使用callback异步回调。 |
| [subscribe](arkts-basicservices-commoneventmanager-subscribe-f.md#subscribe) | 订阅公共事件。使用callback异步回调。 |
| [subscribeToEvent](arkts-basicservices-commoneventmanager-subscribetoevent-f.md#subscribetoevent) | 订阅公共事件，并返回订阅成功或失败信息。使用Promise异步回调。 |
| [unsubscribe](arkts-basicservices-commoneventmanager-unsubscribe-f.md#unsubscribe) | 取消订阅公共事件。使用callback异步回调。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [publishAsUser](arkts-basicservices-commoneventmanager-publishasuser-f-sys.md#publishasuser) | 向指定用户发布公共事件。使用callback异步回调。 |
| [publishAsUser](arkts-basicservices-commoneventmanager-publishasuser-f-sys.md#publishasuser-1) | 向指定用户发布公共事件并指定发布信息。使用callback异步回调。 |
| [removeStickyCommonEvent](arkts-basicservices-commoneventmanager-removestickycommonevent-f-sys.md#removestickycommonevent) | 移除粘性公共事件。使用callback异步回调。 |
| [removeStickyCommonEvent](arkts-basicservices-commoneventmanager-removestickycommonevent-f-sys.md#removestickycommonevent-1) | 移除已发布的粘性公共事件。使用Promise异步回调。 |
| [setStaticSubscriberState](arkts-basicservices-commoneventmanager-setstaticsubscriberstate-f-sys.md#setstaticsubscriberstate) | 为当前应用设置静态订阅事件使能或去使能状态。使用callback异步回调。 |
| [setStaticSubscriberState](arkts-basicservices-commoneventmanager-setstaticsubscriberstate-f-sys.md#setstaticsubscriberstate-1) | 为当前应用设置静态订阅事件使能或去使能状态。使用Promise异步回调。 |
| [setStaticSubscriberState](arkts-basicservices-commoneventmanager-setstaticsubscriberstate-f-sys.md#setstaticsubscriberstate-2) | 设置当前应用的静态订阅公共事件的使能状态。使用Promise异步回调。 |
| [setStaticSubscriberState](arkts-basicservices-commoneventmanager-setstaticsubscriberstate-f-sys.md#setstaticsubscriberstate-3) | 为当前应用设置静态订阅事件的使能状态，并且记录事件名称。使用Promise异步回调。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [Support](arkts-basicservices-commoneventmanager-support-e.md) | 系统公共事件是指由系统服务或系统应用发布的事件，订阅这些公共事件需要特定的权限，并使用相应的事件值。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [Support](arkts-basicservices-commoneventmanager-support-e-sys.md) | 系统公共事件是指由系统服务或系统应用发布的事件，订阅这些公共事件需要特定的权限，并使用相应的事件值。 |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [CommonEventData](arkts-basicservices-commoneventmanager-commoneventdata-t.md) | 表示公共事件的数据。 |
| [CommonEventPublishData](arkts-basicservices-commoneventmanager-commoneventpublishdata-t.md) | 描述公共事件内容和属性。 |
| [CommonEventSubscribeInfo](arkts-basicservices-commoneventmanager-commoneventsubscribeinfo-t.md) | 描述公共事件订阅者的信息。 |
| [CommonEventSubscriber](arkts-basicservices-commoneventmanager-commoneventsubscriber-t.md) | 描述公共事件的订阅者。 |

