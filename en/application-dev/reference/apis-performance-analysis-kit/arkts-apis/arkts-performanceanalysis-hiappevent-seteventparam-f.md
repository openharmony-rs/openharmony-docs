# setEventParam

## Modules to Import

```TypeScript
import { hiAppEvent } from '@kit.PerformanceAnalysisKit';
```

## setEventParam

```TypeScript
function setEventParam(params: Record<string, ParamType>, domain: string, name?: string): Promise<void>
```

Sets custom event parameters. This API uses a promise to return the result. During the same lifecycle, system events and application events can be associated through event domain and event name.System events only support crash, freeze and resource leak events.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| params | Record&lt;string, [ParamType](arkts-performanceanalysis-hiappevent-paramtype-t.md)&gt; | Yes | Custom parameter object. The parameter name and value are defined as follows:<br>- A parameter name is a string that contains a maximum of 32 characters, including digits (0 to 9), letters (a to z)(A to Z), underscore (_), and dollar sign (&#36;). It must start with a letter or dollar sign (&#36;) and end with a digit or letter. <br>- The parameter value is of the [ParamType](arkts-performanceanalysis-hiappevent-paramtype-t.md) and contains a maximum of 1024 characters.<br>- The number of parameters must be less than 64. |
| domain | string | Yes | Event domain. The event domain can be associated with application events and system events (hiAppEvent.domain.OS). |
| name | string | No | Event name. The default value is an empty string, which indicates all event names in the associated event domain. Event names can be used to associate application events and system events. System events can only be associated with the following events:<br>- [Crash event](../../../dfx/hiappevent-watcher-crash-events.md) (**hiAppEvent.event.APP_CRASH**)<br>- [Application freeze event](../../../dfx/hiappevent-watcher-freeze-events.md) (**hiAppEvent.event.APP_FREEZE**) <br>- [Resource leak event](../../../dfx/hiappevent-watcher-resourceleak-events.md) (**hiAppEvent.event.RESOURCE_OVERLIMIT**).<br>**Note:**  Since API version 20, the [resource leak event](../../../dfx/hiappevent-watcher-resourceleak-events.md) is supported. |

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
| [11101004](../errorcode-hiappevent.md#11101004-invalid-event-parameter-string-length) | Invalid string length of the event parameter. |
| [11101005](../errorcode-hiappevent.md#11101005-invalid-event-parameter-name) | Invalid event parameter name. Possible causes: 1. Contain invalid characters;<br>2. Length is invalid. |
| [11101007](../errorcode-hiappevent.md#11101007-invalid-number-of-custom-event-parameters) | The number of parameter keys exceeds the limit. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let params: Record<string, hiAppEvent.ParamType> = {
  "int_data": 100,
  "str_data": "strValue",
};

// Add custom parameters to the application event.
hiAppEvent.setEventParam(params, "test_domain", "test_event").then(() => {
  hilog.info(0x0000, 'hiAppEvent', `success to set event param`);
}).catch((err: BusinessError) => {
  hilog.error(0x0000, 'hiAppEvent', `code: ${err.code}, message: ${err.message}`);
});
```
