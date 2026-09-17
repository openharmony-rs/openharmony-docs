# createHttpResponseCache

## Modules to Import

```TypeScript
import { http } from '@kit.NetworkKit';
```

## createHttpResponseCache

```TypeScript
function createHttpResponseCache(cacheSize?: number): HttpResponseCache
```

Creates an **HttpResponseCache** object that stores the response data of HTTP requests. You can call [flush](arkts-network-http-httpresponsecache-i.md#flush) and [delete](arkts-network-http-httpresponsecache-i.md#delete) in the object.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| cacheSize | number | No | Cache size. The maximum value is 10*1024*1024 (10 MB). The maximum value is used by default. |

**Return value:**

| Type | Description |
| --- | --- |
| [HttpResponseCache](arkts-network-http-httpresponsecache-i.md) | Object that stores the response to the HTTP request. |

**Examples**

```TypeScript
createHttpResponseCache(cacheSize?: number): HttpResponseCache

Creates an HttpResponseCache object that stores the response data of HTTP requests. You can call flush and delete in the object.

Atomic service API: This API can be used in atomic services since API version 11.

System capability: SystemCapability.Communication.NetStack

Parameters

Return value
```

```TypeScript
createHttpResponseCache(cacheSize?: number): HttpResponseCache

Creates an HttpResponseCache object that stores the response data of HTTP requests. You can call flush and delete in the object.

Atomic service API: This API can be used in atomic services since API version 11.

System capability: SystemCapability.Communication.NetStack

Parameters

Return value

Defines an object that stores the response to an HTTP request. Before invoking APIs provided by HttpResponseCache, you must call createHttpResponseCache() to create an HttpRequestTask object.

Usage of Keywords in the Response Header

: specifies the cache policy, for example, , , , , or .

: specifies the expiration time of a resource. The value is in the GMT format.

: identifies the resource version. The client can use the  request header to check whether the resource has been modified.

: specifies the last modification time of a resource. The client can use the  request header to check whether a resource has been modified.

: specifies the parts of the request header that affect the cached response. This field is used to distinguish different cache versions.

When using these keywords, ensure that the response header is correctly configured on the server. The client determines whether to use the cached resource and how to verify whether the resource is the latest based on the response header. Correct cache policies help to improve application performance and user experience.

How to Set the Cache-Control Header

is a common header, but it is usually used on the server. It allows you to define when, how, and how long a response should be cached. The following are some common  directives:

: indicates that the response can be stored in the cache, but it must be verified with the origin server before each reuse. If the resource remains unchanged, the response status code is 304 (Not Modified). In this case, the resource content is not sent, and the resource in the cache is used. If the resource has expired, the response status code is 200 and the resource content is sent.

: indicates that resources cannot be cached. Resources must be obtained from the server for each request.

: specifies the maximum cache duration, in seconds. For example,  indicates that the valid cache duration is 3,600 seconds (that is, 1 hour).

: indicates that the response can be cached by any object, for example, the client that sends the request or the proxy server.

: indicates that the response can be cached only by a single user and cannot be used as a shared cache (that is, the response cannot be cached by the proxy server).

: indicates that a resource must be revalidated with the origin server once it has become stable.

: indicates that the proxy server is not allowed to modify the response content.

: works in a way similar to , but applies only to shared caches.

: works in a way similar to , but applies only to shared caches.
```
