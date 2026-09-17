# newSEService

## Modules to Import

```TypeScript
import { omapi } from '@kit.ConnectivityKit';
```

## newSEService('serviceState')

```TypeScript
function newSEService(type: 'serviceState', callback: Callback<ServiceState>): SEService
```

Creates an **SEService** instance for connecting to all available SEs in the system. The connection is time- consuming. Therefore, this API supports only the asynchronous mode. This API uses an asynchronous callback to return the result.

The returned **SEService** instance is available only when **true** is returned by the specified callback or [isConnected](arkts-connectivity-omapi-seservice-i.md#isconnected).

> **NOTE:** 
> 
> This API is supported since API version 10 and deprecated since API version 12. Use
> [createService](arkts-connectivity-omapi-createservice-f.md) instead.

**Since:** 10

**Deprecated since:** 12

**Substitutes:** [createService](arkts-connectivity-omapi-createservice-f.md)

**System capability:** SystemCapability.Communication.SecureElement

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'serviceState' | Yes | Type of the SE service to create. It has a fixed value of **'serviceState'**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ServiceState](arkts-connectivity-omapi-servicestate-e.md)&gt; | Yes | Callback used to return the SE service state. |

**Return value:**

| Type | Description |
| --- | --- |
| [SEService](arkts-connectivity-omapi-seservice-i.md) | **SEService** instance created. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |

**Examples**

```TypeScript
import { omapi } from '@kit.ConnectivityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let seService : omapi.SEService;

function secureElementDemo() {
    // Obtain the service.
    try {
        seService = omapi.newSEService("serviceState", (state) => {
            hilog.info(0x0000, 'testTag', 'se service state = %{public}s', JSON.stringify(state));
        });
    } catch (error) {
        hilog.error(0x0000, 'testTag', 'newSEService error %{public}s', JSON.stringify(error));
    }
    if (seService == undefined || !seService.isConnected()) {
        hilog.error(0x0000, 'testTag', 'secure element service disconnected.');
        return;
    }
}
```
