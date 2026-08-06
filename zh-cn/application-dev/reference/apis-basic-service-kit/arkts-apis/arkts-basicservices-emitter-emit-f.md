# emit

## emit

```TypeScript
function emit(event: InnerEvent, data?: EventData): void
```

发送指定事件。 该接口支持跨线程传输数据对象，需要遵循数据跨线程传输的规格约束，详见\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_。目前不支持使用 \_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_、 \_\_\_MD\_LINK\_DESC\_USD\_2\_\_\_等装饰器修饰的复杂类型数据。 该接口发布某个事件后，不保证该事件立刻执行，执行时间取决于事件队列里面的事件数量以及各事件的执行效率。

**起始版本：** 7

**ArkTS模式：** ArkTS-Dyn起始版本为7；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-emitter-function emit(event: InnerEvent, data?: EventData): void--><!--Device-emitter-function emit(event: InnerEvent, data?: EventData): void-End-->

**系统能力：** SystemCapability.Notification.Emitter

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 发送的事件，其中[EventPriority]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_用于指定事件被发送的优先级。 |
| data | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 事件携带的数据，默认为空。 |

**示例：**

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


## emit

```TypeScript
function emit(eventId: string, data?: EventData): void
```

发送指定事件。 该接口支持跨线程传输数据对象，需要遵循数据跨线程传输的规格约束，详见\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_。目前不支持使用 \_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_、 \_\_\_MD\_LINK\_DESC\_USD\_2\_\_\_等装饰器修饰的复杂类型数据。 该接口发布某个事件后，不保证该事件立刻执行，执行时间取决于事件队列里面的事件数量以及各事件的执行效率。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-emitter-function emit(eventId: string, data?: EventData): void--><!--Device-emitter-function emit(eventId: string, data?: EventData): void-End-->

**系统能力：** SystemCapability.Notification.Emitter

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventId | string | 是 | 发送的事件ID。不可为空字符串，大小不超过10240字节，超出部分会被截断。 |
| data | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 事件携带的数据，默认为空。 |

**示例：**

```TypeScript
let eventData: emitter.EventData = {
  data: {
  "content": "content",
  "id": 1,
  }
};

emitter.emit("eventId", eventData);
```


## emit

```TypeScript
function emit(eventId: string): void
```

发送指定事件。 该接口支持跨线程传输数据对象，需要遵循数据跨线程传输的规格约束，详见\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-emitter-function emit(eventId: string): void--><!--Device-emitter-function emit(eventId: string): void-End-->

**系统能力：** SystemCapability.Notification.Emitter

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventId | string | 是 | 发送的事件ID。取值为长度不超过10240字节的自定义字符串，且不可为空字符。 |

**示例：**

```TypeScript
emitter.emit("eventId");
```


## emit

```TypeScript
function emit(eventId: string, data: EventData): void
```

发送指定事件。 该接口支持跨线程传输数据对象，需要遵循数据跨线程传输的规格约束，详见\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-emitter-function emit(eventId: string, data: EventData): void--><!--Device-emitter-function emit(eventId: string, data: EventData): void-End-->

**系统能力：** SystemCapability.Notification.Emitter

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventId | string | 是 | 发送的事件ID。取值为长度不超过10240字节的自定义字符串，且不可为空字符。 |
| data | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 事件携带的数据。 |

**示例：**

```TypeScript
import { RecordData } from '@ohos.base';

let record: Record<string, RecordData> = {
  "content": "content",
  "id": 1,
};

let eventData: emitter.EventData = {
  data: record // 现在类型兼容
};

emitter.emit("eventId", eventData);
```


## emit

```TypeScript
function emit<T>(eventId: string, data?: GenericEventData<T>): void
```

发送指定事件。 该接口支持跨线程传输数据对象，需要遵循数据跨线程传输的规格约束，详见\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_。目前不支持使用 \_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_、 \_\_\_MD\_LINK\_DESC\_USD\_2\_\_\_等装饰器修饰的复杂类型数据。 该接口发布某个事件后，不保证该事件立刻执行，执行时间取决于事件队列里面的事件数量以及各事件的执行效率。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-emitter-function emit<T>(eventId: string, data?: GenericEventData<T>): void--><!--Device-emitter-function emit<T>(eventId: string, data?: GenericEventData<T>): void-End-->

