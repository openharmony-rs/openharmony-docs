# query

## Modules to Import

```TypeScript
import { FaultLogger } from '@kit.PerformanceAnalysisKit';
```

## query

```TypeScript
function query(faultType: FaultType, callback: AsyncCallback<Array<FaultLogInfo>>): void
```

Obtains the fault information about the current application. This API uses an asynchronous callback to return the fault information array obtained, which contains a maximum of 10 pieces of fault information.

**Since:** 9

**Deprecated since:** 18

**Substitutes:** [addWatcher](arkts-performanceanalysis-hiappevent-addwatcher-f.md)

**System capability:** SystemCapability.HiviewDFX.Hiview.FaultLogger

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| faultType | [FaultType](arkts-performanceanalysis-faultlogger-faulttype-e.md) | Yes | Fault type. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[FaultLogInfo](arkts-performanceanalysis-faultlogger-faultloginfo-i.md)&gt;&gt; | Yes | Callback used to return the fault information array.<br> **value** is the fault information array obtained. If **value** is **undefined**, an exception occurs during the information retrieval. In this case, an error string will be returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed, Parameter type error |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: The specified SystemCapability name was not found. |
| [10600001](../errorcode-faultlogger.md#10600001-service-faulty-or-not-started) | The service is not started or is faulty |

**Examples**

```TypeScript
import { FaultLogger } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

function queryFaultLogCallback(error: BusinessError, value: Array<FaultLogger.FaultLogInfo>) {
    if (error) {
        console.error(`error code:${error.code}, error msg:${error.message}`);
    } else {
        console.info("value length is " + value.length);
        let len: number = value.length;
        for (let i = 0; i < len; i++) {
            console.info(`log: ${i}`);
            console.info(`Log pid: ${value[i].pid}`);
            console.info(`Log uid: ${value[i].uid}`);
            console.info(`Log type: ${value[i].type}`);
            console.info(`Log timestamp: ${value[i].timestamp}`);
            console.info(`Log reason: ${value[i].reason}`);
            console.info(`Log module: ${value[i].module}`);
            console.info(`Log summary: ${value[i].summary}`);
            console.info(`Log text: ${value[i].fullLog}`);
        }
    }
}
try {
    FaultLogger.query(FaultLogger.FaultType.JS_CRASH, queryFaultLogCallback);
} catch (err) {
    console.error(`code: ${(err as BusinessError).code}, message: ${(err as BusinessError).message}`);
}
```

```TypeScript
import { FaultLogger } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function getLog() {
  try {
    let value: Array<FaultLogger.FaultLogInfo> = await FaultLogger.query(FaultLogger.FaultType.JS_CRASH);
    if (value) {
      console.info(`value length: ${value.length}`);
      let len: number = value.length;
      for (let i = 0; i < len; i++) {
        console.info(`log: ${i}`);
        console.info(`Log pid: ${value[i].pid}`);
        console.info(`Log uid: ${value[i].uid}`);
        console.info(`Log type: ${value[i].type}`);
        console.info(`Log timestamp: ${value[i].timestamp}`);
        console.info(`Log reason: ${value[i].reason}`);
        console.info(`Log module: ${value[i].module}`);
        console.info(`Log summary: ${value[i].summary}`);
        console.info(`Log text: ${value[i].fullLog}`);
      }
    }
  } catch (err) {
    console.error(`code: ${(err as BusinessError).code}, message: ${(err as BusinessError).message}`);
  }
}
```


## query

```TypeScript
function query(faultType: FaultType): Promise<Array<FaultLogInfo>>
```

Obtains the fault information about the current application. This API uses a promise to return the fault information array obtained, which contains a maximum of 10 pieces of fault information.

**Since:** 9

**Deprecated since:** 18

**Substitutes:** [addWatcher](arkts-performanceanalysis-hiappevent-addwatcher-f.md)

**System capability:** SystemCapability.HiviewDFX.Hiview.FaultLogger

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| faultType | [FaultType](arkts-performanceanalysis-faultlogger-faulttype-e.md) | Yes | Fault type. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[FaultLogInfo](arkts-performanceanalysis-faultlogger-faultloginfo-i.md)&gt;&gt; | Promise used to return the fault information array. You can obtain the fault information instance in its **then()** method or use **await**.<br>**value** is the fault information array obtained. If **value** is **undefined**, an exception occurs during the information retrieval. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed, Parameter type error |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: The specified SystemCapability name was not found. |
| [10600001](../errorcode-faultlogger.md#10600001-service-faulty-or-not-started) | The service is not started or is faulty |

**Examples**

See [query](#query)
