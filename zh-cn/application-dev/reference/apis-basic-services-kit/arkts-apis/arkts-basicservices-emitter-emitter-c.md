# Emitter

该功能支持在同一进程的同一Emitter类实例中，跨不同线程或同一线程内发送和处理事件。它能够实现持续订阅 事件、单次订阅事件、取消订阅事件以及将事件发送到事件队列，适用于需要基于独立实例进行线程间通信和 事件管理的场景，不同Emitter实例类之间相互隔离，互不影响。

**起始版本：** 22

**系统能力：** SystemCapability.Notification.Emitter

## 导入模块

```TypeScript
import { emitter } from '@kit.BasicServicesKit';
```

## constructor

```TypeScript
constructor()
```

构造函数。

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Notification.Emitter

**示例**

```TypeScript
let emitter1: emitter.Emitter = new emitter.Emitter();
```

## emit

```TypeScript
emit(eventId: string, data?: EventData): void
```

发送指定事件到当前Emitter类实例。该接口支持跨线程传输数据对象，需要遵循数据跨线程传输的规格约束，详见[线程间通信对象](../../../arkts-utils/serializable-overview.md)。目前不支持使用 [@State装饰器](../../../ui/state-management/arkts-state.md)、 [@Observed装饰器](../../../ui/state-management/arkts-observed-and-objectlink.md)等装饰器修饰的复杂类型数据。该接口发布某个事件后，不保证该事件立刻执行，执行时间取决于事件队列里面的事件数量以及各事件的执行效率。

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Notification.Emitter

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventId | string | 是 | 发送的事件ID。 不可为空字符串，大小不超过10240字节，超出部分会被截断。 |
| data | [EventData](arkts-basicservices-emitter-eventdata-i.md) | 否 | 事件携带的数据，默认为空。 |

**示例**

```TypeScript
let eventData: emitter.EventData = {
  data: {
    "content": "content",
    "id": 1,
  }
};

emitter.emit('eventId', eventData);
```

```TypeScript
let emitter1: emitter.Emitter = new emitter.Emitter();
let eventData: emitter.EventData = {
  data: {
    "content": "content",
    "id": 1,
  }
};

emitter1.emit('eventId', eventData);
```

## emit

```TypeScript
emit<T>(eventId: string, data?: GenericEventData<T>): void
```

发送指定事件到当前Emitter类实例。该接口支持跨线程传输数据对象，需要遵循数据跨线程传输的规格约束，详见[线程间通信对象](../../../arkts-utils/serializable-overview.md)。目前不支持使用 [@State装饰器](../../../ui/state-management/arkts-state.md)、 [@Observed装饰器](../../../ui/state-management/arkts-observed-and-objectlink.md)等装饰器修饰的复杂类型数据。该接口发布某个事件后，不保证该事件立刻执行，执行时间取决于事件队列里面的事件数量以及各事件的执行效率。

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Notification.Emitter

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventId | string | 是 | 发送的事件ID。 不可为空字符串，大小不超过10240字节，超出部分会被截断。 |
| data | [GenericEventData](arkts-basicservices-emitter-genericeventdata-i.md)&lt;T&gt; | 否 | 事件携带的数据，默认为空。 |

**示例**

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

let emitter1: emitter.Emitter = new emitter.Emitter();

let eventData: emitter.GenericEventData<Sample> = {
  data: new Sample()
};

emitter1.emit('eventId', eventData);
```

## emit

```TypeScript
emit(eventId: string, options: Options, data?: EventData): void
```

发送指定优先级事件到当前Emitter类实例。该接口支持跨线程传输数据对象，需要遵循数据跨线程传输的规格约束，详见[线程间通信对象](../../../arkts-utils/serializable-overview.md)。目前不支持使用 [@State装饰器](../../../ui/state-management/arkts-state.md)、 [@Observed装饰器](../../../ui/state-management/arkts-observed-and-objectlink.md)等装饰器修饰的复杂类型数据。该接口发布某个事件后，不保证该事件立刻执行，执行时间取决于事件队列里面的事件数量以及各事件的执行效率。

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Notification.Emitter

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventId | string | 是 | 发送的事件ID。 不可为空字符串，大小不超过10240字节，超出部分会被截断。 |
| options | Options | 是 | 事件优先级。 |
| data | [EventData](arkts-basicservices-emitter-eventdata-i.md) | 否 | 事件携带的数据，默认为空。 |

**示例**

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

```TypeScript
let emitter1: emitter.Emitter = new emitter.Emitter();

