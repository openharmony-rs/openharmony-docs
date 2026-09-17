# Reader

Obtains the SE supported by the device. If eSE, SIM, and SIM2 are supported, three instances will be returned. SIM2 is supported since API version 22. You can use [SEService.getReaders](arkts-connectivity-omapi-seservice-i.md#getreaders) to obtain a **Reader** instance.

**Since:** 10

**System capability:** SystemCapability.Communication.SecureElement

## Modules to Import

```TypeScript
import { omapi } from '@kit.ConnectivityKit';
```

## closeSessions

```TypeScript
closeSessions(): void
```

Closes all sessions opened on this reader. All channels opened by these sessions will be closed.

**Since:** 10

**System capability:** SystemCapability.Communication.SecureElement

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [3300101](../errorcode-se.md#3300101-abnormal-se-service-status) | IllegalStateError, service state exception. |

**Examples**

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
import { omapi } from '@kit.ConnectivityKit';

let seReaders : omapi.Reader[];
let seSession : omapi.Session;
let reader : omapi.Reader;

// Initialize seReaders before using it.
function secureElementDemo() {
    try {
        reader = seReaders[0]; // Set the expected reader (eSE, SIM, or SIM2).
        seSession = reader.openSession();
    } catch (error) {
        hilog.error(0x0000, 'testTag', 'openSession error %{public}s', JSON.stringify(error));
    }
    if (seSession == undefined) {
        hilog.error(0x0000, 'testTag', 'seSession invalid.');
        // Release the SE service resources.
        seService.shutdown();
        return;
    }
    try {
        reader.closeSessions();
    } catch (error) {
        hilog.error(0x0000, 'testTag', 'closeSessions error %{public}s', JSON.stringify(error));
    }
}
```

## getName

```TypeScript
getName(): string
```

Obtains the name of this reader. The name is **SIM** for a SIM reader, **SIM2** for a SIM2 reader, and **eSE** for an eSE.

**Since:** 10

**System capability:** SystemCapability.Communication.SecureElement

**Return value:**

| Type | Description |
| --- | --- |
| string | [Reader](arkts-connectivity-omapi-reader-i.md) name obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |

**Examples**

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
import { omapi } from '@kit.ConnectivityKit';

let seReaders : omapi.Reader[];

// Initialize seReaders before using it.

try {
    let reader = seReaders[0]; // Set the expected reader (eSE, SIM, or SIM2).
    let name = reader.getName();
    hilog.info(0x0000, 'testTag', 'name %{public}s', JSON.stringify(name));
} catch (error) {
    hilog.error(0x0000, 'testTag', 'getName error %{public}s', JSON.stringify(error));
}
```

## isSecureElementPresent

```TypeScript
isSecureElementPresent(): boolean
```

Checks whether the SE corresponding to this reader is available.

**Since:** 10

**System capability:** SystemCapability.Communication.SecureElement

**Return value:**

| Type | Description |
| --- | --- |
| boolean | **true** if the SE is available; **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [3300101](../errorcode-se.md#3300101-abnormal-se-service-status) | IllegalStateError, service state exception. |

**Examples**

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
import { omapi } from '@kit.ConnectivityKit';

let seReaders : omapi.Reader[];

// Initialize seReaders before using it.

try {
    let reader = seReaders[0]; // Set the expected reader (eSE, SIM, or SIM2).
    let isPresent = reader.isSecureElementPresent();
    hilog.info(0x0000, 'testTag', 'isPresent %{public}s', JSON.stringify(isPresent));
} catch (error) {
    hilog.error(0x0000, 'testTag', 'isSecureElementPresent error %{public}s', JSON.stringify(error));
}
```

## openSession

```TypeScript
openSession(): Session
```

Opens a session to connect to an SE in this reader. Multiple sessions can be opened on a reader at the same time.

**Since:** 10

**System capability:** SystemCapability.Communication.SecureElement

**Return value:**

| Type | Description |
| --- | --- |
| [Session](arkts-connectivity-omapi-session-i.md) | Session instance opened. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [3300101](../errorcode-se.md#3300101-abnormal-se-service-status) | IllegalStateError, service state exception. |
| [3300104](../errorcode-se.md#3300104-se-chip-io-exception) | IOError, there is a communication problem to the reader or the SE. |

**Examples**

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
import { omapi } from '@kit.ConnectivityKit';

let seReaders : omapi.Reader[];
let seSession : omapi.Session;

// Initialize seReaders before using it.
function secureElementDemo() {
    try {
        let reader = seReaders[0]; // Set the expected reader (eSE, SIM, or SIM2).
        seSession = reader.openSession();
    } catch (error) {
        hilog.error(0x0000, 'testTag', 'openSession error %{public}s', JSON.stringify(error));
    }
    if (seSession == undefined) {
        hilog.error(0x0000, 'testTag', 'seSession invalid.');
        return;
    }
}
```
