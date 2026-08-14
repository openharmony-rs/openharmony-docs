# offGenericEventData

## offGenericEventData

```TypeScript
function offGenericEventData<T>(eventId: string, callback: Callback<GenericEventData<T>>): void
```

取消订阅当前Emitter类实例的事件。仅当已使用 onGenericEventData或 onceGenericEventData接口订阅了事件ID为eventId且回调处理函数为callback的事件时，该接口才生效。 使用该接口取消事件订阅后，已通过emit接口发布但尚未执行的事件将被取消。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-emitter-function offGenericEventData<T>(eventId: string, callback: Callback<GenericEventData<T>>): void--><!--Device-emitter-function offGenericEventData<T>(eventId: string, callback: Callback<GenericEventData<T>>): void-End-->

**系统能力：** SystemCapability.Notification.Emitter

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventId | string | 是 | 事件ID。取值为长度不超过10240字节的自定义字符串，且不可为空字符。 |
| callback | [Callback](arkts-basicservices-callback-t.md)&lt;[GenericEventData](arkts-basicservices-emitter-genericeventdata-i.md)&lt;T&gt;&gt; | 是 | 事件的回调处理函数。 |

## 示例

```TypeScript
import { Callback } from '@kit.BasicServicesKit';

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
  let storage: Sample = eventData.data! as Sample;
  storage.printCount();
}
// 取消eventID为"eventId"的事件回调处理函数，callback对象应使用订阅时的对象
// 如果该回调处理函数没有被订阅，则不做任何处理
emitter.offGenericEventData("eventId", callback);
```