let options: emitter.Options = {
  priority: emitter.EventPriority.HIGH
};
let eventData: emitter.EventData = {
  data: {
    "content": "content",
    "id": 1,
  }
};

emitter1.emit('eventId', options, eventData);
```

## emit

```TypeScript
emit<T>(eventId: string, options: Options, data?: GenericEventData<T>): void
```

发送指定优先级事件到当前Emitter类实例。该接口支持跨线程传输数据对象，需要遵循数据跨线程传输的规格约束，详见[线程间通信对象](../../../arkts-utils/serializable-overview.md)。目前不支持使用 [@State装饰器](../../../ui/state-management/arkts-state.md)、 [@Observed装饰器](../../../ui/state-management/arkts-observed-and-objectlink.md)等装饰器修饰的复杂类型数据。该接口发布某个事件后，不保证该事件立刻执行，执行时间取决于事件队列里面的事件数量以及各事件的执行效率。

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Notification.Emitter

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventId | string | 是 | 发送的事件ID。 不可为空字符串，大小不超过10240字节，超出部分会被截断。 |
| options | Options | 是 | 事件优先级。 |
| data | [GenericEventData](arkts-basicservices-emitter-genericeventdata-i.md)&lt;T&gt; | 否 | 事件携带的数据，默认为空。 |

**示例**

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

let emitter1: emitter.Emitter = new emitter.Emitter();

let options: emitter.Options = {
  priority: emitter.EventPriority.HIGH
};
let eventData: emitter.GenericEventData<Sample> = {
  data: new Sample()
};

emitter1.emit('eventId', options, eventData);
```

## getListenerCount

```TypeScript
getListenerCount(eventId: string): number
```

获取当前Emitter类实例指定事件的订阅数。

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Notification.Emitter

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventId | string | 是 | 事件ID。 不可为空字符串，大小不超过10240字节，超出部分会被截断。。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 指定事件的订阅数。 |

**示例**

```TypeScript
let emitter1: emitter.Emitter = new emitter.Emitter();
let count: number = emitter1.getListenerCount('eventId');
```

## off

```TypeScript
off(eventId: string): void
```

取消当前Emitter类实例事件ID为eventId的所有订阅。使用该接口取消某个事件订阅后，已通过emit接口发布但尚未被执行的事件将被取消。

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Notification.Emitter

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventId | string | 是 | 事件ID。 不可为空字符串，大小不超过10240字节，超出部分会被截断。 |

**示例**

```TypeScript
// 取消eventId为"eventId1"的所有事件回调处理函数
emitter.off('eventId1');
```

```TypeScript
let emitter1: emitter.Emitter = new emitter.Emitter();

emitter1.off('eventId');
```

## off

```TypeScript
off(eventId: string, callback: Callback<EventData>): void
```

取消订阅当前Emitter类实例的事件。仅当已使用on或 once接口订阅了事件ID为eventId且回调处理函数为 callback的事件时，该接口才生效。使用该接口取消事件订阅后，已通过emit接口发布但尚未被执行的事件将被取消。

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Notification.Emitter

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventId | string | 是 | 事件ID。 不可为空字符串，大小不超过10240字节，超出部分会被截断。 |
| callback | [Callback](arkts-basicservices-base-callback-i.md)&lt;[EventData](arkts-basicservices-emitter-eventdata-i.md)&gt; | 是 | 回调函数，指定要取消订阅的事件处理函数。 |

**示例**

```TypeScript
import { Callback } from '@kit.BasicServicesKit';

let callback: Callback<emitter.EventData> = (eventData: emitter.EventData) => {
  console.info(`eventData: ${JSON.stringify(eventData)}`);
};
// 取消eventId为"eventId1"的事件回调处理函数，callback对象应使用订阅时的对象
// 如果该回调处理函数没有被订阅，则不做任何处理
emitter.off('eventId1', callback);
```

