# WebHttpBodyStream

WebHttpBodyStream is an HTTP request body data stream object used to read the request body data of POST, PUT, and other requests in custom scheme interception scenarios. This object is obtained through the getHttpBodyStream method of WebSchemeHandlerRequest and supports data of the BYTES, FILE, BLOB, and CHUNKED types. Developers can use this API to read uplink data in a custom protocol interceptor, enabling inspection or forwarding of the request body. Note: Other APIs in this class can be called only after [initialize](#initialize) succeeds.

WebHttpBodyStream works in conjunction with [WebSchemeHandlerRequest](arkts-arkweb-webview-webschemehandlerrequest-c.md): WebSchemeHandlerRequest represents the intercepted request, and WebHttpBodyStream represents the HTTP body data stream of that request. By reading data from the stream, developers can obtain the complete request body content.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## Modules to Import

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## getPosition

```TypeScript
getPosition(): number
```

Reads the current read position in this **WebHttpBodyStream** instance.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| number | Current read position in WebHttpBodyStream. Unit: Byte. |

## getSize

```TypeScript
getSize(): number
```

Obtains the size of data in this **WebHttpBodyStream** instance. This API always returns zero when chunked transfer is used.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| number | Data size of the WebHttpBodyStream, in bytes. |

## initialize

```TypeScript
initialize(): Promise<void>
```

Initializes this **WebHttpBodyStream** instance.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100022](../errorcode-webview.md#17100022-failed-to-initialize-webhttpbodystream) | Failed to initialize the HTTP body stream. |

## isChunked

```TypeScript
isChunked(): boolean
```

Checks whether this **WebHttpBodyStream** instance is transmitted by chunk.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the **WebHttpBodyStream** instance is transmitted by chunk. The value **true** indicates that the **WebHttpBodyStream** instance is transmitted by chunk, and **false** indicates the opposite. |

## isEof

```TypeScript
isEof(): boolean
```

Checks whether all data in this **WebHttpBodyStream** instance has been read.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether all data in the **WebHttpBodyStream** instance has been read.<br>This API returns **true** if all data in the **WebHttpBodyStream** instance is read. It returns **false** before the first read attempt is made for the **WebHttpBodyStream** instance that uses chunked transfer. |

## isInMemory

```TypeScript
isInMemory(): boolean
```

Checks whether the uploaded data in this **WebHttpBodyStream** instance is in memory.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the uploaded data in the **WebHttpBodyStream** instance is stored in memory.<br>This API returns **true** if all the upload data in the **WebHttpBodyStream** instance is in memory and all read requests will be completed synchronously. **false** is returned if the data is chunked. |

## read

```TypeScript
read(size: number): Promise<ArrayBuffer>
```

Reads data from this **WebHttpBodyStream** instance.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| size | number | Yes | Number of bytes to read from the WebHttpBodyStream. Unit: byte. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;ArrayBuffer&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
