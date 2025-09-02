# @ohos.events.emitter (Emitter)
<!--Kit: Basic Services Kit-->
<!--Subsystem: Notification-->
<!--Owner: @michael_woo888-->
<!--Designer: @dongqingran; @wulong158-->
<!--Tester: @wanghong1997-->
<!--Adviser: @huipeizi-->

本模块提供了在同一进程不同线程间或同一线程内发送和处理事件的能力，支持持续订阅事件、单次订阅事件、取消订阅事件及发送事件到事件队列。

> **说明：**
>
> 本模块首批接口从API version 7开始支持。后续版本新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```ts
import { emitter } from '@kit.BasicServicesKit';
```

## 权限列表

无权限要求。

## emitter.on

on(event: InnerEvent, callback: Callback\<EventData\>): void

持续订阅指定的事件，并在接收到该事件时，执行对应的回调处理函数。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**: `SystemCapability.Notification.Emitter`

**参数：**

| 参数名   | 类型                                | 必填 | 说明                                                         |
| -------- | ----------------------------------- | ---- | ------------------------------------------------------------ |
| event    | [InnerEvent](#innerevent)           | 是   | 持续订阅的事件，其中[EventPriority](#eventpriority)，在订阅事件时无需指定，也不生效。 |
| callback | Callback\<[EventData](#eventdata)\> | 是   | 接收到该事件时需要执行的回调处理函数。                       |

**示例：**

```ts
import { Callback } from '@kit.BasicServicesKit';

let innerEvent: emitter.InnerEvent = {
  eventId: 1
};

let callback: Callback<emitter.EventData> = (eventData: emitter.EventData) => {
  console.info(`data type: ${typeof eventData.data}`);
}

// 收到eventId为1的事件后执行回调函数
emitter.on(innerEvent, callback);
```

## emitter.on<sup>11+</sup>

on(eventId: string, callback:  Callback\<EventData\>): void

持续订阅指定的事件，并在接收到该事件时，执行对应的回调处理函数。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**: `SystemCapability.Notification.Emitter`

**参数：**

| 参数名   | 类型                                | 必填 | 说明                                   |
| -------- | ----------------------------------- | ---- | -------------------------------------- |
| eventId    | string                              | 是   | 持续订阅的事件。取值为长度不超过10240字节的自定义字符串，且不可为空字符。                       |
| callback | Callback\<[EventData](#eventdata)\> | 是   | 接收到该事件时需要执行的回调处理函数。 |

**示例：**

```ts
import { Callback } from '@kit.BasicServicesKit';

let callback: Callback<emitter.EventData> = (eventData: emitter.EventData) => {
  console.info(`data type: ${typeof eventData.data}`);
}
// 收到eventId为"eventId"的事件后执行回调函数
emitter.on(`eventId`, callback);
```

## emitter.on<sup>12+</sup>

on<T\>(eventId: string, callback:  Callback\<GenericEventData<T\>\>): void

持续订阅指定的事件，并在接收到该事件时，执行对应的回调处理函数。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力**: `SystemCapability.Notification.Emitter`

**参数：**

| 参数名   | 类型                                | 必填 | 说明                                   |
| -------- | ----------------------------------- | ---- | -------------------------------------- |
| eventId    | string                              | 是   | 持续订阅的事件。取值为长度不超过10240字节的自定义字符串，且不可为空字符。                       |
| callback | Callback\<[GenericEventData<T\>](#genericeventdatat12)\> | 是   | 接收到该事件时需要执行的回调处理函数。 |

**示例：**

ArkTS1.1示例：
```ts
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
  console.info(`data type: ${typeof eventData.data}`);
  if (eventData?.data instanceof Sample) {
    eventData?.data?.printCount();
  }
}
// 收到eventId为"eventId"的事件后执行回调函数
emitter.on("eventId", callback);
```

ArkTS1.2示例：
```ts
import { Callback } from '@kit.BasicServicesKit';
// ArkTS1.2中，不再依赖Sendable特性，无需添加@Sendable装饰器
class Sample {
  constructor() {
    this.count = 100;
  }
  printCount() {
    console.info('Print count : ' + this.count);
  }
  count: long;
}

let callback: Callback<emitter.GenericEventData<Sample>> = (eventData: emitter.GenericEventData<Sample>): void => {
  console.info(`data type: ${typeof eventData.data}`);
  if (eventData?.data instanceof Sample) {
    let data: Sample = eventData?.data as Sample;
    data.printCount();
  }
}
// 收到eventId为"eventId"的事件后执行回调函数
emitter.on("eventId", callback);
```

## emitter.once

once(event: InnerEvent, callback: Callback\<EventData\>): void

单次订阅指定的事件，在接收到该事件且执行完对应的回调函数后，自动取消订阅。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**: `SystemCapability.Notification.Emitter`

**参数：**

| 参数名   | 类型                                | 必填 | 说明                                                         |
| -------- | ----------------------------------- | ---- | ------------------------------------------------------------ |
| event    | [InnerEvent](#innerevent)           | 是   | 单次订阅的事件，其中[EventPriority](#eventpriority)，在订阅事件时无需指定，也不生效。 |
| callback | Callback\<[EventData](#eventdata)\> | 是   | 接收到该事件时需要执行的回调处理函数。                       |

**示例：**

```ts
import { Callback } from '@kit.BasicServicesKit';

let innerEvent: emitter.InnerEvent = {
  eventId: 1
};

let callback: Callback<emitter.EventData> = (eventData: emitter.EventData) => {
  console.info(`data type: ${typeof eventData.data}`);
}
// 收到eventId为1的事件后执行该回调函数
emitter.once(innerEvent, callback);
```

## emitter.once<sup>11+</sup>

once(eventId: string, callback: Callback\<EventData\>): void

单次订阅指定的事件，在接收到该事件且执行完对应的回调函数后，自动取消订阅。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**: `SystemCapability.Notification.Emitter`

**参数：**

| 参数名   | 类型                                | 必填 | 说明                                   |
| -------- | ----------------------------------- | ---- | -------------------------------------- |
| eventId    | string                              | 是   | 单次订阅的事件。取值为长度不超过10240字节的自定义字符串，且不可为空字符。                       |
| callback | Callback\<[EventData](#eventdata)\> | 是   | 接收到该事件时需要执行的回调处理函数。 |

**示例：**

```ts
import { Callback } from '@kit.BasicServicesKit';

let callback: Callback<emitter.EventData> = (eventData: emitter.EventData) => {
  console.info(`data type: ${typeof eventData.data}`);
}
// 收到eventId为"eventId"的事件后执行该回调函数
emitter.once("eventId", callback);
```

## emitter.once<sup>12+</sup>

once<T\>(eventId: string, callback: Callback\<GenericEventData<T\>\>): void

单次订阅指定的事件，在接收到该事件且执行完相应的回调函数后，自动取消订阅。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力**: `SystemCapability.Notification.Emitter`

**参数：**

| 参数名   | 类型                                | 必填 | 说明                                   |
| -------- | ----------------------------------- | ---- | -------------------------------------- |
| eventId    | string                              | 是   | 单次订阅的事件。取值为长度不超过10240字节的自定义字符串，且不可为空字符。                       |
| callback | Callback\<[GenericEventData<T\>](#genericeventdatat12)\> | 是   | 接收到该事件时需要执行的回调处理函数。 |

**示例：**

ArkTS1.1示例：
```ts
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
  console.info(`data type: ${typeof eventData.data}`);
  if (eventData?.data instanceof Sample) {
    eventData?.data?.printCount();
  }
}
// 收到eventId为"eventId"的事件后执行回调函数
emitter.once("eventId", callback);
```

ArkTS1.2示例：
```ts
import { Callback } from '@kit.BasicServicesKit';

// ArkTS1.2中，不再依赖Sendable特性，无需添加@Sendable装饰器
class Sample {
  constructor() {
    this.count = 100;
  }
  printCount() {
    console.info('Print count : ' + this.count);
  }
  count: long;
}

let callback: Callback<emitter.GenericEventData<Sample>> = (eventData: emitter.GenericEventData<Sample>): void => {
  console.info(`data type: ${typeof eventData.data}`);
  if (eventData?.data instanceof Sample) {
    let data: Sample = eventData?.data as Sample;
    data.printCount();
  }
}
// 收到eventId为"eventId"的事件后执行回调函数
emitter.once("eventId", callback);
```

## emitter.off

ArkTS1.1: off(eventId: number): void

ArkTS1.2: off(eventId: long): void

取消事件ID为eventId的所有订阅。

使用该接口取消某个事件订阅后，已通过[emit](#emitteremit)接口发布但尚未被执行的事件将被取消。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**: `SystemCapability.Notification.Emitter`

**参数：**

| 参数名  | 类型   | 必填 | 说明     |
| ------- | ------ | ---- | -------- |
| eventId | ArkTS1.1: number<br/>ArkTS1.2: long | 是   | 事件ID。 |

**示例：**

```ts
// 取消eventID为1的所有事件回调处理函数
emitter.off(1);
```

## emitter.off<sup>11+</sup>

off(eventId: string): void

取消事件ID为eventId的所有订阅。

使用该接口取消某个事件订阅后，已通过[emit](#emitteremit11)接口发布但尚未被执行的事件将被取消。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**: `SystemCapability.Notification.Emitter`

**参数：**

| 参数名  | 类型   | 必填 | 说明     |
| ------- | ------ | ---- | -------- |
| eventId | string | 是   | 事件ID。取值为长度不超过10240字节的自定义字符串，且不可为空字符。 |

**示例：**

```ts
// 取消eventID为"eventId"的所有事件回调处理函数
emitter.off("eventId");
```

## emitter.off<sup>10+</sup>

ArkTS1.1: off(eventId: number, callback: Callback\<EventData\>): void

ArkTS1.2: off(eventId: long, callback: Callback\<EventData\>): void

取消事件ID为eventId且回调处理函数为callback的订阅。仅当已使用[on](#emitteron)或[once](#emitteronce)接口订阅callback时，该接口才生效。

使用该接口取消某个事件订阅后，已通过[emit](#emitteremit)接口发布但尚未被执行的事件将被取消。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**: `SystemCapability.Notification.Emitter`

**参数：**

| 参数名  | 类型   | 必填 | 说明   |
| ------- | ------ | ---- | ------ |
| eventId | ArkTS1.1: number<br/>ArkTS1.2: long | 是   | 事件ID。 |
| callback | Callback\<[EventData](#eventdata)\> | 是   | 事件的回调处理函数。   |

**示例：**

```ts
import { Callback } from '@kit.BasicServicesKit';

let callback: Callback<emitter.EventData> = (eventData: emitter.EventData) => {
  console.info(`data type: ${typeof eventData.data}`);
}
// 取消eventID为1的事件回调处理函数，callback对象应使用订阅时的对象
// 如果该回调处理函数没有被订阅，则不做任何处理
emitter.off(1, callback);
```

## emitter.off<sup>11+</sup>

off(eventId: string, callback: Callback\<EventData\>): void

取消事件ID为eventId且回调处理函数为callback的订阅。仅当已使用[on](#emitteron11)或[once](#emitteronce11)接口订阅callback时，该接口才生效。

使用该接口取消某个事件订阅后，已通过[emit](#emitteremit11)接口发布但尚未被执行的事件将被取消。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**: `SystemCapability.Notification.Emitter`

**参数：**

| 参数名   | 类型                                | 必填 | 说明                       |
| -------- | ----------------------------------- | ---- | -------------------------- |
| eventId  | string                              | 是   | 事件ID。取值为长度不超过10240字节的自定义字符串，且不可为空字符。                   |
| callback | Callback\<[EventData](#eventdata)\> | 是   | 事件的回调处理函数。 |

**示例：**

```ts
import { Callback } from '@kit.BasicServicesKit';

let callback: Callback<emitter.EventData> = (eventData: emitter.EventData) => {
  console.info(`data type: ${typeof eventData.data}`);
}
// 取消eventID为"eventId"的事件回调处理函数，callback对象应使用订阅时的对象
// 如果该回调处理函数没有被订阅，则不做任何处理
emitter.off("eventId", callback);
```

## emitter.off<sup>12+</sup>

off<T\>(eventId: string, callback: Callback\<GenericEventData<T\>\>): void

取消事件ID为eventId且回调处理函数为callback的订阅。仅当已使用[on](#emitteron12)或[once](#emitteronce12)接口订阅callback时，该接口才生效。

使用该接口取消某个事件订阅后，已通过[emit](#emitteremit12)接口发布但尚未被执行的事件将被取消。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力**: `SystemCapability.Notification.Emitter`

**参数：**

| 参数名   | 类型                                | 必填 | 说明                       |
| -------- | ----------------------------------- | ---- | -------------------------- |
| eventId  | string                              | 是   | 事件ID。取值为长度不超过10240字节的自定义字符串，且不可为空字符。                   |
| callback | Callback\<[GenericEventData<T\>](#genericeventdatat12)\> | 是   | 事件的回调处理函数。 |

**示例：**

ArkTS1.1示例：
```ts
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
  console.info(`data type: ${typeof eventData.data}`);
  if (eventData?.data instanceof Sample) {
    eventData?.data?.printCount();
  }
}
// 取消eventID为"eventId"的事件回调处理函数，callback对象应使用订阅时的对象
// 如果该回调处理函数没有被订阅，则不做任何处理
emitter.off("eventId", callback);
```

ArkTS1.2示例：
```ts
import { Callback } from '@kit.BasicServicesKit';

// ArkTS1.2中，不再依赖Sendable特性，无需添加@Sendable装饰器
class Sample {
  constructor() {
    this.count = 100;
  }
  printCount() {
    console.info('Print count : ' + this.count);
  }
  count: long;
}

let callback: Callback<emitter.GenericEventData<Sample>> = (eventData: emitter.GenericEventData<Sample>): void => {
  console.info(`data type: ${typeof eventData.data}`);
  if (eventData?.data instanceof Sample) {
    let data: Sample = eventData?.data as Sample;
    data.printCount();
  }
}
// 取消eventID为"eventId"的事件回调处理函数，callback对象应使用订阅时的对象
// 如果该回调处理函数没有被订阅，则不做任何处理
emitter.off("eventId", callback);
```

## emitter.emit

emit(event: InnerEvent, data?: EventData): void

发送指定事件。

ArkTS1.1: 该接口支持跨线程传输数据对象，需要遵循数据跨线程传输的规格约束，详见[线程间通信对象](../../arkts-utils/serializable-overview.md)。目前不支持使用[@State装饰器](../../ui/state-management/arkts-state.md)、[@Observed装饰器](../../ui/state-management/arkts-observed-and-objectlink.md)等装饰器修饰的复杂类型数据。

ArkTS1.2: 该接口支持跨线程传输数据对象，需要遵循数据跨线程传输的规格约束，详见[ArkTS1.2并发迁移规则](../../quick-start/arkts-v1.1-v1.2-concurrency-rules.md)。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**: `SystemCapability.Notification.Emitter`

**参数：**

| 参数名 | 类型                      | 必填 | 说明           |
| ------ | ------------------------- | ---- | ------------- |
| event  | [InnerEvent](#innerevent) | 是   | 发送的事件，其中[EventPriority](#eventpriority)用于指定事件被发送的优先级。 |
| data   | [EventData](#eventdata)   | 否   | 事件携带的数据。 |

**示例：**

ArkTS1.1示例：
```ts
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

ArkTS1.2示例：
```ts
let record: Record<string, Object> = {
  "content": "content",
  "id": 1,
}
let eventData: emitter.EventData = {
  data: record
};

let innerEvent: emitter.InnerEvent = {
  eventId: 1,
  priority: emitter.EventPriority.HIGH
};

emitter.emit(innerEvent, eventData);
```

## emitter.emit<sup>11+</sup>

emit(eventId: string, data?: EventData): void

发送指定事件。

ArkTS1.1: 该接口支持跨线程传输数据对象，需要遵循数据跨线程传输的规格约束，详见[线程间通信对象](../../arkts-utils/serializable-overview.md)。目前不支持使用[@State装饰器](../../ui/state-management/arkts-state.md)、[@Observed装饰器](../../ui/state-management/arkts-observed-and-objectlink.md)等装饰器修饰的复杂类型数据。

ArkTS1.2: 该接口支持跨线程传输数据对象，需要遵循数据跨线程传输的规格约束，详见[ArkTS1.2并发迁移规则](../../quick-start/arkts-v1.1-v1.2-concurrency-rules.md)。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**: `SystemCapability.Notification.Emitter`

**参数：**

| 参数名  | 类型                    | 必填 | 说明             |
| ------- | ----------------------- | ---- | ---------------- |
| eventId | string                  | 是   | 发送的事件ID。取值为长度不超过10240字节的自定义字符串，且不可为空字符。   |
| data    | [EventData](#eventdata) | 否   | 事件携带的数据。 |

**示例：**

ArkTS1.1示例：
```ts
let eventData: emitter.EventData = {
  data: {
  "content": "content",
  "id": 1,
  }
};

emitter.emit("eventId", eventData);
```

ArkTS1.2示例：
```ts
let record: Record<string, Object> = {
  "content": "content",
  "id": 1,
}
let eventData: emitter.EventData = {
  data: record
};

emitter.emit("eventId", eventData);
```

## emitter.emit<sup>12+</sup>

emit<T\>(eventId: string, data?: GenericEventData<T\>): void

发送指定事件。

ArkTS1.1: 该接口支持跨线程传输数据对象，需要遵循数据跨线程传输的规格约束，详见[线程间通信对象](../../arkts-utils/serializable-overview.md)。目前不支持使用[@State装饰器](../../ui/state-management/arkts-state.md)、[@Observed装饰器](../../ui/state-management/arkts-observed-and-objectlink.md)等装饰器修饰的复杂类型数据。

ArkTS1.2: 该接口支持跨线程传输数据对象，需要遵循数据跨线程传输的规格约束，详见[ArkTS1.2并发迁移规则](../../quick-start/arkts-v1.1-v1.2-concurrency-rules.md)。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力**: `SystemCapability.Notification.Emitter`

**参数：**

| 参数名  | 类型                    | 必填 | 说明             |
| ------- | ----------------------- | ---- | ---------------- |
| eventId | string                  | 是   | 发送的事件ID。取值为长度不超过10240字节的自定义字符串，且不可为空字符。   |
| data    | [GenericEventData<T\>](#genericeventdatat12) | 否   | 事件携带的数据。 |

**示例：**

ArkTS1.1示例：
```ts
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

ArkTS1.2示例：
```ts
// ArkTS1.2中，不再依赖Sendable特性，无需添加@Sendable装饰器
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

## emitter.emit<sup>11+</sup>

emit(eventId: string, options: Options, data?: EventData): void

发送指定优先级事件。

ArkTS1.1: 该接口支持跨线程传输数据对象，需要遵循数据跨线程传输的规格约束，详见[线程间通信对象](../../arkts-utils/serializable-overview.md)。目前不支持使用[@State装饰器](../../ui/state-management/arkts-state.md)、[@Observed装饰器](../../ui/state-management/arkts-observed-and-objectlink.md)等装饰器修饰的复杂类型数据。

ArkTS1.2: 该接口支持跨线程传输数据对象，需要遵循数据跨线程传输的规格约束，详见[ArkTS1.2并发迁移规则](../../quick-start/arkts-v1.1-v1.2-concurrency-rules.md)。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**: `SystemCapability.Notification.Emitter`

**参数：**

| 参数名  | 类型                    | 必填 | 说明             |
| ------- | ----------------------- | ---- | ---------------- |
| eventId | string                  | 是   | 发送的事件ID。取值为长度不超过10240字节的自定义字符串，且不可为空字符。   |
| options | [Options](#options11)   | 是   | 事件优先级。     |
| data    | [EventData](#eventdata) | 否   | 事件携带的数据。 |

**示例：**

ArkTS1.1示例：
```ts
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

ArkTS1.2示例：
```ts
let record: Record<string, Object> = {
  "content": "content",
  "id": 1,
}
let eventData: emitter.EventData = {
  data: record
};

let options: emitter.Options = {
  priority: emitter.EventPriority.HIGH
};

emitter.emit("eventId", options, eventData);
```

## emitter.emit<sup>12+</sup>

emit<T\>(eventId: string, options: Options, data?: GenericEventData<T\>): void

发送指定优先级事件。

ArkTS1.1: 该接口支持跨线程传输数据对象，需要遵循数据跨线程传输的规格约束，详见[线程间通信对象](../../arkts-utils/serializable-overview.md)。目前不支持使用[@State装饰器](../../ui/state-management/arkts-state.md)、[@Observed装饰器](../../ui/state-management/arkts-observed-and-objectlink.md)等装饰器修饰的复杂类型数据。

ArkTS1.2: 该接口支持跨线程传输数据对象，需要遵循数据跨线程传输的规格约束，详见[ArkTS1.2并发迁移规则](../../quick-start/arkts-v1.1-v1.2-concurrency-rules.md)。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力**: `SystemCapability.Notification.Emitter`

**参数：**

| 参数名  | 类型                    | 必填 | 说明             |
| ------- | ----------------------- | ---- | ---------------- |
| eventId | string                  | 是   | 发送的事件ID。取值为长度不超过10240字节的自定义字符串，且不可为空字符。   |
| options | [Options](#options11)   | 是   | 事件优先级。     |
| data    | [GenericEventData<T\>](#genericeventdatat12) | 否   | 事件携带的数据。 |

**示例：**

ArkTS1.1示例：
```ts
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

ArkTS1.2示例：
```ts
// ArkTS1.2中，不再依赖Sendable特性，无需添加@Sendable装饰器
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

## emitter.getListenerCount<sup>11+</sup>

ArkTS1.1: getListenerCount(eventId: number | string): number

ArkTS1.2: getListenerCount(eventId: long | string): long

获取指定事件的订阅数。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**: `SystemCapability.Notification.Emitter`

**参数：**

| 参数名  | 类型           | 必填 | 说明     |
| ------- | -------------- | ---- | -------- |
| eventId | ArkTS1.1: number \| string<br/>ArkTS1.2: long \| string | 是   | 事件ID，string类型的eventId取值为长度不超过10240字节的自定义字符串，且不可为空字符。 |

**返回值：**

| 类型     | 说明         |
| ------- |------------|
| ArkTS1.1: number<br/>ArkTS1.2: long | 指定事件的订阅数。 |


**示例：**

```ts
let count = emitter.getListenerCount("eventId");
```

## EventPriority

表示事件的优先级。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**:  `SystemCapability.Notification.Emitter`

| 名称      | 值    | 说明                                                |
| --------- | ---- | --------------------------------------------------- |
| IMMEDIATE | 0    | 表示事件被立即投递。                                  |
| HIGH      | 1    | 表示事件先于LOW优先级投递。                           |
| LOW       | 2    | 表示事件优于IDLE优先级投递，事件的默认优先级是LOW。     |
| IDLE      | 3    | 表示在没有其他事件的情况下，才投递该事件。             |

## InnerEvent

订阅或发送的事件，订阅事件时`EventPriority`不生效。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**: `SystemCapability.Notification.Emitter`

| 名称     | 类型                        | 只读 | 可选 | 说明                                 |
| -------- | ------------------------------- | ---- | ---- | ------------------------------ |
| eventId  | ArkTS1.1: number<br/>ArkTS1.2: long | 否   | 否   | 事件ID，由开发者定义，用于辨别事件。 |
| priority | [EventPriority](#eventpriority) | 否   | 是   | 事件的优先级，默认值为EventPriority.LOW。             |

## EventData

发送事件时传递的数据。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**: `SystemCapability.Notification.Emitter`

| 名称 | 类型           | 只读 | 可选 | 说明           |
| ---- | ------------------ | ---- | ---- | -------------- |
| data | ArkTS1.1: { [key: string]: any }<br/>ArkTS1.2: Record<string, Object> \| ESObject | 否   | 是   | 发送事件时传递的数据，支持数据类型包括Array、ArrayBuffer、Boolean、DataView、Date、Error、Map、Number、Object、Primitive（除了symbol）、RegExp、Set、String、TypedArray，数据大小最大为16M。 |

## Options<sup>11+</sup>

发送事件的优先级。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力**: `SystemCapability.Notification.Emitter`

| 名称     | 类型                            | 只读 | 可选 | 说明           |
| -------- | ------------------------------- | ---- | ---- | -------------- |
| priority | [EventPriority](#eventpriority) | 否   | 是   | 事件的优先级，默认值为EventPriority.LOW。 |

## GenericEventData<T\><sup>12+</sup>

发送事件时传递的泛型数据。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力**: `SystemCapability.Notification.Emitter`

| 名称     | 类型                            | 只读 | 可选 | 说明           |
| -------- | ------------------------------- | ---- | ---- | -------------- |
| data | ArkTS1.1: T<br/>ArkTS1.2: T \| ESObject | 否   | 是   | 发送事件时传递的数据。T：泛型类型，ESObject：ArkTS1.2中ArkTS1.1对象的代理类型。 |