```TypeScript
import { Callback } from '@kit.BasicServicesKit';

let emitter1: emitter.Emitter = new emitter.Emitter();

let callback: Callback<emitter.EventData> = (eventData: emitter.EventData) => {
  console.info(`eventData: ${JSON.stringify(eventData)}`);
};

emitter1.off('eventId', callback);
```

## off

```TypeScript
off<T>(eventId: string, callback: Callback<GenericEventData<T>>): void
```

取消订阅当前Emitter类实例的事件。仅当已使用 on或 once接口订阅了事件ID为eventId且 回调处理函数为callback的事件时，该接口才生效。使用该接口取消事件订阅后，已通过emit接口发布但尚未被执行的事件将被取消。

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Notification.Emitter

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventId | string | 是 | 事件ID。 不可为空字符串，大小不超过10240字节，超出部分会被截断。 |
| callback | [Callback](arkts-basicservices-base-callback-i.md)&lt;[GenericEventData](arkts-basicservices-emitter-genericeventdata-i.md)&lt;T&gt;&gt; | 是 | 回调函数，指定要取消订阅的事件处理函数。 |

**示例**

```TypeScript
import { Callback } from '@kit.BasicServicesKit';

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

let callback: Callback<emitter.GenericEventData<Sample>> = (eventData: emitter.GenericEventData<Sample>): void => {
  console.info(`eventData: ${JSON.stringify(eventData?.data)}`);
  if (eventData?.data instanceof Sample) {
    eventData?.data?.printCount();
  }
};
// 取消eventId为"eventId1"的事件回调处理函数，callback对象应使用订阅时的对象
// 如果该回调处理函数没有被订阅，则不做任何处理
emitter.off('eventId1', callback);
```

```TypeScript
import { Callback } from '@kit.BasicServicesKit';

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

let emitter1: emitter.Emitter = new emitter.Emitter();

let callback: Callback<emitter.GenericEventData<Sample>> = (eventData: emitter.GenericEventData<Sample>): void => {
  console.info(`eventData: ${JSON.stringify(eventData?.data)}`);
  if (eventData?.data instanceof Sample) {
    eventData?.data?.printCount();
  }
};

emitter1.off('eventId', callback);
```

## on

```TypeScript
on(eventId: string, callback: Callback<EventData>): void
```

持续订阅当前Emitter类实例指定的事件，并在接收到该事件时，使用callback异步回调。

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Notification.Emitter

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventId | string | 是 | 持续订阅的事件ID。 不可为空字符串，大小不超过10240字节，超出部分会被截断。 |
| callback | [Callback](arkts-basicservices-base-callback-i.md)&lt;[EventData](arkts-basicservices-emitter-eventdata-i.md)&gt; | 是 | 回调函数，在接收到该事件时被调用。 |

**示例**

```TypeScript
import { Callback } from '@kit.BasicServicesKit';

let callback: Callback<emitter.EventData> = (eventData: emitter.EventData) => {
  console.info(`eventData: ${JSON.stringify(eventData)}`);
};
// 收到eventId为"eventId"的事件后执行回调处理函数
emitter.on('eventId', callback);
```

```TypeScript
import { Callback } from '@kit.BasicServicesKit';

let emitter1: emitter.Emitter = new emitter.Emitter();

let callback: Callback<emitter.EventData> = (eventData: emitter.EventData) => {
  console.info(`eventData: ${JSON.stringify(eventData)}`);
};

emitter1.on('eventId', callback);
```

## on

```TypeScript
on<T>(eventId: string, callback: Callback<GenericEventData<T>>): void
```

持续订阅当前Emitter类实例指定的事件，并在接收到该事件时，使用callback异步回调。

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Notification.Emitter

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventId | string | 是 | 持续订阅的事件ID。 不可为空字符串，大小不超过10240字节，超出部分会被截断。 |
| callback | [Callback](arkts-basicservices-base-callback-i.md)&lt;[GenericEventData](arkts-basicservices-emitter-genericeventdata-i.md)&lt;T&gt;&gt; | 是 | 回调函数，在接收到该事件时被调用。 |

