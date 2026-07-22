# write

## 导入模块

```TypeScript
import { hiAppEvent } from '@kit.PerformanceAnalysisKit';
```

## write

```TypeScript
function write(info: AppEventInfo): Promise<void>
```

应用事件打点方法，将AppEventInfo类型的事件进行存储，使用Promise方式作为异步回调。通过此接口写入的事件对象是开发者自定义的对象，为了避免与系统事件产生冲突混淆，不建议写入系统事件（[Event](arkts-performanceanalysis-hiappevent-event-n.md#event)中定义的系统事件名称常量）。此接口写入的事件可通过订阅事件观察者（[addWatcher](arkts-performanceanalysis-hiappevent-addwatcher-f.md#addwatcher)）进行处理。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-hiAppEvent-function write(info: AppEventInfo): Promise<void>--><!--Device-hiAppEvent-function write(info: AppEventInfo): Promise<void>-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | [AppEventInfo](arkts-performanceanalysis-hiappevent-appeventinfo-i.md) | 是 | 应用事件对象。其中的事件名称建议避免与[Event](arkts-performanceanalysis-hiappevent-event-n.md#event)中定义的系统事件名称常量冲突混淆。<br>**起始版本：** 11 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |
| [11100001](../errorcode-hiappevent.md#11100001-打点功能被关闭) | Function disabled. Possibly caused by the param disable in ConfigOption is true. |
| [11101001](../errorcode-hiappevent.md#11101001-非法的事件领域名称) | Invalid event domain. Possible causes: 1. Contain invalid characters;<br>2. Length is invalid. |
| [11101002](../errorcode-hiappevent.md#11101002-非法的事件名称) | Invalid event name. Possible causes: 1. Contain invalid characters;<br>2. Length is invalid. |
| [11101003](../errorcode-hiappevent.md#11101003-非法的事件参数数量) | Invalid number of event parameters. Possibly caused by the number of parameters<br>is over 32. |
| [11101004](../errorcode-hiappevent.md#11101004-非法的事件参数字符串长度) | Invalid string length of the event parameter. |
| [11101005](../errorcode-hiappevent.md#11101005-非法的事件参数名称) | Invalid event parameter name. Possible causes: 1. Contain invalid characters;<br>2. Length is invalid. |
| [11101006](../errorcode-hiappevent.md#11101006-非法的事件参数数组长度) | Invalid array length of the event parameter. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let eventParams: Record<string, number | string> = {
  "int_data": 100,
  "str_data": "strValue",
};

// 应用事件打点，使用Promise方式作为异步回调
hiAppEvent.write({
  domain: "test_domain",
  name: "test_event",
  eventType: hiAppEvent.EventType.FAULT,
  params: eventParams,
}).then(() => {
  hilog.info(0x0000, 'hiAppEvent', `success to write event`);
}).catch((err: BusinessError) => {
  hilog.error(0x0000, 'hiAppEvent', `code: ${err.code}, message: ${err.message}`);
});

```


## write

```TypeScript
function write(info: AppEventInfo, callback: AsyncCallback<void>): void
```

应用事件打点方法，将AppEventInfo类型的事件进行存储，使用callback方式作为异步回调。通过此接口写入的事件对象是开发者自定义的对象，为了避免与系统事件产生冲突混淆，不建议写入系统事件（[Event](arkts-performanceanalysis-hiappevent-event-n.md#event)中定义的系统事件名称常量）。此接口写入的事件可通过订阅事件观察者（[addWatcher](arkts-performanceanalysis-hiappevent-addwatcher-f.md#addwatcher)）进行订阅。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-hiAppEvent-function write(info: AppEventInfo, callback: AsyncCallback<void>): void--><!--Device-hiAppEvent-function write(info: AppEventInfo, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | [AppEventInfo](arkts-performanceanalysis-hiappevent-appeventinfo-i.md) | 是 | 应用事件对象。其内部定义的事件名称建议避免与[Event](arkts-performanceanalysis-hiappevent-event-n.md#event)中定义的系统事件名称常量产生冲突。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 打点回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |
| [11100001](../errorcode-hiappevent.md#11100001-打点功能被关闭) | Function disabled. Possibly caused by the param disable in ConfigOption is true. |
| [11101001](../errorcode-hiappevent.md#11101001-非法的事件领域名称) | Invalid event domain. Possible causes: 1. Contain invalid characters;<br>2. Length is invalid. |
| [11101002](../errorcode-hiappevent.md#11101002-非法的事件名称) | Invalid event name. Possible causes: 1. Contain invalid characters;<br>2. Length is invalid. |
| [11101003](../errorcode-hiappevent.md#11101003-非法的事件参数数量) | Invalid number of event parameters. Possibly caused by the number of parameters<br>is over 32. |
| [11101004](../errorcode-hiappevent.md#11101004-非法的事件参数字符串长度) | Invalid string length of the event parameter. |
| [11101005](../errorcode-hiappevent.md#11101005-非法的事件参数名称) | Invalid event parameter name. Possible causes: 1. Contain invalid characters;<br>2. Length is invalid. |
| [11101006](../errorcode-hiappevent.md#11101006-非法的事件参数数组长度) | Invalid array length of the event parameter. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let eventParams: Record<string, number | string> = {
  "int_data": 100,
  "str_data": "strValue",
};

// 应用事件打点，使用callback方式作为异步回调
hiAppEvent.write({
  domain: "test_domain",
  name: "test_event",
  eventType: hiAppEvent.EventType.FAULT,
  params: eventParams,
}, (err: BusinessError) => {
  if (err) {
    hilog.error(0x0000, 'hiAppEvent', `code: ${err.code}, message: ${err.message}`);
    return;
  }
  hilog.info(0x0000, 'hiAppEvent', `success to write event`);
});

```

