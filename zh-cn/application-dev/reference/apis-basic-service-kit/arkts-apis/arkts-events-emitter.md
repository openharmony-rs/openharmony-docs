# @ohos.events.emitter

本模块提供了在同一进程不同线程间或同一线程内发送和处理事件的能力，支持持续订阅事件、单次订阅事件、取消订阅事件及发送事件到事件队列。

**起始版本：** 7

<!--Device-unnamed-declare namespace emitter--><!--Device-unnamed-declare namespace emitter-End-->

**系统能力：** SystemCapability.Notification.Emitter

## 导入模块

```TypeScript
import { emitter } from '@kit.BasicServicesKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [emit](arkts-basicservices-emitter-emit-f.md#emit) | 发送指定事件。  该接口支持跨线程传输数据对象，需要遵循数据跨线程传输的规格约束，详见[线程间通信对象](../../../arkts-utils/serializable-overview.md)。目前不支持使用[@State装饰器](../../../ui/state-management/arkts-state.md)、[@Observed装饰器](../../../ui/state-management/arkts-observed-and-objectlink.md)等装饰器修饰的复杂类型数据。  该接口发布某个事件后，不保证该事件立刻执行，执行时间取决于事件队列里面的事件数量以及各事件的执行效率。 |
| [emit](arkts-basicservices-emitter-emit-f.md#emit-1) | 发送指定事件。  该接口支持跨线程传输数据对象，需要遵循数据跨线程传输的规格约束，详见[线程间通信对象](../../../arkts-utils/serializable-overview.md)。目前不支持使用[@State装饰器](../../../ui/state-management/arkts-state.md)、[@Observed装饰器](../../../ui/state-management/arkts-observed-and-objectlink.md)等装饰器修饰的复杂类型数据。  该接口发布某个事件后，不保证该事件立刻执行，执行时间取决于事件队列里面的事件数量以及各事件的执行效率。 |
| [emit](arkts-basicservices-emitter-emit-f.md#emit-2) | 发送指定事件。  该接口支持跨线程传输数据对象，需要遵循数据跨线程传输的规格约束，详见[线程间通信对象](../../../arkts-utils/serializable-overview.md)。目前不支持使用[@State装饰器](../../../ui/state-management/arkts-state.md)、[@Observed装饰器](../../../ui/state-management/arkts-observed-and-objectlink.md)等装饰器修饰的复杂类型数据。  该接口发布某个事件后，不保证该事件立刻执行，执行时间取决于事件队列里面的事件数量以及各事件的执行效率。 |
| [emit](arkts-basicservices-emitter-emit-f.md#emit-3) | 发送指定优先级事件。  该接口支持跨线程传输数据对象，需要遵循数据跨线程传输的规格约束，详见[线程间通信对象](../../../arkts-utils/serializable-overview.md)。目前不支持使用[@State装饰器](../../../ui/state-management/arkts-state.md)、[@Observed装饰器](../../../ui/state-management/arkts-observed-and-objectlink.md)等装饰器修饰的复杂类型数据。  该接口发布某个事件后，不保证该事件立刻执行，执行时间取决于事件队列里面的事件数量以及各事件的执行效率。 |
| [emit](arkts-basicservices-emitter-emit-f.md#emit-4) | 发送指定优先级事件。  该接口支持跨线程传输数据对象，需要遵循数据跨线程传输的规格约束，详见[线程间通信对象](../../../arkts-utils/serializable-overview.md)。目前不支持使用[@State装饰器](../../../ui/state-management/arkts-state.md)、[@Observed装饰器](../../../ui/state-management/arkts-observed-and-objectlink.md)等装饰器修饰的复杂类型数据。  该接口发布某个事件后，不保证该事件立刻执行，执行时间取决于事件队列里面的事件数量以及各事件的执行效率。 |
| [getListenerCount](arkts-basicservices-emitter-getlistenercount-f.md#getlistenercount) | 获取指定事件的订阅数。 |
| [off](arkts-basicservices-emitter-off-f.md#off) | 取消事件ID为eventId的所有订阅。  使用该接口取消某个事件订阅后，已通过[emit](emitter.emit(eventId: string))接口发布但尚未被执行的事件将被取消。 |
| [off](arkts-basicservices-emitter-off-f.md#off-1) | 取消事件ID为eventId的所有订阅。  使用该接口取消某个事件订阅后，已通过[emit](emitter.emit(eventId: string))接口发布但尚未被执行的事件将被取消。 |
| [off](arkts-basicservices-emitter-off-f.md#off-2) | 取消事件ID为eventId且回调处理函数为callback的订阅。仅当已使用[on](emitter.on(event: InnerEvent, callback: Callback<EventData>))或[once](emitter.once(event: InnerEvent, callback: Callback<EventData>))接口订阅callback时，该接口才生效。  使用该接口取消某个事件订阅后，已通过[emit](emitter.emit(eventId: string))接口发布但尚未被执行的事件将被取消。 |
| [off](arkts-basicservices-emitter-off-f.md#off-3) | 取消事件ID为eventId且回调处理函数为callback的订阅。仅当已使用[on](emitter.on(eventId: string, callback: Callback<EventData>))或[once](emitter.once(eventId: string, callback: Callback<EventData>))接口订阅callback时，该接口才生效。  使用该接口取消某个事件订阅后，已通过[emit](emitter.emit(eventId: string))接口发布但尚未被执行的事件将被取消。 |
| [off](arkts-basicservices-emitter-off-f.md#off-4) | 取消事件ID为eventId且回调处理函数为callback的订阅。仅当已使用[on](emitter.on<T>(eventId: string, callback: Callback&lt;GenericEventData<T>&gt;))或[once](emitter.once<T>(eventId: string, callback: Callback&lt;GenericEventData<T>&gt;))接口订阅callback时，该接口才生效。  使用该接口取消某个事件订阅后，已通过[emit](emitter.emit(eventId: string))接口发布但尚未被执行的事件将被取消。 |
| [on](arkts-basicservices-emitter-on-f.md#on) | 持续订阅指定的事件，并在接收到该事件时，执行对应的回调处理函数。 |
| [on](arkts-basicservices-emitter-on-f.md#on-1) | 持续订阅指定的事件，并在接收到该事件时，执行对应的回调处理函数。 |
| [on](arkts-basicservices-emitter-on-f.md#on-2) | 持续订阅指定的事件，并在接收到该事件时，执行对应的回调处理函数。 |
| [once](arkts-basicservices-emitter-once-f.md#once) | 单次订阅指定的事件，在接收到该事件且执行完对应的回调函数后，自动取消订阅。 |
| [once](arkts-basicservices-emitter-once-f.md#once-1) | 单次订阅指定的事件，在接收到该事件且执行完对应的回调函数后，自动取消订阅。 |
| [once](arkts-basicservices-emitter-once-f.md#once-2) | 单次订阅指定的事件，在接收到该事件且执行完相应的回调函数后，自动取消订阅。 |

### 类

| 名称 | 说明 |
| --- | --- |
| [Emitter](arkts-basicservices-emitter-emitter-c.md) | 该功能支持在同一进程的同一Emitter类实例中，跨不同线程或同一线程内发送和处理事件。它能够实现持续订阅事件、单次订阅事件、取消订阅事件以及将事件发送到事件队列。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [EventData](arkts-basicservices-emitter-eventdata-i.md) | 发送事件时传递的数据。 |
| [GenericEventData](arkts-basicservices-emitter-genericeventdata-i.md) | 发送事件时传递的泛型数据。 |
| [InnerEvent](arkts-basicservices-emitter-innerevent-i.md) | 订阅或发送的事件，订阅事件时`EventPriority`不生效。 |
| [Options](arkts-basicservices-emitter-options-i.md) | 发送事件的优先级。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [EventPriority](arkts-basicservices-emitter-eventpriority-e.md) | 表示事件的优先级。 |

