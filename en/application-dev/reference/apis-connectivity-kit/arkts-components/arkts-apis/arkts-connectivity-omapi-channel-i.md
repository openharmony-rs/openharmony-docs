# Channel

A **Channel** instance indicates a channel set up by a **Session** instance. The channel can be a basic channel or a logical channel. You can use [Session.openBasicChannel](arkts-connectivity-omapi-session-i.md#openbasicchannel) or [Session.openLogicalChannel](arkts-connectivity-omapi-session-i.md#openlogicalchannel) to obtain a channel instance.

**Since:** 10

**System capability:** SystemCapability.Communication.SecureElement

## Modules to Import

```TypeScript
import { omapi } from '@kit.ConnectivityKit';
```

## close

```TypeScript
close(): void
```

Closes this channel.

**Since:** 10

**System capability:** SystemCapability.Communication.SecureElement

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |

**Examples**

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
import { omapi } from '@kit.ConnectivityKit';

let seChannel : omapi.Channel;

// Initialize seChannel before using it.
try {
    seChannel.close();
} catch (exception) {
    hilog.error(0x0000, 'testTag', 'close exception %{public}s', JSON.stringify(exception));
}
```

## getSelectResponse

```TypeScript
getSelectResponse(): number[]
```

Obtains the response data including the status word of **SELECT Applet**.

**Since:** 10

**System capability:** SystemCapability.Communication.SecureElement

**Return value:**

| Type | Description |
| --- | --- |
| number[] | Response data including the status word obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |

**Examples**

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
import { omapi } from '@kit.ConnectivityKit';

let seChannel : omapi.Channel;

// Initialize seChannel before using it.
try {
    let response = seChannel.getSelectResponse();
    hilog.info(0x0000, 'testTag', 'response = %{public}s', JSON.stringify(response));
} catch (exception) {
    hilog.error(0x0000, 'testTag', 'getSelectResponse exception %{public}s', JSON.stringify(exception));
}
```

## getSession

```TypeScript
getSession(): Session
```

Obtains the session used to open this channel.

**Since:** 10

**System capability:** SystemCapability.Communication.SecureElement

**Return value:**

| Type | Description |
| --- | --- |
| [Session](arkts-connectivity-omapi-session-i.md) | Session instance obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |

**Examples**

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
import { omapi } from '@kit.ConnectivityKit';

let seSession : omapi.Session;
let seChannel : omapi.Channel;

// Initialize seChannel before using it.

try {
    seSession = seChannel.getSession();
} catch (exception) {
    hilog.error(0x0000, 'testTag', 'getSession exception %{public}s', JSON.stringify(exception));
}
```

## isBasicChannel

```TypeScript
isBasicChannel(): boolean
```

Checks whether this channel is a basic channel.

**Since:** 10

**System capability:** SystemCapability.Communication.SecureElement

**Return value:**

| Type | Description |
| --- | --- |
| boolean | **true** if the channel is a basic channel; **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |

**Examples**

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
import { omapi } from '@kit.ConnectivityKit';

let seChannel : omapi.Channel;

// Initialize seChannel before using it.
try {
    let isBasic = seChannel.isBasicChannel();
    hilog.info(0x0000, 'testTag', 'isBasic = %{public}s', JSON.stringify(isBasic));
} catch (exception) {
    hilog.error(0x0000, 'testTag', 'isBasicChannel exception %{public}s', JSON.stringify(exception));
}
```

## isClosed

```TypeScript
isClosed(): boolean
```

Checks whether this channel is closed.

**Since:** 10

**System capability:** SystemCapability.Communication.SecureElement

**Return value:**

| Type | Description |
| --- | --- |
| boolean | **true** if the channel is closed; **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |

**Examples**

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
import { omapi } from '@kit.ConnectivityKit';

let seChannel : omapi.Channel;

// Initialize seChannel before using it.
try {
    let isClosed = seChannel.isClosed();
    hilog.info(0x0000, 'testTag', 'isClosed = %{public}s', JSON.stringify(isClosed));
} catch (exception) {
    hilog.error(0x0000, 'testTag', 'isClosed exception %{public}s', JSON.stringify(exception));
}
```

## transmit

```TypeScript
transmit(command: number[]): Promise<number[]>
```

Transmits APDU data (as per ISO/IEC 7816) to the SE. This API uses a promise to return the result.

**Since:** 10

**System capability:** SystemCapability.Communication.SecureElement

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| command | number[] | Yes | APDU data to send. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number[]&gt; | Promise used to return the response received, in a number array. If the chip captures an exception, an all zero value is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [3300101](../errorcode-se.md#3300101-abnormal-se-service-status) | IllegalStateError, an attempt is made to use an SE session or channel that has been closed. |
| [3300103](../errorcode-se.md#3300103-failed-to-obtain-the-access-rule) | SecurityError, the command is filtered by the security policy. |
| [3300104](../errorcode-se.md#3300104-se-chip-io-exception) | IOError, there is a communication problem to the reader or the SE. |

**Examples**

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
import { omapi } from '@kit.ConnectivityKit';

let seChannel : omapi.Channel;

// Initialize seChannel before using it.
let cmdData = [0x01, 0x02, 0x03, 0x04]; // Set command data correctly.
try {
    seChannel.transmit(cmdData).then((response) => {
        // If the chip captures an exception, an all zero value is returned for response.
        hilog.info(0x0000, 'testTag', 'transmit response = %{public}s.', JSON.stringify(response));
    }).catch((error : BusinessError) => {
        hilog.error(0x0000, 'testTag', 'transmit error = %{public}s.', JSON.stringify(error));
    });
} catch (exception) {
    hilog.error(0x0000, 'testTag', 'transmit exception = %{public}s.', JSON.stringify(exception));
}
```

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
import { omapi } from '@kit.ConnectivityKit';

let seChannel : omapi.Channel;

// Initialize seChannel before using it.
let cmdData = [0x01, 0x02, 0x03, 0x04]; // Set command data correctly.
try {
    seChannel.transmit(cmdData, (error, response) => {
        if (error) {
            hilog.error(0x0000, 'testTag', 'transmit error %{public}s', JSON.stringify(error));
        } else {
            // If the chip captures an exception, an all zero value is returned for response.
            hilog.info(0x0000, 'testTag', 'transmit response = %{public}s.', JSON.stringify(response));
        }
    });
} catch (exception) {
    hilog.error(0x0000, 'testTag', 'transmit exception %{public}s', JSON.stringify(exception));
}
```

## transmit

```TypeScript
transmit(command: number[], callback: AsyncCallback<number[]>): void
```

Transmits APDU data (as per ISO/IEC 7816) to the SE. This API uses an asynchronous callback to return the result.

**Since:** 10

**System capability:** SystemCapability.Communication.SecureElement

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| command | number[] | Yes | APDU data to send. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number[]&gt; | Yes | Callback used to return the response received, in a number array. If the chip captures an exception, an all zero value is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [3300101](../errorcode-se.md#3300101-abnormal-se-service-status) | IllegalStateError, an attempt is made to use an SE session or channel that has been closed. |
| [3300103](../errorcode-se.md#3300103-failed-to-obtain-the-access-rule) | SecurityError, the command is filtered by the security policy. |
| [3300104](../errorcode-se.md#3300104-se-chip-io-exception) | IOError, there is a communication problem to the reader or the SE. |

**Examples**

See [transmit](#transmit)
