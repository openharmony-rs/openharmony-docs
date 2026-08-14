# offEventData

## offEventData

```TypeScript
function offEventData(eventId: string, callback: Callback<EventData>): void
```

取消事件ID为eventId且回调处理函数为callback的订阅。仅当已使用 [onEventData](arkts-basicservices-emitter-oneventdata-f.md#onEventData)或 [onceEventData](arkts-basicservices-emitter-onceeventdata-f.md#onceEventData)接口订阅callback时，该接口才生效。 使用该接口取消某个事件订阅后，已通过emit接口发布但尚未被执行的事件将被取消。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-emitter-function offEventData(eventId: string, callback: Callback<EventData>): void--><!--Device-emitter-function offEventData(eventId: string, callback: Callback<EventData>): void-End-->

**系统能力：** SystemCapability.Notification.Emitter

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventId | string | 是 | 事件ID。取值为长度不超过10240字节的自定义字符串，且不可为空字符。 |
| callback | [Callback](arkts-basicservices-callback-t.md)&lt;[EventData](arkts-basicservices-emitter-eventdata-i.md)&gt; | 是 | 事件的回调处理函数。 |

## 示例

```TypeScript
import { Callback } from '@kit.BasicServicesKit';

let callback: Callback<emitter.EventData> = (eventData: emitter.EventData | undefined | null) => {
  console.info(`eventData: ${JSON.stringify(eventData)}`);
}

// 取消eventID为"eventId"的事件回调处理函数，callback对象应使用订阅时的对象
// 如果该回调处理函数没有被订阅，则不做任何处理
emitter.offEventData("eventId", callback);
```

