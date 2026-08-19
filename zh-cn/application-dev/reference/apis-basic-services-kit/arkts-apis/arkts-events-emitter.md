# @ohos.events.emitter

本模块提供进程内线程间或线程内事件的发送与处理能力。开发者可以使用本模块的 API，订阅事件（持续订阅或 单次订阅）、取消订阅事件，发送事件到事件队列中，以及查询事件的订阅数量，从而实现同一进程内不同线程之 间、以及同一线程内的事件通信。适用于跨线程通信、模块解耦、事件驱动等场景，能够帮助开发者实现轻量级 的发布-订阅模式，降低组件间的耦合度，提升代码的可维护性和可扩展性。 提供两种事件处理入口，开发者可根据隔离需求选择： - **命名空间级 API**（`emitter` 命名空间下的 `on`、`once`、`off`、`emit`、`getListenerCount` 等函 数）：提供进程内全局范围的事件订阅与发布能力。该入口基于全局事件队列工作，同进程内任意线程均可订阅和 发布事件，适用于跨线程事件通信。 - **实例级 API**（`Emitter` 类）：提供同一 `Emitter` 实例范围内的事件订阅与发布能力。不同 `Emitter` 实例之间相互隔离，开发者可创建多个独立的事件通信通道，适用于需要事件隔离或按实例分组的 场景。 **API 组合使用关系说明：** 本模块的事件通信遵循"订阅 → 发布 → 处理 → 取消订阅"的组合调用模式。无论是命名空间级 API 还是实例 级 API，均需先订阅事件，再由其他线程或同一线程发布事件，收到事件后执行回调处理；当不再需要接收事件 时，应取消订阅以释放资源。同时，事件订阅具有明确的生命周期，开发者应注意资源管理： - **持续订阅**（`on`）：订阅后持续有效，直至调用 `off` 取消订阅。若未取消，订阅将一直保留。 - **单次订阅**（`once`）：订阅后，仅在首次接收到事件并执行回调后自动取消，无需手动调用 `off`。 - **取消订阅的时机**：调用 `off` 取消订阅后，已通过 `emit` 发布但尚未执行的事件也将被取消，不再 触发回调。同时需要注意，取消指定回调时，需传入对应的 `callback` 函数；若未指定，表示取消该事件的所有 订阅。

