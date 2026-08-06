# off

## off

```TypeScript
function off(eventId: long): void
```

取消事件ID为eventId的所有订阅。 使用该接口取消某个事件订阅后，已通过[emit]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_接口发布但尚未被执行的事件将被取消。

**起始版本：** 7

**ArkTS模式：** ArkTS-Dyn起始版本为7；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-emitter-function off(eventId: long): void--><!--Device-emitter-function off(eventId: long): void-End-->

**系统能力：** SystemCapability.Notification.Emitter

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventId | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：long | 是 | 事件ID，由开发者定义，用于辨别事件。 |

**示例：**

```TypeScript
// 取消eventId为1的所有事件回调处理函数
emitter.off(1);
```


## off

```TypeScript
function off(eventId: string): void
```

取消事件ID为eventId的所有订阅。 使用该接口取消某个事件订阅后，已通过[emit]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_接口发布但尚未被执行的事件将被取消。

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-emitter-function off(eventId: string): void--><!--Device-emitter-function off(eventId: string): void-End-->

**系统能力：** SystemCapability.Notification.Emitter

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventId | string | 是 | 事件ID。不可为空字符串，大小不超过10240字节，超出部分会被截断。 |

**示例：**

```TypeScript
// 取消eventId为'eventId1'的所有事件回调处理函数
emitter.off('eventId1');
```


## off

```TypeScript
function off(eventId: long, callback: Callback<EventData>): void
```

取消事件ID为eventId且回调处理函数为callback的订阅。仅当已使用[on]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_或 [once]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_接口订阅callback时，该接口才生效。 使用该接口取消某个事件订阅后，已通过[emit]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_接口发布但尚未被执行的事件将被取消。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-emitter-function off(eventId: long, callback: Callback<EventData>): void--><!--Device-emitter-function off(eventId: long, callback: Callback<EventData>): void-End-->

**系统能力：** SystemCapability.Notification.Emitter

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventId | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：long | 是 | 事件ID，由开发者定义，用于辨别事件。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;EventData&gt; | 是 | 回调函数，指定要取消订阅的事件处理函数，需与订阅时使用的callback一致。 |

**示例：**

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


## off

```TypeScript
function off(eventId: string, callback: Callback<EventData>): void
```

取消事件ID为eventId且回调处理函数为callback的订阅。仅当已使用[on]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_或 [once]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_接口订阅callback时，该接口才生效。 使用该接口取消某个事件订阅后，已通过[emit]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_接口发布但尚未被执行的事件将被取消。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-emitter-function off(eventId: string, callback: Callback<EventData>): void--><!--Device-emitter-function off(eventId: string, callback: Callback<EventData>): void-End-->

**系统能力：** SystemCapability.Notification.Emitter

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventId | string | 是 | 事件ID。不可为空字符串，大小不超过10240字节，超出部分会被截断。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;EventData&gt; | 是 | 回调函数，指定要取消订阅的事件处理函数，需与订阅时使用的callback一致。 |

**示例：**

```TypeScript
import { Callback } from '@kit.BasicServicesKit';

let callback: Callback<emitter.EventData> = (eventData: emitter.EventData) => {
  console.info(`eventData: ${JSON.stringify(eventData)}`);
}
// 取消eventId为'eventId1'的事件回调处理函数，callback对象应使用订阅时的对象
// 如果该回调处理函数没有被订阅，则不做任何处理
emitter.off('eventId1', callback);
```


## off

```TypeScript
function off<T>(eventId: string, callback: Callback<GenericEventData<T>>): void
```

取消事件ID为eventId且回调处理函数为callback的订阅。仅当已使用 [on]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_或 [once]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_接口订阅callback时，该接口才生效。 使用该接口取消某个事件订阅后，已通过[emit]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_接口发布但尚未被执行的事件将被取消。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-emitter-function off<T>(eventId: string, callback: Callback<GenericEventData<T>>): void--><!--Device-emitter-function off<T>(eventId: string, callback: Callback<GenericEventData<T>>): void-End-->

**系统能力：** SystemCapability.Notification.Emitter

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventId | string | 是 | 事件ID。不可为空字符串，大小不超过10240字节，超出部分会被截断。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;GenericEventData&lt;T&gt;&gt; | 是 | 回调函数，指定要取消订阅的事件处理函数，需与订阅时使用的callback一致。 |

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
// 取消eventId为'eventId1'的事件回调处理函数，callback对象应使用订阅时的对象
// 如果该回调处理函数没有被订阅，则不做任何处理
emitter.off('eventId1', callback);
```

