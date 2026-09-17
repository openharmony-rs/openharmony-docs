# write

## Modules to Import

```TypeScript
import { hiAppEvent } from '@kit.PerformanceAnalysisKit';
```

## write

```TypeScript
function write(info: AppEventInfo): Promise<void>
```

Writes events of the **AppEventInfo** type. This API uses a promise to return the result. The event object written by calling this API is a custom object. To avoid conflicts with system events, you are not advised to write it to system events (system event name constants defined in [Event](arkts-performanceanalysis-hiappevent-event-n.md)). The events written by this API can be subscribed to through ([addWatcher](arkts-performanceanalysis-hiappevent-addwatcher-f.md)).

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| info | [AppEventInfo](arkts-performanceanalysis-hiappevent-appeventinfo-i.md) | Yes | Application event object. You are advised to avoid the conflict between the custom event name and the system event name constant defined in [Event](arkts-performanceanalysis-hiappevent-event-n.md).<br>**Since:** 11 |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |
| [11100001](../errorcode-hiappevent.md#11100001-application-event-logging-disabled) | Function disabled. Possibly caused by the param disable in ConfigOption is true. |
| [11101001](../errorcode-hiappevent.md#11101001-invalid-event-domain-name) | Invalid event domain. Possible causes: 1. Contain invalid characters;<br>2. Length is invalid. |
| [11101002](../errorcode-hiappevent.md#11101002-invalid-event-name) | Invalid event name. Possible causes: 1. Contain invalid characters;<br>2. Length is invalid. |
| [11101003](../errorcode-hiappevent.md#11101003-invalid-number-of-event-parameters) | Invalid number of event parameters. Possibly caused by the number of parameters<br>is over 32. |
| [11101004](../errorcode-hiappevent.md#11101004-invalid-event-parameter-string-length) | Invalid string length of the event parameter. |
| [11101005](../errorcode-hiappevent.md#11101005-invalid-event-parameter-name) | Invalid event parameter name. Possible causes: 1. Contain invalid characters;<br>2. Length is invalid. |
| [11101006](../errorcode-hiappevent.md#11101006-invalid-array-length-of-event-parameter-values) | Invalid array length of the event parameter. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let eventParams: Record<string, number | string> = {
  "int_data": 100,
  "str_data": "strValue",
};

// Application event logging. This API uses an asynchronous callback to return the result.
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

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let eventParams: Record<string, number | string> = {
  "int_data": 100,
  "str_data": "strValue",
};

// Application event logging. This API uses a promise to return the result.
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

Writes events of the **AppEventInfo** type. This API uses an asynchronous callback to return the result. The event object written by calling this API is a custom object. To avoid conflicts with system events, you are not advised to write it to system events (system event name constants defined in [Event](arkts-performanceanalysis-hiappevent-event-n.md)). The events written by this API can be subscribed to through ([addWatcher](arkts-performanceanalysis-hiappevent-addwatcher-f.md)).

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| info | [AppEventInfo](arkts-performanceanalysis-hiappevent-appeventinfo-i.md) | Yes | Application event object. You are advised to avoid the conflict between the custom event name and the system event name constant defined in [Event](arkts-performanceanalysis-hiappevent-event-n.md). |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |
| [11100001](../errorcode-hiappevent.md#11100001-application-event-logging-disabled) | Function disabled. Possibly caused by the param disable in ConfigOption is true. |
| [11101001](../errorcode-hiappevent.md#11101001-invalid-event-domain-name) | Invalid event domain. Possible causes: 1. Contain invalid characters;<br>2. Length is invalid. |
| [11101002](../errorcode-hiappevent.md#11101002-invalid-event-name) | Invalid event name. Possible causes: 1. Contain invalid characters;<br>2. Length is invalid. |
| [11101003](../errorcode-hiappevent.md#11101003-invalid-number-of-event-parameters) | Invalid number of event parameters. Possibly caused by the number of parameters<br>is over 32. |
| [11101004](../errorcode-hiappevent.md#11101004-invalid-event-parameter-string-length) | Invalid string length of the event parameter. |
| [11101005](../errorcode-hiappevent.md#11101005-invalid-event-parameter-name) | Invalid event parameter name. Possible causes: 1. Contain invalid characters;<br>2. Length is invalid. |
| [11101006](../errorcode-hiappevent.md#11101006-invalid-array-length-of-event-parameter-values) | Invalid array length of the event parameter. |

**Examples**

See [write](#write)
