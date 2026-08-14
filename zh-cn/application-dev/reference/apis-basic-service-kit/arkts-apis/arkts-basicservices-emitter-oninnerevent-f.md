# on_InnerEvent

## on_InnerEvent

```TypeScript
function on(event: InnerEvent, callback: Callback<EventData>): void
```

持续订阅指定的事件，并在接收到该事件时，执行对应的回调处理函数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-emitter-function on(event: InnerEvent, callback: Callback<EventData>): void--><!--Device-emitter-function on(event: InnerEvent, callback: Callback<EventData>): void-End-->

**系统能力：** SystemCapability.Notification.Emitter

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [InnerEvent](arkts-basicservices-emitter-innerevent-i.md) | 是 | 持续订阅的事件，其中[EventPriority](arkts-basicservices-emitter-eventpriority-e.md#EventPriority)在订阅事件时无需指定，也不生效。 |
| callback | [Callback](arkts-basicservices-callback-t.md)&lt;[EventData](arkts-basicservices-emitter-eventdata-i.md)&gt; | 是 | 接收到该事件时需要执行的回调处理函数。 |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { Callback } from '@kit.BasicServicesKit';

let innerEvent: emitter.InnerEvent = {
  eventId: 1
};

let callback: Callback<emitter.EventData> = (eventData: emitter.EventData) => {
  console.info(`eventData: ${JSON.stringify(eventData)}`);
}

// 收到eventId为1的事件后执行回调函数
emitter.on(innerEvent, callback);
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

// 收到eventId为1的事件后执行回调函数
emitter.on(innerEvent, callback);
```