**系统能力：** SystemCapability.Notification.Emitter

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventId | string | 是 | 发送的事件ID。不可为空字符串，大小不超过10240字节，超出部分会被截断。 |
| data | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;T&gt; | 否 | 事件携带的数据，默认为空。 |

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
emitter.emit("eventId", eventData);
```


## emit

```TypeScript
function emit<T>(eventId: string, data: GenericEventData<T>): void
```

发送指定事件。 该接口支持跨线程传输数据对象，需要遵循数据跨线程传输的规格约束，详见\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-emitter-function emit<T>(eventId: string, data: GenericEventData<T>): void--><!--Device-emitter-function emit<T>(eventId: string, data: GenericEventData<T>): void-End-->

**系统能力：** SystemCapability.Notification.Emitter

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventId | string | 是 | 发送的事件ID。取值为长度不超过10240字节的自定义字符串，且不可为空字符。 |
| data | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;T&gt; | 是 | 事件携带的数据，默认为空。 |


## emit

```TypeScript
function emit(eventId: string, options: Options, data?: EventData): void
```

发送指定优先级事件。 该接口支持跨线程传输数据对象，需要遵循数据跨线程传输的规格约束，详见\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_。目前不支持使用 \_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_、 \_\_\_MD\_LINK\_DESC\_USD\_2\_\_\_等装饰器修饰的复杂类型数据。 该接口发布某个事件后，不保证该事件立刻执行，执行时间取决于事件队列里面的事件数量以及各事件的执行效率。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-emitter-function emit(eventId: string, options: Options, data?: EventData): void--><!--Device-emitter-function emit(eventId: string, options: Options, data?: EventData): void-End-->

**系统能力：** SystemCapability.Notification.Emitter

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventId | string | 是 | 发送的事件ID。不可为空字符串，大小不超过10240字节，超出部分会被截断。 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 事件优先级。 |
| data | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 事件携带的数据，默认为空。 |

**示例：**

ArkTS-Dyn示例：

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

emitter.emit("eventId", options, eventData);
```


## emit

```TypeScript
function emit(eventId: string, options: Options): void
```

发送指定优先级事件。 该接口支持跨线程传输数据对象，需要遵循数据跨线程传输的规格约束，详见\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-emitter-function emit(eventId: string, options: Options): void--><!--Device-emitter-function emit(eventId: string, options: Options): void-End-->

**系统能力：** SystemCapability.Notification.Emitter

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventId | string | 是 | 发送的事件ID。取值为长度不超过10240字节的自定义字符串，且不可为空字符。 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 事件优先级。 |

**示例：**

```TypeScript
let options: emitter.Options = {
  priority: emitter.EventPriority.HIGH
};

emitter.emit("eventId", options);
```


## emit

```TypeScript
function emit(eventId: string, options: Options, data: EventData): void
```

发送指定优先级事件。 该接口支持跨线程传输数据对象，需要遵循数据跨线程传输的规格约束，详见\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-emitter-function emit(eventId: string, options: Options, data: EventData): void--><!--Device-emitter-function emit(eventId: string, options: Options, data: EventData): void-End-->

**系统能力：** SystemCapability.Notification.Emitter

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventId | string | 是 | 发送的事件ID。取值为长度不超过10240字节的自定义字符串，且不可为空字符。 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 事件优先级。 |
| data | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 事件携带的数据，默认为空。 |

**示例：**

```TypeScript
let record: Record<string, RecordData> = {
  "content": "content",
  "id": 1,
};

let eventData: emitter.EventData = {
  data: record // 现在类型兼容
};

let options: emitter.Options = {
  priority: emitter.EventPriority.HIGH
};

emitter.emit("eventId", options, eventData);
```


## emit

```TypeScript
function emit<T>(eventId: string, options: Options, data?: GenericEventData<T>): void
```

发送指定优先级事件。 该接口支持跨线程传输数据对象，需要遵循数据跨线程传输的规格约束，详见\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_。目前不支持使用 \_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_、 \_\_\_MD\_LINK\_DESC\_USD\_2\_\_\_等装饰器修饰的复杂类型数据。 该接口发布某个事件后，不保证该事件立刻执行，执行时间取决于事件队列里面的事件数量以及各事件的执行效率。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-emitter-function emit<T>(eventId: string, options: Options, data?: GenericEventData<T>): void--><!--Device-emitter-function emit<T>(eventId: string, options: Options, data?: GenericEventData<T>): void-End-->

**系统能力：** SystemCapability.Notification.Emitter

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventId | string | 是 | 发送的事件ID。不可为空字符串，大小不超过10240字节，超出部分会被截断。 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 事件优先级。 |
| data | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;T&gt; | 否 | 事件携带的数据，默认为空。 |

**示例：**

ArkTS-Dyn示例：

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

emitter.emit("eventId", options, eventData);
```

ArkTS-Sta示例：

```TypeScript
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

emitter.emit("eventId", options, eventData);
```


## emit

```TypeScript
function emit<T>(eventId: string, options: Options, data: GenericEventData<T>): void
```

发送指定优先级事件。 该接口支持跨线程传输数据对象，需要遵循数据跨线程传输的规格约束，详见\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-emitter-function emit<T>(eventId: string, options: Options, data: GenericEventData<T>): void--><!--Device-emitter-function emit<T>(eventId: string, options: Options, data: GenericEventData<T>): void-End-->

**系统能力：** SystemCapability.Notification.Emitter

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventId | string | 是 | 发送的事件ID。取值为长度不超过10240字节的自定义字符串，且不可为空字符。 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 事件优先级。 |
| data | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;T&gt; | 是 | 事件携带的数据，默认为空。 |

