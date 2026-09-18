# write (System API)

## Modules to Import

```TypeScript
import { hiSysEvent } from '@kit.PerformanceAnalysisKit';
```

## write

```TypeScript
function write(info: SysEventInfo): Promise<void>
```

Writes event information to the event file. This API uses a promise to return the result.

**Since:** 9

**System capability:** SystemCapability.HiviewDFX.HiSysEvent

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| info | [SysEventInfo](arkts-performanceanalysis-hisysevent-syseventinfo-i-sys.md) | Yes | System event information. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. Depending on whether event writing is successful, you can use the **then()** or **catch()** method to process the callback. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| 11200001 | Invalid event domain. |
| 11200002 | Invalid event name. |
| [11200003](../errorcode-hisysevent-sys.md#11200003-environment-error) | Abnormal environment. |
| [11200004](../errorcode-hisysevent-sys.md#11200004-invalid-event-length) | The event length exceeds the limit. |
| [11200051](../errorcode-hisysevent-sys.md#11200051-invalid-event-parameter) | Invalid event parameter. |
| [11200052](../errorcode-hisysevent-sys.md#11200052-length-of-event-parameter-values-of-the-string-type-exceeding-the-limit) | The size of the event parameter of the string type exceeds the limit. |
| [11200053](../errorcode-hisysevent-sys.md#11200053-number-of-event-parameters-exceeding-the-limit) | The number of event parameters exceeds the limit. |
| [11200054](../errorcode-hisysevent-sys.md#11200054-length-of-event-parameter-values-of-the-array-type-exceeding-the-limit) | The number of event parameters of the array type exceeds the limit. |

**Examples**

```TypeScript
import { hiSysEvent } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let customizedParams: Record<string, string | number> = {
    'PID': 487,
    'UID': 103,
    'PACKAGE_NAME': "com.ohos.hisysevent.test",
    'PROCESS_NAME': "syseventservice",
    'MSG': "no msg."
  };
  let eventInfo: hiSysEvent.SysEventInfo = {
    domain: "RELIABILITY",
    name: "STACK",
    eventType: hiSysEvent.EventType.FAULT,
    params: customizedParams
  };
  hiSysEvent.write(eventInfo, (err: BusinessError) => {
    // do something here.
  });
} catch (err) {
  console.error(`error code: ${(err as BusinessError).code}, error msg: ${(err as BusinessError).message}`);
}
```

```TypeScript
import { hiSysEvent } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let customizedParams: Record<string, string | number> = {
    'PID': 487,
    'UID': 103,
    'PACKAGE_NAME': "com.ohos.hisysevent.test",
    'PROCESS_NAME': "syseventservice",
    'MSG': "no msg."
  };
  let eventInfo: hiSysEvent.SysEventInfo = {
    domain: "RELIABILITY",
    name: "STACK",
    eventType: hiSysEvent.EventType.FAULT,
    params: customizedParams
  };
  hiSysEvent.write(eventInfo).then(
    () => {
      // do something here.
    }
  ).catch(
    (err: BusinessError) => {
      console.error(`error code: ${err.code}, error msg: ${err.message}`);
    }
  );
} catch (err) {
  console.error(`error code: ${(err as BusinessError).code}, error msg: ${(err as BusinessError).message}`);
}
```


## write

```TypeScript
function write(info: SysEventInfo, callback: AsyncCallback<void>): void
```

Writes event information to the event file. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.HiviewDFX.HiSysEvent

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| info | [SysEventInfo](arkts-performanceanalysis-hisysevent-syseventinfo-i-sys.md) | Yes | System event information. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to process the received return value.<br>- Value **0**: The event verification is successful, and the event will be written to the event file asynchronously. <br>- A value greater than **0**: Invalid parameters are present in the event, and the event will be written to the event file asynchronously after the invalid parameters are ignored. <br>- A value smaller than **0**: The event parameter verification fails, and the event will not be written to the event file. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| 11200001 | Invalid event domain. |
| 11200002 | Invalid event name. |
| [11200003](../errorcode-hisysevent-sys.md#11200003-environment-error) | Abnormal environment. |
| [11200004](../errorcode-hisysevent-sys.md#11200004-invalid-event-length) | The event length exceeds the limit. |
| [11200051](../errorcode-hisysevent-sys.md#11200051-invalid-event-parameter) | Invalid event parameter. |
| [11200052](../errorcode-hisysevent-sys.md#11200052-length-of-event-parameter-values-of-the-string-type-exceeding-the-limit) | The size of the event parameter of the string type exceeds the limit. |
| [11200053](../errorcode-hisysevent-sys.md#11200053-number-of-event-parameters-exceeding-the-limit) | The number of event parameters exceeds the limit. |
| [11200054](../errorcode-hisysevent-sys.md#11200054-length-of-event-parameter-values-of-the-array-type-exceeding-the-limit) | The number of event parameters of the array type exceeds the limit. |

**Examples**

See [write](#write)
