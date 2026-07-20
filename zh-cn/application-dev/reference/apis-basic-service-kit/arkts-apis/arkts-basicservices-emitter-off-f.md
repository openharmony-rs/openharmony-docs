# off

## 导入模块

```TypeScript
import { emitter } from '@kit.BasicServicesKit';
```

<a id="off"></a>
## off

```TypeScript
function off(eventId: number): void
```

取消事件ID为eventId的所有订阅。

使用该接口取消某个事件订阅后，已通过[emit](emitter.emit(eventId: string))接口发布但尚未被执行的事件将被取消。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-emitter-function off(eventId: long): void--><!--Device-emitter-function off(eventId: long): void-End-->

**系统能力：** SystemCapability.Notification.Emitter

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventId | number | 是 | 事件ID。 |

**示例：**

```TypeScript
// 取消eventId为1的所有事件回调处理函数
emitter.off(1);

```


<a id="off-1"></a>
## off

```TypeScript
function off(eventId: string): void
```

取消事件ID为eventId的所有订阅。

使用该接口取消某个事件订阅后，已通过[emit](emitter.emit(eventId: string))接口发布但尚未被执行的事件将被取消。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-emitter-function off(eventId: string): void--><!--Device-emitter-function off(eventId: string): void-End-->

**系统能力：** SystemCapability.Notification.Emitter

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventId | string | 是 | 事件ID。取值为长度不超过10240字节的自定义字符串，且不可为空字符。 |

**示例：**

```TypeScript
// 取消eventId为"eventId1"的所有事件回调处理函数
emitter.off("eventId1");

```


<a id="off-2"></a>
## off

```TypeScript
function off(eventId: number, callback: Callback<EventData>): void
```

取消事件ID为eventId且回调处理函数为callback的订阅。仅当已使用[on](emitter.on(event: InnerEvent, callback: Callback<EventData>))或[once](emitter.once(event: InnerEvent, callback: Callback<EventData>))接口订阅callback时，该接口才生效。

使用该接口取消某个事件订阅后，已通过[emit](emitter.emit(eventId: string))接口发布但尚未被执行的事件将被取消。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-emitter-function off(eventId: long, callback: Callback<EventData>): void--><!--Device-emitter-function off(eventId: long, callback: Callback<EventData>): void-End-->

**系统能力：** SystemCapability.Notification.Emitter

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventId | number | 是 | 事件ID。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;EventData&gt; | 是 | 事件的回调处理函数。 |

**示例：**

```TypeScript
import { Callback } from '@kit.BasicServicesKit';

let callback: Callback<emitter.EventData> = (eventData: emitter.EventData) => {
  console.info(`eventData: ${JSON.stringify(eventData)}`);
};
// 取消eventId为1的事件回调处理函数，callback对象应使用订阅时的对象
// 如果该回调处理函数没有被订阅，则不做任何处理
emitter.off(1, callback);

```


<a id="off-3"></a>
## off

```TypeScript
function off(eventId: string, callback: Callback<EventData>): void
```

取消事件ID为eventId且回调处理函数为callback的订阅。仅当已使用[on](emitter.on(eventId: string, callback: Callback<EventData>))或[once](emitter.once(eventId: string, callback: Callback<EventData>))接口订阅callback时，该接口才生效。

使用该接口取消某个事件订阅后，已通过[emit](emitter.emit(eventId: string))接口发布但尚未被执行的事件将被取消。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-emitter-function off(eventId: string, callback: Callback<EventData>): void--><!--Device-emitter-function off(eventId: string, callback: Callback<EventData>): void-End-->

**系统能力：** SystemCapability.Notification.Emitter

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventId | string | 是 | 事件ID。取值为长度不超过10240字节的自定义字符串，且不可为空字符。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;EventData&gt; | 是 | 事件的回调处理函数。 |

**示例：**

```TypeScript
import { Callback } from '@kit.BasicServicesKit';

let callback: Callback<emitter.EventData> = (eventData: emitter.EventData) => {
  console.info(`eventData: ${JSON.stringify(eventData)}`);
};
// 取消eventId为"eventId1"的事件回调处理函数，callback对象应使用订阅时的对象
// 如果该回调处理函数没有被订阅，则不做任何处理
emitter.off("eventId1", callback);

```


<a id="off-4"></a>
## off

```TypeScript
function off<T>(eventId: string, callback: Callback<GenericEventData<T>>): void
```

取消事件ID为eventId且回调处理函数为callback的订阅。仅当已使用[on](emitter.on<T>(eventId: string, callback: Callback<GenericEventData<T>>))或[once](emitter.once<T>(eventId: string, callback: Callback<GenericEventData<T>>))接口订阅callback时，该接口才生效。

使用该接口取消某个事件订阅后，已通过[emit](emitter.emit(eventId: string))接口发布但尚未被执行的事件将被取消。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-emitter-function off<T>(eventId: string, callback: Callback<GenericEventData<T>>): void--><!--Device-emitter-function off<T>(eventId: string, callback: Callback<GenericEventData<T>>): void-End-->

**系统能力：** SystemCapability.Notification.Emitter

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventId | string | 是 | 事件ID。取值为长度不超过10240字节的自定义字符串，且不可为空字符。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;GenericEventData&lt;T&gt;&gt; | 是 | 事件的回调处理函数。 |

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
// 取消eventId为"eventId1"的事件回调处理函数，callback对象应使用订阅时的对象
// 如果该回调处理函数没有被订阅，则不做任何处理
emitter.off("eventId1", callback);

```

