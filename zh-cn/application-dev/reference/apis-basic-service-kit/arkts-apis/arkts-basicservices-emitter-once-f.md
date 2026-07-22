# once

## 导入模块

```TypeScript
import { emitter } from '@kit.BasicServicesKit';
```

## once

```TypeScript
function once(event: InnerEvent, callback: Callback<EventData>): void
```

单次订阅指定的事件，在接收到该事件且执行完对应的回调函数后，自动取消订阅。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-emitter-function once(event: InnerEvent, callback: Callback<EventData>): void--><!--Device-emitter-function once(event: InnerEvent, callback: Callback<EventData>): void-End-->

**系统能力：** SystemCapability.Notification.Emitter

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [InnerEvent](arkts-basicservices-emitter-innerevent-i.md) | 是 | 单次订阅的事件，其中[EventPriority](arkts-basicservices-emitter-eventpriority-e.md)，在订阅事件时无需指定，也不生效。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;EventData&gt; | 是 | 接收到该事件时需要执行的回调处理函数。 |

**示例：**

```TypeScript
import { Callback } from '@kit.BasicServicesKit';

let innerEvent: emitter.InnerEvent = {
  eventId: 1
};

let callback: Callback<emitter.EventData> = (eventData: emitter.EventData) => {
  console.info(`eventData: ${JSON.stringify(eventData)}`);
};
// 收到eventId为1的事件后执行该回调处理函数
emitter.once(innerEvent, callback);

```


## once

```TypeScript
function once(eventId: string, callback: Callback<EventData>): void
```

单次订阅指定的事件，在接收到该事件且执行完对应的回调函数后，自动取消订阅。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-emitter-function once(eventId: string, callback: Callback<EventData>): void--><!--Device-emitter-function once(eventId: string, callback: Callback<EventData>): void-End-->

**系统能力：** SystemCapability.Notification.Emitter

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventId | string | 是 | 单次订阅的事件。取值为长度不超过10240字节的自定义字符串，且不可为空字符。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;EventData&gt; | 是 | 接收到该事件时需要执行的回调处理函数。 |

**示例：**

```TypeScript
import { Callback } from '@kit.BasicServicesKit';

let callback: Callback<emitter.EventData> = (eventData: emitter.EventData) => {
  console.info(`eventData: ${JSON.stringify(eventData)}`);
};
// 收到eventId为"eventId"的事件后执行该回调函数
emitter.once('eventId', callback);

```


## once

```TypeScript
function once<T>(eventId: string, callback: Callback<GenericEventData<T>>): void
```

单次订阅指定的事件，在接收到该事件且执行完相应的回调函数后，自动取消订阅。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-emitter-function once<T>(eventId: string, callback: Callback<GenericEventData<T>>): void--><!--Device-emitter-function once<T>(eventId: string, callback: Callback<GenericEventData<T>>): void-End-->

**系统能力：** SystemCapability.Notification.Emitter

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventId | string | 是 | 单次订阅的事件。取值为长度不超过10240字节的自定义字符串，且不可为空字符。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;GenericEventData&lt;T&gt;&gt; | 是 | 接收到该事件时需要执行的回调处理函数。 |

**示例：**

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

