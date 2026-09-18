# setAppHttpProxy

## Modules to Import

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## setAppHttpProxy

```TypeScript
function setAppHttpProxy(httpProxy: HttpProxy): void
```

Sets the application-level HTTP proxy configuration.

> **NOTE:** 
> 
> If you want to use the proxy information configured by this API, set **usingProxy** in
> [HttpRequestOptions](arkts-network-http-httprequestoptions-i.md) to **true** to enable proxy forwarding. This
> API is used only for configuring proxy rules. It does not verify the validity of the proxy service.

**Since:** 11

**System capability:** SystemCapability.Communication.NetManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| httpProxy | [HttpProxy](arkts-network-connection-httpproxy-i.md) | Yes | Application-level HTTP proxy configuration. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| [2100001](../errorcode-net-connection.md#2100001-invalid-parameter-value) | Invalid http proxy. |

**Examples**

```TypeScript
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { http } from '@kit.NetworkKit';

let exclusionStr = "192.168,baidu.com";
let exclusionArray = exclusionStr.split(',');
connection.setAppHttpProxy({
  host: "192.168.xx.xxx",
  port: 8080,
  exclusionList: exclusionArray
} as connection.HttpProxy);
let httpRequest = http.createHttp();
let options: http.HttpRequestOptions = {
  usingProxy: true, // This field specifies whether to use the network proxy. It is supported since API version 10.
};
// Initiate an HTTP request.
httpRequest.request("EXAMPLE_URL", options, (err: BusinessError, data: http.HttpResponse) => {
  if (!err) {
   console.info(`Result: ${data.result}`);
   console.info(`code: ${data.responseCode}`);
   console.info(`type: ${JSON.stringify(data.resultType)}`);
   console.info(`header: ${JSON.stringify(data.header)}`);
   console.info(`cookies: ${data.cookies}`); // Cookies are supported since API version 8.
  } else {
   console.error(`error: ${JSON.stringify(err)}`);
  }
});
```
