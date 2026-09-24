# HttpInterceptorChain

```TypeScript
export class HttpInterceptorChain
```

Defines HTTP interceptor chain.

**Since:** 22

**System capability:** SystemCapability.Communication.NetStack

## Modules to Import

```TypeScript
import { http } from '@kit.NetworkKit';
```

## addChain

```TypeScript
public addChain(chain: HttpInterceptor[]): boolean
```

Adds an interceptor to the HTTP client.

> **NOTE:** 
> 
> An interceptor chain cannot contain interceptor instances of the same type. If interceptors of the same type
> are passed in, the error code **2300802** (Duplicated interceptor type in the chain) is reported.

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| chain | [HttpInterceptor](arkts-network-http-httpinterceptor-i.md)[] | Yes | Interception chain composed of interceptor instances. A single interceptor or multiple interceptors of different types can be passed in. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the interceptor is added successfully. The value **true** indicates that the interceptor is successfully added, and the value **false** indicates the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 2300801 | Parameter type not supported by the interceptor. |
| 2300802 | Duplicated interceptor type in the chain. |
| [2300999](../errorcode-net-http.md#2300999-internal-error) | Internal error. |

**Examples**

### addChain

addChain(chain: HttpInterceptor[]): boolean

Adds an interceptor to the HTTP client.

> NOTE
> 
> An interceptor chain cannot contain interceptor instances of the same type. If interceptors of the same type are passed in, the error code 2300802 (Duplicated interceptor type in the chain) is reported.

Atomic service API: This API can be used in atomic services since API version 22.

System capability: SystemCapability.Communication.NetStack

Parameters

Return value

Error codes

For details about the error codes, see [Common Error Codes](../../errorcode-universal.md) and [HTTP Error Codes](../errorcode-net-http.md).The HTTP error code mapping is in the format of 2300000 + Curl error code. For more common error codes, see [Curl Error Codes](https://curl.se/libcurl/c/libcurl-errors.html).

```TypeScript
import { http } from '@kit.NetworkKit';

// Create an authentication interceptor.
class AuthInterceptor implements http.HttpInterceptor {
  interceptorType: http.InterceptorType = http.InterceptorType.INITIAL_REQUEST;

  async interceptorHandle(reqContext: http.HttpRequestContext, rspContext: http.HttpResponse): Promise<http.ChainContinue> {
    // Add the authentication header in the initial request phase.
    reqContext.header['Authorization'] = 'Bearer token';
    console.info('Interceptor: Added authorization header');
    return true; // Continue to process the interceptor chain.
  }
}

class LoggingInterceptor implements http.HttpInterceptor {
  interceptorType: http.InterceptorType = http.InterceptorType.FINAL_RESPONSE;

  async interceptorHandle(reqContext: http.HttpRequestContext, rspContext: http.HttpResponse): Promise<http.ChainContinue> {
    // Record logs in the final response phase.
    console.info(`LoggingInterceptor: Request to ${reqContext.url} completed with status ${rspContext.responseCode}`);
    return true; // Continue to process the interceptor chain.
  }
}

// Create an interceptor chain and apply the interceptor chain to the request.
let interceptorChain = new http.HttpInterceptorChain();
let authInterceptor = new AuthInterceptor();
let loggingInterceptor = new LoggingInterceptor();

// Add the interceptor to the chain.
try {
  let success = interceptorChain.addChain([authInterceptor, loggingInterceptor]);
  if (!success) {
    console.error('Failed to add interceptor chain');
  }
} catch (e) {
  console.error(`Interceptor chain add failed: code=${e.code}, message=${e.message}`);
}
```

## apply

```TypeScript
public apply(httpRequest: HttpRequest): boolean
```

Adds an interceptor chain to the target HTTP request. Each HTTP request instance can have only one interceptor chain attached.

> **NOTE:** 
> 
> After an interceptor chain is attached to an [HttpRequest](arkts-network-http-httprequest-i.md) instance, when the instance
> initiates an HTTP request, interceptors of the corresponding type in the attached interceptor chain are
> triggered.

> For more information about how to trigger interceptors using HTTP requests, see
> [HTTP Interceptor Function Code Example](../../../network/http-request.md#http-interceptor).

> The HTTP interceptor feature is supported only by
> [HttpRequest.request](arkts-network-http-httprequest-i.md#request) APIs,
> and is not supported by
> [HttpRequest.requestInStream](arkts-network-http-httprequest-i.md#requestinstream)
> APIs (streaming transmission).

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| httpRequest | [HttpRequest](arkts-network-http-httprequest-i.md) | Yes | [HttpRequest](arkts-network-http-httprequest-i.md) that initiates an HTTP request. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the interceptor is attached successfully. The value **true** indicates that the interceptor is successfully added, and the value **false** indicates the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 2300801 | Parameter type not supported by the interceptor. |
| [2300999](../errorcode-net-http.md#2300999-internal-error) | Internal error. |

**Examples**

### apply

apply(httpRequest: HttpRequest): boolean

Adds an interceptor chain to the target HTTP request. Each HTTP request instance can have only one interceptor chain attached.

> NOTE
> 
> After an interceptor chain is attached to an HttpRequest instance, when the instance initiates an HTTP request, interceptors of the corresponding type in the attached interceptor chain are triggered.For more information about how to trigger interceptors using HTTP requests, see [HTTP Interceptor Function Code Example](../../../network/http-request.md#http-interceptor).The HTTP interceptor feature is supported only by HttpRequest.request APIs, and is not supported by [HttpRequest.requestInStream](arkts-network-http-httprequest-i.md#requestinstream) APIs (streaming transmission).

Atomic service API: This API can be used in atomic services since API version 22.

System capability: SystemCapability.Communication.NetStack

Parameters

Return value

Error codes

For details about the error codes, see [Common Error Codes](../../errorcode-universal.md) and [HTTP Error Codes](../errorcode-net-http.md).The HTTP error code mapping is in the format of 2300000 + Curl error code. For more common error codes, see [Curl Error Codes](https://curl.se/libcurl/c/libcurl-errors.html).

```TypeScript
import { http } from '@kit.NetworkKit';

// Create an authentication interceptor.
class AuthInterceptor implements http.HttpInterceptor {
  interceptorType: http.InterceptorType = http.InterceptorType.INITIAL_REQUEST;

  async interceptorHandle(reqContext: http.HttpRequestContext, rspContext: http.HttpResponse): Promise<http.ChainContinue> {
    // Add the authentication header in the initial request phase.
    reqContext.header['Authorization'] = 'Bearer token';
    console.info('Interceptor: Added authorization header');
    return true; // Continue to process the interceptor chain.
  }
}

class LoggingInterceptor implements http.HttpInterceptor {
  interceptorType: http.InterceptorType = http.InterceptorType.FINAL_RESPONSE;

  async interceptorHandle(reqContext: http.HttpRequestContext, rspContext: http.HttpResponse): Promise<http.ChainContinue> {
    // Record logs in the final response phase.
    console.info(`LoggingInterceptor: Request to ${reqContext.url} completed with status ${rspContext.responseCode}`);
    return true; // Continue to process the interceptor chain.
  }
}

// Create an interceptor chain.
let interceptorChain = new http.HttpInterceptorChain();
let authInterceptor = new AuthInterceptor();
let loggingInterceptor = new LoggingInterceptor();

// Create an HTTP request.
let httpRequest = http.createHttp();

try {
  // Add the interceptor to the chain.
  let success = interceptorChain.addChain([authInterceptor, loggingInterceptor]);
  if (!success) {
    console.error('Failed to add interceptor chain');
  }

  // Apply the interceptor chain to the HTTP request.
  let applySuccess = interceptorChain.apply(httpRequest);
  if (!applySuccess) {
    console.error('Failed to apply interceptor chain');
  }
} catch (e) {
  console.error(`Interceptor chain add failed: code=${e.code}, message=${e.message}`);
}

// Initiate an HTTP request. If interception is required, the request can be initiated only through the request API.
httpRequest.request("EXAMPLE_URL", {
  method: http.RequestMethod.GET,
  header: { 'Content-Type': 'application/json' }
}, (err: Error, data: http.HttpResponse) => {
  if (!err) {
    console.info('Request completed with response code: ' + data.responseCode);
  } else {
    console.error('Request failed: ' + JSON.stringify(err));
  }
  httpRequest.destroy();
});
```

## getChain

```TypeScript
public getChain(): HttpInterceptor[]
```

Obtains all interceptor instances in the current interceptor chain.

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Communication.NetStack

**Return value:**

| Type | Description |
| --- | --- |
| [HttpInterceptor](arkts-network-http-httpinterceptor-i.md)[] | Returns all interceptor instances added by the [addChain](#addchain) method. |

**Examples**

### getChain

getChain(): HttpInterceptor[]

Obtains all interceptor instances in the current interceptor chain.

Atomic service API: This API can be used in atomic services since API version 22.

System capability: SystemCapability.Communication.NetStack

Return value

```TypeScript
import { http } from '@kit.NetworkKit';

// Create a custom interceptor.
class CustomInterceptor implements http.HttpInterceptor {
  interceptorType: http.InterceptorType = http.InterceptorType.INITIAL_REQUEST;

  async interceptorHandle(reqContext: http.HttpRequestContext, rspContext: http.HttpResponse): Promise<http.ChainContinue> {
    // Add the authentication header in the initial request phase.
    reqContext.header['Authorization'] = 'Bearer token';
    console.info('Interceptor: Added authorization header');
    return true; // Continue to process the interceptor chain.
  }
}

// Create an interceptor chain and apply the interceptor chain to the request.
let interceptorChain = new http.HttpInterceptorChain();
let customInterceptor = new CustomInterceptor();

// Add the interceptor to the chain.
try {
  let success = interceptorChain.addChain([customInterceptor]);
  if (!success) {
    console.error('Failed to add interceptor chain');
  }
} catch (e) {
  console.error(`Interceptor chain add failed: code=${e.code}, message=${e.message}`);
}

// Obtain all interceptors in the current interceptor chain.
let chain = interceptorChain.getChain();
console.info(`Current interceptor chain has ${chain.length} interceptors`);
```
