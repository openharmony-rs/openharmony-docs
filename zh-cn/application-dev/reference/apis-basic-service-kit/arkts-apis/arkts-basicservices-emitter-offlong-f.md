# off_long

## off_long

```TypeScript
function off(eventId: long): void
```

取消事件ID为eventId的所有订阅。 使用该接口取消某个事件订阅后，已通过emit接口发布但尚未被执行的事件将被取消。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-emitter-function off(eventId: long): void--><!--Device-emitter-function off(eventId: long): void-End-->

**系统能力：** SystemCapability.Notification.Emitter

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventId | long | 是 | 事件ID，由开发者定义，用于辨别事件。 |

## 示例

```TypeScript
// 取消eventId为1的所有事件回调处理函数
emitter.off(1);
```


## off_long

```TypeScript
function off(eventId: long, callback: Callback<EventData>): void
```

取消事件ID为eventId且回调处理函数为callback的订阅。仅当已使用[on](arkts-basicservices-emitter-oninnerevent-f.md#on_InnerEvent)或 once接口订阅callback时，该接口才生效。 使用该接口取消某个事件订阅后，已通过emit接口发布但尚未被执行的事件将被取消。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-emitter-function off(eventId: long, callback: Callback<EventData>): void--><!--Device-emitter-function off(eventId: long, callback: Callback<EventData>): void-End-->

**系统能力：** SystemCapability.Notification.Emitter

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventId | long | 是 | 事件ID，由开发者定义，用于辨别事件。 |
| callback | [Callback](arkts-basicservices-callback-t.md)&lt;[EventData](arkts-basicservices-emitter-eventdata-i.md)&gt; | 是 | 回调函数，指定要取消订阅的事件处理函数，需与订阅时使用的 callback一致。 |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { Callback } from '@kit.BasicServicesKit';

let callback: Callback<emitter.EventData> = (eventData: emitter.EventData) => {
  console.info(`eventData: ${JSON.stringify(eventData)}`);
}
// 取消eventId为1的事件回调处理函数，callback对象应使用订阅时的对象
// 如果该回调处理函数没有被订阅，则不做任何处理
emitter.off(1, callback);
```

ArkTS-Sta示例：

```TypeScript
import { Callback } from '@kit.BasicServicesKit';

let callback: Callback<emitter.EventData> = (eventData: emitter.EventData | undefined | null) => {
  console.info(`eventData: ${JSON.stringify(eventData?.data)}`);
}
// 取消eventID为1的事件回调处理函数，callback对象应使用订阅时的对象
// 如果该回调处理函数没有被订阅，则不做任何处理
emitter.off(1, callback);
```

