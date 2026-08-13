# emit_InnerEvent

## emit_InnerEvent

```TypeScript
function emit(event: InnerEvent, data?: EventData): void
```

发送指定事件。 该接口支持跨线程传输数据对象，需要遵循数据跨线程传输的规格约束，详见[线程间通信对象](../../../arkts-utils/serializable-overview.md)。目前不支持使用 [@State装饰器](../../../ui/state-management/arkts-state.md)、 [@Observed装饰器](../../../ui/state-management/arkts-observed-and-objectlink.md)等装饰器修饰的复杂类型数据。 该接口发布某个事件后，不保证该事件立刻执行，执行时间取决于事件队列里面的事件数量以及各事件的执行效率。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-emitter-function emit(event: InnerEvent, data?: EventData): void--><!--Device-emitter-function emit(event: InnerEvent, data?: EventData): void-End-->

**系统能力：** SystemCapability.Notification.Emitter

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [InnerEvent](arkts-basicservices-emitter-innerevent-i.md) | 是 | 发送的事件，其中[EventPriority](arkts-basicservices-emitter-eventpriority-e.md#EventPriority)用于指定事件被发送的优先级。 |
| data | [EventData](arkts-basicservices-emitter-eventdata-i.md) | 否 | 事件携带的数据，默认为空。 |

## 示例

ArkTS-Dyn示例：

```TypeScript
let eventData: emitter.EventData = {
  data: {
    "content": "content",
    "id": 1,
  }
};

let innerEvent: emitter.InnerEvent = {
  eventId: 1,
  priority: emitter.EventPriority.HIGH
};

emitter.emit(innerEvent, eventData);
```

ArkTS-Sta示例：

```TypeScript
import { RecordData } from '@ohos.base';

let record: Record<string, RecordData> = {
  "content": "content",
  "id": 1,
};

let eventData: emitter.EventData = {
  data: record // 现在类型兼容
};

let innerEvent: emitter.InnerEvent = {
  eventId: 1,
  priority: emitter.EventPriority.HIGH
};

emitter.emit(innerEvent, eventData);
```

