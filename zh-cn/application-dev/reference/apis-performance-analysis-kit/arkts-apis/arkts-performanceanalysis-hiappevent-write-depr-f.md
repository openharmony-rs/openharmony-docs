# write

<a id="write"></a>
## write

```TypeScript
function write(eventName: string, eventType: EventType, keyValues: object): Promise<void>
```

应用事件打点方法，将事件写入到当天的事件文件中，使用Promise方式作为异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** write

<!--Device-hiAppEvent-function write(eventName: string, eventType: EventType, keyValues: object): Promise<void>--><!--Device-hiAppEvent-function write(eventName: string, eventType: EventType, keyValues: object): Promise<void>-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventName | string | 是 | 事件名称。 |
| eventType | [EventType](../../apis-arkts/arkts-apis/arkts-arkts-xml-eventtype-e.md) | 是 | 事件类型。 |
| keyValues | object | 是 | 事件参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，可以在其then()、catch()方法中分别对事件写入成功、写入异常的情况进行异步处理。 |

**示例：**

```TypeScript
import { BusinessError } from '@ohos.base';
import { hilog } from '@kit.PerformanceAnalysisKit';

let eventParams: Record<string, number | string> = {
  "int_data": 100,
  "str_data": "strValue",
};
hiAppEvent.write("test_event", hiAppEvent.EventType.FAULT, eventParams).then(() => {
  // 事件写入正常
  hilog.info(0x0000, 'hiAppEvent', `success to write event`);
}).catch((err: BusinessError) => {
  // 事件写入异常：事件存在异常参数时忽略异常参数后继续写入，或者事件校验失败时不执行写入
  hilog.error(0x0000, 'hiAppEvent', `code: ${err.code}, message: ${err.message}`);
});

```


<a id="write-1"></a>
## write

```TypeScript
function write(eventName: string, eventType: EventType, keyValues: object, callback: AsyncCallback<void>): void
```

应用事件打点方法，将事件写入到当天的事件文件中，使用callback方式作为异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** write

<!--Device-hiAppEvent-function write(eventName: string, eventType: EventType, keyValues: object, callback: AsyncCallback<void>): void--><!--Device-hiAppEvent-function write(eventName: string, eventType: EventType, keyValues: object, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventName | string | 是 | 事件名称。 |
| eventType | [EventType](../../apis-arkts/arkts-apis/arkts-arkts-xml-eventtype-e.md) | 是 | 事件类型。 |
| keyValues | object | 是 | 事件参数。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 事件回调函数。 |

**示例：**

```TypeScript
import { BusinessError } from '@ohos.base';
import { hilog } from '@kit.PerformanceAnalysisKit';

let eventParams: Record<string, number | string> = {
  "int_data": 100,
  "str_data": "strValue",
};
hiAppEvent.write("test_event", hiAppEvent.EventType.FAULT, eventParams, (err: BusinessError) => {
  if (err) {
    // 事件写入异常：事件存在异常参数时忽略异常参数后继续写入，或者事件校验失败时不执行写入
    hilog.error(0x0000, 'hiAppEvent', `failed to write event, code: ${err.code}, message: ${err.message}`);
    return;
  }
  // 事件写入正常
  hilog.info(0x0000, 'hiAppEvent', `success to write event`);
});

```

