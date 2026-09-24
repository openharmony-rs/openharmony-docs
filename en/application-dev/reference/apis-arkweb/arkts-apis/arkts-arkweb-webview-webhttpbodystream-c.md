# WebHttpBodyStream

```TypeScript
class WebHttpBodyStream
```

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

**Examples**

For the complete sample code, see [initialize](#initialize).

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

**Examples**

For the complete sample code, see [initialize](#initialize).

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

**Examples**

```TypeScript
// xxx.ets
import { webview } from '@kit.ArkWeb';
import { BusinessError } from '@kit.BasicServicesKit';
import { buffer } from '@kit.ArkTS';

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController();
  schemeHandler: webview.WebSchemeHandler = new webview.WebSchemeHandler();
  htmlData: string = "<html><body bgcolor=\"white\">Source:<pre>source</pre></body></html>";

  build() {
    Column() {
      Button('postUrl')
        .onClick(() => {
          try {
            let postData = buffer.from(this.htmlData);
            this.controller.postUrl('https://www.example.com', postData.buffer);
          } catch (error) {
            console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
        })
      Web({ src: 'https://www.example.com', controller: this.controller })
        .onControllerAttached(() => {
          try {
            this.schemeHandler.onRequestStart((request: webview.WebSchemeHandlerRequest, resourceHandler: webview.WebResourceHandler) => {
              console.info("[schemeHandler] onRequestStart");
              try {
                let stream = request.getHttpBodyStream();
                if (stream) {
                  stream.initialize().then(() => {
                    if (!stream) {
                      return;
                    }
                    console.info("[schemeHandler] onRequestStart postDataStream size:" + stream.getSize());
                    console.info("[schemeHandler] onRequestStart postDataStream position:" + stream.getPosition());
                    console.info("[schemeHandler] onRequestStart postDataStream isChunked:" + stream.isChunked());
                    console.info("[schemeHandler] onRequestStart postDataStream isEof:" + stream.isEof());
                    console.info("[schemeHandler] onRequestStart postDataStream isInMemory:" + stream.isInMemory());
                    stream.read(stream.getSize()).then((buffer) => {
                      if (!stream) {
                        return;
                      }
                      console.info("[schemeHandler] onRequestStart postDataStream readlength:" + buffer.byteLength);
                      console.info("[schemeHandler] onRequestStart postDataStream isEof:" + stream.isEof());
                      console.info("[schemeHandler] onRequestStart postDataStream position:" + stream.getPosition());
                    }).catch((error: BusinessError) => {
                      console.error(`ErrorCode: ${error.code},  Message: ${error.message}`);
                    })
                  }).catch((error: BusinessError) => {
                    console.error(`ErrorCode: ${error.code},  Message: ${error.message}`);
                  })
                } else {
                  console.info("[schemeHandler] onRequestStart has no http body stream");
                }
              } catch (error) {
                console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
              }

              return false;
            })

            this.schemeHandler.onRequestStop((request: webview.WebSchemeHandlerRequest) => {
              console.info("[schemeHandler] onRequestStop");
            });

            this.controller.setWebSchemeHandler('https', this.schemeHandler);
          } catch (error) {
            console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
        })
        .javaScriptAccess(true)
        .domStorageAccess(true)
    }
  }
}
```

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

**Examples**

For the complete sample code, see [initialize](#initialize).

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

**Examples**

For the complete sample code, see [initialize](#initialize).

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

**Examples**

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

**Examples**

For the complete sample code, see [initialize](#initialize).
