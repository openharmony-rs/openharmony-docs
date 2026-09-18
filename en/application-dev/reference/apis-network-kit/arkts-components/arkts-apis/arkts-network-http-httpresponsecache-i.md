# HttpResponseCache

Defines an object that stores the response to an HTTP request. Before invoking APIs provided by **HttpResponseCache**, you must call [createHttpResponseCache()](arkts-network-http-createhttpresponsecache-f.md) to create an **HttpRequestTask** object.

**Usage of Keywords in the Response Header**  
- **`Cache-Control`**: specifies the cache policy, for example, `no-cache`, `no-store`, `max-age`, `public`, or  
`private`.  
- **`Expires`**: specifies the expiration time of a resource. The value is in the GMT format.  
- **`ETag`**: identifies the resource version. The client can use the `If-None-Match` request header to check  
whether the resource has been modified.  
- **`Last-Modified`**: specifies the last modification time of a resource. The client can use the  
`If-Modified-Since` request header to check whether a resource has been modified.  
- **`Vary`**: specifies the parts of the request header that affect the cached response. This field is used to  
distinguish different cache versions.

When using these keywords, ensure that the response header is correctly configured on the server. The client determines whether to use the cached resource and how to verify whether the resource is the latest based on the response header. Correct cache policies help to improve application performance and user experience.

**How to Set the Cache-Control Header** `Cache-Control` is a common header, but it is usually used on the server. It allows you to define when, how, and how long a response should be cached. The following are some common `Cache-Control` directives:

- **`no-cache`**: indicates that the response can be stored in the cache, but it must be verified with the origin  
server before each reuse. If the resource remains unchanged, the response status code is 304 (Not Modified). In this case, the resource content is not sent, and the resource in the cache is used. If the resource has expired, the response status code is 200 and the resource content is sent.  
- `no-store`: indicates that resources cannot be cached. Resources must be obtained from the server for each  
request.  
- `max-age`: specifies the maximum cache duration, in seconds. For example, `Cache-Control: max-age=3600` indicates  
that the valid cache duration is 3,600 seconds (that is, 1 hour).  
- `public`: indicates that the response can be cached by any object, for example, the client that sends the request  
or the proxy server.  
- `private`: indicates that the response can be cached only by a single user and cannot be used as a shared cache (  
that is, the response cannot be cached by the proxy server).  
- `must-revalidate`: indicates that a resource must be revalidated with the origin server once it has become  
stable.  
- **`no-transform`**: indicates that the proxy server is not allowed to modify the response content.  
- **`proxy-revalidate`**: works in a way similar to `must-revalidate`, but applies only to shared caches.  
- **`s-maxage`**: works in a way similar to `max-age`, but applies only to shared caches.

**Since:** 9

**System capability:** SystemCapability.Communication.NetStack

## Modules to Import

```TypeScript
import { http } from '@kit.NetworkKit';
```

## delete

```TypeScript
delete(callback: AsyncCallback<void>): void
```

Disables the cache and deletes the data in it. This API uses an asynchronous callback to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object. |

**Examples**

```TypeScript
### delete

delete(callback: AsyncCallback<void>): void

Disables the cache and deletes the data in it. This API uses an asynchronous callback to return the result.

Atomic service API: This API can be used in atomic services since API version 11.

System capability: SystemCapability.Communication.NetStack

Parameters
```

```TypeScript
### delete

delete(): Promise<void>

Disables the cache and deletes the data in it. This API uses a promise to return the result.

Atomic service API: This API can be used in atomic services since API version 11.

System capability: SystemCapability.Communication.NetStack

Return value
```

```TypeScript
### delete

delete(): Promise<void>

Disables the cache and deletes the data in it. This API uses a promise to return the result.

Atomic service API: This API can be used in atomic services since API version 11.

System capability: SystemCapability.Communication.NetStack

Return value

Defines HTTP request context data. The object instance is passed as a parameter in the [interceptorHandle](arkts-network-http-httpinterceptor-i.md#interceptorhandle) method of the interceptor. You can use this object to obtain and modify the information about the HTTP request.

Atomic service API: This API can be used in atomic services since API version 22.

System capability: SystemCapability.Communication.NetStack

Defines the HTTP interceptor API, which is used to define the interception processing function.

Atomic service API: This API can be used in atomic services since API version 22.

System capability: SystemCapability.Communication.NetStack

### Attributes
```

## delete

```TypeScript
delete(): Promise<void>
```

Disables the cache and deletes the data in it. This API uses a promise to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

See [delete](#delete)

## flush

```TypeScript
flush(callback: AsyncCallback<void>): void
```

Flushes data in the cache to the file system so that the cached data can be accessed in the next HTTP request. This API uses an asynchronous callback to return the result. Cached data includes the response header (header), response body (result), cookies, request time (requestTime), and response time (responseTime).

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**Examples**

```TypeScript
### flush

flush(callback: AsyncCallback<void>): void

Flushes data in the cache to the file system so that the cached data can be accessed in the next HTTP request. This API uses an asynchronous callback to return the result. Cached data includes the response header (header), response body (result), cookies, request time (requestTime), and response time (responseTime).

Atomic service API: This API can be used in atomic services since API version 11.

System capability: SystemCapability.Communication.NetStack

Parameters
```

```TypeScript
### flush

flush(): Promise<void>

Flushes data in the cache to the file system so that the cached data can be accessed in the next HTTP request. This API uses a promise to return the result.

Atomic service API: This API can be used in atomic services since API version 11.

System capability: SystemCapability.Communication.NetStack

Return value
```

## flush

```TypeScript
flush(): Promise<void>
```

Flushes data in the cache to the file system so that the cached data can be accessed in the next HTTP request. This API uses a promise to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

See [flush](#flush)
