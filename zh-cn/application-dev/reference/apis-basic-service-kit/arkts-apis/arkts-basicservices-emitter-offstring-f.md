# off_string

## off_string

```TypeScript
function off(eventId: string): void
```

取消事件ID为eventId的所有订阅。 使用该接口取消某个事件订阅后，已通过emit接口发布但尚未被执行的事件将被取消。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-emitter-function off(eventId: string): void--><!--Device-emitter-function off(eventId: string): void-End-->

**系统能力：** SystemCapability.Notification.Emitter

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventId | string | 是 | 事件ID。 不可为空字符串，大小不超过10240字节，超出部分会被截断。 |

## 示例

```TypeScript
// 取消eventId为'eventId1'的所有事件回调处理函数
emitter.off('eventId1');
```


## off_string

```TypeScript
function off(eventId: string, callback: Callback<EventData>): void
```

取消事件ID为eventId且回调处理函数为callback的订阅。仅当已使用[on](arkts-basicservices-emitter-oninnerevent-f.md#on_InnerEvent)或 once接口订阅callback时，该接口才生效。 使用该接口取消某个事件订阅后，已通过emit接口发布但尚未被执行的事件将被取消。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-emitter-function off(eventId: string, callback: Callback<EventData>): void--><!--Device-emitter-function off(eventId: string, callback: Callback<EventData>): void-End-->

**系统能力：** SystemCapability.Notification.Emitter

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventId | string | 是 | 事件ID。 不可为空字符串，大小不超过10240字节，超出部分会被截断。 |
| callback | [Callback](arkts-basicservices-callback-t.md)&lt;[EventData](arkts-basicservices-emitter-eventdata-i.md)&gt; | 是 | 回调函数，指定要取消订阅的事件处理函数，需与订阅时使用的 callback一致。 |

## 示例

```TypeScript
import { Callback } from '@kit.BasicServicesKit';

let callback: Callback<emitter.EventData> = (eventData: emitter.EventData) => {
  console.info(`eventData: ${JSON.stringify(eventData)}`);
}
// 取消eventId为'eventId1'的事件回调处理函数，callback对象应使用订阅时的对象
// 如果该回调处理函数没有被订阅，则不做任何处理
emitter.off('eventId1', callback);
```


## off_string

```TypeScript
function off<T>(eventId: string, callback: Callback<GenericEventData<T>>): void
```

取消事件ID为eventId且回调处理函数为callback的订阅。仅当已使用 on或 once接口订阅callback时，该接口才生效。 使用该接口取消某个事件订阅后，已通过emit接口发布但尚未被执行的事件将被取消。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-emitter-function off<T>(eventId: string, callback: Callback<GenericEventData<T>>): void--><!--Device-emitter-function off<T>(eventId: string, callback: Callback<GenericEventData<T>>): void-End-->

**系统能力：** SystemCapability.Notification.Emitter

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventId | string | 是 | 事件ID。 不可为空字符串，大小不超过10240字节，超出部分会被截断。 |
| callback | [Callback](arkts-basicservices-callback-t.md)&lt;[GenericEventData](arkts-basicservices-emitter-genericeventdata-i.md)&lt;T&gt;&gt; | 是 | 回调函数，指定要取消订阅的事件处理函数，需与订阅时使用的 callback一致。 |

## 示例

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
// 取消eventId为'eventId1'的事件回调处理函数，callback对象应使用订阅时的对象
// 如果该回调处理函数没有被订阅，则不做任何处理
emitter.off('eventId1', callback);
```