**示例**

```TypeScript
import { Callback } from '@kit.BasicServicesKit';

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

let callback: Callback<emitter.GenericEventData<Sample>> = (eventData: emitter.GenericEventData<Sample>): void => {
  console.info(`eventData: ${JSON.stringify(eventData?.data)}`);
  if (eventData?.data instanceof Sample) {
    eventData?.data?.printCount();
  }
};
// 收到eventId为"eventId"的事件后执行回调函数
emitter.on('eventId', callback);
```

```TypeScript
import { Callback } from '@kit.BasicServicesKit';

let emitter1: emitter.Emitter = new emitter.Emitter();

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

let callback: Callback<emitter.GenericEventData<Sample>> = (eventData: emitter.GenericEventData<Sample>): void => {
  console.info(`eventData: ${JSON.stringify(eventData?.data)}`);
  if (eventData?.data instanceof Sample) {
    eventData?.data?.printCount();
  }
};

emitter1.on('eventId', callback);
```

## once

```TypeScript
once(eventId: string, callback: Callback<EventData>): void
```

单次订阅当前Emitter类实例指定的事件，在接收到该事件且执行完对应的回调处理函数后，自动取消订阅。使用callback异步回调。

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Notification.Emitter

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventId | string | 是 | 单次订阅的事件ID。 不可为空字符串，大小不超过10240字节，超出部分会被截断。 |
| callback | [Callback](arkts-basicservices-base-callback-i.md)&lt;[EventData](arkts-basicservices-emitter-eventdata-i.md)&gt; | 是 | 回调函数，在接收到该事件时被调用。 |

**示例**

```TypeScript
import { Callback } from '@kit.BasicServicesKit';

let callback: Callback<emitter.EventData> = (eventData: emitter.EventData) => {
  console.info(`eventData: ${JSON.stringify(eventData)}`);
};
// 收到eventId为"eventId"的事件后执行该回调函数
emitter.once('eventId', callback);
```

```TypeScript
import { Callback } from '@kit.BasicServicesKit';

let emitter1: emitter.Emitter = new emitter.Emitter();

let callback: Callback<emitter.EventData> = (eventData: emitter.EventData) => {
  console.info(`eventData: ${JSON.stringify(eventData)}`);
};

emitter1.once('eventId', callback);
```

## once

```TypeScript
once<T>(eventId: string, callback: Callback<GenericEventData<T>>): void
```

单次订阅当前Emitter类实例指定的事件，在接收到该事件且执行完对应的回调处理函数后，自动取消订阅。使用callback异步回调。

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Notification.Emitter

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventId | string | 是 | 单次订阅的事件ID。 不可为空字符串，大小不超过10240字节，超出部分会被截断。 |
| callback | [Callback](arkts-basicservices-base-callback-i.md)&lt;[GenericEventData](arkts-basicservices-emitter-genericeventdata-i.md)&lt;T&gt;&gt; | 是 | 回调函数，在接收到该事件时被调用。 |

**示例**

```TypeScript
import { Callback } from '@kit.BasicServicesKit';

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

let callback: Callback<emitter.GenericEventData<Sample>> = (eventData: emitter.GenericEventData<Sample>): void => {
  console.info(`eventData: ${JSON.stringify(eventData?.data)}`);
  if (eventData?.data instanceof Sample) {
    eventData?.data?.printCount();
  }
};
// 收到eventId为"eventId"的事件后执行回调函数
emitter.once('eventId', callback);
```

```TypeScript
import { Callback } from '@kit.BasicServicesKit';

let emitter1: emitter.Emitter = new emitter.Emitter();

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

let callback: Callback<emitter.GenericEventData<Sample>> = (eventData: emitter.GenericEventData<Sample>): void => {
  console.info(`eventData: ${JSON.stringify(eventData?.data)}`);
  if (eventData?.data instanceof Sample) {
    eventData?.data?.printCount();
  }
};

emitter1.once('eventId', callback);
```
