# createService

## Modules to Import

```TypeScript
import { omapi } from '@kit.ConnectivityKit';
```

## createService

```TypeScript
function createService(): Promise<SEService>
```

Creates an **SEService** instance for connecting to all available SEs in the system. The connection is time- consuming. Therefore, only asynchronous APIs are provided. This API uses a promise to return the result.

The **SEService** object is available only when [isConnected](arkts-connectivity-omapi-seservice-i.md#isconnected) returns **true**.

**Since:** 12

**System capability:** SystemCapability.Communication.SecureElement

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[SEService](arkts-connectivity-omapi-seservice-i.md)&gt; | Promise used to return the **SEService** instance created. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |

**Examples**

```TypeScript
import { omapi } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let seService : omapi.SEService;

function secureElementDemo() {
    omapi.createService().then((data) => {
        seService = data;
        if (seService == undefined || !seService.isConnected()) {
            hilog.error(0x0000, 'testTag', 'seservice state disconnected');
            return;
        }
        hilog.info(0x0000, 'testTag', 'seservice state connected');
    }).catch((error : BusinessError) => {
        hilog.error(0x0000, 'testTag', 'createService error %{public}s', JSON.stringify(error));
    });
}
```
