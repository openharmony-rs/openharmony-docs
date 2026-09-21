# SEService

```TypeScript
export interface SEService
```

**SEService** indicates the connection service used to connect to all available SEs in the system. You can use [createService](arkts-connectivity-omapi-createservice-f.md) to create an **SEService** instance.

**Since:** 10

**System capability:** SystemCapability.Communication.SecureElement

## Modules to Import

```TypeScript
import { omapi } from '@kit.ConnectivityKit';
```

## getReaders

```TypeScript
getReaders(): Reader[]
```

Obtains available SE readers, which include all the SEs on the device.

**Since:** 10

**System capability:** SystemCapability.Communication.SecureElement

**Return value:**

| Type | Description |
| --- | --- |
| [Reader](arkts-connectivity-omapi-reader-i.md)[] | Available readers obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |

**Examples**

```TypeScript
import { omapi } from '@kit.ConnectivityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let seService : omapi.SEService;
let seReaders : omapi.Reader[];

// Initialize seService before using it.
function secureElementDemo() {
    // Obtain readers.
    try {
        seReaders = seService.getReaders();
    } catch (error) {
        hilog.error(0x0000, 'testTag', 'getReaders error %{public}s', JSON.stringify(error));
    }
    if (seReaders == undefined || seReaders.length == 0) {
        hilog.error(0x0000, 'testTag', 'no valid reader found.');
        // Release the SE service resources.
        seService.shutdown();
        return;
    }
}
```

## getVersion

```TypeScript
getVersion(): string
```

Obtains the version of the Open Mobile API (OMAPI) specification used.

**Since:** 10

**System capability:** SystemCapability.Communication.SecureElement

**Return value:**

| Type | Description |
| --- | --- |
| string | OMAPI version obtained. For example, **3.3** indicates Open Mobile API Specification v3.3. |

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

// Initialize seService before using it.

try {
    let version = seService.getVersion();
    hilog.error(0x0000, 'testTag', 'version %{public}s', JSON.stringify(version));
} catch (error) {
    hilog.error(0x0000, 'testTag', 'getVersion error %{public}s', JSON.stringify(error));
}
```

## isConnected

```TypeScript
isConnected(): boolean
```

Checks whether this SE service is connected.

**Since:** 10

**System capability:** SystemCapability.Communication.SecureElement

**Return value:**

| Type | Description |
| --- | --- |
| boolean | **true** if the SE service is connected; **false** otherwise. |

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

## shutdown

```TypeScript
shutdown(): void
```

Releases all SE resources allocated to this SE service. After that, [isConnected](#isconnected) returns **false**.

**Since:** 10

**System capability:** SystemCapability.Communication.SecureElement

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

// Initialize seService before using it.

try {
    seService.shutdown();
} catch (error) {
    hilog.error(0x0000, 'testTag', 'shutdown error %{public}s', JSON.stringify(error));
}
```
