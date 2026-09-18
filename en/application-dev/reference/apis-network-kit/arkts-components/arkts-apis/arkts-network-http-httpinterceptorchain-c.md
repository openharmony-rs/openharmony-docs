# HttpInterceptorChain

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

```TypeScript
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

```TypeScript
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

```TypeScript
### getChain

getChain(): HttpInterceptor[]

Obtains all interceptor instances in the current interceptor chain.

Atomic service API: This API can be used in atomic services since API version 22.

System capability: SystemCapability.Communication.NetStack

Return value
```
