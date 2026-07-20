# emit

## 导入模块

```TypeScript
import { emitter } from '@kit.BasicServicesKit';
```

<a id="emit"></a>
## emit

```TypeScript
function emit(event: InnerEvent, data?: EventData): void
```

发送指定事件。

该接口支持跨线程传输数据对象，需要遵循数据跨线程传输的规格约束，详见[线程间通信对象](docroot://arkts-utils/serializable-overview.md)。目前不支持使用[@State装饰器](docroot://ui/state-management/arkts-state.md)、[@Observed装饰器](docroot://ui/state-management/arkts-observed-and-objectlink.md)等装饰器修饰的复杂类型数据。

该接口发布某个事件后，不保证该事件立刻执行，执行时间取决于事件队列里面的事件数量以及各事件的执行效率。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-emitter-function emit(event: InnerEvent, data?: EventData): void--><!--Device-emitter-function emit(event: InnerEvent, data?: EventData): void-End-->

**系统能力：** SystemCapability.Notification.Emitter

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [InnerEvent](arkts-basicservices-emitter-innerevent-i.md) | 是 | 发送的事件，其中[EventPriority](arkts-basicservices-emitter-eventpriority-e.md)用于指定事件被发送的优先级。 |
| data | [EventData](arkts-basicservices-emitter-eventdata-i.md) | 否 | 事件携带的数据，默认为空。 |

**示例：**

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


<a id="emit-1"></a>
## emit

```TypeScript
function emit(eventId: string, data?: EventData): void
```

发送指定事件。

该接口支持跨线程传输数据对象，需要遵循数据跨线程传输的规格约束，详见[线程间通信对象](docroot://arkts-utils/serializable-overview.md)。目前不支持使用[@State装饰器](docroot://ui/state-management/arkts-state.md)、[@Observed装饰器](docroot://ui/state-management/arkts-observed-and-objectlink.md)等装饰器修饰的复杂类型数据。

该接口发布某个事件后，不保证该事件立刻执行，执行时间取决于事件队列里面的事件数量以及各事件的执行效率。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-emitter-function emit(eventId: string, data?: EventData): void--><!--Device-emitter-function emit(eventId: string, data?: EventData): void-End-->

**系统能力：** SystemCapability.Notification.Emitter

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventId | string | 是 | 发送的事件ID。取值为长度不超过10240字节的自定义字符串，且不可为空字符。 |
| data | [EventData](arkts-basicservices-emitter-eventdata-i.md) | 否 | 事件携带的数据，默认为空。 |

**示例：**

```TypeScript
let eventData: emitter.EventData = {
  data: {
    "content": "content",
    "id": 1,
  }
};

emitter.emit('eventId', eventData);

```


<a id="emit-2"></a>
## emit

```TypeScript
function emit<T>(eventId: string, data?: GenericEventData<T>): void
```

发送指定事件。

该接口支持跨线程传输数据对象，需要遵循数据跨线程传输的规格约束，详见[线程间通信对象](docroot://arkts-utils/serializable-overview.md)。目前不支持使用[@State装饰器](docroot://ui/state-management/arkts-state.md)、[@Observed装饰器](docroot://ui/state-management/arkts-observed-and-objectlink.md)等装饰器修饰的复杂类型数据。

该接口发布某个事件后，不保证该事件立刻执行，执行时间取决于事件队列里面的事件数量以及各事件的执行效率。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-emitter-function emit<T>(eventId: string, data?: GenericEventData<T>): void--><!--Device-emitter-function emit<T>(eventId: string, data?: GenericEventData<T>): void-End-->

**系统能力：** SystemCapability.Notification.Emitter

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventId | string | 是 | 发送的事件ID。取值为长度不超过10240字节的自定义字符串，且不可为空字符。 |
| data | [GenericEventData](arkts-basicservices-emitter-genericeventdata-i.md)&lt;T&gt; | 否 | 事件携带的数据，默认为空。 |

**示例：**

```TypeScript
@Sendable
class Sample {
  constructor() {
    this.count = 100;
  }
  printCount() {
    console.info('Print count : ' + this.count);
  }
  count: number;
}

let eventData: emitter.GenericEventData<Sample> = {
  data: new Sample()
};
emitter.emit('eventId', eventData);

```


<a id="emit-3"></a>
## emit

```TypeScript
function emit(eventId: string, options: Options, data?: EventData): void
```

发送指定优先级事件。

该接口支持跨线程传输数据对象，需要遵循数据跨线程传输的规格约束，详见[线程间通信对象](docroot://arkts-utils/serializable-overview.md)。目前不支持使用[@State装饰器](docroot://ui/state-management/arkts-state.md)、[@Observed装饰器](docroot://ui/state-management/arkts-observed-and-objectlink.md)等装饰器修饰的复杂类型数据。

该接口发布某个事件后，不保证该事件立刻执行，执行时间取决于事件队列里面的事件数量以及各事件的执行效率。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-emitter-function emit(eventId: string, options: Options, data?: EventData): void--><!--Device-emitter-function emit(eventId: string, options: Options, data?: EventData): void-End-->

**系统能力：** SystemCapability.Notification.Emitter

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventId | string | 是 | 发送的事件ID。取值为长度不超过10240字节的自定义字符串，且不可为空字符。 |
| options | [Options](arkts-basicservices-zlib-options-i.md) | 是 | 事件优先级。 |
| data | [EventData](arkts-basicservices-emitter-eventdata-i.md) | 否 | 事件携带的数据，默认为空。 |

**示例：**

```TypeScript
let eventData: emitter.EventData = {
  data: {
    "content": "content",
    "id": 1,
  }
};

let options: emitter.Options = {
  priority: emitter.EventPriority.HIGH
};

emitter.emit('eventId', options, eventData);

```


<a id="emit-4"></a>
## emit

```TypeScript
function emit<T>(eventId: string, options: Options, data?: GenericEventData<T>): void
```

发送指定优先级事件。

该接口支持跨线程传输数据对象，需要遵循数据跨线程传输的规格约束，详见[线程间通信对象](docroot://arkts-utils/serializable-overview.md)。目前不支持使用[@State装饰器](docroot://ui/state-management/arkts-state.md)、[@Observed装饰器](docroot://ui/state-management/arkts-observed-and-objectlink.md)等装饰器修饰的复杂类型数据。

该接口发布某个事件后，不保证该事件立刻执行，执行时间取决于事件队列里面的事件数量以及各事件的执行效率。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-emitter-function emit<T>(eventId: string, options: Options, data?: GenericEventData<T>): void--><!--Device-emitter-function emit<T>(eventId: string, options: Options, data?: GenericEventData<T>): void-End-->

**系统能力：** SystemCapability.Notification.Emitter

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventId | string | 是 | 发送的事件ID。取值为长度不超过10240字节的自定义字符串，且不可为空字符。 |
| options | [Options](arkts-basicservices-zlib-options-i.md) | 是 | 事件优先级。 |
| data | [GenericEventData](arkts-basicservices-emitter-genericeventdata-i.md)&lt;T&gt; | 否 | 事件携带的数据，默认为空。 |

**示例：**

```TypeScript
@Sendable
class Sample {
  constructor() {
    this.count = 100;
  }
  printCount() {
    console.info('Print count : ' + this.count);
  }
  count: number;
}

let options: emitter.Options = {
  priority: emitter.EventPriority.HIGH
};
let eventData: emitter.GenericEventData<Sample> = {
  data: new Sample()
};

emitter.emit('eventId', options, eventData);

```

