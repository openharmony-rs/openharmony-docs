# once

## once

```TypeScript
function once(event: InnerEvent, callback: Callback<EventData>): void
```

单次订阅指定的事件，在接收到该事件且执行完对应的回调处理函数后，自动取消订阅。

**起始版本：** 7

**ArkTS模式：** ArkTS-Dyn起始版本为7；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-emitter-function once(event: InnerEvent, callback: Callback<EventData>): void--><!--Device-emitter-function once(event: InnerEvent, callback: Callback<EventData>): void-End-->

**系统能力：** SystemCapability.Notification.Emitter

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 单次订阅的事件，其中[EventPriority]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_在订阅事件时无需指定，也不生效。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;EventData&gt; | 是 | 接收到该事件时需要执行的回调处理函数。 |

**示例：**

ArkTS-Dyn示例：

```TypeScript
import { Callback } from '@kit.BasicServicesKit';

let innerEvent: emitter.InnerEvent = {
  eventId: 1
};

let callback: Callback<emitter.EventData> = (eventData: emitter.EventData) => {
  console.info(`eventData: ${JSON.stringify(eventData)}`);
}
// 收到eventId为1的事件后执行该回调函数
emitter.once(innerEvent, callback);
```

ArkTS-Sta示例：

```TypeScript
import { Callback } from '@kit.BasicServicesKit';

let innerEvent: emitter.InnerEvent = {
  eventId: 1
};

let callback: Callback<emitter.EventData> = (eventData: emitter.EventData) => {
  console.info(`eventData: ${JSON.stringify(eventData?.data)}`);
}
// 收到eventId为1的事件后执行该回调函数
emitter.once(innerEvent, callback);
```


## once

```TypeScript
function once(eventId: string, callback: Callback<EventData>): void
```

单次订阅指定的事件，在接收到该事件且执行完对应的回调处理函数后，自动取消订阅。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-emitter-function once(eventId: string, callback: Callback<EventData>): void--><!--Device-emitter-function once(eventId: string, callback: Callback<EventData>): void-End-->

**系统能力：** SystemCapability.Notification.Emitter

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventId | string | 是 | 单次订阅的事件ID。不可为空字符串，大小不超过10240字节，超出部分会被截断。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;EventData&gt; | 是 | 接收到该事件时需要执行的回调处理函数。 |

**示例：**

```TypeScript
import { Callback } from '@kit.BasicServicesKit';

let callback: Callback<emitter.EventData> = (eventData: emitter.EventData) => {
  console.info(`eventData: ${JSON.stringify(eventData)}`);
}
// 收到eventId为"eventId"的事件后执行该回调函数
emitter.once("eventId", callback);
```


## once

```TypeScript
function once<T>(eventId: string, callback: Callback<GenericEventData<T>>): void
```

单次订阅指定的事件，在接收到该事件且执行完对应的回调处理函数后，自动取消订阅。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-emitter-function once<T>(eventId: string, callback: Callback<GenericEventData<T>>): void--><!--Device-emitter-function once<T>(eventId: string, callback: Callback<GenericEventData<T>>): void-End-->

**系统能力：** SystemCapability.Notification.Emitter

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventId | string | 是 | 单次订阅的事件ID。不可为空字符串，大小不超过10240字节，超出部分会被截断。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;GenericEventData&lt;T&gt;&gt; | 是 | 接收到该事件时需要执行的回调处理函数。 |

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
}
// 收到eventId为"eventId"的事件后执行回调函数
emitter.once("eventId", callback);
```

