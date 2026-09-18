# Session

A **Session** instance indicates a session created on an SE **Reader** instance. You can use [Reader.openSession](arkts-connectivity-omapi-reader-i.md#opensession) to obtain a **Session** instance.

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

Closes the session with the SE. All channels opened by this session will be closed.

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

let seSession : omapi.Session;

// Initialize seSession before using it.

try {
    seSession.close();
} catch (error) {
    hilog.error(0x0000, 'testTag', 'close error %{public}s', JSON.stringify(error));
}
```

## closeChannels

```TypeScript
closeChannels(): void
```

Closes all channels opened on this session.

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

let seSession : omapi.Session;

// Initialize seSession before using it.

try {
    seSession.closeChannels();
} catch (error) {
    hilog.error(0x0000, 'testTag', 'closeChannels error %{public}s', JSON.stringify(error));
}
```

## getATR

```TypeScript
getATR(): number[]
```

Obtains the Answer to Reset (ATR) of this SE. If the ATR of this SE is not available, an empty array will be returned.

**Since:** 10

**System capability:** SystemCapability.Communication.SecureElement

**Return value:**

| Type | Description |
| --- | --- |
| number[] | ATR if the SE has an available ATR; an empty array otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [3300101](../errorcode-se.md#3300101-abnormal-se-service-status) | IllegalStateError, service state exception. |

**Examples**

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
import { omapi } from '@kit.ConnectivityKit';

let seSession : omapi.Session;

// Initialize seSession before using it.

try {
    let atr = seSession.getATR();
    hilog.info(0x0000, 'testTag', 'atr %{public}s', JSON.stringify(atr));
} catch (error) {
    hilog.error(0x0000, 'testTag', 'getATR error %{public}s', JSON.stringify(error));
}
```

## getReader

```TypeScript
getReader(): Reader
```

Obtains the reader that provides this session.

**Since:** 10

**System capability:** SystemCapability.Communication.SecureElement

**Return value:**

| Type | Description |
| --- | --- |
| [Reader](arkts-connectivity-omapi-reader-i.md) | Reader instance obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |

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
        return;
    }
    try {
        let sessionReader = seSession.getReader();
    } catch (error) {
        hilog.error(0x0000, 'testTag', 'getReader error %{public}s', JSON.stringify(error));
    }
}
```

## isClosed

```TypeScript
isClosed(): boolean
```

Check if this session is closed.

**Since:** 10

**System capability:** SystemCapability.Communication.SecureElement

**Return value:**

| Type | Description |
| --- | --- |
| boolean | True if the session is closed, false otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |

**Examples**

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
import { omapi } from '@kit.ConnectivityKit';

let seSession : omapi.Session;

// Initialize seSession before using it.

try {
    let isClosed = seSession.isClosed();
    hilog.info(0x0000, 'testTag', 'isClosed %{public}s', JSON.stringify(isClosed));
} catch (error) {
    hilog.error(0x0000, 'testTag', 'isClosed error %{public}s', JSON.stringify(error));
}
```

## openBasicChannel

```TypeScript
openBasicChannel(aid: number[]): Promise<Channel>
```

Opens a basic channel, as defined in ISO/IEC 7816-4. If the SE cannot provide the basic channel or the application does not have the permission to access the SE, null is returned. This API uses a promise to return the result.

**Since:** 10

**System capability:** SystemCapability.Communication.SecureElement

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| aid | number[] | Yes | AID of the Applet to be selected on this channel as a byte array, or an empty array if no Applet is to be selected. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Channel](arkts-connectivity-omapi-channel-i.md)&gt; | Promise used to return the basic channel instance obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [3300101](../errorcode-se.md#3300101-abnormal-se-service-status) | IllegalStateError, an attempt is made to use an SE session that has been closed. |
| [3300102](../errorcode-se.md#3300102-failed-to-find-the-desired-se) | NoSuchElementError, the AID on the SE is not available or cannot be selected. |
| [3300103](../errorcode-se.md#3300103-failed-to-obtain-the-access-rule) | SecurityError, the calling application cannot be granted access to this AID or the default applet on this session. |
| [3300104](../errorcode-se.md#3300104-se-chip-io-exception) | IOError, there is a communication problem to the reader or the SE. |

**Examples**

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
import { omapi } from '@kit.ConnectivityKit';

let seSession : omapi.Session;
let seChannel : omapi.Channel;
let aidArray : number[] = [0xA0, 0x00, 0x00, 0x00, 0x03, 0x10, 0x10];

// Initialize seSession before using it.
function secureElementDemo() {
    try {
        // Set the AID of the application selected on the channel.
        seSession.openBasicChannel(aidArray).then((data) => {
            seChannel = data;
        }).catch((error : BusinessError) => {
            hilog.error(0x0000, 'testTag', 'openBasicChannel error %{public}s', JSON.stringify(error));
        });
    } catch (exception) {
        hilog.error(0x0000, 'testTag', 'openBasicChannel exception %{public}s', JSON.stringify(exception));
    }
    if (seChannel == undefined) {
        hilog.error(0x0000, 'testTag', 'seChannel invalid.');
        return;
    }
}
```

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
import { omapi } from '@kit.ConnectivityKit';

let seSession : omapi.Session;
let seChannel : omapi.Channel;
let aidArray : number[] = [0xA0, 0x00, 0x00, 0x00, 0x03, 0x10, 0x10];

// Initialize seSession before using it.
function secureElementDemo() {
    try {
        // Set the AID of the application selected on the channel.
        seSession.openBasicChannel(aidArray, (error, data) => {
            if (error) {
                hilog.error(0x0000, 'testTag', 'openBasicChannel error %{public}s', JSON.stringify(error));
            } else {
                seChannel = data;
            }
        });
    } catch (exception) {
        hilog.error(0x0000, 'testTag', 'openBasicChannel exception %{public}s', JSON.stringify(exception));
    }
    if (seChannel == undefined) {
        hilog.error(0x0000, 'testTag', 'seChannel invalid.');
        return;
    }
}
```

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
import { omapi } from '@kit.ConnectivityKit';

let seSession : omapi.Session;
let seChannel : omapi.Channel;
let aidArray : number[] = [0xA0, 0x00, 0x00, 0x00, 0x03, 0x10, 0x10];
let p2 : number = 0x00;

// Initialize seSession before using it.
function secureElementDemo() {
    try {
        // Set the AID of the application selected on the channel.
        seSession.openBasicChannel(aidArray, p2).then((data) => {
            seChannel = data;
        }).catch((error : BusinessError) => {
            hilog.error(0x0000, 'testTag', 'openBasicChannel error %{public}s', JSON.stringify(error));
        });
    } catch (exception) {
        hilog.error(0x0000, 'testTag', 'openBasicChannel exception %{public}s', JSON.stringify(exception));
    }
    if (seChannel == undefined) {
        hilog.error(0x0000, 'testTag', 'seChannel invalid.');
        return;
    }
}
```

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
import { omapi } from '@kit.ConnectivityKit';

let seSession : omapi.Session;
let seChannel : omapi.Channel;
let aidArray : number[] = [0xA0, 0x00, 0x00, 0x00, 0x03, 0x10, 0x10];
let p2 : number = 0x00;

// Initialize seSession before using it.
function secureElementDemo() {
    try {
        // Set the AID of the application selected on the channel.
        seSession.openBasicChannel(aidArray, p2, (error, data) => {
            if (error) {
                hilog.error(0x0000, 'testTag', 'openBasicChannel error %{public}s', JSON.stringify(error));
            } else {
                seChannel = data;
            }
        });
    } catch (exception) {
        hilog.error(0x0000, 'testTag', 'openBasicChannel exception %{public}s', JSON.stringify(exception));
    }
    if (seChannel == undefined) {
        hilog.error(0x0000, 'testTag', 'seChannel invalid.');
        return;
    }
}
```

## openBasicChannel

```TypeScript
openBasicChannel(aid: number[], callback: AsyncCallback<Channel>): void
```

Opens a basic channel, as defined in ISO/IEC 7816-4. If the SE cannot provide the basic channel or the application does not have the permission to access the SE, null is returned. This API uses an asynchronous callback to return the result.

**Since:** 10

**System capability:** SystemCapability.Communication.SecureElement

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| aid | number[] | Yes | AID of the Applet to be selected on this channel as a byte array, or an empty array if no Applet is to be selected. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[Channel](arkts-connectivity-omapi-channel-i.md)&gt; | Yes | Callback used to return the basic channel instance obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [3300101](../errorcode-se.md#3300101-abnormal-se-service-status) | IllegalStateError, an attempt is made to use an SE session that has been closed. |
| [3300102](../errorcode-se.md#3300102-failed-to-find-the-desired-se) | NoSuchElementError, the AID on the SE is not available or cannot be selected. |
| [3300103](../errorcode-se.md#3300103-failed-to-obtain-the-access-rule) | SecurityError, the calling application cannot be granted access to this AID or the default applet on this session. |
| [3300104](../errorcode-se.md#3300104-se-chip-io-exception) | IOError, there is a communication problem to the reader or the SE. |

**Examples**

See [openBasicChannel](#openbasicchannel)

## openBasicChannel

```TypeScript
openBasicChannel(aid: number[], p2: number): Promise<Channel>
```

Opens a basic channel, as defined in ISO/IEC 7816-4. If the SE cannot provide the basic channel or the application does not have the permission to access the SE, null is returned. This API uses a promise to return the result.

**Since:** 10

**System capability:** SystemCapability.Communication.SecureElement

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| aid | number[] | Yes | AID of the Applet to be selected on this channel as a byte array, or an empty array if no Applet is to be selected. |
| p2 | number | Yes | P2 parameter of the **SELECT APDU** command executed on this channel. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Channel](arkts-connectivity-omapi-channel-i.md)&gt; | Promise used to return the basic channel instance obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [3300101](../errorcode-se.md#3300101-abnormal-se-service-status) | IllegalStateError, an attempt is made to use an SE session that has been closed. |
| [3300102](../errorcode-se.md#3300102-failed-to-find-the-desired-se) | NoSuchElementError, the AID on the SE is not available or cannot be selected. |
| [3300103](../errorcode-se.md#3300103-failed-to-obtain-the-access-rule) | SecurityError, the calling application cannot be granted access to this AID or the default applet on this session. |
| [3300104](../errorcode-se.md#3300104-se-chip-io-exception) | IOError, there is a communication problem to the reader or the SE. |

**Examples**

See [openBasicChannel](#openbasicchannel)

## openBasicChannel

```TypeScript
openBasicChannel(aid: number[], p2: number, callback: AsyncCallback<Channel>): void
```

Opens a basic channel, as defined in ISO/IEC 7816-4. If the SE cannot provide the basic channel or the application does not have the permission to access the SE, null is returned. This API uses an asynchronous callback to return the result.

**Since:** 10

**System capability:** SystemCapability.Communication.SecureElement

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| aid | number[] | Yes | AID of the Applet to be selected on this channel as a byte array, or an empty array if no Applet is to be selected. |
| p2 | number | Yes | P2 parameter of the **SELECT APDU** command executed on this channel. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[Channel](arkts-connectivity-omapi-channel-i.md)&gt; | Yes | Callback used to return the basic channel instance obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [3300101](../errorcode-se.md#3300101-abnormal-se-service-status) | IllegalStateError, an attempt is made to use an SE session that has been closed. |
| [3300102](../errorcode-se.md#3300102-failed-to-find-the-desired-se) | NoSuchElementError, the AID on the SE is not available or cannot be selected. |
| [3300103](../errorcode-se.md#3300103-failed-to-obtain-the-access-rule) | SecurityError, the calling application cannot be granted access to this AID or the default applet on this session. |
| [3300104](../errorcode-se.md#3300104-se-chip-io-exception) | IOError, there is a communication problem to the reader or the SE. |

**Examples**

See [openBasicChannel](#openbasicchannel)

## openLogicalChannel

```TypeScript
openLogicalChannel(aid: number[]): Promise<Channel>
```

Opens a logical channel, as defined in ISO/IEC 7816-4. If the SE cannot provide the logical channel or the application does not have the permission to access the SE, null is returned. This API uses a promise to return the result.

**Since:** 10

**System capability:** SystemCapability.Communication.SecureElement

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| aid | number[] | Yes | AID of the Applet to be selected on this channel as a byte array, or an empty array if no Applet is to be selected. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Channel](arkts-connectivity-omapi-channel-i.md)&gt; | Promise used to return the logical channel instance obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [3300101](../errorcode-se.md#3300101-abnormal-se-service-status) | IllegalStateError, an attempt is made to use an SE session that has been closed. |
| [3300102](../errorcode-se.md#3300102-failed-to-find-the-desired-se) | NoSuchElementError, the AID on the SE is not available or cannot be selected or a logical channel is already open to a non-multi-selectable applet. |
| [3300103](../errorcode-se.md#3300103-failed-to-obtain-the-access-rule) | SecurityError, the calling application cannot be granted access to this AID or the default applet on this session. |
| [3300104](../errorcode-se.md#3300104-se-chip-io-exception) | IOError, there is a communication problem to the reader or the SE. |

**Examples**

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
import { omapi } from '@kit.ConnectivityKit';

let seSession : omapi.Session;
let seChannel : omapi.Channel;
let aidArray : number[] = [0xA0, 0x00, 0x00, 0x00, 0x03, 0x10, 0x10];

// Initialize seSession before using it.
function secureElementDemo() {
    try {
        // Set the AID of the application selected on the channel.
        seSession.openLogicalChannel(aidArray).then((data) => {
            seChannel = data;
        }).catch((error : BusinessError) => {
            hilog.error(0x0000, 'testTag', 'openLogicalChannel error %{public}s', JSON.stringify(error));
        });
    } catch (exception) {
        hilog.error(0x0000, 'testTag', 'openLogicalChannel exception %{public}s', JSON.stringify(exception));
    }
    if (seChannel == undefined) {
        hilog.error(0x0000, 'testTag', 'seChannel invalid.');
        return;
    }
}
```

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
import { omapi } from '@kit.ConnectivityKit';

let seSession : omapi.Session;
let seChannel : omapi.Channel;
let aidArray : number[] = [0xA0, 0x00, 0x00, 0x00, 0x03, 0x10, 0x10];

// Initialize seSession before using it.
function secureElementDemo() {
    try {
        // Set the AID of the application selected on the channel.
        seSession.openLogicalChannel(aidArray, (error, data) => {
            if (error) {
                hilog.error(0x0000, 'testTag', 'openLogicalChannel error %{public}s', JSON.stringify(error));
            } else {
                seChannel = data;
            }
        });
    } catch (exception) {
        hilog.error(0x0000, 'testTag', 'openLogicalChannel exception %{public}s', JSON.stringify(exception));
    }
    if (seChannel == undefined) {
        hilog.error(0x0000, 'testTag', 'seChannel invalid.');
        return;
    }
}
```

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
import { omapi } from '@kit.ConnectivityKit';

let seSession : omapi.Session;
let seChannel : omapi.Channel;
let aidArray : number[] = [0xA0, 0x00, 0x00, 0x00, 0x03, 0x10, 0x10];
let p2 : number = 0x00;

// Initialize seSession before using it.
function secureElementDemo() {
    try {
        // Set the AID of the application selected on the channel.
        seSession.openLogicalChannel(aidArray, p2).then((data) => {
            seChannel = data;
        }).catch((error : BusinessError) => {
            hilog.error(0x0000, 'testTag', 'openLogicalChannel error %{public}s', JSON.stringify(error));
        });
    } catch (exception) {
        hilog.error(0x0000, 'testTag', 'openLogicalChannel exception %{public}s', JSON.stringify(exception));
    }
    if (seChannel == undefined) {
        hilog.error(0x0000, 'testTag', 'seChannel invalid.');
        return;
    }
}
```

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
import { omapi } from '@kit.ConnectivityKit';

let seSession : omapi.Session;
let seChannel : omapi.Channel;
let aidArray : number[] = [0xA0, 0x00, 0x00, 0x00, 0x03, 0x10, 0x10];
let p2 : number = 0x00;

// Initialize seSession before using it.
function secureElementDemo() {
    try {
        // Change to the AID of the App selected on this channel.
        seSession.openLogicalChannel(aidArray, p2, (error, data) => {
            if (error) {
                hilog.error(0x0000, 'testTag', 'openLogicalChannel error %{public}s', JSON.stringify(error));
            } else {
                seChannel = data;
            }
        });
    } catch (exception) {
        hilog.error(0x0000, 'testTag', 'openLogicalChannel exception %{public}s', JSON.stringify(exception));
    }
    if (seChannel == undefined) {
        hilog.error(0x0000, 'testTag', 'seChannel invalid.');
        return;
    }
}
```

## openLogicalChannel

```TypeScript
openLogicalChannel(aid: number[], callback: AsyncCallback<Channel>): void
```

Opens a logical channel, as defined in ISO/IEC 7816-4. If the SE cannot provide the logical channel or the application does not have the permission to access the SE, null is returned. This API uses an asynchronous callback to return the result.

**Since:** 10

**System capability:** SystemCapability.Communication.SecureElement

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| aid | number[] | Yes | AID of the Applet to be selected on this channel as a byte array, or an empty array if no Applet is to be selected. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[Channel](arkts-connectivity-omapi-channel-i.md)&gt; | Yes | Callback used to return the logical channel instance obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [3300101](../errorcode-se.md#3300101-abnormal-se-service-status) | IllegalStateError, an attempt is made to use an SE session that has been closed. |
| [3300102](../errorcode-se.md#3300102-failed-to-find-the-desired-se) | NoSuchElementError, the AID on the SE is not available or cannot be selected or a logical channel is already open to a non-multi-selectable applet. |
| [3300103](../errorcode-se.md#3300103-failed-to-obtain-the-access-rule) | SecurityError, the calling application cannot be granted access to this AID or the default applet on this session. |
| [3300104](../errorcode-se.md#3300104-se-chip-io-exception) | IOError, there is a communication problem to the reader or the SE. |

**Examples**

See [openLogicalChannel](#openlogicalchannel)

## openLogicalChannel

```TypeScript
openLogicalChannel(aid: number[], p2: number): Promise<Channel>
```

Opens a logical channel, as defined in ISO/IEC 7816-4. If the SE cannot provide the logical channel or the application does not have the permission to access the SE, null is returned. This API uses a promise to return the result.

**Since:** 10

**System capability:** SystemCapability.Communication.SecureElement

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| aid | number[] | Yes | AID of the Applet to be selected on this channel as a byte array, or an empty array if no Applet is to be selected. |
| p2 | number | Yes | P2 parameter of the **SELECT APDU** command executed on this channel. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Channel](arkts-connectivity-omapi-channel-i.md)&gt; | Promise used to return the logical channel instance obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [3300101](../errorcode-se.md#3300101-abnormal-se-service-status) | IllegalStateError, an attempt is made to use an SE session that has been closed. |
| [3300102](../errorcode-se.md#3300102-failed-to-find-the-desired-se) | NoSuchElementError, the AID on the SE is not available or cannot be selected or a logical channel is already open to a non-multi-selectable applet. |
| [3300103](../errorcode-se.md#3300103-failed-to-obtain-the-access-rule) | SecurityError, the calling application cannot be granted access to this AID or the default applet on this session. |
| [3300104](../errorcode-se.md#3300104-se-chip-io-exception) | IOError, there is a communication problem to the reader or the SE. |

**Examples**

See [openLogicalChannel](#openlogicalchannel)

## openLogicalChannel

```TypeScript
openLogicalChannel(aid: number[], p2: number, callback: AsyncCallback<Channel>): void
```

Opens a logical channel, as defined in ISO/IEC 7816-4. If the SE cannot provide the logical channel or the application does not have the permission to access the SE, null is returned. This API uses an asynchronous callback to return the result.

**Since:** 10

**System capability:** SystemCapability.Communication.SecureElement

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| aid | number[] | Yes | AID of the Applet to be selected on this channel as a byte array, or an empty array if no Applet is to be selected. |
| p2 | number | Yes | P2 parameter of the **SELECT APDU** command executed on this channel. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[Channel](arkts-connectivity-omapi-channel-i.md)&gt; | Yes | Callback used to return the logical channel instance obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [3300101](../errorcode-se.md#3300101-abnormal-se-service-status) | IllegalStateError, an attempt is made to use an SE session that has been closed. |
| [3300102](../errorcode-se.md#3300102-failed-to-find-the-desired-se) | NoSuchElementError, the AID on the SE is not available or cannot be selected or a logical channel is already open to a non-multi-selectable applet. |
| [3300103](../errorcode-se.md#3300103-failed-to-obtain-the-access-rule) | SecurityError, the calling application cannot be granted access to this AID or the default applet on this session. |
| [3300104](../errorcode-se.md#3300104-se-chip-io-exception) | IOError, there is a communication problem to the reader or the SE. |

**Examples**

See [openLogicalChannel](#openlogicalchannel)