**起始版本：** 23

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
| [emit_InnerEvent](arkts-basicservices-emitter-emitinnerevent-f.md#emit_innerevent) | 发送指定事件。 该接口支持跨线程传输数据对象，需要遵循数据跨线程传输的规格约束，详见[线程间通信对象](../../../arkts-utils/serializable-overview.md)。目前不支持使用 [@State装饰器](../../../ui/state-management/arkts-state.md)、 [@Observed装饰器](../../../ui/state-management/arkts-observed-and-objectlink.md)等装饰器修饰的复杂类型数据。 该接口发布某个事件后，不保证该事件立刻执行，执行时间取决于事件队列里面的事件数量以及各事件的执行效率。 |
| [emit_string](arkts-basicservices-emitter-emitstring-f.md#emit_string) | 发送指定事件。 该接口支持跨线程传输数据对象，需要遵循数据跨线程传输的规格约束，详见[线程间通信对象](../../../arkts-utils/serializable-overview.md)。目前不支持使用 [@State装饰器](../../../ui/state-management/arkts-state.md)、 [@Observed装饰器](../../../ui/state-management/arkts-observed-and-objectlink.md)等装饰器修饰的复杂类型数据。 该接口发布某个事件后，不保证该事件立刻执行，执行时间取决于事件队列里面的事件数量以及各事件的执行效率。 |
| [emit_string](arkts-basicservices-emitter-emitstring-f.md#emit_string) | 发送指定事件。 该接口支持跨线程传输数据对象，需要遵循数据跨线程传输的规格约束，详见ArkTS-Sta并发迁移规则 |
| [emit_string](arkts-basicservices-emitter-emitstring-f.md#emit_string) | 发送指定事件。 该接口支持跨线程传输数据对象，需要遵循数据跨线程传输的规格约束，详见ArkTS-Sta并发迁移规则 |
| [emit_string](arkts-basicservices-emitter-emitstring-f.md#emit_string) | 发送指定事件。 该接口支持跨线程传输数据对象，需要遵循数据跨线程传输的规格约束，详见[线程间通信对象](../../../arkts-utils/serializable-overview.md)。目前不支持使用 [@State装饰器](../../../ui/state-management/arkts-state.md)、 [@Observed装饰器](../../../ui/state-management/arkts-observed-and-objectlink.md)等装饰器修饰的复杂类型数据。 该接口发布某个事件后，不保证该事件立刻执行，执行时间取决于事件队列里面的事件数量以及各事件的执行效率。 |
| [emit_string](arkts-basicservices-emitter-emitstring-f.md#emit_string) | 发送指定事件。 该接口支持跨线程传输数据对象，需要遵循数据跨线程传输的规格约束，详见ArkTS-Sta并发迁移规则 |
| [emit_string](arkts-basicservices-emitter-emitstring-f.md#emit_string) | 发送指定优先级事件。 该接口支持跨线程传输数据对象，需要遵循数据跨线程传输的规格约束，详见[线程间通信对象](../../../arkts-utils/serializable-overview.md)。目前不支持使用 [@State装饰器](../../../ui/state-management/arkts-state.md)、 [@Observed装饰器](../../../ui/state-management/arkts-observed-and-objectlink.md)等装饰器修饰的复杂类型数据。 该接口发布某个事件后，不保证该事件立刻执行，执行时间取决于事件队列里面的事件数量以及各事件的执行效率。 |
| [emit_string](arkts-basicservices-emitter-emitstring-f.md#emit_string) | 发送指定优先级事件。 该接口支持跨线程传输数据对象，需要遵循数据跨线程传输的规格约束，详见ArkTS-Sta并发迁移规则 |
| [emit_string](arkts-basicservices-emitter-emitstring-f.md#emit_string) | 发送指定优先级事件。 该接口支持跨线程传输数据对象，需要遵循数据跨线程传输的规格约束，详见ArkTS-Sta并发迁移规则 |
| [emit_string](arkts-basicservices-emitter-emitstring-f.md#emit_string) | 发送指定优先级事件。 该接口支持跨线程传输数据对象，需要遵循数据跨线程传输的规格约束，详见[线程间通信对象](../../../arkts-utils/serializable-overview.md)。目前不支持使用 [@State装饰器](../../../ui/state-management/arkts-state.md)、 [@Observed装饰器](../../../ui/state-management/arkts-observed-and-objectlink.md)等装饰器修饰的复杂类型数据。 该接口发布某个事件后，不保证该事件立刻执行，执行时间取决于事件队列里面的事件数量以及各事件的执行效率。 |
| [emit_string](arkts-basicservices-emitter-emitstring-f.md#emit_string) | 发送指定优先级事件。 该接口支持跨线程传输数据对象，需要遵循数据跨线程传输的规格约束，详见ArkTS-Sta并发迁移规则 |
| [getListenerCount](arkts-basicservices-emitter-getlistenercount-f.md) | 获取指定事件的订阅数。 |
| [offEventData](arkts-basicservices-emitter-offeventdata-f.md) | 取消事件ID为eventId且回调处理函数为callback的订阅。仅当已使用 [onEventData](arkts-basicservices-emitter-oneventdata-f.md)或 [onceEventData](arkts-basicservices-emitter-onceeventdata-f.md)接口订阅callback时，该接口才生效。 使用该接口取消某个事件订阅后，已通过emit接口发布但尚未被执行的事件将被取消。 |
| [offGenericEventData](arkts-basicservices-emitter-offgenericeventdata-f.md) | 取消订阅当前Emitter类实例的事件。仅当已使用 onGenericEventData或 onceGenericEventData接口订阅了事件ID为eventId且回调处理函数为callback的事件时，该接口才生效。 使用该接口取消事件订阅后，已通过emit接口发布但尚未执行的事件将被取消。 |
| [off_long](arkts-basicservices-emitter-offlong-f.md#off_long) | 取消事件ID为eventId的所有订阅。 使用该接口取消某个事件订阅后，已通过emit接口发布但尚未被执行的事件将被取消。 |
| [off_long](arkts-basicservices-emitter-offlong-f.md#off_long) | 取消事件ID为eventId且回调处理函数为callback的订阅。仅当已使用[on](arkts-basicservices-emitter-oninnerevent-f.md#on_innerevent)或 once接口订阅callback时，该接口才生效。 使用该接口取消某个事件订阅后，已通过emit接口发布但尚未被执行的事件将被取消。 |
| [off_string](arkts-basicservices-emitter-offstring-f.md#off_string) | 取消事件ID为eventId的所有订阅。 使用该接口取消某个事件订阅后，已通过emit接口发布但尚未被执行的事件将被取消。 |
| [off_string](arkts-basicservices-emitter-offstring-f.md#off_string) | 取消事件ID为eventId且回调处理函数为callback的订阅。仅当已使用[on](arkts-basicservices-emitter-oninnerevent-f.md#on_innerevent)或 once接口订阅callback时，该接口才生效。 使用该接口取消某个事件订阅后，已通过emit接口发布但尚未被执行的事件将被取消。 |
| [off_string](arkts-basicservices-emitter-offstring-f.md#off_string) | 取消事件ID为eventId且回调处理函数为callback的订阅。仅当已使用 on或 once接口订阅callback时，该接口才生效。 使用该接口取消某个事件订阅后，已通过emit接口发布但尚未被执行的事件将被取消。 |
| [onEventData](arkts-basicservices-emitter-oneventdata-f.md) | 持续订阅指定的事件，并在接收到该事件时，使用callback异步回调。 |
| [onGenericEventData](arkts-basicservices-emitter-ongenericeventdata-f.md) | 持续订阅指定的事件，并在接收到该事件时，使用callback异步回调。 |
| [on_InnerEvent](arkts-basicservices-emitter-oninnerevent-f.md#on_innerevent) | 持续订阅指定的事件，并在接收到该事件时，执行对应的回调处理函数。 |
| [on_string](arkts-basicservices-emitter-onstring-f.md#on_string) | 持续订阅指定的事件，并在接收到该事件时，执行对应的回调处理函数。 |
| [on_string](arkts-basicservices-emitter-onstring-f.md#on_string) | 持续订阅指定的事件，并在接收到该事件时，执行对应的回调处理函数。 |
| [onceEventData](arkts-basicservices-emitter-onceeventdata-f.md) | 单次订阅指定的事件，在接收到该事件且执行完对应的回调函数后，自动取消订阅。 |
| [onceGenericEventData](arkts-basicservices-emitter-oncegenericeventdata-f.md) | 单次订阅当前Emitter类实例指定的事件，在接收到该事件且执行完相应的回调函数后，自动取消订阅。使用callback异步回调。 |
| [once_InnerEvent](arkts-basicservices-emitter-onceinnerevent-f.md#once_innerevent) | 单次订阅指定的事件，在接收到该事件且执行完对应的回调处理函数后，自动取消订阅。 |
| [once_string](arkts-basicservices-emitter-oncestring-f.md#once_string) | 单次订阅指定的事件，在接收到该事件且执行完对应的回调处理函数后，自动取消订阅。 |
| [once_string](arkts-basicservices-emitter-oncestring-f.md#once_string) | 单次订阅指定的事件，在接收到该事件且执行完对应的回调处理函数后，自动取消订阅。 |

### 类

| 名称 | 说明 |
| --- | --- |
| [Emitter](arkts-basicservices-emitter-emitter-c.md) | 该功能支持在同一进程的同一Emitter类实例中，跨不同线程或同一线程内发送和处理事件。它能够实现持续订阅 事件、单次订阅事件、取消订阅事件以及将事件发送到事件队列，适用于需要基于独立实例进行线程间通信和 事件管理的场景，不同Emitter实例类之间相互隔离，互不影响。 |

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

