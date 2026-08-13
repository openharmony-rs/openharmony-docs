# onEventData

## onEventData

```TypeScript
function onEventData(eventId: string, callback: Callback<EventData>): void
```

持续订阅指定的事件，并在接收到该事件时，使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-emitter-function onEventData(eventId: string, callback: Callback<EventData>): void--><!--Device-emitter-function onEventData(eventId: string, callback: Callback<EventData>): void-End-->

**系统能力：** SystemCapability.Notification.Emitter

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventId | string | 是 | 持续订阅的事件。取值为长度不超过10240字节的自定义字符串，且不可为空字符。 |
| callback | [Callback](arkts-basicservices-callback-t.md)&lt;[EventData](arkts-basicservices-emitter-eventdata-i.md)&gt; | 是 | 接收到该事件时需要执行的回调处理函数。 |

## 示例

```TypeScript
import { Callback } from '@kit.BasicServicesKit';

let callback: Callback<emitter.EventData> = (eventData: emitter.EventData) => {
  console.info(`eventData: ${JSON.stringify(eventData)}`);
}

// 收到eventId为"eventId"的事件后执行回调函数
emitter.onEventData(`eventId`, callback);
```

